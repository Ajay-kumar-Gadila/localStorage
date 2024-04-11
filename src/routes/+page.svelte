<script>
    //@ts-nocheck
    let foggerTime = 0; // Initialize foggerTime as 0 seconds
    let contactTime = 0; // Initialize contactTime as 0 seconds
    let blowerTime = 0; // Initialize blowerTime as 0 seconds
  
    let selectedInput = ''; // To track the currently selected input field
  
    // Function to handle button click and increment time by 1 minute (60 seconds)
    function handleButtonClick() {
      if (selectedInput === 'foggerTime') {
        foggerTime += 60; // Increment foggerTime by 1 minute (60 seconds)
      } else if (selectedInput === 'contactTime') {
        contactTime += 60; // Increment contactTime by 1 minute (60 seconds)
      } else if (selectedInput === 'blowerTime') {
        blowerTime += 60; // Increment blowerTime by 1 minute (60 seconds)
      }
    }
  
    // Function to save input values to local storage
    function saveValues() {
      localStorage.setItem('foggerTime', foggerTime);
      localStorage.setItem('contactTime', contactTime);
      localStorage.setItem('blowerTime', blowerTime);
    }
  
    // Function to convert time in seconds to timer format (HH:MM:SS)
    function formatTime(timeInSeconds) {
      const hours = Math.floor(timeInSeconds / 3600);
      const minutes = Math.floor((timeInSeconds % 3600) / 60);
      const seconds = timeInSeconds % 60;
      return `${padZero(hours)}:${padZero(minutes)}:${padZero(seconds)}`;
    }
  
    // Function to pad single-digit numbers with a leading zero
    function padZero(num) {
      return num.toString().padStart(2, '0');
    }
  
    // Computed variable for formatted foggerTime
    $: formattedFoggerTime = formatTime(foggerTime);
    $: formattedContactTime = formatTime(contactTime);
    $: formattedBlowerTime = formatTime(blowerTime);
  </script>
  
  <div class="flex justify-between">
    <!-- Div containing three input fields -->
    <div>
      <div>
        <!-- Input for foggerTime -->
        <input type="text" bind:value={formattedFoggerTime} placeholder="Fogger Time" on:click={() => selectedInput = 'foggerTime'} />
      </div>
      <div>
        <!-- Input for contactTime -->
        <input type="text" bind:value={formattedContactTime} placeholder="Contact Time" on:click={() => selectedInput = 'contactTime'} />
      </div>
      <div>
        <!-- Input for blowerTime -->
        <input type="text" bind:value={formattedBlowerTime} placeholder="Blower Time" on:click={() => selectedInput = 'blowerTime'} />
      </div>
    </div>
  
    <!-- Div containing three buttons -->
    <div>
      <!-- Button for incrementing value by 1 minute in the selected input -->
      <button on:click={handleButtonClick}>1</button>
      <!-- Button for incrementing value by 2 minutes in the selected input -->
      <button on:click={handleButtonClick}>2</button>
      <!-- Button for incrementing value by 3 minutes in the selected input -->
      <button on:click={handleButtonClick}>3</button>
      
      <!-- Save Button -->
      <button on:click={saveValues}>Save</button>
    </div>
  </div>
  