# Flask_App_Using_GitHub_Action

## Setup
- Python application repository on GitHub
![alt text](Readme_File_Images/image.png)

- Repository has a main branch and a staging branch
![alt text](Readme_File_Images/image-1.png)

- Created .github/workflows directory in repository and inside it created a YAML file to define the workflow
![alt text](Readme_File_Images/image-2.png)

## Defined below workflow Steps
- Install Dependencies
- run_tests
- build
- deploy_staging
- deploy_production

![alt text](Readme_File_Images/image-3.png)
![alt text](Readme_File_Images/image-4.png)
![alt text](Readme_File_Images/image-5.png)
![alt text](Readme_File_Images/image-6.png)
![alt text](Readme_File_Images/image-7.png)
![alt text](Readme_File_Images/image-8.png)
![alt text](Readme_File_Images/image-9.png)
![alt text](Readme_File_Images/image-10.png)

- Created GitHub Secrets to store sensitive information required for deployments
![alt text](Readme_File_Images/image-11.png)

## Install Dependencies: 
- Install all necessary dependencies for the Python application using pip.
## Run Tests: 
- Execute the test suite using a framework pytest.
## Build:
- When tests pass, prepare the application for deployment.
## Deploy to Staging: 
- Deploy the application to a staging environment when changes are pushed to the staging branch.
![alt text](Readme_File_Images/image-12.png)
## Deploy to Production:
- Deploy the application to production when a release is tagged.
- Created release tag and pushed to Github
![alt text](Readme_File_Images/image-13.png)
![alt text](Readme_File_Images/image-14.png)
![alt text](Readme_File_Images/image-15.png)

- After Deployment to production, verified all files are available on Deployment server
![alt text](Readme_File_Images/image-16.png)
![alt text](Readme_File_Images/image-17.png)

## Run below commands on Source machine
```bash
sudo apt update
sudo apt install python3
sudo apt install python3-pip
python3 -m venv myenv && source myenv/Scripts/activate
pip install flask pytest
pip freeze > requirements.txt
cat requirements.txt
mkdir src
create app.py file
mkdir tests
create test_app.py
export PYTHONPATH=src
push changes to repository
ssh keygen -t rsa -b 4096 -C "Flask-App"

 ## Run below commands on Deployment machine
 ```bash 
 sudo apt update
 sudo apt install python3
 sudo apt install python3-pip
 python3 -m venv myenv && source myenv/Scripts/activate
 pip install flask pytest
 pip install gunicorn
 sudo ufw enable
 sudo ufw allow 22
 sudo ufw allow 80
 sudo ufw allow 5000
 sudo ufw reload
 gunicorn --bind 0.0.0.0:5000 app:app
 sudo touch /etc/systemd/system/flaskapp.service
 sudo sh -c 'printf "[Unit]\nDescription=Flask Application\nAfter=network.target\n\n[Service]\nUser=ubuntu\nGroup=ubuntu\nWorkingDirectory=/home/ubuntu/Flask-Deployment\nExecStart=/home/ubuntu/.local/bin/gunicorn --workers 3 --bind unix:flaskapp.sock app:app\nRestart=always\n\n[Install]\nWantedBy=multi-user.target\n" > /etc/systemd/system/flaskapp.service'
 sudo systemctl daemon-reload
 sudo systemctl enable --now flask-app.service
 git tag v1.2.3
 git push origin v1.2.3



