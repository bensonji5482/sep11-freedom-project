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

### 11/10/2025 Day 3
```js
useEffect(() => {
  const savedTodos = localStorage.getItem('todos');
  if (savedTodos) {
    setTodos(JSON.parse(savedTodos));
  }
}, []);
```
* Runs only once when the component first loads (because of the empty dependency array `[]`).
* Looks in the browser’s `localStorage` for saved todos.
* If found, it loads them into the `todos` state using `setTodos`.
* This makes todos persist between page reloads.
```js
useEffect(() => {
  localStorage.setItem('todos', JSON.stringify(todos));
}, [todos]);
```
* Runs every time `todos` changes.
* Saves the current `todos` array into `localStorage`.
* Keeps your list synced with the browser’s storage.
```js
useEffect(() => {
  document.title = `Todos: ${todos.filter(t => !t.completed).length} remaining`;
}, [todos]);
```
* Runs every time `todos` changes.
* Counts how many todos aren’t completed (`!t.completed`).
* Updates the browser tab’s title (e.g. “Todos: 3 remaining”).

### 11/17/2025 Day 4
```js
const [inputText, setInputText] = useState('');
```
* Creates a state variable called **inputText** to store what the user types.
* `setInputText` updates that text.
```js
const handleInputChange = (event) => {
  setInputText(event.target.value);
};
```
* Runs **every time the user types** in the box.
* Updates the state with the current input value.
```js
const handleSubmit = (event) => {
  event.preventDefault(); // stops page reload
  if (inputText.trim()) {
    addTodo();
  }
};
```
* Prevents the form from refreshing the page.
* Checks if the input isn’t empty.
* Calls `addTodo()` — presumably a function that adds the todo to a list.
* ⚠️ **Important:** `addTodo()` isn’t defined here — it must be passed in as a prop or created elsewhere.
```js
const handleKeyPress = (event) => {
  if (event.key === 'Enter') {
    handleSubmit(event);
  }
};
```
* Detects when the user presses **Enter** inside the input.
* Makes Enter behave exactly like clicking the Add button.
```js
<form onSubmit={handleSubmit}>
  <input
    type="text"
    value={inputText}
    onChange={handleInputChange}
    onKeyPress={handleKeyPress}
    placeholder="Add a todo..."
  />
  <button type="submit">Add</button>
</form>
```
* A form with:
   * A controlled input field (it uses React state for its value)
   * An "Add" button
* Submitting works by:
   * Pressing Enter
   * Clicking the button

### 12/1/2025: Day 5
The parent component renders a list of TodoItem components
```js
<TodoItem 
  key={todo.id}
  todo={todo}
  onToggle={toggleTodo}
  onDelete={deleteTodo}
/>
```
* For each `todo` in the list, the parent creates a `<TodoItem />`.
* It passes:
  * the actual todo data (`todo`)
  * a function to toggle it (`toggleTodo`)
  * a function to delete it (`deleteTodo`)
The child component displays a single todo
```js
const TodoItem = ({ todo, onToggle, onDelete }) => {
  return (
    <div className={`todo-item ${todo.completed ? 'completed' : ''}`}>
      <input
        type="checkbox"
        checked={todo.completed}
        onChange={() => onToggle(todo.id)}
      />
      <span>{todo.text}</span>
      <button onClick={() => onDelete(todo.id)}>Delete</button>
    </div>
  );
};
```
* Inside the child:
* Shows the todo text
  * The `<span>` displays whatever text is stored in `todo.text`.
* Shows whether it's completed
* The checkbox uses:
```js
checked={todo.completed}
```
So it automatically reflects the todo’s current state.
* Calls back to the parent when the checkbox changes
* When the user clicks the checkbox:
```js
onToggle(todo.id)
```
This tells the parent which todo to toggle.
* Calls back to the parent when the Delete button is clicked
```js
onDelete(todo.id)
```
This tells the parent to delete that todo.
The child NEVER changes state itself
It only displays info and triggers events.
The parent updates the actual list of todos.

### 12/8/2025: Day 6
```js
{todos.map(todo => (
  <TodoItem
    key={todo.id} // Helps React identify which items changed
    todo={todo}
    onToggle={toggleTodo}
  />
))}
```
`todos.map(...)`
* This is looping over an array called `todos`.
* For each `todo` in the array, it creates a `<TodoItem>` component.

`<TodoItem ... />`
* This is a child component representing a single todo item.
* `todo={todo}` passes the data for that todo to the component.
* `onToggle={toggleTodo}` passes a function so the item can be marked complete/incomplete.

`key={todo.id}`
* The key is a special prop in React.
* It must be unique for each item in the list.
* React uses it in its reconciliation process to figure out which items changed, were added, or removed.

Why Keys Matter
* Imagine a list of items like boxes in a moving truck.
* Without keys, React doesn’t know which box is which. If one box moves, React might unnecessarily re-render all boxes instead of just the one that changed.
* With keys, React can match each box to its previous position and only update what actually changed.
































<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
