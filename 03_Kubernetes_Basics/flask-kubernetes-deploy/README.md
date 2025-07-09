✅ STEP 5: Kubernetes + Minikube

🔧 Project: Deploy above Flask app on Kubernetes (Minikube)

Start Minikube:

bash
Copy

minikube start
Create YAML files:

deployment.yaml

yaml
Copy

apiVersion: apps/v1
kind: Deployment
metadata:
  name: flask-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: flask
  template:
    metadata:
      labels:
        app: flask
    spec:
      containers:
      - name: flask
        image: <your-dockerhub-username>/flask-docker-app:v1
        ports:
        - containerPort: 5000
service.yaml

yaml
Copy

apiVersion: v1
kind: Service
metadata:
  name: flask-service
spec:
  type: NodePort
  selector:
    app: flask
  ports:
    - port: 5000
      targetPort: 5000
      nodePort: 30007
Apply:

bash
Copy

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
minikube service flask-service
