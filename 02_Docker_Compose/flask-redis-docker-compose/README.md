✅ STEP 4: Mini-Project 2 — Docker Compose for Multi-Container App

🔧 Project: Flask + Redis App using Docker Compose

Flask hits Redis to count visits.

Create folder flask-redis-app

Files:

app.py

python
Copy



from flask import Flask
import redis

app = Flask(__name__)
r = redis.Redis(host='redis', port=6379)

@app.route('/')
def home():
    count = r.incr('visits')
    return f"Visit count: {count}"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
Dockerfile, requirements.txt (same as above, plus redis)



docker-compose.yml

yaml
Copy

version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: redis:alpine
Run:


bash
Copy


docker-compose up --build
