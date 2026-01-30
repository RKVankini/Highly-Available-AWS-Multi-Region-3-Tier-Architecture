# 🚀 3-Tier Application on AWS

This repository is created to learn and deploy a 3-tier application on AWS Cloud.  
The project follows a simple architecture consisting of Presentation Layer, Application Layer, and Database Layer.

------------------------------------------------------------

## 🏠 Architecture

![Architecture of the application](architecture.gif)

------------------------------------------------------------

## 🧰 Tech Stack

- React
- Node.js
- MySQL

------------------------------------------------------------

## 📌 Project Overview

This project includes the following components:

1. MySQL database hosted on Amazon RDS inside private subnets  
2. Backend application deployed on a private EC2 instance  
3. Frontend application deployed on a separate EC2 instance  
4. Two Target Groups and two Application Load Balancers:
   - One for frontend
   - One for backend  
5. Load Balancers are deployed in public subnets and configured as internet-facing  

------------------------------------------------------------

## ⚙️ Backend Setup

### Step 1: Connect to Backend Server

git clone https://github.com/RKVankini/Highly-Available-AWS-Multi-Region-3-Tier-Architecture.git

cd backend

------------------------------------------------------------

### Step 2: Configure Database Connection

Create a `.env` file inside the backend directory.

Path: backend/.env


Add the following content:

DB_HOST=book.rds.com # Replace with your RDS endpoint
DB_USERNAME=admin # Replace with your RDS username
DB_PASSWORD=your_password # Replace with your RDS password
PORT=3306

------------------------------------------------------------

### Step 3: Install MySQL Client and Initialize Database

sudo yum install mariadb105-server -y
mysql -h book.rds.com -u admin -p < test.sql

------------------------------------------------------------

### Step 4: Backend Deployment

sudo dnf install -y nodejs
npm install
npm install dotenv
npm install -g pm2

pm2 start index.js --name node-app
pm2 startup
pm2 save

After deployment, attach the backend instance to a target group and verify the response using the backend load balancer.

------------------------------------------------------------

## 🌐 Frontend Setup

### Step 1: Clone Repository on Frontend Server

git clone https://github.com/RKVankini/Highly-Available-AWS-Multi-Region-3-Tier-Architecture.git

cd client

------------------------------------------------------------

### Step 2: Update Backend API URL

Edit the following file:

client/src/pages/config.js

Update the API URL: const API_BASE_URL = "http://<backend-load-balancer-dns>";


------------------------------------------------------------

### Step 3: Frontend Deployment

sudo dnf install -y nodejs
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd

npm install
npm run build

sudo cp -r build/* /var/www/html

After this step, attach the frontend instance to the frontend target group and verify the application through the frontend load balancer.

------------------------------------------------------------

## ✅ Final Output

Once all components are configured:
- Frontend communicates with backend through Load Balancer  
- Backend connects securely to RDS  
- Application works as a complete 3-tier setup on AWS  

------------------------------------------------------------

**Thank you for reading 🙂**
