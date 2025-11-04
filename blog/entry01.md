# Entry 1
##### 11/3/2025

### Content
I `took this code from react js` and what this code does is that `first it has a total of 3 items` in the todo list and `2 of them is completed`, by `having a space to type something out` and `having a button to add`, you can add another item to the list. The only `downside` to this is that you `can't mark` the `item complete` since it `has to be hard coded` to make it complete and the `button only hides todos` that `are done` which is `useless` unless I `can mark it done` but this is just a `basic start` to what `I can do` with react. By using [this link](https://react.dev/learn/you-might-not-need-an-effect) here, I am able to access some key parts that I can use for my freedom project.

```js
import { useState } from 'react';
import { initialTodos, createTodo } from './todos.js';

export default function TodoList() {
  const [todos, setTodos] = useState(initialTodos);
  const [showActive, setShowActive] = useState(false);
  const activeTodos = todos.filter(todo => !todo.completed);
  const visibleTodos = showActive ? activeTodos : todos;

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
      <NewTodo onAdd={newTodo => setTodos([...todos, newTodo])} />
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
    setText('');
    onAdd(createTodo(text));
  }

  return (
    <>
      <input value={text} onChange={e => setText(e.target.value)} />
      <button onClick={handleAddClick}>
        Add
      </button>
    </>
  );
}
```

### EDP
I am currently on the stage of `trying` to `figure out various things about my tool` and `how to get access to the parts that I need` for a `to-do list project`. Bascially more like between the `first and second stages` as I want to see `what the tool offers` then I can try to `outline my own thoughts` onto a `separate document` or a `spread sheet` to see how far I can go and progress over time.

### Skills I learned 
I learned to try and be more `observant` since I `need to look over` the tool `multiple times` since it is hard to use and by being observant, I can at least understand it to a certain point in my learning. I also learned how to `manage my project`, because of my teacher I was able to learn how to do that since the `last year` I had this class. He taught us how to od blogs like the one I'm writing currently and had us take notes on lessons as well as letting us have our own time to learn our tools at a good pace.


[Next](entry02.md)

[Home](../README.md)
