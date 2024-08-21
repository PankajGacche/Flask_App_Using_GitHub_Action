# Flask_App_Using_GitHub_Action

 python3 --version
 python3 -m venv myenv
 ls
 source myenv/Scripts/activate
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
 sudo apt install python3 python3-pip python3-venv
 sudo ufw enable
 sudo ufw allow 5000
 sudo ufw reload
 sudo ufw status
 gunicorn --bind 0.0.0.0:5004 app:app
 cd /etc/systemd/system/flaskapp.service
 /ubuntu/home/Flask/venv/bin
 sudo systemctl daemon-reload
 sudo systemctl enable --now flask-app.service
 sudo systemctl status flaskapp.service

 git tag v1.2.3
 git push origin v1.2.3



