# React Basic

Category: React
First Refrence: What%20is%20Virtual%20DOM%2083ed1eea91844ed38b7b2a12a1811038.md, What%20is%20ShadowDOM%20c40ecb6d7cfe4563abefdcd444c19b36.md, What%20is%20the%20difference%20between%20ShadowDOM%20and%20Virtu%2097bc6e7e21f447969ce23528d7a97009.md, What%20is%20JSX%209aa006cf295148a2b6f92e5f7e562cfb.md, Why%20need%20to%20use%20render()%20in%20React%2004debc7ac80b4dcb8bb2a78138cbba3a.md, Have%20you%20ever%20integrated%20jQuery%20into%20your%20React%20pr%20e85068aa36fd41fcb7d1182e0469dfb0.md, How%20to%20paging%20by%20scroll%20bce8d0daa16f464f9da9c4837ae22065.md, Does%20React%20component%20need%20to%20define%20internal%20compo%20264d9c767af14ba8a4ef23fc9ce26e8b.md
Tags: Basic, Concept

## Virtual DOM

- `The virtual DOM` (VDOM) is a programming `concept` that `representation of a UI` is kept in `memory` and `synced` with the `“real” DOM` by a `library` such as ReactDOM.
    - The virtual DOM is a concept implemented by libraries in JavaScript on top of browser APIs.****
- Virtual DOM is a `lightweight JavaScript data format` that is used to `represent` the `content` of the `DOM` at a given `point in time`.
    - It has all the `same properties` as the `DOM` but is `not` as `interoperable` as the DOM.
    - When the `state changes`, `update` the `Virtual DOM first` and then `find` the `corresponding element` on the `real DOM` and to `re-render only it`.
- React `abstracts` away the `DOM` from you, giving a `simpler programming model` and `better performance`.

### Shadow DOM

<aside>
💡 A Shadow DOM is a `hidden DOM` which can be `attached` to any element `inside real DOM`.

</aside>

- `The Shadow DOM` is a `browser technology` designed primarily for `scoping variables` and `CSS` in `web components`.
- It works `like a normal DOM`.
- In Shadow DOM, `all of its markup and style will be scoped`.
- It refers to the browser’s potential to `add` a `subtree of DOM elements` into the `rendering of a document`, but `not` into the `DOM tree` of the `main document`.

| Virtual DOM | Shadow DOM |
| --- | --- |
| It revolves around solving performance issues. | It revolves around the concept of encapsulation. |
| It is a complete representation of an actual DOM.	 | It is not a complete representation of the entire DOM. |
| It groups together several changes and does a single re-render instead of many small ones.	 | It adds a subtree of DOM elements into the rendering of a document, instead of adding it to the main document’s DOM tree. |
| It creates a copy of the whole DOM object.	 | It creates small pieces of the DOM object having their own, isolated scope. |
| It does not isolate the DOM.	 | It isolates the DOM. |
| It does not help with CSS scoping.	 | It helps with CSS scoping. |

## Render function

- Every React component is `required` to have the `render()` function.
- The `render()` function `returns only` the `React element`.
- The `render()` function is a specific `description of the UI` at `any given time`.
- So if the `data changes`, React will perform the `UI update` with the `corresponding data`.
- When the data changes, React will `automatically call` the `render()` function to update the UI.

### JSX

- JSX is a `syntax extension` to Javascript `used in ReactJS` that allows writing `Javascript` that looks `similar to HTML`.
- `After the compilation`, the JSX is translated to `React.createElement` calls.
- JSX just provides `syntactic sugar` for the `React.createElement(component, props, ...children)` function.
- Using JSX to create `HTML elements` as a `JavaScript code`, that will be `placed inside the DOM without` using `createElement()` or `appendChild()` methods.

---

# Vocabulary

- Integrate: tích hợp
- Potential: có tiềm năng
- Interoperable: có thể tương tác
- Corresponding: phù hợp