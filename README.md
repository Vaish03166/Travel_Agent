# Travel Agent using IBM Cloud

🚀 Overview:
The AI Travel Planner Agent is an intelligent assistant designed to simplify and personalize travel planning. Built using IBM Cloud Lite services and powered by IBM Granite foundation models, this agent provides real-time recommendations, creates optimized itineraries, and manages bookings — all tailored to user preferences and constraints.

Whether you're planning a solo adventure, a family vacation, or a business trip, this smart assistant handles the complexity so you can focus on enjoying your journey.

## Tech
IBM Cloud Watsonx AI Studio

IBM Cloud Watsonx AI runtime

IBM Cloud Agent Lab

IBM Granite foundation model

## Code Snippet
import requests

# NOTE: you must manually set API_KEY below using information retrieved from your IBM Cloud account (https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-authentication.html?context=wx)
API_KEY = "aKm8bfjGgc_dM14WEYEW8F1Lbu3XKYAzKY4RYFd7mPXw"
token_response = requests.post('https://iam.cloud.ibm.com/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
mltoken = token_response.json()["access_token"]

header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}

# NOTE:  manually define and pass the array(s) of values to be scored in the next line
payload_scoring = {"messages":[{"content":"","role":""}]}

response_scoring = requests.post('https://us-south.ml.cloud.ibm.com/ml/v4/deployments/ab068d3b-461e-43a6-baa5-1726b021518e/ai_service_stream?version=2021-05-01', json=payload_scoring,
 headers={'Authorization': 'Bearer ' + mltoken})

print("Scoring response")
try:
    print(response_scoring.json())
except ValueError:
    print(response_scoring.text)
except Exception as e:
    print(f"An unexpected error occurred: {e}")

# RESULTS

   <img width="1600" height="763" alt="image" src="https://github.com/user-attachments/assets/6c93a032-dc12-40f8-9cd7-7d9440b90159" />
   <img width="1600" height="758" alt="image" src="https://github.com/user-attachments/assets/b4f486cf-54d8-4f66-92ef-1f133d6e9926" />
   <img width="1600" height="761" alt="image" src="https://github.com/user-attachments/assets/f189d772-ad1f-4c9b-990d-f1595fe6761c" />
   <img width="1600" height="760" alt="image" src="https://github.com/user-attachments/assets/529daeac-fedb-4caf-81d8-168640a27f18" />
   <img width="1600" height="761" alt="image" src="https://github.com/user-attachments/assets/ff9321d0-e3a3-46a9-a839-bf34335441a4" />

