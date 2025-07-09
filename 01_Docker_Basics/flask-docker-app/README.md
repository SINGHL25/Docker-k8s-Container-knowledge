
✅ STEP 2: Mini-Project 1 — Simple Containerized App
🔧 Project: Hello Flask App in Docker

Create app:

bash
Copy

mkdir flask-docker-app && cd flask-docker-app

app.py

python
Copy

from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Dockerized Flask!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
    
requirements.txt

nginx

Copy

flask
Dockerfile


dockerfile
Copy

FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
EXPOSE 5000
CMD ["python", "app.py"]


Build and run:

bash


docker build -t flask-docker-app .
docker run -p 5000:5000 flask-docker-app

Test:

Visit http://localhost:5000
