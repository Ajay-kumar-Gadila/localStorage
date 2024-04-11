<script>
    //@ts-nocheck
    import { onMount } from 'svelte';
  
    let inputValue = ''; // Initialize input value
    let timerValue = 0; // Initialize timer value
    let timer; // Timer variable
  
    // Function to start the timer
    function startTimer() {
      timer = setInterval(() => {
        if (timerValue > 0) {
          timerValue--; // Decrement timer value
        } else {
          clearInterval(timer); // Stop the timer
          // Navigate to the next page
          window.location.href = '/checktime';
        }
      }, 1000); // Timer tick every second
    }
  
    // Function to handle page load
    onMount(() => {
      // Check if timer value exists in local storage
      if (localStorage.getItem('timerValue')) {
        // Retrieve timer value from local storage
        timerValue = parseInt(localStorage.getItem('timerValue'));
        // Start the timer
        startTimer();
      }
    });
  
    // Function to save the input value to local storage
    function saveInputValue() {
      localStorage.setItem('timerValue', inputValue * 60); // Save timer value to local storage (in seconds)
    }
  </script>
  
  <div>
    <!-- Input field for entering value in minutes -->
    <input type="number" bind:value={inputValue} placeholder="Enter value in minutes" />
  
    <!-- Save button to save the input value -->
    <button on:click={saveInputValue}>Save</button>
    
    <!-- Display the timer value -->
    <p>Timer Value: {Math.floor(timerValue / 60)}:{(timerValue % 60).toString().padStart(2, '0')}</p>
  </div>
  