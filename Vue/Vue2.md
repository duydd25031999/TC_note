# Vue instance

- 1 Vue instance = tree của Virtual DOM

```  
Tree => object JS => Node  
Document  
	Body                       =>  Event Bus  
		Header 
			Title    
			Navigation  
		Main  
		Footer  
Data (state) => tree => update DOM thật  
<form> => submit = gửi API =response=> HTML   
```

# Lifecycle

- Lifecycle là quá trình từ lúc Component được khởi tạo, nhúng vào DOM, xóa khỏi DOM  
- Hook là nhưng function chèn custom logic vào các giai đoạn của Lifecycle  
  - Hook chạy bất đồng bộ (async) nên nó chỉ được gọi xong chạy tiếp code tiếp theo mà không cần phải đợi hoàn thành  
  - Lifecycle chỉ gọi chứ không đợi (await) hook  
  - Phase tiếp theo có thể chạy mà không bị block bởi hook  
- Lifecycle của Vue Component gồm 4 giai đoạn (phase)  
1. Creation  
- Khởi tạo Component  
- Tạo instance của component trong quá trình runtime JS  
- Diễn ra trước khi nhúng vào DOM  
- Tạo composition api của component: data, props, computed, watch, method  
- (Nuxt) khởi tạo ở server side  
1. beforeCreate:  
- Chạy trước khi component được khởi tạo instance  
- (Optional) khởi tạo observer cho data, chứ chưa gán initial value => undefined  
2. created:  
- Hoàn thành khởi tạo (Composition Api) data và methods của component  
- Do đó có thể bắt đầu update data, call method => gọi api để lấy data từ bây giờ cũng được  
2. Mounting  
- Bắt đầu nhúng component đó vào DOM  
- Render component lần đầu tiên  
1. beforeMount’  
- Trước khi render lần đầu  
2. mounted  
- Sau khi component nhúng vào DOM và render lần đầu  
- Có thể truy cập các thông số HTML (thông qua this.$el) như kích thước, tọa độ, các giá trị css khác  
- Có thể lấy được giá trị của $ref trong <template> 
3. Updating  
- Khi phát hiện sự thay đổi của dữ liệu như data, prop, inject, vuex state thì component trigger cập nhật giao diện theo sự thay đổi đó.  
- (Cá nhân) Chuyên dùng để cập nhật dữ liệu sau khi thay đổi giao diện  
  - Chức năng kéo / thả, di chuyển trên màn hình  
  - Chart  
  - Draw canva  
1. beforeUpdate  
- Ngay sau khi xác định data hoặc props thay đổi  
- Ngay trước khi component re-render lại  
2. updated  
- Sau khi cập nhật re-render thay đổi  
4. Destruction (Unmounting)  
- Khi component được hủy và loại khỏi DOM  
- Thường sử dụng trong các mục đích  
  - Dọn dẹp, unsubscribe (socket, interval)  
  - Tự động gửi phân tích, lưu form  
1. beforeDestroy  
- Gọi trước khi destroy  
2. destroyed  
- sau khi component được hủy và loại khỏi DOM  
- Data và method đã bị hủy nên không dùng lại được

# Directive

- Attribute của element thuộc về vue  
  - Attribute “v-”: v-if, v-show, v-for, …  
- V-show = display: none | bình thường  
- V-if = xóa khỏi DOM  
- v-for [1, 2, …, 1000] => Sửa 900 => element ứng với 900 update => những thằng còn lại không sao cả  
  - Key: (primary key của DB) = Unique  
  - Nó ứng với 1 cái khóa độc nhất với từng item trong array của v-for  
  - Khi list thêm | sửa | xóa 1 item => sẽ chỉ cần tác động tới element tương ứng với item đó mà không phải render lại cả list  
  - Tối ưu performance cho app  
  - (Lưu ý) không nên gán key với index  
    - Vue tối ưu bằng cách đối chiếu key với item thay đổi  
    - Khi xóa 1 item trong array không phải phần từ cuối   
      - thay đổi index của 1 loạt item   
      - thay đổi key của 1 loạt item  
      - re-render lại 1 loại item

Props

- Truyền dữ liệu từ component parent => child theo 1 cấp  
- Props của vue có những option để cài đặt phù hợp với yêu cầu  
- type: để xác định data type  
- required: để bắt buộc truyền giá trị vào props = false  
- default: giá trị default cho props  
- validator: hàm để validate giá trị truyền vào (ít dùng)  
  - Email   
  - Phone

