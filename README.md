## Title of the Project
Small description about the project like one below
The integration of a chatbot within a hostel booking system, aimed at streamlining the reservation process for students and improving the overall user experience.

## About
<!--Detailed Description about the project-->
Tailored Chatbot for Hostel Booking System is a project designed to integrate a chatbot that leverages advanced natural language processing techniques to understand and respond to user queries to the hostel booking system. Traditional hostel booking processes are often time-consuming and involve manual searches and extensive communication with hostel staff. This project seeks to overcome these challenges by creating an easy-to-use chatbot interface that assists students in addressing inquiries.

## Features
<!--List the features of the project as shown below-->
- Implements advance neural network method.
- A framework based application for deployment purpose.
- High scalability.
- Less time complexity.
- A specific scope of Chatbot response model, using json data format.

## Requirements
<!--List the requirements of the project as shown below-->
* Operating System: Requires a 64-bit OS (Windows 10 or Ubuntu) for compatibility with deep learning frameworks.
* Development Environment: Python 3.6 or later is necessary for coding the sign language detection system.
* Deep Learning Frameworks: TensorFlow for model training, MediaPipe for hand gesture recognition.
* Image Processing Libraries: OpenCV is essential for efficient image processing and real-time hand gesture recognition.
* Version Control: Implementation of Git for collaborative development and effective code management.
* IDE: Use of VSCode as the Integrated Development Environment for coding, debugging, and version control integration.
* Additional Dependencies: Includes scikit-learn, TensorFlow (versions 2.4.1), TensorFlow GPU, OpenCV, and Mediapipe for deep learning tasks.

## System Architecture
<!--Embed the system architecture diagram as shown below-->
This graphic provides a concise and understandable description of all the entities currently integrated into the system. System architecture refers to the high-level design and structure of a system, illustrating how various components interact, the flow of data, and how the system is organized to fulfill its functional and non-functional requirements.

<img width="515" alt="image" src="https://github.com/user-attachments/assets/9e5d87e2-7d07-43ba-8674-fbb25ea8d0a1" />

This architecture ensures that Travel Genie: Your Custom Itinerary Planner is efficient, flexible, and capable of handling complex user requirements while providing a seamless and personalized experience.

## Program :

```
Home page.ipynb:
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport"
content="width=device-width,
initial-scale=1.0">
<title>Tourism Bot</title>
<link rel="stylesheet"
href="static/styles.css">
</head>
<body>
<header>
<div class="nav">
<div class="logo">Travel
Genie</div>
<div class="menu">
<a href="#">Home</a>
<a href="#">Chatbot</a>
<a href="#">Contact Us</a>
<a href="#">Sign In</a>
<a href="#">Sign Up</a>
</div>
</div>
</header>
<main>
<div class="chat-container">
<div class="chat-header">
<h1>CHAT WITH TB</h1>
<p>Welcome user, please be
patient and let TB know your
requirements!</p>
</div>
<div class="chat-window"
id="chat-window">
<div class="chat-message
bot">Hello, I am TB to help you
out</div>
</div>
<div class="chat-input">
<input type="text"
id="user-input" placeholder="Type
your message here...">
<button
id="send-btn">Send</button>
</div>
</div>
</main>
<script src="script.js"></script>
</body>
</html>
Css.py
body {
margin: 0;
font-family: Arial,sans-serif;
background-color: #f4f4f4;
}
header {
background-color: #512b58;
color: white;
padding: 1rem 2rem;
display: flex;
justify-content: space-between;
align-items: center;
}
.nav .logo {
font-size: 1.5rem;
font-weight: bold;
}
.nav .menu a {
color: white;
margin-left: 1rem;
text-decoration: none;
}
main {
display: flex;
justify-content: center;
align-items: center;
height: calc(100vh - 100px);
}
.chat-container {
width: 50%;
max-width: 500px;
background-color: #d9e6dc;
padding: 2rem;
border-radius: 10px;
box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}
.chat-header {
text-align: center;
}
.chat-header h1 {
margin: 0;
color: #ffdf57;
}
.chat-window {
height: 300px;
background-color: white;
margin: 1rem 0;
overflow-y: auto;
padding: 1rem;
border: 1px solid #ccc;
border-radius: 10px;
}
.chat-message {
margin-bottom: 1rem;
}
.chat-message.bot {
color: #512b58;
font-weight: bold;
}
.chat-message.user {
text-align: right;
color: #006699;
}
.chat-input {
display: flex;
align-items: center;
gap: 0.5rem;
}
.chat-input input {
flex-grow: 1;
padding: 0.5rem;
border: 1px solid #ccc;
border-radius: 5px;
}
.chat-input button {
padding: 0.5rem 1rem;
background-color: #ffdf57;
border: none;
border-radius: 5px;
cursor: pointer;
}
.chat-input button:hover {
background-color: #ffd233;
}
camera.py:
import cv2
from detection import AccidentDetectionModel
import numpy as np
import os
import tkinter as tk
from tkinter import
*
from tkinter import filedialog
from tkinter.filedialog import askopenfile
from PIL import Image, ImageTk
model = AccidentDetectionModel("model.json",
'model_weights.h5') font = cv2.FONT_HERSHEY_SIMPLEX
my_w = tk.Tk()
my_w.geometry("410x300")
my_w.title('Accident Detection')
my_font1=('times', 18, 'bold')
l1 = tk.Label(my_w,text='Upload the Video',width=30,font=my_font1)
l1.grid(row=1,column=1,columnspan=4)
b1 = tk.Button(my_w, text='Upload File',
width=20,command =
lambda:open_file())
b1.grid(row=2,column=1,columnspan=4)
def open_file():
filepath = tk.filedialog.askopenfilename()
if filepath is not None:
startapplication(filepath)
def startapplication(filepath):
vid=open(filepath,'r')
video = cv2.VideoCapture(vid.name)
vid.close()
while True:
ret, frame = video.read()
if not ret:
return prob
gray_frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
roi = cv2.resize(gray_frame, (250, 250))
pred, prob = model.predict_accident(roi[np.newaxis, :, :])
if(pred == "Accident"):
prob = (round(prob[0][0]*100, 2))
cv2.rectangle(frame, (0, 0), (280, 40), (0, 0, 0), -1)
cv2.putText(frame, pred+" "+str(prob), (20, 30), font, 1, (255, 255, 0), 2)
if cv2.waitKey(33) & 0xFF == ord('q'):
return
cv2.imshow('Video', frame)
if name == ' main ':
open_file()
python.py:
from flask import Flask, render_template, request, jsonify
import requests
app = Flask(_name_)
API_KEY =
"Ysk-proj-V4kEH8QHKDLJ1GU1LOoQiGQtsg-j2Bg6739atNlY-1z0Gu_1KCzFJtSt7btyLgJh
Vhjw_PAf_T3BlbkFJMGiI20cVgtDco9tPZLCfgRS0qmvpQrQvGbbdo3V-SEhmWCJXderglw
PT5JWuf2vvg9Hsch7cA"
def fetch_hotel_suggestions(destination):
try:
headers = {"Authorization": f"Bearer {API_KEY}"}
params = {"destination": destination}
response = requests.get(API_URL, headers=headers, params=params)
if response.status_code == 200:
hotels = response.json().get("hotels", [])
if hotels:
return [f"{hotel['name']} - {hotel['price']} {hotel['currency']}" for hotel in hotels]
else:
return ["No hotels found for the specified destination."]
else:
return ["Failed to fetch hotel data from the API."]
except Exception as e:
return [f"Error occurred: {str(e)}"]
@app.route("/")
def home():
return render_template("index.html")
@app.route("/chat", methods=["POST"])
def chat():
user_message = request.json.get("message", "").lower()
if "hello" in user_message or "hi" in user_message:
bot_message = "Hello! How can I assist you with your travel plans today?"
elif "hotel" in user_message:
bot_message = "Please provide a destination for hotel suggestions."
elif "destination:" in user_message:
destination = user_message.split("destination:")[1].strip()
hotel_suggestions = fetch_hotel_suggestions(destination)
bot_message = "\n".join(hotel_suggestions)
elif "thank" in user_message:
bot_message = "You're welcome! Have a great day!"
else:
bot_message = "I'm sorry, I didn't understand that. Can you please rephrase your
question?"
return jsonify({"bot_message": bot_message})
if _name_ == "_main_":
app.run(debug=True)
```

