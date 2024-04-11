<script>
    //@ts-nocheck
    import { onMount } from 'svelte';

    let foggerTime = 0; // Initialize foggerTime as 0 minutes
    let contactTime = 0; // Initialize contactTime as 0 minutes
    let blowerTime = 0; // Initialize blowerTime as 0 minutes

    // Function to save input values to local storage
    function saveValues() {
        localStorage.setItem('foggerTime', foggerTime * 60); // Convert foggerTime to seconds and save to local storage
        localStorage.setItem('contactTime', contactTime * 60); // Convert contactTime to seconds and save to local storage
        localStorage.setItem('blowerTime', blowerTime * 60); // Convert blowerTime to seconds and save to local storage
        // Navigate to the display page
        window.location.href = '/checklocal';
    }
</script>

<div>
    <!-- Input field for foggerTime -->
    <div>
        <label for="foggerTime">Fogger Time:</label>
        <input type="number" id="foggerTime" bind:value={foggerTime} placeholder="Enter fogger time in minutes" />
    </div>

    <!-- Input field for contactTime -->
    <div>
        <label for="contactTime">Contact Time:</label>
        <input type="number" id="contactTime" bind:value={contactTime} placeholder="Enter contact time in minutes" />
    </div>

    <!-- Input field for blowerTime -->
    <div>
        <label for="blowerTime">Blower Time:</label>
        <input type="number" id="blowerTime" bind:value={blowerTime} placeholder="Enter blower time in minutes" />
    </div>

    <!-- Save button to save the input values -->
    <button on:click={saveValues}>Save</button>
</div>
