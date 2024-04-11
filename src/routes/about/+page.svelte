<script>
    import { onMount } from 'svelte';
  
    let foggerTime = '';
    let contactTime = '';
    let blowerTime = '';
  
    onMount(() => {
      // Check if localStorage is available before accessing it
      if (typeof localStorage !== 'undefined') {
        foggerTime = localStorage.getItem('foggerTime') || '';
        contactTime = localStorage.getItem('contactTime') || '';
        blowerTime = localStorage.getItem('blowerTime') || '';
      }
    });
  </script>
  
  <div>
    <h1>Local Storage Items</h1>
    <p>Fogger Time: {foggerTime}</p>
    <p>Contact Time: {contactTime}</p>
    <p>Blower Time: {blowerTime}</p>
  </div>
  