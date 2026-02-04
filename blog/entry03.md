# Entry 3
##### 2/3/26

### More changes
Previously I have been trying to modifiy the code that I got from [this link](https://react.dev/learn/you-might-not-need-an-effect) to make the to-do list work better. Last time I added a part of code called useNemo
`js
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
`


[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
