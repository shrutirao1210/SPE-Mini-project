## Project Structure

### Root Files
- **Dockerfile** – Defines instructions for building a Docker image.  
- **Jenkinsfile** – Specifies CI/CD pipeline steps for Jenkins automation.  
- **README.md** – Documentation file explaining the project setup and usage.

### Source Code & Logic
- **main.py** – Main script containing the scientific calculator logic.  
- **test.py** – Test script for verifying functionality (probably using pytest).

### Deployment & Automation
- **deploy.yml** – Ansible playbook for automated deployment.  
- **inventory** – Ansible inventory file listing target servers.

### Dependencies
- **requirements.txt** – Lists Python dependencies required for the project.

### Frontend Files
- **static/** – Contains static web files for the frontend.  
- **index.html** – The HTML file for the web-based calculator UI.
