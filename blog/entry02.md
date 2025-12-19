# Entry 2
##### 12/17/25

### New changes
Previously I took some code from react.js and with [this link](https://react.dev/learn/you-might-not-need-an-effect) I can access significant parts for my freedom project. Recently when I took this code all it could do was simply to show what is completed already and what isn't by simply checking a box and there is a space where you can type and add a task. Then I did make a small little tweak. Since I was work loaded on the week I am writing this I was only able to add some small things that had to do with Memo. The part that was added made it so that you can't simply just leave the typing part empty to add a empty task.
```js
import { useState, useMemo, useCallback } from 'react';
import { initialTodos, createTodo } from './todos.js';

export default function TodoList() {
  const [todos, setTodos] = useState(initialTodos);
  const [showActive, setShowActive] = useState(false);

  const activeTodos = useMemo(
    () => todos.filter(todo => !todo.completed),
    [todos]
  );

  const visibleTodos = showActive ? activeTodos : todos;

  const handleAddTodo = useCallback(
    (text) => {
      setTodos(prevTodos => [...prevTodos, createTodo(text)]);
    },
    []
  );

  return (
    <>
      <label>
        <input
          type="checkbox"
          checked={showActive}
          onChange={e => setShowActive(e.target.checked)}
        />
        Show only active todos
      </label>

      <NewTodo onAdd={handleAddTodo} />

      <ul>
        {visibleTodos.map(todo => (
          <li key={todo.id}>
            {todo.completed ? <s>{todo.text}</s> : todo.text}
          </li>
        ))}
      </ul>

      <footer>
        {activeTodos.length} todos left
      </footer>
    </>
  );
}

function NewTodo({ onAdd }) {
  const [text, setText] = useState('');

  function handleAddClick() {
    if (!text.trim()) return; // prevents empty todos
    onAdd(text);
    setText('');
  }

  return (
    <>
      <input
        value={text}
        onChange={e => setText(e.target.value)}
        placeholder="New todo"
      />
      <button onClick={handleAddClick}>
        Add
      </button>
    </>
  );
}
```
### EDP
I am currently on the stage of `changing things about the code I took to make it better` for a `to-do list project`. By `changing` stuff about the code I took from react.js, I can potentially `upgrade my code` to `slowly make it better` as I continue `using react.js` for `more things to test`. Basically probably `second` stage of EDP (didn't check the list).

### Takeaways


[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
