# todomvc-revisited

This project explores the use of state machine developed in a [previous project](https://github.com/mapteb/js-state-machine-v2) to the [TodoMVC problem](http://todomvc.com/). Plain vanilla Javascript is used to illustate the idea.

## Source

All the HTML and javascript source needed is in one [todoApp.html](https://raw.githubusercontent.com/mapteb/todomvc-revisited/master/docs/todoApp.html) file.

## Demo

An online demo of this application is available at the [Todo App](https://mapteb.github.io/todomvc-revisited/todoApp.html).

The State transition for each UI action is printed at the top of the above page.

The following state transitions are implemented:

<pre>
=================================================================================================================================
     Initial State              |  Pre-event |   Processor      |      Post-event               |     Final State
=================================================================================================================================
uknownState                     - onload     - processOnload     - onloadSuccess                 - readyForAdd 
readyForAdd                     - addTodo    - processAddTodo    - addTodoSuccessNoneSelected    - readyForAddSelect
readyForAddSelect               - addTodo    - processAddTodo    - addTodoSuccessNoneSelected    - readyForAddSelect
readyForAddSelect               - changeTodo - processChangeTodo - changeTodoSuccessSomeSelected - readyForAddSelectUnselectDelete 
readyForAddSelect               - changeTodo - processChangeTodo - changeTodoSuccessAllSelected  - readyForAddUnselectDelete
readyForAddUnselectDelete       - addTodo    - processAddTodo    - addTodoSuccessSomeSelected    - readyForAddSelectUnselectDelete
readyForAddUnselectDelete       - changeTodo - processchangeTodo - changeTodoSuccessNoneSelected - readyForAddSelect
readyForAddUnselectDelete       - changeTodo - processchangeTodo - changeTodoSuccessSomeSelected - readyForAddSelectUnselectDelete
readyForAddUnselectDelete       - deleteTodo - processDeleteTodo - deleteTodoSuccessAllDeleted   - readyForAdd
readyForAddSelectUnselectDelete - addTodo    - processAddTodo    - addTodoSuccessSomeSelected    - readyForAddUnselectDelete
readyForAddSelectUnselectDelete - changeTodo - processChangeTodo - changeTodoSuccessAllSelected  - readyForAddUnselectDelete
readyForAddSelectUnselectDelete - changeTodo - processChangeTodo - changeTodoSuccessSomeSelected - readyForAddSelectUnselectDelete
readyForAddSelectUnselectDelete - changeTodo - processChangeTodo - changeTodoSuccessNoneSelected - readyForAddSelect
readyForAddSelectUnselectDelete - changeTodo - processChangeTodo - changeTodoSuccessSomeSelected - readyForAddSelectUnselectDelete
readyForAddSelectUnselectDelete - deleteTodo - processDeleteTodo - deleteTodoSuccessNoneSelected - readyForAddSelect
</pre>

### More Info

More info about this project is also available at:  [dzone](https://dzone.com/articles/the-todomvc-revisited)
