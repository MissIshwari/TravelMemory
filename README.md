# Travel Memory

`.env` file to work with the backend:

```
MONGO_URI='ENTER_YOUR_URL'
PORT=3000
```

`.env` file for frontend code to connect to backend base url
```
REACT_APP_BACKEND='backend url'
```

Data format to be added: 

```json
{
    "tripName": "Incredible India",
    "startDateOfJourney": "19-03-2022",
    "endDateOfJourney": "27-03-2022",
    "nameOfHotels":"Hotel Namaste, Backpackers Club",
    "placesVisited":"Delhi, Kolkata, Chennai, Mumbai",
    "totalCost": 800000,
    "tripType": "leisure",
    "experience": "Lorem Ipsum, Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum, ",
    "image": "https://t3.ftcdn.net/jpg/03/04/85/26/360_F_304852693_nSOn9KvUgafgvZ6wM0CNaULYUa7xXBkA.jpg",
    "shortDescription":"India is a wonderful country with rich culture and good people.",
    "featured": true
}
```

Deployment on AWS cloud

Created 2 EC2 instances of t2 micro instance type, and key pair, allowing http, https and SSH traffic.

Updated backend EC2 instance with 
sudo apt update

Installed git in it
sudo apt install git

Created a fork from the original repo and cloned it
git clone https://github.com/MissIshwari/TravelMemory.git

Installed node with the below commands
sudo apt install curl
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash –
sudo apt-get install nodejs -y

Installation of backend packages from package.json within the backend folder
npm install

Created a .env file in the backend folder
Updated Mongodb URI and port for backend as suggested in Readme.md

Pasted the backend EC2 instance IP to base_url in url.js of frontend folder
Added inbound rules to access port 3000 for both frontend and backend on EC2 instances.

Created a database named travelmemory with collections named mem and tripdetails

Created access entry to access travelmemory db from everywhere.

Installed nginx on both frontend and backend and set up a proxy to redirect to running code on port 3000 on both EC2 instances.

Changed the URL to ip of the backend as the default configuration internally accesses http://localhost:3000 for the backend server

Started both servers
frontend by
npm start

backend by
node index.js

Restarted the nginx
The backend and frontend applications are accessed through IP from the browser.
-----------------------------------------------------------

Created a domain name fortest.shop on Hostinger. 
Registered it onto Cloudflare

Updated registrar Hostinger with nameservers of Cloudflare.

Created a load balancer which is internet facing and provided appropriate VPC of the EC2 instances

Selected all Availability zones to route by load balancer.
Selected default security group


Created a target group for load balancer
Provided target group name as ishwari-target-group2
Protocol is http and port is 80
IP Address type as IPv4

Created CNAME for load balancer with www as name
Another CNAME for load balancer with its dns in the IP address and an A record for backend that points to api.fortest.shop.

Created a client certificate on cloudflare under SSL/TLS >> Client certificates
Private key type – RS 2048
Certificate validity – 10 years

Accessed the website https://fortest.shop through the browser.





 

