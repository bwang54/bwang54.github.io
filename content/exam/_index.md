---
title: "Exam"
description: "For Exam Purpose."
---

{{< rawhtml >}}
<style>
    /* 1. Container: Forces elements to space out evenly and breaks out of theme's max-width */
    .exam-board {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        align-items: center;
        min-height: 80vh;
        width: 90vw;
        position: relative;
        left: 50%;
        transform: translateX(-50%);
        text-align: center;
        padding: 2vh 0;
        box-sizing: border-box;
    }

    /* 2. Live Clock: Uses monospace so numbers don't wiggle as seconds tick */
    #live-clock {
        font-size: 12vh;
        font-weight: bold;
        font-family: ui-monospace, SFMono-Regular, Consolas, monospace;
        letter-spacing: -2px;
    }

    /* 3. Time Container and Label */
    .time-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1vh;
    }

    .time-label {
        font-size: 3.5vh;
        font-weight: bold;
        font-family: inherit;
        opacity: 0.8;
    }

    /* Editable Time Input: Minimalist styling */
    .time-input {
        font-size: 6vh;
        font-weight: bold;
        font-family: inherit;
        padding: 1vh 2vw;
        border: none;
        border-bottom: 2px solid transparent; /* Hidden by default */
        opacity: 0.8;
        text-align: center;
        background: transparent;
        outline: none;
        transition: opacity 0.2s, border-bottom-color 0.2s;
        min-width: 50vw;
    }
    
    /* Shows a subtle underline only when hovering or clicking to edit */
    .time-input:hover,
    .time-input:focus {
        opacity: 1;
        border-bottom-color: currentColor; 
    }

    /* 4. Instructions: Minimalist, no background or borders */
    .instructions-box {
        font-size: 3.5vh;
        line-height: 1.6;
        text-align: left;
        width: 100%;
        max-width: 1200px;
        padding: 2vh 4vw;
        border: none; /* Removed thick left border */
        background: transparent; /* Removed grey background */
        box-sizing: border-box;
    }

    .instructions-box ol {
        margin: 0;
        padding-left: 3vw;
    }

    .instructions-box li {
        margin-bottom: 1.5vh;
    }
</style>

<div class="exam-board">
    
    <div id="live-clock">00:00:00</div>

    <div class="time-container">
        <div class="time-label">Exam Time:</div>
        <div contenteditable="true" class="time-input">
            9:00 AM - 11:00 AM
        </div>
    </div>

    <div class="instructions-box">
        <ol>
            <li>You may remove the staple if needed.</li>
            <li>Place your phone on your desk and keep it there for the duration of the exam.</li>
            <li>Write all your work and answers clearly on the Answer Sheet.</li>
            <li>Any cheating or use of unauthorized devices will result in your exam being invalid and reported.</li>
        </ol>
    </div>

</div>

<script>
    function updateExamClock() {
        const now = new Date();
        let hours = now.getHours();
        let minutes = now.getMinutes();
        let seconds = now.getSeconds();
        const ampm = hours >= 12 ? 'PM' : 'AM';
        
        hours = hours % 12;
        hours = hours ? hours : 12;
        minutes = minutes < 10 ? '0' + minutes : minutes;
        seconds = seconds < 10 ? '0' + seconds : seconds;
        
        const timeString = hours + ':' + minutes + ':' + seconds + ' ' + ampm;
        document.getElementById('live-clock').textContent = timeString;
    }
    
    updateExamClock();
    setInterval(updateExamClock, 1000);
</script>
{{< /rawhtml >}}