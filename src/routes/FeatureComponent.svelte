
<script>
    export let title;
    import { createEventDispatcher } from 'svelte';
  
    // Step 5
    const dispatch = createEventDispatcher();
  
    function triggerFeatureEvent() {
        dispatch('featureEvent');
    }
</script>
  
<div>
    <h2>{title}</h2>
    <button on:click={triggerFeatureEvent}>Feature Event</button>
</div>
