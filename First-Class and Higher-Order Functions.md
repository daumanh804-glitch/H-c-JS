Tư duy **"Hàm là một giá trị"** (First-Class Citizen) chính là chìa khóa. 🗝️

Nếu nó giống số 5, nghĩa là:

1. Lưu trữ: Bạn gán số 5 vào biến (let a = 5) -> Bạn cũng gán được hàm vào biến (const add = ...).
2. Truyền đi: Bạn đưa số 5 vào hàm khác (tinhTong(5)) -> Bạn cũng đưa được cả một hàm vào hàm khác.
3. Trả về: Một hàm có thể return 5 -> Một hàm cũng có thể return một hàm khác.

# Để bạn dễ nhớ nhất, hãy tưởng tượng thế này:#

- First-Class Functions: Là TÍNH CHẤT của ngôn ngữ JavaScript (nó cho phép làm điều đó).
- Higher-Order Functions: Là KỸ THUẬT chúng ta sử dụng (tận dụng tính chất trên để viết code xịn).
  Dưới đây là bản tổng hợp chi tiết và dễ hiểu nhất:

## 1. First-Class Functions (Hàm Hạng Nhất) 🥇

Khái niệm: JavaScript coi Hàm (Function) giống hệt như một giá trị bình thường (như số 10, chuỗi 'Hello', hay một Object). Nó là một "công dân hạng nhất", có đầy đủ quyền lợi như các kiểu dữ liệu khác.

Quyền năng của nó: Vì là một "giá trị", Hàm có thể:

- Được gán vào một biến.
- Được lưu trong một Object (lúc này gọi là Method).
- Được truyền vào hàm khác làm tham số.
- Được trả về từ một hàm khác.
  Ví dụ minh họa:

```javascript
// 1. Gán hàm vào biến (giống gán số vào biến)
const sayHi = function () {
  return 'Xin chào!';
};

// 2. Lưu trong Object
const person = {
  name: 'Teo',
  greet: sayHi, // Gán hàm sayHi vào đây
};
```

# 2. Higher-Order Functions (Hàm Bậc Cao) 🎩

Khái niệm: Đây là những hàm đóng vai trò "Sếp" hoặc "Nhà máy". Để được gọi là Hàm Bậc Cao, nó phải làm được ít nhất một trong hai việc sau:

A. Nhận một hàm khác làm đầu vào (Input)
Hàm được truyền vào gọi là Callback Function (Hàm gọi lại).

Tại sao dùng? Để chia nhỏ công việc. Hàm bậc cao lo logic chung, còn hàm Callback lo chi tiết cụ thể.
Ví dụ:

```javascript
// Hàm bậc cao (Nhận hàm fn làm tham số)
function mayTinh(a, b, fn) {
    return fn(a, b);
}

// Các hàm nhỏ (Callback)
const cong = (x, y) => x + y;
const tru = (x, y) => x - y;

// Sử dụng
mayTinh(5, 3, cong); // Kết quả: 8
mayTinh(5, 3, tru);  // Kết quả: 2
```
Giải thích: mayTinh là Hàm bậc cao vì nó nhận hàm cong hoặc tru để xử lý.

B. Trả về một hàm khác làm đầu ra (Output)
Nó giống như một cái máy sinh ra các hàm con khác nhau tùy theo cài đặt ban đầu.

Tại sao dùng? Để tạo ra các hàm chuyên biệt từ một hàm tổng quát (liên quan đến Closure).
Ví dụ:
```javascript
// Hàm bậc cao (Trả về một hàm mới)
function taoHamChao(loiChao) {
    return function(ten) {
        console.log(`${loiChao}, ${ten}!`);
    };
}

// Tạo ra các hàm con
const chaoKieuAnh = taoHamChao('Hello');
const chaoKieuViet = taoHamChao('Xin chào');

// Sử dụng hàm con
chaoKieuAnh('John'); // In ra: Hello, John!
chaoKieuViet('Tèo'); // In ra: Xin chào, Tèo!
```
Giải thích: taoHamChao là Hàm bậc cao vì nó đẻ ra hàm chaoKieuAnh và chaoKieuViet.

🧠 Bảng so sánh chốt hạ
Đặc điểm	| First-Class Functions	| Higher-Order Functions
Là gì?	|Là khả năng của ngôn ngữ JS.	|Là cách dùng hàm trong thực tế.
Tư duy	|"Hàm là dữ liệu" (Function is Value).|	"Hàm xử lý hàm" (Function on Function).
Vai trò	|Nền tảng lý thuyết.	|Ứng dụng thực tế (Callback, Array Methods, v.v.).



