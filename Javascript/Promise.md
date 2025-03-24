### Single Threading

- Queue  
  - Cấu trúc hàng đợi theo cơ chế First-in First-out  
1. Cái đến trước được xử lý trước  
2. Cái đến sau phải đợi cái liền trước  
3. Cái đến sau nữa thì cứ đứng chờ thành 1 hàng  
- Event Loop là 1 hàng chờ tuân theo quy tắc \`First-in First out\`.  
1. Sự kiện đầu kích hoạt (hay còn gọi là trigger) ⇒ nó được đưa vào event loop  
2. JS engine thấy event loop có sự kiện thì lấy cái gần nhất ra xử lý  
3. Sự kiện thứ 2 được đẩy vào thì sẽ phải chờ sự kiện đầu xử lý xong  
4. Rồi sự kiện thứ 3 tiếp tục đưa vào hàng chờ và đợi cái thứ 2 xong mới được thực hiện  
- Event loop như 1 cái to-do list cho thread  
1. Thread sẽ xử lý tuần tự những task trong Event loop  
2. Event loop rỗng thì Thread sẽ tạm dừng  
3. Đẩy sự kiện vào Thread thì nó lại chạy tiếp  
- Single Threading có lợi ích gì?  
1. Tập trung xử lý từng vấn đề độc lập  
- Với đa luồng thì CPU sẽ phải chia tài nguyên cho tất cả các luồng  
- Nhưng với cơ chế đơn luồng thì chỉ xử lý 1 vấn đề tại 1 thời điểm  
- Do đó tốc độ xử lý 1 vấn đề sẽ nhanh gấp mấy lần đa luồng  
- Có khi 1 vấn đề chỉ xử lý trong 1 nghìn phần giây nên không thể nhận ra sự khác biệt  
2. Bộ nhớ không bị xung đột  
- Với đa luồng không chỉ CPU mà bộ nhớ tạm như RAM cũng sẽ chia sẻ với các luồng  
- Ví dụ cho 1 biến A  
  - Mà Thread 1 và Thread 2 cùng sử dụng A cùng 1 thời điểm  
  - Thì chắc chắn sẽ bị lỗi  
3. Luồng hoạt động liên tục  
- Đa luồng thì có luồng làm ít, luồng làm nhiều  
- Thì luồng nào làm ít thì xong trước thì cứ chờ ở đó, gây tốn tài nguyên vì vẫn phải duy trì luồng đó  
- Còn đơn luồng công việc làm liên tục  
- Chưa tắt phần mềm thì nó còn chạy  
- Làm sao Javascript có thể xử lý Multitasking?  
1. Chia mỗi task thành các sub-tasks cực nhỏ  
2. Trộn lẫn các sub-tasks thành 1 hàng  
3. Rồi xử tuần tự từng sub-task  
- Tại 1 thời điểm cả 2 tasks lớn cùng trong quá trình xử lý  
- Mỗi sub-task được xử lý quá nhanh gần như tức thì  
- Tiếp theo vì xen kẽ các sub-tasks nên task sau sẽ không phải đợi task trước hoàn thành 100%

# Promise conept

- Promise là 1 đối tượng biểu thị 1 giá trị sẽ được nhận về trong tương lai
- Giá trị đó có thể là lỗi nếu gặp sự cố, hay còn gọi là trạng thái rejected
- Và mục đích của Promise chỉ là quản lý callback khi xử lý bất đồng bộ
- Promise sẽ giúp điều phối callback khi xử lý bất đồng bộ tốt hơn

---

- Event hoàn thành promise ⇒ promise response value (resolve | reject)
- Thay vì chia 1 async task ⇒ n sync step ⇒ chia 1 async task ⇒ n async step ⇒ tiếp tục chia
- Không cần phải lo chi tiết step ⇒ chỉ cần biết step tiếp theo là step nào thôi

---

- A promise is an object that may produce a single value some time in the future with either a resolved value or a reason that it’s not resolved.
- Promise is a variable to manage callbacks for asynchronous processing.
    - Writing the cleaner code
    - Reducing callback hell

## Promise state

- Promises có 3 trạng thái:
1. **Pending:** trạng thái sự việc đang chạy chưa xong
2. **Fulfilled:** trạng thái sự việc chạy thành công
3. **Rejected:** trạng thái sự việc gặp vấn để và phải throws Error

---

Promises have three states:

1. **Pending:** This is an initial state of the Promise while the operation is processing.
2. **Fulfilled:** This state indicates that the specified operation was completed.
3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

## Promise method

### all

```jsx
Promise.all([ ...promiseArray ])
```

- Xử lý đồng thời nhiều Promise cùng lúc
- Return giá trị là 1 promise
- Returned promise đó resolve 1 mảng chứa resolve của các Promise tham số
- Thứ tự resolve chính là thứ tự Promise tham số
- Nếu có 1 promise bị rejected thì `Promise.all` sẽ reject luôn
    - Tuy nhiên các promise khác vẫn chạy bình thường
    - Do return promise của hàm `all` reject từ promise tham số đầu tiên bị reject
    
    ⇒ Những cái sau promise đều không trả về error cho return promise của hàm `all`
    

---

- Iterable of promises ⇒ returns a single Promise that resolves to an array of the results of the input promises.
- If 1 or N input promises is rejected ⇒ `Promise.all` rejected at the first rejected input promise
    - But other promise of input array still running.
    - Even if there are some promises can be rejected, they still run and don’t throw error.

### race

```jsx
Promise.race([ ...promiseArray ])
```

- Iterable of promises ⇒ returns a single Promise that resolves to first promise responses.
- It can be fulfill or rejected

### any

```jsx
Promise.any([ ...promiseArray ])
```

- Iterable of promises ⇒ returns a single Promise that resolves to first promise is fulfilled.

### resolve

```jsx
Promise.resolve(value)
```

- Promise.resolve(..) will return a received fulfill Promise directly, or unwrap a received thenable.
- It can actually result in either fulfillment or rejection

### reject

```jsx
Promise.resolve(value)
```

- Return rejected Promise

### then

```jsx
p.then(onFulfilled, onRejected?);
```

- Thì hàm `then` trong promise cũng là lắng nghe việc Promise dừng lại
- `Then` bắt cả sự kiện Promise xử lý thành công cũng như thất bại
- Then return 1 Promise khác
    - Return của callback `onFulfilled` và `onRejected` cũng trả về new promise.
    - Nếu `onFulfilled == null` ⇒ Promise sẽ chỉ nhận được reject của promise trước
    - `onRejected == null` ⇒ Promise sẽ chỉ nhận được resolve của promise trước

---

- 1 Promise gán listener cho việc hoàn thành asynchronous action

```jsx
// sequentially
promise1
	.then(...) //promise 1.1
	.then(...) //promise 1.2

