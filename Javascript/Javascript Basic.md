# Javascript Language

- JavaScript là ngôn ngữ lập trình được sử dụng để tạo trang web tương tác.  
  - Sau này do sự phát triển của NodeJS thì Javascript có thể dùng cho multiplatform như backend, mobile, window app, etc  
- Loosely typing  
  - Không khai báo cụ thể kiểu biến  
  - javascript  
  - php  
  - ruby  
  - python  
- Dynamically typed  
  - Ngôn ngữ có kiểu dữ liệu được nhận biết trong quá trình runtime.  
  - 1 biến có thể được gán cho bất kì loại kiểu biến nào  
- Weakly typed  
  - Kiểu dữ liệu có thể được suy ra từ một kiểu dữ liệu khác.

# Data Type

- Primary \- Nguyên thủy  
  - Tuân theo tham trị  
  - string  
  - number  
  - boolean  
  - bigint  
  - symbol  
  - Mỗi lần gán giá trị tham trị sẽ được vào 1 ô nhớ mới  
  - Nếu gán biến A với biến B có giá trị tham trị  
    - Copy giá trị của B ra ô nhớ mới  
    - Gán ô nhớ mới đó cho A  
    - A và B không liên kết với nhau  
    - A thay đổi thì B không đổi và ngược lại  
- Reference - Tham chiếu  
  - Tuân theo tham chiếu  
  - object  
  - array  
  - function  
  - null  
  - undefined  
  - Giá trị tham chiếu sẽ cùng tham chiếu tới cùng 1 ô nhớ với mỗi lần gán  
  - Gán giá trị tham chiếu lần đầu, tạo ô nhớ mới  
    - Từ lần gán thứ 2, chỉ là gán địa chỉ ô nhớ tới biến đó  
  - Nếu gán biến A với biến B có giá trị tham chiếu  
    - A được gán địa chỉ ô nhớ của B  
    - Giá trị bên trong B thay đổi thì A cũng thay đổi và ngược lại  
- 1+"23"=?  
  - 123  
  - Khi cộng số với string, số sẽ chuyển sang kiểu string rồi ghép với string kia