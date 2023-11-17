<script>
        // prop => title
    export let title;
    import { createEventDispatcher } from 'svelte';
  
    // Step 5
    // Create EventDispatcher 
    const dispatch = createEventDispatcher();
  // Dispatch featureEvent
    function triggerFeatureEvent() {
        dispatch('featureEvent');
    }
</script>
  
<div>

    <!-- render title prop in header 2 -->
 <h2>{title}</h2>
 
     <!-- feature event button -->
    <button on:click={triggerFeatureEvent}>Feature Event</button>
</div>