// parallel
promise1.then(...) //promise 1.1
promise1.then(...) //promise 1.1
```

- Việc giữ chỗ khiến thời gian đợi lấy giữ liệu ⇒ độc lập

---

- Listen promise response
    - Both resolve & reject of promise
    - 1 promise can assign multiple then
- Return new promise
    - Return of `onFulfilled` or `onRejected` is also response of new promise.
    - `onFulfilled == null` ⇒ Take resolve of previous promise (if have)
    - `onRejected == null` ⇒  Take reject of previous promise (if have)

### catch

- Là chỉ bắt sự kiện của `onRejected` của `then`

```jsx
p.catch(onRejected);
// same
p.then(null, onRejected);
```

### finally

```jsx
p.finally(onFinally);
```

- Giống `finally` trong `try - catch`
- Thì callback này được gọi khi Promise dừng lại (sau `then()`)

---

- Whenever promise response (resolve | reject) ⇒ call finally

# Async function

- Async function là function dựa trên Promise chuyên để xử lý  tuần tự chuối Promise
- Khi có 1 chuỗi Promise mà Promise sau chỉ được bắt đầu khi Promise trước hoàn thiện
- Keyword `await` dùng để đợi `Promise`.
    - Nó dùng thay thế cho hàm `then`
    - Nó chỉ sử dụng trong `async` function

---

- Việc để code theo kiểu *now & later* ở mỗi step ⇒ nhiều steps ⇒ loạn + khó kiểm soát
    
    ⇒ Để tất cả step = async
    

---

- An async function is a function declared with the `async` keyword which enables asynchronous.
- Promise-based behavior to be written in a cleaner style by avoiding promise chains.
- The `await`operator is used to wait for a `Promise`.
    - It can only be used inside an `async` function

```jsx

