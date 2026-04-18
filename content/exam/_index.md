---
title: "Exam"
description: "For Exam Purpose."
---

{{< rawhtml >}}
<style>
    /* 1. Container: Forces elements to space out evenly without scrolling */
    .exam-board {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        align-items: center;
        min-height: 80vh; /* Takes up 80% of the screen height */
        width: 100%;
        text-align: center;
        padding: 2vh 0;
    }

    /* 2. Live Clock: Uses monospace so numbers don't wiggle as seconds tick */
    #live-clock {
        font-size: 12vh; /* Scales relative to screen height */
        font-weight: bold;
        font-family: ui-monospace, SFMono-Regular, Consolas, monospace;
        letter-spacing: -2px;
    }

    /* 3. Editable Time Input: Clear border to show it can be clicked */
    .time-input {
        font-size: 6vh;
        font-weight: bold;
        font-family: inherit;
        padding: 2vh 4vw;
        border: 3px dashed currentColor;
        opacity: 0.6;
        border-radius: 12px;
        text-align: center;
        background: transparent;
        outline: none;
        transition: opacity 0.2s, border-style 0.2s;
        min-width: 50vw;
    }
    
    /* Changes to solid border when you click it to edit */
    .time-input:focus {
        opacity: 1;
        border-style: solid; 
    }

    /* 4. Instructions: Left-aligned but centered on screen */
    .instructions-box {
        font-size: 3.5vh; /* Massive on projector, perfect on laptop */
        line-height: 1.6;
        text-align: left;
        max-width: 90vw;
        padding: 3vh 4vw;
        border-radius: 12px;
        background: rgba(128, 128, 128, 0.08); /* Subtle box, works in Light & Dark mode */
        border-left: 8px solid currentColor;
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

    <div contenteditable="true" class="time-input">
        9:00 AM - 11:00 AM
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
    // Native script to generate an infinitely scalable live clock
    function updateExamClock() {
        const now = new Date();
        let hours = now.getHours();
        let minutes = now.getMinutes();
        let seconds = now.getSeconds();
        const ampm = hours >= 12 ? 'PM' : 'AM';
        
        hours = hours % 12;
        hours = hours ? hours : 12; // convert hour '0' to '12'
        minutes = minutes < 10 ? '0' + minutes : minutes;
        seconds = seconds < 10 ? '0' + seconds : seconds;
        
        const timeString = hours + ':' + minutes + ':' + seconds + ' ' + ampm;
        document.getElementById('live-clock').textContent = timeString;
    }
    
    // Initialize clock immediately, then update every second
    updateExamClock();
    setInterval(updateExamClock, 1000);
</script>
{{< /rawhtml >}}