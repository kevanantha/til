# Three Ways To Handle `onClick` e.g Delete Todo

## Currying

```jsx
const App = () => {
  const [todos, setTodos] = useState([])

  const onDeleteTodo = (id) => () => {
    setTodos((prevTodos) => prevTodos.filter((todo) => todo.id !== id))
  }

  return <TodoList todos={todos} onDeleteTodo={onDeleteTodo} />
}

const TodoList = ({ todos, onDeleteTodo }) => (
  <ul>
    {todos.map((todo) => (
      <li key={todo.id} onClick={onDeleteTodo(todo.id)}>
        {todo.text}
      </li>
    ))}
  </ul>
)
```

## Anonymous Function

```jsx
const App = () => {
  const [todos, setTodos] = useState([])

  const onDeleteTodo = (id) {
    setTodos((prevTodos) => prevTodos.filter((todo) => todo.id !== id))
  }

  return <TodoList todos={todos} onDeleteTodo={onDeleteTodo} />
}

const TodoList = ({ todos, onDeleteTodo }) => (
  <ul>
    {todos.map((todo) => (
      <li key={todo.id} onClick={() => onDeleteTodo(todo.id)}>
        {todo.text}
      </li>
    ))}
  </ul>
)
```

## Bind

```jsx
const App = () => {
  const [todos, setTodos] = useState([])

  const onDeleteTodo = (id) {
    setTodos((prevTodos) => prevTodos.filter((todo) => todo.id !== id))
  }

  return <TodoList todos={todos} onDeleteTodo={onDeleteTodo} />
}

const TodoList = ({ todos, onDeleteTodo }) => (
  <ul>
    {todos.map((todo) => (
      <li key={todo.id} onClick={onDeleteTodo.bind(null, todo.id)}>
        {todo.text}
      </li>
    ))}
  </ul>
)
```

---

## Refs

- [Stackoverflow](https://stackoverflow.com/questions/51977823/type-void-is-not-assignable-to-type-event-mouseeventhtmlinputelement)

## Tags
- #react
