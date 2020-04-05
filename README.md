# todomvc-revisited

This project explores the use of state machine developed in a [previous project](https://github.com/mapteb/js-state-machine-v2) to the [TodoMVC problem](http://todomvc.com/). Plain vanilla Javascript is used to illustate the idea.

## Source

All the HTML and javascript source needed is in one [todoApp.html](https://raw.githubusercontent.com/mapteb/todomvc-revisited/master/docs/todoApp.html) file.

## Demo

An online demo of this application is available at the [Todo App](https://mapteb.github.io/todomvc-revisited/todoApp.html).

## Usage

To use this framework the following steps are suggested:

1. Write the state transitions (see the table below for an example)
2. Configure the states and events in JavaScript const variables.
   See appStates and appEvents in the [HTML file](https://raw.githubusercontent.com/mapteb/todomvc-revisited/master/docs/todoApp.html).
3. Setup the HTML template,
   Identify the Comp tags for the application.
   See the InputComp, CheckboxGroupComp and ButtonComp tags  used in this demo.
4. Create the helper functions needed for the processors.
   See the appEvents object for an example.

The state transitions assumed for the demo TodoMVC app are:

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

## Salient Features

Some interesting features of the proposed framework include:

1. Enforces use of state machine and therefore ensures robust application.
2. The helper functions (like createInputTextElement, createInputCheckboxElement, etc.) that support the processos can be reused in other projects. he modular nature of these functions suggest maybe these functions could be swapped with web components. See, for instance, the next version of this project - [State Transitions with Web Components](https://github.com/mapteb/state-transitions-with-webcomponents)
3. The state transitions table serve both as requirements and as a checklist of test cases.

### More Info

More info about this project is also available at:  [dzone](https://dzone.com/articles/the-todomvc-revisited)
