<script>

    let newTask, updatedTask;
    let allTasks = [
        {task: "live", done: false, editing:false},
        {task: "love", done:false, editing:false},
        {task: "laugh", done:false, editing:false}
    ]

    function handleNewTask(){
        allTasks = [...allTasks, newTask]
        newTask = ""
    }

    function handleTaskDelete(i){
        allTasks = allTasks.splice(i, 1)
    }

    function setEditMode(i){
        allTasks[i].editing = true;
        allTasks = allTasks;
    }

    function handleTaskUpdate(i){
        allTasks[i].editing = false;
        allTasks = allTasks;
    }


</script>

<div>

    <h1>to do app</h1>

    <form on:submit|preventDefault={handleNewTask}>
        <input placeholder="what has got to be done?" bind:value={newTask}/>
        <button>add task</button>
    </form>

        {#each allTasks as task, i}
            <div key={i}>
                <input type="checkbox" bind:checked={task.done}/>
                {#if task.editing}
                    <input bind:value={task.task}/>
                    <button on:click={() => handleTaskUpdate(i)}>save</button>
                {:else}
                    {task.task}
                    <button on:click={() => setEditMode(i)}>edit</button>
                    <button on:click={() => handleTaskDelete(i)}>delete</button>
                {/if}  
            </div>
        {/each}
   


</div>