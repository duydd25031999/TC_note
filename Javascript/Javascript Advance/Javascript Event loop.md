# Event Loop


# Javascript Engine

## Single Threading

## Queue

<aside>
💡 Cấu trúc hàng đợi theo cơ chế `First-in First-out`

</aside>

1. Cái đến trước được xử lý trước
2. Cái đến sau phải đợi cái liền trước
3. Cái đến sau nữa thì cứ đứng chờ thành 1 hàng

## Javascript Environment

- Javascript cấu tạo bằng 2 thành phần chính

### 1. Environment:

- Environment nhận các Event từ I/O và các chỗ khác
- Enviroment sắp xếp thứ tự công việc (event) mà JS engine thực thi

### 2. Javascript Engine

- Javascript Engine sẽ không đợt (ưu tiên thời gian cho cái gì) mà sẽ execute liên tục bất kì code nào ⇒ 1 thread
- Không có một step có thể xác định để interrupt || leave khỏi thread
- Chạy đến đâu kết thúc đến đó
- Tức là cái trước phải finish trước khi cái sau start
- 1 process tách ra thành nhiều operations
- 2 processes chạy đồng thời khi trộn operations của cả 2 ⇒ 1 queue

⇒ Các operations chạy tuần tự nhưng process xử lý đồng thời

### setTimeout & setInterval

1. Gọi setTimeout thì nó sẽ tạo 1 bộ bấm giờ
2. Khi bộ bấm giờ đó hết thúc thì nó đẩy callback vào event loop
3. Nhớ là nó vào event loop trước rồi chờ đến lượt mới được xử lý
    - Chứ không phải cứ đến đúng thời điểm là được xử lý
- Nếu có 2 setTimeout cùng đặt vào 1 thời điểm thì 2 callback sẽ được xử lý tuần tự
- Tạo flag ở global để check hoạt động của mỗi processes.
- Dùng nhiều thủ thuật `setTimeout(eachStep, 0)`  ⇒ tạo nhiều timer ⇒ nặng RAM
- Thứ tự excute trong JS engine có thể không giống với thứ tự trong code

## Single Threading

- Cơ chế **đơn luồng**

### Single Threading có lợi ích gì?

1. Tập trung xử lý từng vấn đề độc lập
    - Với đa luồng thì CPU sẽ phải chia tài nguyên cho tất cả các luồng
    - Nhưng với cơ chế đơn luồng thì chỉ xử lý 1 vấn đề tại 1 thời điểm
    - Do đó tốc độ xử lý 1 vấn đề sẽ nhanh gấp mấy lần đa luồng
    - Có khi 1 vấn đề chỉ xử lý trong 1 nghìn phần giây
    - Thì chỉ có nhận thức của Superman hay Flash mới nhận ra được
2. Bộ nhớ không bị xung đội
    - Với đa luồng không chỉ CPU mà bộ nhớ tạm như RAM cũng sẽ chia sẻ với các luồng
    - Ví dụ cho 1 biến A
    - Mà Thread 1 và Thread 2 cùng sử dụng A cùng 1 thời điểm
    - Thì chắc chắn sẽ bị lỗi
    - Còn đơn luồng thì nó là độc tôn rồi
    - Sẽ chỉ có chuyện code ngố thôi chứ hệ thống của JS không bao giờ tự gây lỗi bộ nhớ được
3. Luồng hoạt động liên tục
    - Đa luồng thì có luồng làm ít, luồng làm nhiều
    - Thì luồng nào làm ít thì xong trước thì cứ chờ ở đó, gây tốn tài nguyên vì vẫn phải duy trì luồng đó
    - Còn đơn luồng công việc làm liên tục
    - Chưa tắt phần mềm thì nó còn chạy

## Async Console

---

- Do I/O chậm và bị chặn bởi các event khác nên `console.log` sẽ có thể chậm vài mini giây
- Do chậm nên dùng `console.log` cho các biến reference sẽ hiển thị giá trị cuối cùng của nó chứ không phải giá trị tại vị trí gọi log

