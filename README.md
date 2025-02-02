# Trellix Analytic Service Integrator
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

This service provides the ability to integrate various Trellix solutions with Malware Analytic Services such as Detection-On-Demand (Detection as a Service). The following two use cases are implemented in the current design.

1. Integrates Trellix Endpoint and Trellix TIE (Threat Intelligence Exchange) with Trellix DaaS (Detection as a Service).
2. Integrates Skyhigh Web Gateway (on-premise) with Trellix DaaS (Detection as a Service).
3. Integrates Skyhigh Security Service Edge (SSE) with Trellix DaaS (Detection as a Service)

This service is written as a flask web application that simulates the ATD|TIS (Advanced Threat Detection | Trellix Intelligence Sandbox) APIs. 
This service can be used with every Trellix solution that natively integrates with ATD|TIS.

## Installation

This is proof of concept code only. In production please make sure to not store username, password and API keys in clear text inside the script.

1. Install > Python3.6

2. Make sure the following dependencies are installed

   ```
   python3 -m pip install requests flask
   ```

3. Place the app.py and report.json in a folder and browse to that folder location (e.g. location /opt/app/)

   ```
   cd /opt/app/
   ```
   
4. Enter a username and password in line 17 and 18. This username and password will need to be the same as configured in TIE and MWG.

   <img width="800" alt="1" src="https://user-images.githubusercontent.com/25227268/178490885-6313649d-9f54-48fb-89fe-cb41d9f7b574.png">
   
5. Generate an API Key in DaaS and enter this key in line 21. 

<img width="2127" alt="Screenshot 2022-11-10 at 17 13 57" src="https://user-images.githubusercontent.com/58554206/201149202-354b8f83-77df-48e2-b4f1-c4992fcfcd40.png">


6. Run the flask app with the following command. Specify the listening IP address and Port. (e.g. listen on all IPs and port 8080)

   ```
   flask run --host 0.0.0.0 --port 8080
   ```
   
## Trellix TIE Configuration

1. Open the TIE Server Policy in EPO and select the Sandboxing Tab inside the policy.

2. Enter the username and password entered in Installation Step 4.

   <img width="800" alt="2" src="https://user-images.githubusercontent.com/25227268/178493586-41bc486d-adcf-41a2-9461-5e00adf7a0fc.png">
   
3. Configure the IP address and Port to point to the Flask Application.

## On-premise Skyhigh Web Gateway Configuration

1. Open the Web Gateway Policy and import a new Rule Set from the Library.

2. Add the Advanced Threat Detection Rule Set or modify the existing ATD policy.

   <img width="800" alt="3" src="https://user-images.githubusercontent.com/25227268/178501940-64104886-0f1d-44c4-83ea-90f208617c48.png">
   
3. Configure the Policy to point to the Flask App and enter the username and password entered in Installation Step 4.

   <img width="800" alt="4" src="https://user-images.githubusercontent.com/25227268/178503192-7ab4a74b-c990-49a6-a9fb-d2ed57b78cdf.png">
   
## Skyhigh Security Service Edge Configuration
   
1. On Skyhigh Security Service Edge open Web policy and click on Anti-Malware for Trellix ATD.
2. Configure the Policy to point to the Flask App and enter the username and password entered in Installation Step 4.

<img width="2560" alt="Screenshot 2022-11-10 at 16 52 47" src="https://user-images.githubusercontent.com/58554206/201146965-5d339db1-4113-4fbb-86a2-37cf0e3913b5.png">

3. Make sure Advanced Threat Detection Rule Set is enabled

<img width="2129" alt="Screenshot 2022-11-10 at 17 09 00" src="https://user-images.githubusercontent.com/58554206/201147929-2b5e799a-4da2-4c9f-9d42-d3f9a9854096.png">

4. DaaS dashboard with the number of submissions

<img width="2123" alt="Screenshot 2022-11-10 at 17 18 18" src="https://user-images.githubusercontent.com/58554206/201149871-e6b5d6ae-62d1-43e7-a9b9-e6200af23d00.png">

