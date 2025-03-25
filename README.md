<h1> Chatbot</h1>
User interaction with chatbot static message
We'll set up a serverless chatbot system on AWS Free Tier step by step. I'll guide you through everything, including architecture, AWS services, deployment, and testing.

<h2> 🔹 What We’ll Build</h2>

<h2>🚀 Technologies Used</h2>
    <ul> A basic chatbot using:      
        <li>✅ AWS Lambda – Serverless function for chatbot logic</li>
        <li>✅ Amazon API Gateway – Handles user requests</li>
        <li>✅ Amazon DynamoDB – Stores chatbot messages</li>
        <li>✅ Amazon S3 – Stores logs for future analysis</li>
        <li>✅ AWS CloudWatch – Monitors chatbot activity</li>
        <li>✅ IAM Roles & Policies – Secures access</li>
    </ul>
</div>
 
 


<h2>🔹 Step-by-Step Guide</h2>
I’ll provide detailed steps along with sample data so you can follow along easily. Here’s the plan:

1️⃣ Set up AWS Free Tier – Ensure your account is ready.
2️⃣ Create a Lambda Function – Write the chatbot logic.
3️⃣ Set Up API Gateway – Connect users to Lambda.
4️⃣ Create a DynamoDB Table – Store chatbot messages.
5️⃣ Store Logs in S3 – Save chatbot interactions.
6️⃣ Set Up Monitoring – Use CloudWatch for alerts.
7️⃣ Test the Chatbot – Verify end-to-end functionality.
8️⃣ Deploy & Scale – Automate using Infrastructure as Code.

<h1>🔹 Step 1: Create an AWS Lambda Function (Chatbot Logic)</h1>
✅ What is AWS Lambda?
AWS Lambda is a serverless compute service that runs your chatbot’s code only when needed, so you don’t need to manage any servers.

✅ What Will This Function Do?
1️⃣ Receive a user message (e.g., “Hello”) from API Gateway.
2️⃣ Process the message using a simple chatbot logic.
3️⃣ Return a response (e.g., “Hi! How can I help you?”).

<h1>🔹 Step-by-Step Guide</h1>
1️⃣ Open AWS Lambda Console
Go to AWS Lambda Console
Click “Create function”
Choose "Author from scratch"
Function name: ChatbotLambda
Runtime: Choose Python 3.9 (or latest available version)
Permissions: Choose "Create a new role with basic Lambda permissions"
Click “Create function”

<h1>2️⃣ Write the Lambda Function Code</h1>
Once your function is created:

Scroll down to the Code section
Delete any default code and copy-paste this Python code:

<h1>3️⃣ Deploy the Lambda Function</h1>
Click “Deploy”
Your Lambda function is now ready!

Python Code

<h1>🔹 Step 2: Set Up API Gateway (User Interaction Endpoint)</h1>
✅ What is API Gateway?
Amazon API Gateway is a fully managed service that allows users to send requests to your Lambda function via an HTTP URL.

<h1>✅ Why Do We Need It?</h1>
Users can send messages to the chatbot using a simple web request (URL).
API Gateway will trigger the Lambda function, process the message, and return a response.
This allows your chatbot to be accessed from websites, mobile apps, or third-party applications.
🔹 Step-by-Step Guide
1️⃣ Open API Gateway Console
Go to API Gateway Console
Click “Create API”
Choose "HTTP API"
Click "Build"
2️⃣ Configure the API
API name: ChatbotAPI
Click “Next”
3️⃣ Add a Lambda Integration
Click “Add Integration”
Choose Lambda Function
Select the function we created earlier: ChatbotLambda
Click "Next"
4️⃣ Set Up Routes (User Request Handling)
Under "Routes", click "Create"
Method: GET
Resource path: /chatbot (This will be the endpoint: https://xyz.amazonaws.com/chatbot)
Click "Create"
5️⃣ Attach the Route to Lambda
Click on the /chatbot route
Click “Add integration”
Select "Lambda Function"
Choose ChatbotLambda
Click "Save"
6️⃣ Deploy the API
Click "Deploy"
Copy the Invoke URL (this is your chatbot’s public API link).
Example: https://xyz.execute-api.us-east-1.amazonaws.com/chatbot

