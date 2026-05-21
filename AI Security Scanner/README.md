<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# AI Security Scanner for Python

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-security-audit-copy)

**Author:** Abhinaya Balakumar  
**Email:** balakumarabhinaya@gmail.com

---

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_tz9xp5km)

---

## Introducing Today's Project!

In this project, I’m going to build an AI-powered security scanner that uses the Gemini API to detect vulnerabilities in Python code. This will help me learn how to integrate APIs, apply prompt engineering, and understand common cybersecurity risks like SQL injection and insecure hashing. I’m interested in this because it combines AI and security, two areas I want to explore further in real-world software development.


### Key tools and concepts

The key tools I used in this project include Python, the Google Gemini API, `google-genai`, `python-dotenv`, virtual environments (`venv`), and the command line.

Key concepts I learned include API integration, prompt engineering, secure API key storage with `.env` files, and common cybersecurity vulnerabilities such as SQL Injection, Command Injection, insecure MD5 hashing, and hardcoded credentials. I also learned how AI can help automate security analysis and suggest secure coding fixes.


### Challenges and wins

I did this project today to learn how to build an AI-powered security scanner using Python and the Gemini API to detect vulnerabilities in code automatically. Another skill I want to learn is how to build more advanced cybersecurity tools with machine learning and real-time threat detection.

---

## Generating the Gemini API Key

Getting an API Key by generating it via Google Gemini.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_h3ymx6kd)

---

## Setting Up the Python Environment

We are setting up the virtual environment by creating a new project folder, installing Python, and finally creating a virtual Python environment to build in.


![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_rb4kj7mz)

### Installing the required packages

Now that I have my virtual environment set up I need to install python-dotenv and google-genai. This is important for my project because we need to securely store our Gemini API Key and recognize Gemini calls written in Python.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_pw6dq3ck)

---

## Connecting to the Gemini API

In this step, I'm connecting to Gemini. This is important because I need to test if the Gemini API connection works.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_yw8dt2jh)

### Securing the API key with a .env file

I got an error! My error was that the script was trying to load a GOOGLE_API_KEY from a .env file, but I haven't created a .env file. So the function .getenv is failing. Having a .env file is important because of security of the API Key.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_kn3jm8tb)

### Verifying the connection

I verified the connection by running python scanner.py. Gemini responded with a response for my prompt, which confirmed that my connection is working.

---

## Engineering the Security Prompt

In this step, I'm writing a security prompt that tells Gemini to analyze code for vulnerabilites and test that it works.This is important because I need to see if Gemini understands its security expert role.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_rk9mb7ys)

---

## Building the File Scanner

In this step, I'm adding file scanning so my scanner can read real Python files from my computer and send their code to Gemini for a full security analysis. This is important because I need to verify that my full scanner code is ready to go.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_jt7px3na)

---

## Running the Security Audit

In this step, I'm testing my scanner by creating a test file with a security flaw. I'll start with one vulnerability first because I need to test if the scanner is working.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_ub6ry1wf)

### Analyzing the vulnerability report

My scanner detected several major security vulnerabilities, including SQL Injection, Insecure Password Hashing using MD5, and Command Injection. These vulnerabilities could allow attackers to bypass logins, steal sensitive data, crack passwords, or even execute harmful system commands on the machine.

The most surprising vulnerability was the Command Injection issue in the `process_input` function. I was surprised because a simple line using `os.system()` with user input can actually allow someone to run arbitrary terminal commands, making it extremely dangerous if left unprotected.

This shows that AI can help with security by quickly identifying insecure coding practices, explaining why they are dangerous, and even suggesting secure alternatives with corrected code examples. Instead of manually reviewing every line of code, AI tools like Gemini can speed up vulnerability detection and help developers learn safer programming techniques.

---

## Adding Color-Coded Severity Ratings

In this secret mission, I am upgrading my AI security scanner to rank vulnerabilities by severity and display them in color-coded format. This helps prioritize the most dangerous issues first so critical bugs like command injection stand out clearly from lower-risk ones like weak hashing.


![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/ai-security-audit-copy_mj7rc2vy)

### How the color system works

I added colour to my responses by using the `colorama` library in Python to style terminal output based on vulnerability severity levels.


---

## Wrapping Up

This project took me approximately 1 hour. 

I did this project today to learn how to build an AI-powered security scanner using Python and the Gemini API to detect vulnerabilities in code automatically. Another skill I want to learn is how to build more advanced cybersecurity tools with machine learning and real-time threat detection.


---

---
