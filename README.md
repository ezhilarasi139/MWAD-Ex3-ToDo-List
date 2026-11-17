# MWAD-Ex3-ToDo-List

# Ex03 To-Do List using JavaScript

## Date: 17.11.26
### Name : EZHILARASI N
### Reg No : 212224040088
## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM

### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM

The application is developed using HTML, CSS, and JavaScript.

#### index.html
```

<!DOCTYPE html>
<html>
<head>
    <title>My To-Do List</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="container">
        <h1>My To-Do List</h1>

        <div class="input-section">
            <input type="text" id="taskInput"
                   placeholder="Enter your task">

            <button onclick="addTask()">Add Task</button>
        </div>

        <ul id="taskList"></ul>

        <button class="clear-btn" onclick="clearCompleted()">
            Clear Completed
        </button>
    </div>

    <script src="script.js"></script>
</body>
</html>

```

#### style.css

```

body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #667eea, #764ba2);
    margin: 0;
    padding: 0;
}

.container {
    width: 400px;
    margin: 80px auto;
    background: white;
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

h1 {
    text-align: center;
    color: #333;
}

.input-section {
    display: flex;
    gap: 10px;
}

input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

button {
    padding: 10px;
    background: #667eea;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background: #4c5acb;
}

ul {
    padding: 0;
    list-style: none;
}

li {
    background: #f2f2f2;
    margin-top: 10px;
    padding: 12px;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 8px;
}

.completed {
    text-decoration: line-through;
    color: gray;
}

.delete-btn {
    background: #e74c3c;
}

.edit-btn {
    background: #f39c12;
}

.clear-btn {
    width: 100%;
    margin-top: 15px;
    background: #333;
}

```

#### script.js
```

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function saveTasks() {
    localStorage.setItem("tasks", JSON.stringify(tasks));
}

function displayTasks() {
    let taskList = document.getElementById("taskList");
    taskList.innerHTML = "";

    tasks.forEach((task, index) => {
        let li = document.createElement("li");

        let span = document.createElement("span");
        span.textContent = task.text;

        if (task.completed) {
            span.classList.add("completed");
        }

        span.onclick = function() {
            tasks[index].completed = !tasks[index].completed;
            saveTasks();
            displayTasks();
        };

        let editButton = document.createElement("button");
        editButton.textContent = "Edit";
        editButton.className = "edit-btn";

        editButton.onclick = function() {
            let newTask = prompt("Edit your task:", task.text);

            if (newTask !== null && newTask.trim() !== "") {
                tasks[index].text = newTask.trim();
                saveTasks();
                displayTasks();
            }
        };

        let deleteButton = document.createElement("button");
        deleteButton.textContent = "Delete";
        deleteButton.className = "delete-btn";

        deleteButton.onclick = function() {
            tasks.splice(index, 1);
            saveTasks();
            displayTasks();
        };

        li.appendChild(span);
        li.appendChild(editButton);
        li.appendChild(deleteButton);

        taskList.appendChild(li);
    });
}

function addTask() {
    let input = document.getElementById("taskInput");
    let taskText = input.value.trim();

    if (taskText === "") {
        alert("Please enter a task!");
        return;
    }

    tasks.push({
        text: taskText,
        completed: false
    });

    input.value = "";
    saveTasks();
    displayTasks();
}

function clearCompleted() {
    tasks = tasks.filter(task => !task.completed);
    saveTasks();
    displayTasks();
}

displayTasks();

```

## OUTPUT

The To-Do List application allows users to add, edit, delete, and complete tasks. It also saves tasks using Local Storage.


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/becfd7a2-9272-470e-85fa-546b9d7126ee" />


## RESULT

The program for creating To-do list using JavaScript is executed successfully.
