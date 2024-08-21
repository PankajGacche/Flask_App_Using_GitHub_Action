# Flask_App_Using_GitHub_Action

# Run below commands on Source machine
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
 # Run below commands on Deployment machine 
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



