# Javascript Callback

Category: Javascript
First Refrence: What%20is%20a%20Callback%20function%203af9077ab4da484e9ad530f59b990486.md, What%20is%20Callback%20in%20Callback%20acade1233918421ca64796a736c3aa7a.md, What%20is%20a%20Callback%20Hell%20a13fad3a6123496c9c0d2a3188735587.md, What%20is%20aware%20of%20Callback%20726de997a549438f8da6683d1ece8928.md, What%20is%20Use%20of%20Callback%202e471dc4b5bf496fb7b04ffe65db9398.md
First Source: Javascript%20Function%2024d903792bfd4ce0876afb08e96fea70.md
Tags: Basic, Concept

<aside>
⚠️ Sự mất kiểm soát ở 1 step ⇒ mất kiểm soát các steps sau

</aside>

- Nếu không có cách kiểm soát hoàn toàn ⇒ bugs

# Concept

- Callback là function mà truyền vào function khác như tham chiếu

---

- A callback is a function passed into another function as an argument.

```jsx
function consoleLogFrom(getMessageCallback) {
  const message = getMessageCallback();
	console.log(message);
}

function sayHelloWorld() {
	return 'hello world';
}

consoleLogFrom(sayHelloWorld); //hello world
```

- This function is `invoked inside the outer function` to complete an action.
    - The other function can call the callback function inside its scope

## Use of Callback

- Callback có rất nhiều tác dụng
- Nhưng có 2 cái được biết đến nhiều nhất

### Đăng kí 1 hành động trừu tượng - 1 abstract action

- 1 hành động trừu tượng, linh hoạt theo hoàn cảnh
- Trừu tượng là mình biết nó tồn tại nhưng nội dung bên trong của nó sẽ thay đổi tùy hoàn cảnh

### Đăng kí 1 hành động sẽ được gọi trong tương lai

- Hành động sẽ được gọi cụ thể tại 1 thời điểm trong tương lai
- Hành động phải đợi hành động phía trước không biết bao giờ xong
- Cái hành động cụ thể trong tương lai có thể do `setTimeout`, `setInterval`
- Hành động phải đợi hành động phía trước không biết bao giờ xong thì trong Jquery có ajax để gọi api

---

- It means `registering` a `pending action` will be executed at the `right time in future`.

# Continuations

## Sequential Brain

- When we `fake multitasking` ⇒  we switch back and `forth between two or more tasks` in rapid succession ⇒ simultaneously progressing on each task in `tiny, fast little chunks`
- We do it so `fast` that to the `outside world` it appears as if we're `doing these things in parallel`.

## Callback Hell

- Callback Hell là 1 lỗi coding với việc để callbacks lồng nhau nhiều quá khiến code khó đọc và debug
    - Nhất là khi sử dụng trong logic bất đồng bộ
- Callback Hell khiến khó biết rõ được thứ tự chạy của callback và thời điểm callback được gọi

---

- Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic.
- Callback Hell is that executing order of different callbacks cannot be determined.
    - Easily occurs with nested callbacks or nested async actions.
    - Can’t determine when callback is executed.
- The difficulty of control callback-driven design is the worst (and yet most subtle) problems.
- The most troublesome problem with callbacks is inversion of control leading to a complete breakdown along all those trust lines.

## Trying to Save Callbacks

- Split callbacks = break into clearly steps in same level, sequence ⇒ pass multiple callback arguments lead to each step.
- Error-first style =  thinking about catching error first then implement case success.
- Call the callback too early
    - Callback is executed before sequential code.
- Call the callback too late (or never)
    - Set timeout = create 1 flag + 1 timeout to make sure not awaiting forever
- Call the callback too few or too many times
- Fail to pass along any necessary environment/parameters
- Swallow any errors/exceptions that may happen

---

- **Vocabulary**
    - inversion: đảo ngược