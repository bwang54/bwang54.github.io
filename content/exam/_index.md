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
        
        /* Breakout trick to bypass narrow theme containers */
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

    /* 3. Time Container and Label: Groups the label and input box together */
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

    /* Editable Time Input */
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
    
    .time-input:focus {
        opacity: 1;
        border-style: solid; 
    }

    /* 4. Instructions: Left-aligned, forced wide */
    .instructions-box {
        font-size: 3.5vh;
        line-height: 1.6;
        text-align: left;
        width: 100%; /* Now takes the full width of the 90vw exam-board */
        max-width: 1200px; /* Prevents it from becoming unreadable on ultra-wide screens */
        padding: 3vh 4vw;
        border-radius: 12px;
        background: rgba(128, 128, 128, 0.08);
        border-left: 8px solid currentColor;
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