## Output

<!--Embed the Output picture at respective places as shown below as shown below-->
#### Output1 

<img width="323" alt="image" src="https://github.com/user-attachments/assets/e5dd55b9-e7a0-4bd0-9070-7a05a1ea5c57" />

#### Output2

<img width="319" alt="image" src="https://github.com/user-attachments/assets/f1461908-69af-4357-9ed4-564d84c43392" />

#### Output3

<img width="311" alt="image" src="https://github.com/user-attachments/assets/e7186887-84fd-4f91-8fb1-53a84b66c95c" />

#### Output4

<img width="461" alt="image" src="https://github.com/user-attachments/assets/ff03a883-c71f-4633-9858-f61848ae4c5e" />


 Accuracy: 95%
Note: These metrics can be customized based on your actual performance evaluations.


## Results and Impact
<!--Give the results and impact as shown below-->
our Custom Itinerary Planner are designed to thoroughly validate the system’sfunctionality across various modules, including user registration, login, itinerary creation,
personalized recommendations, and payment processing. These tests ensure that the systemmeets both functional and non-functional requirements, providing a seamless and user-friendly experience. By conducting comprehensive tests like black box testing, boundary value testing, and UI testing, we can identify potential issues early on and address them before deployment. The successful execution of these test cases guarantees that the application will be robust, secure, and capable of offering customized travel planning solutions to users, thereby enhancing overall satisfaction and performance.

## Articles published / References
[1]	Ilie, C., & Iancu, B., “Applications of Natural Language Processing in Tourism”, Journal of Information Systems and Operations Management
[2]	Xiang, Z., & Fesenmaier, D. R, “AI in Tourism: Trends and Research Directions,” Journal of Travel Research (2017)

[3]	Gavalas, D., et al., “Automatic Generation of Personalized Travel Itineraries” IEEE Transactions on Intelligent Transportation Systems (2014)

[4]	Arslan Ay, S., Erdem, Z., & Orhan, M. A., A Recommender System for Personalized Itineraries in City Tours” Expert Systems with Applications (2020)

[5]	Fesenmaier, D. R., Werthner, H. “Designing Intelligent Travel Systems for Enhanced User Experience” Information Technology & Tourism, 2016

[6]	Brown, T., et al., “Language Models are Few-Shot Learners” Advances in Neural Information Processing Systems (NeurIPS), 2020

[7]	Ricci, F., Cavada, D. “A Survey of Recommender Systems in Tourism” iJournal of Intelligent Information Systems, 2015.

[8]	Ghaderi, Z., Henderson, J. C., “Leveraging AI for Sustainable Tourism: A Systematic Review”
     SustainabilityJournal,2019