function logger() {
	const url = "http://someapi.com/users";

	return fetch(url).then(
	(resolvedValue) => {
		const data = resolvedValue;
		console.log(data);
	},
	(error) => {
		console.error(error);
	},
}

// convert to async

async function logger() {
	const url = "http://someapi.com/users";
	try {
		  let data = await fetch(url); // pause until fetch returns
			 console.log(data);
	} catch (error) {
			console.error(error);
	}
}

logger();
```

## Future value

### Now & Later

Value has been ordered but don’t have it.

- The placeholder essentially makes the value time *independent*.

```jsx
function add(getXCallback, getYCallback, sumCallback) {
	var x, y;
	getXCallback(function(xVal){
		x = xVal; // x = now

		if (y != undefined) { // y = later = don't nknow is ready or not
			sumCallback( x + y ); // send along sum
		}
	});
	getYCallback(function(yVal){
		y = yVal; // y = now

		if (x != undefined) { // x = later = don't nknow is ready or not
			sumCallback( x + y ); // send along sum
		}
	});
} 

// `fetchX()` and `fetchY()` are sync or async
add(fetchX, fetchY, function(sum){
	console.log( sum ); // that was easy, huh?
});
```

### Promise Value

```jsx
function add(xPromise,yPromise) {
	// `Promise.all([ .. ])` takes an array of promises,
	// and returns a new promise that waits on them
	// all to finish
	return Promise.all( [xPromise, yPromise] )
		// when that promise is resolved, let's take the
		// received `X` and `Y` values and add them together.
		.then( function(values){
			// `values` is an array of the messages from the
			// previously resolved promises
			return values[0] + values[1];
		});
} 
// `fetchX()` and `fetchY()` return promises for
// their respective values, which may be ready
// *now* or *later*.
add(fetchX(), fetchY())
	// we get a promise back for the sum of those
	// two numbers.
	// now we chain-call `then(..)` to wait for the
	// resolution of that returned promise.
	.then(
		// fullfillment handler
		function(sum) {
			console.log( sum );
		},
		// rejection handler
		function(err) {
			console.error( err ); // bummer!
		}
	);
```

### Completion Event

- The resolution of a Promise = promise chain mechanism  = a flow-control mechanism
- Chain Flow: A temporal *this-then-that*
    1. .then(...) (next step of 1 promise) process async task
    2. onFullfill | onReject returns Promise 
    3.  next then(...) has to wait Return Promise from (2) response
- For two or more steps in an asynchronous task

### Promise "Events”

```jsx
function bar() {
	// `foo(..)` has definitely finished, so
	// do `bar(..)`'s task
} 

function oopsBar() {
	// oops, something went wrong in `foo(..)`,
	// so `bar(..)` didn't run
} 

// ditto for `baz()` and `oopsBaz()`
var p = foo( 42 );

p.then( bar, oopsBar );
p.then( baz, oopsBaz );
```

## Thenable Duck Typing

```jsx
function isThenable(variable) {
	return p !== null &&
	(
		typeof p === "object" ||
		typeof p === "function"
	) && typeof p.then === "function"
}

var ClassName = function() {} // class contructor

// ClassName implements Thenable
ClassName.prototype.then = function() {}
```

### Calling Too Early

- Promise is always asynchrony.
- Promise is to replace `setTimeout(..,0)` hack.

### Promise Scheduling Quirks

```jsx
var p3 = new Promise( function(resolve,reject){
	resolve( "B" );
});
var p1 = new Promise( function(resolve,reject){
	resolve( p3 );
});
var p2 = new Promise( function(resolve,reject){
	resolve( "A" );
});

p1.then(function(v){
	console.log(v);
});

p2.then(function(v){
	console.log(v);
});
// A B <-- not B A as you might expect
```

### Calling Too Late | Never Calling the Callback

1. Nothing (not even a JS error) can prevent a Promise from notifying its resolution (if it's resolved).
    - Register both fulfillment and rejection ⇒ 1 in 2 will be called
    - Finally always be called
2. Tip: TIMEOUT

```jsx
// a utility for timing out a Promise
function timeoutPromise(delay) {
	return new Promise( function(resolve,reject){
		setTimeout(function(){
			reject( "Timeout!" );
		}, delay);
	});
} 
// setup a timeout for `foo()`
Promise.race( [
	foo(), // attempt `foo()`
	timeoutPromise(3000) // give it 3 seconds
]).then(
	function(){
	// `foo(..)` fulfilled in time!
	},
	function(err){
		// either `foo()` rejected, or it just
		// didn't finish in time, so inspect
		// `err` to know which
	}
);
```

### Invoke too many times

- The Promise will accept only the first resolution.

---