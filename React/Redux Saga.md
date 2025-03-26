# Redux Saga

# Concept

- Redux Saga is a library that helps to manage side effects in Redux app.
- Side effects are things like making network requests, accessing the browser’s local storage, or interacting with the browser’s history.
- This makes code more modular and easier to test.

---

- Redux Saga xử lý những logic phức tạp hỗ trợ cho Redux như xử lý hàm bất đồng bộ, truy cập vào bộ nhớ của browser, tương tác với lịch sử browser
- Tạo ra những `saga` - những kịch bản xử lý logic tương ứng phức tạp với mỗi action
- Khi dispatch bất kì action nào ⇒ gọi tới Root Saga ⇒ từ đó gọi các Saga con ứng với action nào đó

## Effect

- Redux Saga effect = JS object để saga middleware biết dispatch action gì
- Effect chỉ đơn giản là một javascript object có chứa thông tin để saga middleware biết cần phải làm gì.
- Effect là command - chỉ thị cho saga middleware

## Blocking/Non-blocking call

- 2 loại của Effect

## Task

- Process xử lý Effect chạy dưới background
- `yield` 1 Effect ⇒ tạo ra 1 Task để xử lý Effect dó

### `Blocking` call

- A `Blocking` call means that the Saga yielded an Effect and will wait for the outcome of its execution before resuming to the next instruction inside the yielding Generator.

---

- `Blocking` là Effert tạo Task ra và  đợi đến nó thực hiện xong thì mới chuyển sang Effect tiếp theo
    - Thực hiện xử tuần tự
- Lấy result ngay ở `yield`

### `Non-blocking` call

- A Non-blocking call means that the Saga will resume immediately after yielding the Effect.

---

- `Non-blocking` là Effect chỉ khai báo Task và để nó chạy độc lập
    - Task chạy bất đồng bộ
    - Effect tiếp theo được xử lý mà không cần chờ Task của effect trước hoàn thiện
- Lấy task ngay ở `yield`

## Saga

- A saga is a function that is used to take in actions and perform side effects.

---

- Saga là hàm quan sát các action và thực hiện các logic phức tạp hỗ trợ action đó
- 1 Generator function => Return generator object
- Thực thi tất cả các `yield` Effects
- Có thể gọi `saga` con khác bên trong
    - Tạo Task để xử lý `saga` đó

### Luồng chạy của Saga

1. In the first iteration, the middleware invokes the `next()` method to retrieve the next Effect. 
2. The middleware then executes the yielded Effect as specified by the Effects API below. 
3. Meanwhile, the Generator will be suspended until the effect execution terminates. 
4. Upon receiving the result of the execution, the middleware calls `next(result)`
 on the Generator passing it the retrieved result as an argument. 
5. This process is repeated until the Generator terminates normally or by throwing some error.

---

1. Middleware chạy đến `yield` Effect đầu tiên => thực thi task (Non-blocking || Blocking) => Generator tạm dừng
2. Effect đầu hoàn thiện => call `next` => gọi tới `yield` Effect thứ 2
3. Lặp đến khi hết `yield`

## Watcher/Worker

- 2 loại `saga`

### Watcher

- Will watch for dispatched actions and fork a worker on every action

---

- Quan sát dispactch 1 số loại action cụ thể
- Gọi `worker saga` để thực hiện Effect tương ứng với action đó
- `While` liên tục để chạy lại action để kiểm tra

### Worker

- Will handle the action and terminate

---

- `saga` để xử lý logic

# Redux Saga Api

## Middleware API

### `createSagaMiddleware(options)`

- Tạo Redux middleware

### `middleware.run(saga, ...args)`

- Để chạy `saga`
- Call sau khi đã `applyMiddleware`

## Effect creator

- Chỉ là hàm tạo Effect => return Effect object
    - Chưa thực thi luôn
- Middleware trả về Effect object => JS thực thi Effect action
- Effect Creator: là một function trả về một Effect.
    - Ko thực thi cái Effect này
    - Người thực thi là saga middleware, chứ ko phải Effect Creator nhé.

