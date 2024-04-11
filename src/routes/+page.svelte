<script>
    //@ts-nocheck
    let foggerTime = '';
    let contactTime = '';
    let blowerTime = '';
  
    let selectedInput = ''; // To track the currently selected input field
  
    // Function to handle button click and append value to the selected input field
    function handleButtonClick() {
      if (selectedInput === 'foggerTime') {
        foggerTime += this.innerText;
      } else if (selectedInput === 'contactTime') {
        contactTime += this.innerText;
      } else if (selectedInput === 'blowerTime') {
        blowerTime += this.innerText;
      }
    }
  
    // Function to save input values to local storage
    function saveValues() {
      localStorage.setItem('foggerTime', foggerTime);
      localStorage.setItem('contactTime', contactTime);
      localStorage.setItem('blowerTime', blowerTime);
    }
  </script>
  
  <div class="flex justify-between">
    <!-- Div containing three input fields -->
    <div>
      <div>
        <!-- Input for foggerTime -->
        <input type="text" bind:value={foggerTime} placeholder="Fogger Time" on:click={() => selectedInput = 'foggerTime'} />
      </div>
      <div>
        <!-- Input for contactTime -->
        <input type="text" bind:value={contactTime} placeholder="Contact Time" on:click={() => selectedInput = 'contactTime'} />
      </div>
      <div>
        <!-- Input for blowerTime -->
        <input type="text" bind:value={blowerTime} placeholder="Blower Time" on:click={() => selectedInput = 'blowerTime'} />
      </div>
    </div>
  
    <!-- Div containing three buttons -->
    <div>
      <!-- Button for entering 1 in the selected input -->
      <button on:click={handleButtonClick}>1</button>
      <!-- Button for entering 2 in the selected input -->
      <button on:click={handleButtonClick}>2</button>
      <!-- Button for entering 3 in the selected input -->
      <button on:click={handleButtonClick}>3</button>
      
      <!-- Save Button -->
      <button on:click={saveValues}>Save</button>
    </div>
  </div>
  