<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Countdown</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            margin: 0;
        }

        h1 {
            font-family: 'Cursive', sans-serif;
            font-size: 48px;
            color: #ff6f61;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        h2 {
            font-family: 'Serif', sans-serif;
            font-size: 24px;
            color: #333;
            margin-bottom: 40px;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.1);
            text-align: center;
            padding: 0 20px;
        }

        .countdown-container {
            display: flex;
            gap: 20px;
            text-align: center;
        }

        .box {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            animation: pop 1s ease-in-out infinite alternate;
        }

        .box span {
            display: block;
            font-size: 24px;
            font-weight: bold;
        }

        .box label {
            font-size: 14px;
            color: #555;
        }

        .notes-container {
            margin-top: 40px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            width: 300px;
        }

        .notes-title {
            font-size: 20px;
            margin-bottom: 10px;
            text-align: center;
        }

        .notes-area {
            width: 100%;
            height: 100px;
            border: 1px solid #ccc;
            border-radius: 5px;
            padding: 10px;
            font-family: 'Georgia', serif;
            font-size: 16px;
            resize: none;
            outline: none;
        }

        .save-button {
            margin-top: 10px;
            background-color: #ff6f61;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
        }

        .save-button:hover {
            background-color: #ff4c3b;
        }

        .saved-notes {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background: #f9f9f9;
        }

        @keyframes pop {
            from { transform: scale(1); }
            to { transform: scale(1.1); }
        }
    </style>
</head>
<body>

    <h1>Happy Birthday Hero Bhai!</h1>
    <h2>"Time flies, but memories last forever."</h2>

    <div class="countdown-container">
        <div class="box">
            <span id="years"></span>
            <label>Years</label>
        </div>
        <div class="box">
            <span id="months"></span>
            <label>Months</label>
        </div>
        <div class="box">
            <span id="days"></span>
            <label>Days</label>
        </div>
        <div class="box">
            <span id="hours"></span>
            <label>Hours</label>
        </div>
        <div class="box">
            <span id="minutes"></span>
            <label>Minutes</label>
        </div>
        <div class="box">
            <span id="seconds"></span>
            <label>Seconds</label>
        </div>
    </div>

    <div class="notes-container">
        <div class="notes-title">Your Notes</div>
        <textarea class="notes-area" placeholder="Write your notes here..."></textarea>
        <button class="save-button" onclick="saveNotes()">Save Notes</button>
    </div>

    <div class="saved-notes" id="displayNotes"></div>

    <script>
        function countdownFromBirthday() {
            const birthDate = new Date('October 4, 2006 00:00:00').getTime();
            const now = new Date().getTime();
            const diff = now - birthDate;

            const secondsInYear = 31556926;
            const secondsInMonth = 2629743;
            const secondsInDay = 86400;
            const secondsInHour = 3600;
            const secondsInMinute = 60;

            const years = Math.floor(diff / (secondsInYear * 1000));
            const months = Math.floor((diff % (secondsInYear * 1000)) / (secondsInMonth * 1000));
            const days = Math.floor((diff % (secondsInMonth * 1000)) / (secondsInDay * 1000));
            const hours = Math.floor((diff % (secondsInDay * 1000)) / (secondsInHour * 1000));
            const minutes = Math.floor((diff % (secondsInHour * 1000)) / (secondsInMinute * 1000));
            const seconds = Math.floor((diff % (secondsInMinute * 1000)) / 1000);

            document.getElementById('years').innerHTML = years;
            document.getElementById('months').innerHTML = months;
            document.getElementById('days').innerHTML = days;
            document.getElementById('hours').innerHTML = hours;
            document.getElementById('minutes').innerHTML = minutes;
            document.getElementById('seconds').innerHTML = seconds;
        }

        function saveNotes() {
            const notes = document.querySelector('.notes-area').value;
            const displayArea = document.getElementById('displayNotes');

            if (notes) {
                displayArea.innerHTML += `<p>${notes}</p>`;
                document.querySelector('.notes-area').value = ''; // Clear the textarea
                alert('Notes saved successfully!');
            } else {
                alert('Please write something before saving.');
            }
        }

        const interval = setInterval(countdownFromBirthday, 1000);
    </script>

</body>
</html>
