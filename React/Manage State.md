# Manage State

Category: React
First Refrence: How%20many%20ways%20to%20manage%20state%20in%20application%205bd405b7b7e1493da8293e76408fa8c6.md
Tags: Concept, Low

## Local state

- Local state is data we manage in one or another component.
- Local state is most often managed in React using the `useState` or `useReducer`.

## Global state

- Global state is data we manage across multiple components.
- Global state is necessary when we want to get and update data anywhere in our app, or in multiple components at least.

## Server state

- Data that comes from an external server that must be integrated with our UI state.
- Server state is a simple concept, but can be hard to manage alongside all of our local and global UI state.

## URL state

- Data that exists on our URLs, including the pathname and query parameters.
- Using React Router, get all the information using `useHistory` or `useLocation`.