| Name | Type |
| --- | --- |
| takeEvery | Non-blocking |
| takeLatest | Non-blocking |
| takeLeading | Non-blocking |
| throttle | Non-blocking |
| debounce | Non-blocking |
| retry | Blocking |
| take | Blocking |
| take(channel) | Sometimes (see API reference) |
| takeMaybe | Blocking |
| put | Non-blocking |
| putResolve | Blocking |
| put(channel, action) | Non-blocking |
| call | Blocking |
| apply | Blocking |
| cps | Blocking |
| fork | Non-blocking |
| spawn | Non-blocking |
| join | Blocking |
| cancel | Non-blocking |
| select | Non-blocking |
| actionChannel | Non-blocking |
| flush | Blocking |
| cancelled | Blocking |
| race | Blocking |
| delay | Blocking |
| all | Blocks if there is a blocking effect in the array or object |

### `take(pattern)`

- Quan sát mỗi lần dispatch action `pattern`
- Kết hợp `fork(fn, ...args)` mô hình watcher -> worker
- Đợi dispatch action `pattern` thì sẽ thực hiện một cái task nào đó

### `fork(fn, ...args)`

- Tạo ra 1 task riêng biệt nhưng liên kết `saga` hiện tại
    - Non-blocking - tạo xong nhảy tiếp sang `yield` tiếp theo mà không đợi task hoàn thành
    - Riêng biệt nên các task từ `fork(fn, ...args)` trong cùng `saga` chạy song song với nhau

<aside>
⚠️ Task xử lý Saga hoàn thành khi tất cả task của `fork(fn, ...args)`  bên trong nó hoàn thành

</aside>

- 1 Task trong Saga lỗi thì cancels tất cả các tasks khác
- Không catch error trực tiếp từ fork => tạo wrapper saga để try-catch saga có fork

### `spawn(fn, ...args)`

- Giống `fork(fn, ...args)` nhưng task không liên kết với saga
    - Saga kết thúc luôn mà không đợi task hoàn thành

### `takeEvery(pattern, saga, ...args)`

<aside>
💡 Hay dùng

</aside>

- Mỗi lần dispatch action `pattern` => Chạy lại `saga` 1 lần
- Dispatch bao nhiêu sẽ chạy bấy nhiêu lần `saga` đó
- Dispatch nhiều lần trong cùng 1 time => chạy nhiều lần `saga` => tạo ra nhiều `task`

### `takeLatest(pattern, saga, ...args)`

<aside>
💡 Hay dùng

</aside>

- Mỗi lần dispatch action `pattern` => Chạy lại `saga`1 lần nhưng cancel `task` chạy trước đó
- Dispatch bao nhiêu khởi tạo lại bấy nhiêu lần `saga`

<aside>
⚠️ Chỉ có 1 `task` tại 1 thời điểm

</aside>

### `takeLeading(pattern, saga, ...args)`

- Chạy `saga` khi action `pattern` được dispatch
- Những action tiếp theo sẽ bị cancel cho đến khi `saga` trước đó chạy xong.

<aside>
⚠️ Chỉ có 1 `task` tại 1 thời điểm

</aside>

### `put(action)`

- Dispatch action khác từ `saga`

### `call(fn, ...args)`

- Gọi hàm và truyền tham số args vào hàm đó
- Dùng để gọi các hàm API

### `all([...effects])`

- Chạy nhiều effects đồng thời cùng một lúc

### `throttle(ms, pattern, saga, ...args)`

- Throttle cái action `pattern`, đảm bảo chỉ chạy saga 1 lần trong khoảng thời gian ms

### `debounce(ms, pattern, saga, ...args)`

- Debounce cái action `pattern`, đảm bảo chỉ chạy saga 1 lần sau khi đã đợi khoảng thời gian ms

### `retry(maxTries, delay, fn, ...args)`

- Cố gắng gọi lại hàm fn nếu fail, sau mỗi delay milliseconds, và tối đa chỉ thử maxTries lần.

### `delay(ms, [val])`

- Returns an effect descriptor to block execution for `ms` milliseconds and return val value.

# Lưu ý

- Không dùng Redux Saga cho tất cả action
    - Cái nào đơn giản quá thì để như bình thường
    - Những action không cần bất đồng bộ