# Entry 4
##### 3/9/2026

### Content
I have now started to make my freedom project and I have an entire plan based on the timelines that I will create my freedom project by the due date of April 13,2026. The [plan](https://github.com/bensonji5482/sep11-freedom-project/blob/main/prep/plan.md) entails things that I would do for the html part and the js part to make my freedom project functional which in this case would be a to-do list. A to-do list has many functions such ass adding and deleting tasks, sections to display different parts, numbers to show how much tasks you have and so on.

### EDP
I am currently just on stage 6 and 7 where I am currently juts making and testing the to-do list that I currently have by starting off with making the outline for how the to-do list would look using HTML elements to customize the looks and how the user will see the to-do list. This is the outline for the to-do list using HTML ...
```html
<div class="container">
        <header>
            <h1>Simple To-Do List</h1>
            <p class="subtitle">Get things done, one task at a time</p>
        </header>

        <div class="todo-app">
            <div class="input-section">
                <input
                    type="text"
                    id="todo-input"
                    placeholder="What needs to be done?"
                >
                <button id="add-btn">Add Task</button>
            </div>

            <div class="filters">
                <button class="filter-btn active" data-filter="all">All</button>
                <button class="filter-btn" data-filter="active">Active</button>
                <button class="filter-btn" data-filter="completed">Completed</button>
            </div>

            <div class="todo-stats">
                <span id="total-tasks">Total: 0</span>
                <span id="completed-tasks">Completed: 0</span>
                <span id="remaining-tasks">Remaining: 0</span>
            </div>

            <ul class="todo-list" id="todo-list">
                <div class="empty-state">
                    <div class="empty-icon">📝</div>
                    <p>No tasks yet</p>
                </div>
            </ul>
        </div>
    </div>
```
What this did was create a box with an input, 3 sections for the tasks, buttons to add an task, as well as a counter that will later be used by writing some js that manipulates the DOM which is basically how the user will interact with the website. Right now for the js part so far I only have some code that waits until the website is loaded so that it uses `document.querySelector()` to select the elements to control them. This is what I have so far in my js right now ...
```js
document.addEventListener('DOMContentLoaded', function () {
            // selecting elements
            const todoInput = document.getElementById('todo-input');
            const addBtn = document.getElementById('add-btn');
            const todoList = document.getElementById('todo-list');
            const filterBtns = document.querySelectorAll('.filter-btn');
            const totalTasks = document.getElementById('total-tasks');
            const completedTasks = document.getElementById('completed-tasks');
            const remainingTasks = document.getElementById('remaining-tasks');
```

###






[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
