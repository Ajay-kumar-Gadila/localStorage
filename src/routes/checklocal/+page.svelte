<script>
    //@ts-nocheck
    import { onMount } from 'svelte';

    let foggerTime = 0; // Initialize foggerTime
    let contactTime = 0; // Initialize contactTime
    let blowerTime = 0; // Initialize blowerTime

    // Function to handle page load
    onMount(() => {
        // Retrieve timer values from local storage and convert to seconds
        if (localStorage.getItem('foggerTime')) {
            foggerTime = parseInt(localStorage.getItem('foggerTime')); // Get foggerTime from local storage
        }
        if (localStorage.getItem('contactTime')) {
            contactTime = parseInt(localStorage.getItem('contactTime')); // Get contactTime from local storage
        }
        if (localStorage.getItem('blowerTime')) {
            blowerTime = parseInt(localStorage.getItem('blowerTime')); // Get blowerTime from local storage
        }

        // Start the countdown timers
        startTimer('fogger');
        startTimer('contact');
        startTimer('blower');
    });

    // Function to start the countdown timer
    function startTimer(timerType) {
        const timer = setInterval(() => {
            let timerValue;
            switch (timerType) {
                case 'fogger':
                    timerValue = foggerTime;
                    break;
                case 'contact':
                    timerValue = contactTime;
                    break;
                case 'blower':
                    timerValue = blowerTime;
                    break;
                default:
                    return;
            }
            if (timerValue > 0) {
                timerValue--; // Decrement timer value
                // Update the timer value in local storage
                localStorage.setItem(`${timerType}Time`, timerValue);
            } else {
                clearInterval(timer); // Stop the timer
                // Navigate to the next page when timer reaches zero
                navigateNextPage();
            }
        }, 1000); // Timer tick every second
    }

    // Function to navigate to the next page
    function navigateNextPage() {
        // Navigate to the next page
        window.location.href = '/lastnavi';
    }

    // Function to format time in minutes and seconds
    function formatTime(timeInSeconds) {
        const minutes = Math.floor(timeInSeconds / 60); // Calculate minutes
        const seconds = timeInSeconds % 60; // Calculate seconds
        return `${padZero(minutes)}:${padZero(seconds)}`; // Format minutes and seconds
    }

    // Function to pad single-digit numbers with a leading zero
    function padZero(num) {
        return num.toString().padStart(2, '0');
    }
</script>

<div>
    <!-- Display the foggerTime value as timer -->
    <p>Fogger Time: {formatTime(foggerTime)}</p>

    <!-- Display the contactTime value as timer -->
    <p>Contact Time: {formatTime(contactTime)}</p>

    <!-- Display the blowerTime value as timer -->
    <p>Blower Time: {formatTime(blowerTime)}</p>
</div>
