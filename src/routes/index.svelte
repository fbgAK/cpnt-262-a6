<script>
    // Imported functions and components
    import { onMount } from 'svelte';
    import { createEventDispatcher } from 'svelte';
    import FeatureComponent from './FeatureComponent.svelte';

    // Step 2:
    // Array of chores with some default tasks
    let chores = [
        { id: 1, task: 'Clean the dishes' },
        { id: 2, task: 'Take out the trash' },
        // ... (other tasks)
    ];

    // Step 3
    // Stores new tasks inputed
    let newTask = '';
    // Created event dispatcher for components
    const dispatch = createEventDispatcher();

    // Add a new task to the chores array
    function addTask() {
        // Creating a new chore object with a task
        const newChore = { id: chores.length + 1, task: newTask };
        // Updating the chores array with the new task
        chores = [...chores, newChore];
        // Clearing the input field after adding the task
        newTask = '';
        // Dispatching an event to update the chores
        dispatch('updateChores', chores); // Step 3 - Dispatching the event to update chores
    }

    // Function to handle inline events (e.g., manipulating CSS, toggling content)
    function handleInlineEvent() {
        // Example: Manipulate CSS
        const element = document.getElementById('exampleElement');
        element.style.backgroundColor = 'lightblue';

        // Example: Toggle Content
        const toggleElement = document.getElementById('toggleElement');
        toggleElement.classList.toggle('hidden');
    }

    // Dispatch initial data when the component is mounted
    onMount(() => {
        dispatch('updateChores', chores); // Initial data dispatch
    });
</script>

<main>
    <h1>Chores To Do</h1>

    <!-- Step 2 -->
    <!-- Rendering the list of chores -->
    {#each chores as chore (chore.id)}
        <p>{chore.task}</p>
    {/each}

    <!-- Step 3 -->
    <!-- Input field and button for adding new tasks -->
    <input bind:value={newTask} placeholder="Enter new chore" />
    <button on:click={addTask}>Add Chore</button>

    <!-- Button to trigger an inline event -->
    <button id="exampleElement" on:click={handleInlineEvent} tabindex="0">
        Click me to change styling!
    </button>

    <!-- Element to toggle visibility using an inline event -->
    <div id="toggleElement" class="hidden">
        Content to toggle!
    </div>

    <!-- Step 4 -->
    <!-- component that wraps around the component -->
    <FeatureComponent title="Feature Component Title" />
</main>
