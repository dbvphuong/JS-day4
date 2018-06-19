# JS-day4  
# 1 Async  
# 1.1 Sync vs Async  
### Sync code (code đồng bộ) là gì ?  
sync là việc thực thi lần lượt các dòng lệnh từ trên xuống dưới, xong dòng trên thì dòng dưới mới bắt đầu được thực hiện.  
### Async code (code bất đồng bộ) là gì ?  
Asyns là việc thực thi các dòng lệnh không phải đợi lần lượt từ trên xuống dưới.  
### Theo em JavaScript là ngôn ngữ đồng bộ hay bất đồng bộ.  
Javascript là ngôn ngữ đồng bộ.  
# 1.2 setTimeout  
### Cho hàm setTimeout có định nghĩa như sau:  
https://www.w3schools.com/jsref/met_win_settimeout.asp  
setTimeout là hẹn giờ hiển thị thông báo.  
Cú pháp: setTimeout(function(){},số milliseconds)  
### Set đoạn code sau, hãy mô tả chính xác những gì xảy ra và kết quả in ra là gì ?  
```
console.log('Hi');  
setTimeout(function () {  
  console.log('there');  
}, 1000);  
```
Đầu tiên sẽ hiện ra Hi, sau đó 1 giây thì hiện ra there ở dòng dưới.  
### How about this one, can you guess ?  
```
console.log('Hi');  
setTimeout(function () {  
  console.log('there');  
}, 0);  
console.log('Hi again');  
```
Sẽ hiể thị ra:  
Hi  
Hi again  
there  
=>setTimeout sẽ cho ra kết quả hiện thị sau hàm hiển thị bình thường mặc dù hẹn giờ là 0s.  
Vì hiển thị hàm đồng bộ trước, bất đồng bộ sau, hàm setTimeout là bất đồng bộ(setTimeout là của trình duyệt).    

# 1.3 Event Loop  
### Tìm hiểu về Event loop, và giải thích lại đoạn code trên theo ý hiểu của em. Reference:  
https://www.youtube.com/watch?v=8aGhZQkoFbQ  
Hàm setTimeout bị hiển thị sau là vì sau khi hết thời gian chờ là 0s thì nó sẽ bị đẩy vào hàng chờ, và đợi hệ thống chạy hết các thông báo khác thì hàm setTimeout mới được hiển thị.  
# 1.4 Callbacks  
### Tìm hiểu về callback funtions trong JS (https://www.sitepoint.com/callbacks-javascript/)  
### Người ta nói callback functions đóng gói tính liên tục của chương trình. Theo em chương trình dưới sẽ được chạy liên tục ra sao? Ví dụ (1) => (2) => (3)  
```
// (1)  
setTimeout(function () {  
  // (2)  
}, 1000);  
// (3)  
```
Thứ tự chạy là 1 -> 3 -> 2  
Callbacks là truyền 1 đoạn code A (hàm A) vào trong hàm B, khi nào hàm A được hàm B gọi thì lúc ấy gọi là callbacks.

## 1.4.1 Nested/Chained Callbacks  
### Set đoạn code sau, khi người dùng click vào btn thì điều gì xảy ra?  
```
// (0)  
var btn = document.getElementById('btn');  
btn.addEventListener('click', function () {  
  // (1)  
  setTimeout(function () {  
    // (2)  
  }, 1000);  
  // (3)  
});  
```
0 ->1 ->3 ->2  

# 1.5 Promises  
promises là xử lí một kết quả cụ thể(trong bất đồng bộ) có thể là thành công hay thất bại.  
Cú pháp 1 promises:  
 var promises= new Promises(function(resolve, reject){...})  
### What is a future value ?  
giá trị tương lai mình đã định sẵn là resolve, reject.  
### Promise value ?  

### Promise Events ?  

### How to get Promise value?  

### How to handle error in Promise ?  
dùng lệnh: p.catch(onRejected);  

p.catch(function(reason) {  
});  
### How to chain Promises ?  
ta có thể dùng hàm then để gọi liên tiếp các hàm trong chuỗi các function ra.  
ví dụ:  
```
hamtong()  
.then(function1(){});
.then(function2(){});
.then(function3(){});
```
### Promise.all  

### Promise.race  

### finally  


