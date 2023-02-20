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