---

- Some browsers and some conditions make `console.log(..)` **not actually immediately output** what it's given
- The main reason this may happen is because `I/O is a very slow` and `blocked by many programs`

# Event Loop

---

- Event Loop là 1 hàng chờ tuân theo quy tắc `First-in First out`.
    1. Sự kiện đầu kích hoạt (hay còn gọi là trigger) ⇒ nó được đưa vào event loop
    2. JS engine thấy event loop có sự kiện thì lấy cái gần nhất ra xử lý
    3. Sự kiện thứ 2 được đẩy vào thì sẽ phải chờ sự kiện đầu xử lý xong
    4. Rồi sự kiện thứ 3 tiếp tục đưa vào hàng chờ và đợi cái thứ 2 xong mới được thực hiện
- Event loop như 1 cái to-do list cho thread
    1. Thread sẽ xử lý tuần tự những task trong Event loop
    2. Event loop rỗng thì Thread sẽ tạm dừng
    3. Đẩy sự kiện vào Thread thì nó lại chạy tiếp

---

- Javascript = combination of
    - `Synchronous` event = being `one after another`.
    - `Asynchronous` event = `callbacks` or `promises`.
- The Event Loop is a `queue of events` based on `First-in First out`.
    1. The `first event is fired`, it is `pushed into event loop` and `executed immediately`. 
    2. The `second event fired` is also `pushed into event loop`.
        - If `first event isn’t finish`, `second event` will `wait` until the `first is finish` to be executed.
    3. The `third event and then` will also `repeat this queue process`.
- The event loop like a `to-do list for singke thread`.
    1. Thread `execute sequentially` all tasks in that to-do list 
    2. Until `anything left`, it goes to `sleep`.
    3. Once an `event gets into the queue`, it `wakes up` and `does` this thing `all over again`.
- The JS engine runs inside a `hosting environment`.
    - It `doesn't` run in `isolation`.
- Each loop = `1 time` environment `thread call` into JS engine.
- JS engine `executes any JS code arbitrary`.
    - It `doesn’t make priority` to anything.
    - `Environment` will `arrange` the `order of “events”` to be handled.
- When a single `thread picks up an event` and and that even happens to be a `function that calls another function`, the single thread will `follow that stack of function calls` until the first function has `completed executing all of nested function`.
    - The calls is usually managed by most runtimes using call stack - a stack data structure.

```jsx
// `eventLoop` is an array that acts as a queue (first-in, first-out)
var eventLoop = [ ];
var event;

// keep going "forever"
while (true) {
  // perform a "tick" = each iteration of this loop
  if (eventLoop.length > 0) {

    // get the next event in the queue
    event = eventLoop.shift();

    // now, execute the next event
    try {
      event();
    } catch (err) {
      reportError(err);
    }
  }
}
```

- `setTimeout` `doesn’t push` the `callback` into the event loop `immediately`.
    1. Environment `creates a timer` to `wait until needed`.
    2. When `timer is expired`, it `pushes callback into event loop`.
    3. Push at the `right time into queue`, it means callback `isn’t executed immediately`.
        - It has to `wait for previous callbacks to be done` before its turn is processed.

### Parallel Threading

- Tools for `parallel computing` are `processes` and `threads`.
- Processes and threads execute
    - `Independently`
    - `Simultaneously`
    - `Multiple threads` can `share the memory` of a `single process`.
- Threaded programming is very tricky
    - `Don't` take `special steps` to `prevent` this kind of `interruption/interleaving` from happening
- An event loop `breaks its work` into `tasks` and `executes them in serial`
    - It work on `single-threaded environment`.
    - It is based on mechanism `Run to Completion`
    - It **disallows parallel access** and **changes** to **shared memory**.
- Not worry about indeterminacy when processing ⇒ JS is always determinacy.

## Concurrency

---

