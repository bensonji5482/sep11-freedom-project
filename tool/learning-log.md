# Tool Learning Log

## Tool: **React**

## Project: **To-do list**

---

### 9/29/25: Day 1
* I changed the “Add” button by adding inline styles such as background color, padding, and rounded corners as well as changing the label to “Add Task ✅.” The small visual tweak makes the button stand out and shows that I adjusted the UI beyond the starter code.
    * Original `<button onClick={addTask}>Add</button>`
    * After `<button onClick={addTask} style={{ backgroundColor: "#4CAF50", color: "white", padding: "5px 10px", borderRadius: "5px" }}> Add Task ✅ </button>`

### 10/6/25: Day 2
```js
const [todos, setTodos] = useState([]);
const [inputText, setInputText] = useState('');
```
* `todos` is an array of todo items (objects with `id`, `text`, and `completed`).
* `inputText` holds the current text input value from the user.
```js
const addTodo = () => {
  setTodos([...todos, { 
    id: Date.now(), 
    text: inputText, 
    completed: false 
  }]);
  setInputText('');
};
```
* This adds a new todo to the list.
* Uses the **spread operator** to create a new array (for immutability).
* The new todo gets a unique `id` from `Date.now()` and a `completed` status set to `false`.
* Clears the input text after adding.
```js
const toggleTodo = (id) => {
  setTodos(todos.map(todo =>
    todo.id === id ? { ...todo, completed: !todo.completed } : todo
  ));
};
```
* Toggles the `completed` status of a todo item by its `id`.
* Uses `.map()` to create a **new array** where only the matched todo is updated.
* Again, uses spread syntax (`{ ...todo, completed: !todo.completed }`) to ensure immutability.


<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
