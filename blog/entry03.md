# Entry 3
##### 2/3/26

### More changes
Previously I have been trying to modifiy the code that I got from `[this link](https://react.dev/learn/you-might-not-need-an-effect)` to make the to-do list work better. Last time I added a part of code called useMemo. This in turn efficiently computes active todos so it doesn't recalculate every single time, makes it easy to toggle which todos are available and creates a stable function to avoid bugs.
```js
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
```
However I made some improvement and enhancements to the code by making the things more usable and made things work more properly. And by fixing those features, the todo list looks much better and more functionable. This is the code that I added ...
```js
const [filter, setFilter] = useState('all');

  const activeTodos = useMemo(
    () => todos.filter(todo => !todo.completed),
    [todos]
  );

  const completedTodos = useMemo(
    () => todos.filter(todo => todo.completed),
    [todos]
  );

  const visibleTodos = useMemo(() => {
    if (filter === 'active') return activeTodos;
    if (filter === 'completed') return completedTodos;
    return todos;
  }, [filter, todos, activeTodos, completedTodos]);

  const handleAddTodo = useCallback(
    (text) => {
      setTodos(prevTodos => [...prevTodos, createTodo(text)]);
    },
    []
  );

  const handleToggleTodo = useCallback((id) => {
    setTodos(prevTodos =>
      prevTodos.map(todo =>
        todo.id === id
          ? { ...todo, completed: !todo.completed }
          : todo
      )
    );
  }, []);

  const handleDeleteTodo = useCallback((id) => {
    setTodos(prevTodos => prevTodos.filter(todo => todo.id !== id));
  }, []);
```
What this code did to help my todo list was that it improved some of the functionalitys of the todo list such as, fixing the checkboxes from active only to 3 different sections. All, completed and active. Another functionality that was fixed from the todo list was being able to toggle whether if the item is done or able to be deleted. Another functionality it fixed was the dervived state which only had active but now it also has completed.

### EDP
Using [this link](https://hstatsep.github.io/students/) here, I am able to check what process I am at. Simple click on EDP on the page to access it. Right now I am on the process 3-7, as I am just adding and testing the code repeatedly until I get the results that I want from it and I am still tryiing to work on making it more and more better.

### Takeaways
I learned to `persevere` by continuing to make the code better and better even though it is not the results I like. I also learned to `take my time` because I always panic when I think that I don't have time to finish the freedom project but by taking my time, I realized that I have lots of time to edit and change th code to insert it into my freedom project with some HTML and CSS.


[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