1. Chia mỗi task thành các sub-tasks cực nhỏ
2. Trộn lẫn các sub-tasks thành 1 hàng
3. Rồi xử tuần tự từng sub-task
- Tại 1 thời điểm cả 2 tasks lớn cùng trong quá trình xử lý
- Mỗi sub-task được xử lý quá nhanh gần như tức thì
- Tiếp theo vì xen kẽ các sub-tasks nên task sau sẽ không phải đợi task trước hoàn thành 100%

---

- JS process = `virtual process` = task
    - `Represent` by a `logically connected`
    - This is a `sequential series of operations`
- Concurrency = `two or more processes` are `executing simultaneously` over the `same period`
    - Regardless of whether their own operations occur in parallel.

### Cooperation

- When need to `cooperate between two processes`, `break` each process `into small steps`.
    1. Gives the opportunity to `interleave the process's steps`.
    2. `Execute` each step `sequentially`. 
    3. Because the two processes are `not completed at the same time`, they look like `concurrency`.

<aside>
💡  `setTimeout(eachStep, 0)` hack for async scheduling

</aside>

- Means "stick this function at the end of the current event loop queue."
1. Create timer
2. The timer will insert the event at its next opportunity.
- In Node.js, `setTimeout(eachStep, 0) = process.nextTick(eachStep)`

### Noninteracting

- To `avoid indeterminacy`, `avoid the interaction` of two processes
    - Create `different variables` that are only used in the `scope of each process`.

### Interaction

- If the `impact is unavoidable`, `partition` | `explicit conditions` for `each process`.

## Jobs

- `Job queue`  là một phiên bản nhỏ hơn của Event Loop
- `Job queue` sẽ được xử lý tại cuối mỗi phiên trong Event loop
- Job là 1 hành động nhỏ được thêm vào cuối phiên tại của `Job queue`
- 1 Job có thể tạo thêm Job khác và cho vào cuối hàng đợi

---

`Job queue` = `new concept layered` on top of the `event loop queue`.

- Queue `hanging off` the `end of every tick` in the `event loop queue`.
- Job = certain `asynchronous-implied action` added to `end of current tick`'s Job queue.
    
    ⇒ Job = `do later` but it happens `before next tick`
    
- A Job can also `cause more Jobs` to be `added to the end of the same queue`
    - `Job "loop”` = a Job that `keeps adding another Job`
    
    <aside>
    ⚠️ Avoid to move to next tick
    
    </aside>
    

---

[Statement ordering of the Event loop](Statement%20ordering%20of%20the%20Event%20loop%201aad8658dce341899dfe528daa55639b.md) 

---

- **Vocabulary**
    - Isolation = cô lập
    - Arbitrary = bất kỳ; tuỳ ý
    - Arrange = quyết định
    - Independently = độc lập
    - Simultaneously = đồng thời
    - Concurrency: đồng thời
    - Interaction: tác động
    - Noninteracting: không tác động
    - Partition: phân vùng
    - Explicit: rõ ràng
    - Serial: nối tiếp

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

# Statement ordering of the Event loop

Category: Javascript
First Source: Event%20Loop%202b01a5971ff141aa824b2992a51339d4.md
Tags: Concept, Low

- A JavaScript program is (practically) always broken up into two or more chunks.
- Current event = where the first chunk runs now
    - Next event = next chunk runs later
- The Event Loop is composed of the following six phases, which are repeated for as long as the application still has code that needs to be executed:
1. **Timers:** Callbacks scheduled by `setTimeout()` or `setInterval()` are executed in this phase.
2. **I/O Callbacks:** Executes I/O callbacks deferred to the next loop iteration.
3. **Waiting / Preparation:** Internally used only
4. **I/O Polling:** This is the phase in which all the JavaScript code that we write is executed, starting at the beginning of the file, and working down.
5. **`setImmediate()` callbacks:** It invokes `setIntermediate()` callbacks.
6. **Close events:** This phase executes the callbacks of all *close* events.