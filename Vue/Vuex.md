# Vuex dùng để làm gì

- Là 1 thư viện để quản lý tập trung state của các components trong vue app  
- Gồm 5 phần chính:  
1. State: là global state để chứa dữ liệu trong vuex  
2. Getter: để lấy giá trị biến đổi từ state  
3. Mutation: để cập nhật giá trị của state  
4. Action: cũng cập nhật giá trị của state nhưng có thể thực hiện các hành động bất đồng bộ  
- Action có thể cập nhật trực tiếp state hoặc commit mutation  
- Action dùng để giao tiếp giữa các module  
- Action có thể lấy state, getters của module khác  
- Action có thể commit hoặc dispatch action của module  
5. Module: là các phần nhỏ của root store  
- Chia nhỏ store thành các phần riêng biệt  
- Mỗi module có đủ state, getter, mutation, action của riêng nó

# Làm sao để phân biệt các store

- Muốn gọi 1 thành phần của 1 module, phải thêm tên của module đó đằng trước