<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sports Events Tracker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Sports Events Tracker</h1>
        <form id="eventForm">
            <input type="text" id="eventTitle" placeholder="Event Title" required>
            <input type="date" id="eventDate" required>
            <input type="time" id="eventTime" required>
            <textarea id="eventDescription" placeholder="Event Description" required></textarea>
            <button type="submit">Add Event</button>
        </form>
        <h2>Upcoming Events</h2>
        <div id="eventList"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: auto;
    padding: 20px;
    background: white;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1, h2 {
    text-align: center;
}

form {
    display: flex;
    flex-direction: column;
}

input, textarea {
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background-color: #28a745;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

.event-item {
    background: #f8f9fa;
    margins: 10px 0;
    padding: 10px;
    border-radius: 4px;
}

.event-item button {
    background-color: #dc3545;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
}

.event-item button:hover {
    background-color: #c82333;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: auto;
    padding: 20px;
    background: white;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1, h2 {
    text-align: center;
}

form {
    display: flex;
    flex-direction: column;
}

input, textarea {
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background-color: #28a745;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

.event-item {
    background: #f8f9fa;
    margins: 10px 0;
    padding: 10px;
    border-radius: 4px;
}

.event-item button {
    background-color: #dc3545;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
}

.event-item button:hover {
    background-color: #c82333;
}

document.getElementById("eventForm").addEventListener("submit", function(event) {
    event.preventDefault();
    addEvent();
});

let events = [];

function addEvent() {
    const title = document.getElementById("eventTitle").value;
    const date = document.getElementById("eventDate").value;
    const time = document.getElementById("eventTime").value;
    const description = document.getElementById("eventDescription").value;

    const event = {
        title: title,
        date: date,
        time: time,
        description: description
    };

    events.push(event);
    displayEvents();
    clearForm();
}

function displayEvents() {
    const eventList = document.getElementById("eventList");
    eventList.innerHTML = ""; // Clear current events

    events.forEach((event, index) => {
        const eventItem = document.createElement("div");
        eventItem.className = "event-item";
        eventItem.innerHTML = `
            <h3>${event.title}</h3>


            <p>${event.date} at ${event.time}</p>
            <p>${event.description}</p>
            <button onclick="deleteEvent(${index})">Delete Event</button>
        `;
        eventList.appendChild(eventItem);
    });
}

function clearForm() {
    document.getElementById("eventTitle").value = "";
    document.getElementById("eventDate").value = "";
    document.getElementById("eventTime").value = "";
    document.getElementById("eventDescription").value = "";
}

function deleteEvent(index) {
    events.splice(index, 1); // Remove the event from the array
    displayEvents(); // Re-display the events
}
