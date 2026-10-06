<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Student Study Planner</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-gray-100">

    <!-- Header -->
    <header class="bg-blue-600 text-white text-center p-5">
        <h1 class="text-3xl font-bold">Student Study Planner</h1>
        <p class="mt-2">Plan your studies and stay organized</p>
    </header>


    <!-- Main Content -->
    <main class="max-w-3xl mx-auto p-5">

        <!-- Add Task -->
        <div class="bg-white p-5 rounded-lg shadow">

            <h2 class="text-xl font-bold mb-4">
                Add Study Task
            </h2>

            <div class="flex flex-col sm:flex-row gap-3">

                <input
                    type="text"
                    id="taskInput"
                    placeholder="Enter subject or task"
                    class="flex-1 border p-2 rounded"
                >

                <button
                    id="addTask"
                    class="bg-blue-600 text-white px-5 py-2 rounded hover:bg-blue-700"
                >
                    Add Task
                </button>

            </div>

        </div>


        <!-- Task List -->
        <div class="bg-white p-5 rounded-lg shadow mt-6">

            <h2 class="text-xl font-bold mb-4">
                My Study Tasks
            </h2>

            <ul id="taskList" class="space-y-3">
            </ul>

        </div>

    </main>


    <script>

        const input = document.getElementById("taskInput");
        const button = document.getElementById("addTask");
        const taskList = document.getElementById("taskList");


        // Add task
        button.addEventListener("click", function () {

            let task = input.value.trim();

            if (task === "") {
                alert("Please enter a task!");
                return;
            }

            // Create list item
            let li = document.createElement("li");

            li.className =
                "flex items-center justify-between bg-gray-100 p-3 rounded";


            // Task text
            let span = document.createElement("span");

            span.textContent = task;

            span.className = "cursor-pointer";


            // Mark task completed
            span.addEventListener("click", function () {

                span.classList.toggle("line-through");
                span.classList.toggle("text-gray-400");

            });


            // Delete button
            let deleteBtn = document.createElement("button");

            deleteBtn.textContent = "Delete";

            deleteBtn.className =
                "bg-red-500 text-white px-3 py-1 rounded hover:bg-red-600";


            // Delete task
            deleteBtn.addEventListener("click", function () {

                li.remove();

            });


            li.appendChild(span);
            li.appendChild(deleteBtn);

            taskList.appendChild(li);

            input.value = "";

        });


        // Press Enter to add task
        input.addEventListener("keypress", function (event) {

            if (event.key === "Enter") {
                button.click();
            }

        });

    </script>

</body>

</html>
