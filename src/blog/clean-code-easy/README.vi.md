# Viết Code Sạch trong JavaScript

Viết code sạch là điều cần thiết để phát triển phần mềm có thể bảo trì, hiệu quả và ít lỗi. Code sạch không chỉ phản ánh sự chuyên nghiệp của nhà phát triển mà còn giúp dễ dàng bảo trì và phát triển codebase trong tương lai. Hướng dẫn này sẽ đi sâu vào các nguyên tắc của việc viết code sạch, đặc biệt là cho các nhà phát triển JavaScript.

## Giới thiệu

Việc viết code sạch rất quan trọng, đặc biệt là trong các dự án quy mô lớn với hàng ngàn dòng code. Thiết lập và tuân thủ các tiêu chuẩn code giúp đảm bảo rằng code không chỉ hoạt động mà còn sạch sẽ và chuyên nghiệp. Dưới đây, chúng ta sẽ khám phá một số nguyên tắc có thể giúp các nhà phát triển viết code sạch và dễ bảo trì hơn.

## 1. Đặt Tên Có Ý Nghĩa

### Giải thích

Chọn tên rõ ràng, biểu cảm và chuyên nghiệp là một trong những nhiệm vụ khó nhất trong khoa học máy tính. Tên nên chỉ rõ mục đích mà chúng phục vụ trong code.

### Ví dụ

```jsx
// Không tốt
let d; // thời gian đã trôi qua tính bằng ngày

// Tốt
let elapsedTimeInDays;
let daysSinceCreation;
let daysSinceModification;
let fileAgeInDays;
```

## 2. Hàm Chỉ Nên Làm Một Việc

### Giải thích

Hàm nên ngắn gọn và chỉ giải quyết một vấn đề. Điều này làm cho hàm mạnh mẽ hơn, dễ đọc hơn và có thể tái sử dụng.

### Ví dụ

```jsx
// Không tốt: hàm thực hiện nhiều việc
function handleClientData(client) {
  if (client.age > 20) {
    // thực hiện một hành động nào đó
  }
  saveToDatabase(client);
}

// Tốt: chia nhỏ thành các hàm nhỏ hơn
function filterClientsByAge(client) {
  return client.age > 20;
}

function saveClient(client) {
  saveToDatabase(client);
}
```

## 3. Tránh Lặp Code

### Giải thích

Code bị lặp lại có thể dẫn đến sự không nhất quán và khó khăn trong bảo trì. Rất quan trọng để trừu tượng hóa code bị lặp lại thành các hàm hoặc mô-đun có thể tái sử dụng.

### Ví dụ

```jsx
// Không tốt: code bị lặp lại
function showDeveloper(developer) {
  console.log(developer.name);
  console.log(developer.age);
  // Các thuộc tính khác
}

function showManager(manager) {
  console.log(manager.name);
  console.log(manager.age);
  // Các thuộc tính khác
}

// Tốt: hàm thống nhất
function showPerson(person) {
  console.log(person.name);
  console.log(person.age);
  // Các thuộc tính khác
}
```

## 4. Comment Sạch Sẽ

### Giải thích

Comments nên thêm giá trị cho code, giải thích tại sao code lại làm những gì nó làm, không phải là những gì nó làm. Tránh comments hiển nhiên và thay vào đó comment về lý do đằng sau các quyết định phức tạp.

### Ví dụ

```jsx
// Không tốt: comment hiển nhiên
// Kiểm tra nếu người dùng đủ điều kiện cho vay
if (user.creditScore > 700) {
  // ...
}

// Tốt: giải thích tại sao điều kiện này tồn tại
// Người dùng với điểm tín dụng trên 700 được coi là có rủi ro thấp cho vay
if (user.creditScore > 700) {
  // ...
}
```

## 5. Nguyên Tắc Xử Lý Lỗi

### Giải thích

Ưu tiên sử dụng ngoại lệ thay vì trả về mã lỗi. Ngoại lệ không thể bị bỏ qua và có thể mang thông tin lỗi phong phú.

### Ví dụ

```jsx
// Không tốt: sử dụng mã lỗi
function readFile(file) {
  if (!file.exists) {
    return -1;
  }
  // đọc file
  return 0;
}

// Tốt: sử dụng ngoại lệ
function readFile(file) {
  if (!file.exists) {
    throw new Error("File does not exist.");
  }
  // đọc file
}
```

## Kết Luận

Viết code sạch không chỉ là viết code hoạt động mà là viết code có thể dễ dàng được hiểu, chỉnh sửa và bảo trì bởi người khác. Là nhà phát triển, nhiệm vụ của chúng ta không chỉ là giải quyết vấn đề mà còn phải làm sao để những người bảo trì sau này có thể hiểu và phát triển dựa trên nó. Áp dụng các nguyên tắc này không chỉ cải thiện chất lượng code mà còn nâng cao năng suất của nhóm và tuổi thọ của phần mềm.

## Đọc Thêm

- [_Clean Code: A Handbook of Agile Software Craftsmanship_](/src/book/CleanCodeBook.pdf) by Robert C. Martin

---

Hướng dẫn này nhằm giúp các nhà phát triển JavaScript hiểu tầm quan trọng của việc viết code sạch và cách áp dụng các nguyên tắc này trong công việc hàng ngày. Nếu bạn thấy hướng dẫn này hữu ích, xin đừng ngần ngại khám phá các tài liệu chi tiết hơn như cuốn sách của Robert C. Martin đã đề cập ở trên.
