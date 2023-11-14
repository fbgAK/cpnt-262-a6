<script>
    import { onMount } from 'svelte';
    import { createEventDispatcher } from 'svelte';
    import FeatureComponent from './FeatureComponent.svelte'; // Import the FeatureComponent

    // Step 2
    let chores = [
        { id: 1, task: 'Clean the dishes' },
        { id: 2, task: 'Take out the trash' },
        { id: 3, task: 'Vacuum the living room' },
        { id: 4, task: 'Water the plants' },
        { id: 5, task: 'Mop the floors' },
        { id: 6, task: 'Organize the closet' },
        { id: 7, task: 'Clean the windows' },
        { id: 8, task: 'Dust the furniture' },
        { id: 9, task: 'Sort and recycle paper and plastic' },
        { id: 10, task: 'Wipe down kitchen surfaces' },
        { id: 11, task: 'Sweep the front porch' },
        { id: 12, task: 'Clean the bathroom' },
    ];

    // Step 3
    let newTask = '';
    const dispatch = createEventDispatcher();
  
    function addTask() {
        const newChore = { id: chores.length + 1, task: newTask };
        chores = [...chores, newChore];
        newTask = '';
        dispatch('updateChores', chores); // Step 3
    }

    function handleInlineEvent() {
        // Example: Manipulate CSS
        const element = document.getElementById('exampleElement');
        element.style.backgroundColor = 'lightblue';
  
        // Example: Toggle Content
        const toggleElement = document.getElementById('toggleElement');
        toggleElement.classList.toggle('hidden');
    }
  
    onMount(() => {
        dispatch('updateChores', chores); // Initial data dispatch
    });
</script>
  
<main>
    <h1>Chores To Do</h1>
  
    <!-- Step 2 -->
    {#each chores as chore (chore.id)}
        <p>{chore.task}</p>
    {/each}
  
    <!-- Step 3 -->
    <input bind:value={newTask} placeholder="Enter new chore" />
    <button on:click={addTask}>Add Chore</button>

    <button id="exampleElement" on:click={handleInlineEvent} tabindex="0">
        Click me to change styling!
    </button>
  
    <div id="toggleElement" class="hidden">
        Content to toggle!
    </div>
  
    <!-- Step 4 -->
    <FeatureComponent title="Feature Component Title" />
</main>
