# Hook concept

Category: React
First Refrence: How%20many%20types%20of%20components%20React%20510e1cbf8aa04304a20157c381d69758.md, Different%20class%20component%20and%20functional%20component%20d1887a8015ab46e7b1f9bc1de1974b81.md, What%20is%20Hook%20e2af3d601ca3464897d6d2f20388f33b.md, Why%20React%20need%20Hook%20a53cc3fc40ba4bb2b8d2826e6fb23dab.md
Tags: Basic, Concept

## Concept

- Hooks are backwards-compatible.
- Hooks are functions that let you “hook into” React state and lifecycle features from functional components.
- They let using React without classes.

### Problems with React class component

- **It’s hard to reuse stateful logic between components.**
    - React doesn’t offer a way to “attach” reusable behavior to a component.
    - Class components design use render props and higher-order components that try to solve this.
    - *Hooks allow you to reuse stateful logic without changing component hierarchy.*
- **Complex components become hard to understand.**
    - Old lifecycle has many status ⇒ when fetching data will be scattered.
    - Components might perform some data fetching in `componentDidMount` and `componentDidUpdate`. However, the same `componentDidMount`method might also contain some unrelated logic that sets up event listeners, with cleanup performed in `componentWillUnmount`.
    - *Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data).*
- **Classes confuse both people and machines.**
    - People can understand props, state, and top-down data flow perfectly well but still struggle with classes.
    - The distinction between function and class components in React and when to use each one leads to disagreements even between experienced React developers.
    - *Hooks let you use more of React’s features without classes.*

---

# Vocabulary

- hook: cái móc
- backwards-compatible: sự tương thích ngược
- hierarchy: hệ thống cấp bậc
- scatter: rải rác