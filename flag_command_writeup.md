# flag command
I'm using pwnbox which is a cloud-based virtual machine environment on HTB.
Flag Command is a simple web challenge on HTB, where you are presented with four questions and options. By guessing correctly or finding a hidden command, you can uncover the flag

Challenge description
![image](https://github.com/user-attachments/assets/c2bdf03a-fbfa-4178-a9ed-7d73d658b2c6)

Accessing the challenge through the IP address
![image](https://github.com/user-attachments/assets/9b3a0fd9-7c66-45ab-a6fd-3ec9c2e7d318)

After trying to beat the game manually :), I finally gave up.
I decided to view the page source and came across three interesting JavaScript files that seemed important. I looked through command.js and game.js files but I didnt find anything significant there.
![image](https://github.com/user-attachments/assets/48e1f1a2-bbda-4cee-9fb8-5b7cc788276e)

I viewed the main.js file and found a function named CheckMessage() that sends the user command to the /api/monitor endpoint via a POST request.
![image](https://github.com/user-attachments/assets/cf37025b-d35a-4cb6-ba61-143f7d20122a)

By using the the browsers dev tools. I can intercept network traffic and look for the /api/monitor endpoint.
![image](https://github.com/user-attachments/assets/28e29005-19fc-4fc2-ab0f-abe7b31c5da9)

After viewing the response from the api endpoint we see something interesting. We have our four questions with their respetive options, and we also have a secret.
![image](https://github.com/user-attachments/assets/a4420788-030d-4f8d-a3b8-b0ad6fdcd446)

Going back to the main.js file, we see that the function also checks if the command is in availableOptions['secret'], and if it is, it bypasses everything and gives you the flag
![image](https://github.com/user-attachments/assets/48591d0e-e055-4e20-9a6e-bccc4ce1f8fb)



Rabbit holes I went down:
- trying to brute-force through all of the options using a python script.
- Messing around with the requests in burpsuite.

Sorry if this writeup isn't very detailed—I'm new to web challenges and still experimenting on HTB. I'm learning as I go, and I hope this walkthrough can still provide some useful insights!