# $emit

- $emit là 1 property để trigger 1 event của component đó  
- Dùng để tạo custom event cho 1 component  
- Component cha lắng nghe custom event đó directive v-on  
  - HTML element event: click, mouse up, mouse down, mouse hover, … (default)

``` 
$emit(‘tên-event’, payload-data)

@ten-event=’onTenEvent’

Function onTenEven (payload-data) {}  
```

# Event Bus

- Là 1 đối tượng dùng để truyền event mà không cần quan tâm mối quan hệ giữa các component  
  - (Ví dụ): tạo component thông báo (Toast) dùng cho toàn hệ thống  
  - Toast lắng nghe event “toast-notify” với Event bus  
  - Bất kì component gọi EventBus.$emit(‘toast-notify’) của đều trigger cho Toast  
- Theo design pattern: publish \- subscribe  
  - (Optional) Event Bus chỉ đơn giản là 1 vue instance (new Vue())   
  - Project có 1 main Vue instance  
  - Event Bus = Vue instance khác (thứ 2\)  
- $on: đăng kí event listener  
- $off: hủy đăng kí event listener  
- $emit: trigger event đó

# Dynamic Component

- <KeepAlive>
  - Cache bất kì component instance bên trong.   
  - Component instance khi được cache, khi nó bị xóa khỏi DOM thì vẫn được giữ trong component tree  
  - Nó chỉ deactivated state thay vì chạy unmounted  
    - (?) Khi nào gọi mount nhưng không gọi created  
    - (?) Ngăn chặn hook tiếp theo (ví dụ gọi beforeDestroy nhưng chặn không cho chạy đến destroyed bằng cách nào)  
  - (?) Có những cách nào để render lại 1 component  
    - Thay đổi data   
    - Thay đổi props  
    - Sử dụng v-if  
    - Nếu vuex thì thay đổi state liên kết tới component

# Mixin

- Là 1 object chứa 1 phần options của 1 components  
- Sử dụng để kế thường options dùng chung nhiều lần như data, methods, computed, watch  
- (?) Overwrite function  
  - Khai báo 1 method trùng tên trong component đó sẽ ghi đè lại methods cũ  
  - (Ví dụ) ButtonMixin  
  - DeleteButton, SubmitButton có điểm chung => kế thừa từ ButtonMixin

# <slot>

- <slot> là 1 tag của vue để khai báo 1 chỗ trống để component cha điền content vào  
- Giúp mình tái sử dụng code và dễ dàng sửa đổi  
  - (Ví dụ) tạo component Popup thì có thể tái sử dụng và truyền bất kì element nào vào đó  
- Có thể khai báo nhiều slot và mỗi slot có 1 cái tên  
  - (Ví dụ) Component Popup có slot header, main, action  
- Component cha dùng <template> và mapping đúng với slot cần chèn content vào  
- Scoped Slot để truy cập vào data của component đó  
  - Nó tương đương với component gốc truyền props vào slot  
  - Ở component cha thì dùng v-slot (vue 3), slot-scope (vue 2) để lấy slot props truyền vào content

# File “.vue”

- <template> = html  
- <script> = js  
- <style> = css

# <style>

- Scoped CSS (optional)  
  - Khai báo riêng css cho component đó  
  - Có thể overwrite class cho riêng component đó  
  - Còn không thì nó để global  
  - Khi compile thì chèn thêm id của component vào class, id, tag được css trong style  
  - Có thể khai báo nhiều tag style, nó sẽ ghi đè lên nhau   
  - (?) Vừa scoped vừa import css global đc không?  
  - Có thể, scoped css chỉ đóng vai trò ghi đè style cho riêng component thôi

# Provide & Inject (dependency injection)

- Provide & Inject là cách truyền dữ liệu từ component cha tới những component con sâu hơn (nested child component)  
  - Props thì chỉ truyền dữ liệu qua 1 level là component con liền với nó  
  - Nhưng dùng Provide/Inject có thể truyền tới bất kì component con nào bên trong component cha  
- Provide để khai báo những biến truyền dữ liệu xuống những component con  
- Inject để component điền những biến nào sẽ lấy từ provide của component tổ tiên