
🐳 1. Docker, Containers, and Images
🔹 What is Docker?
Docker is a tool that helps you package your application and all its dependencies (Python, Flask, Nginx, etc.) into a single unit called an image.
You can then run this image as a container anywhere — on your laptop, in the cloud, or on a server.

🔹 Analogy
Term	Real World Analogy
Dockerfile	Recipe for baking a cake
Image	The cake (made from the recipe)
Container	A lunchbox containing one cake
Docker Hub	A cake store (public storage for cakes)
Docker	The chef that prepares and packs the cake

🔹 Example: Flask App with Docker
Folder: docker-example-flask/

📄 app.py

python
Copy
Edit
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello from inside Docker!"
📄 Dockerfile

Dockerfile
Copy
Edit
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install flask
CMD ["python", "app.py"]
📄 Commands to Build & Run:

bash
Copy
Edit
docker build -t my-flask-app .
docker run -p 5000:5000 my-flask-app
💡 Now visit: http://localhost:5000
