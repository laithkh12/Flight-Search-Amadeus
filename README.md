# Flight Deal Tracker
This project tracks flight prices between specified cities and sends notifications to registered users when deals are found. By leveraging the Amadeus and Sheety APIs, it retrieves real-time flight data and updates Google Sheets with the best available deals. Notifications are sent through SMS, WhatsApp, or email when a price lower than a set threshold is detected.
---
## Table of Contents
- Features
- Project Structure
- Setup
- Environment Variables
- Usage
- Acknowledgments
## Features
- Tracks flight prices for specific routes
- Updates Google Sheets with destination IATA codes
- Sends notifications when a deal is found via email, SMS, or WhatsApp
- Fetches and maintains a list of users’ email addresses for notifications
---
## Project Structure
```plaintext
|-- data_manager.py
|-- flight_data.py
|-- flight_search.py
|-- main.py
|-- notification_manager.py
|-- .env
```
- **data_manager.py**: Manages data retrieval and updates for Google Sheets. Fetches and updates destination information.
- **flight_data.py**: Defines FlightData and includes helper functions to identify the cheapest flight.
- **flight_search.py**: Handles interaction with the Amadeus API to retrieve flight data and IATA codes.
- **main.py**: The main script orchestrating data retrieval, flight searches, and notifications.
- **notification_manager.py**: Manages notifications through email, SMS, and WhatsApp using environment variables for security.
---
## Setup
1. Clone this repository:
```bash
git clone <repository-url>
```
2. Install Dependencies:
```bash
pip install -r requirements.txt
```
3. Configure Environment Variables: Create a .env file with the necessary credentials and endpoints (see below).
4. Run the Project:
```bash
python main.py
```
--- 
## Environment Variables
The project requires several API credentials and endpoints stored in a .env file. Example:
```plaintext
SHEETY_USERNAME=your_sheety_username
SHEETY_PASSWORD=your_sheety_password
SHEETY_PRICES_ENDPOINT=https://api.sheety.co/<sheety-prices-endpoint>
SHEETY_USERS_ENDPOINT=https://api.sheety.co/<sheety-users-endpoint>
AMADEUS_API_KEY=your_amadeus_api_key
AMADEUS_SECRET=your_amadeus_secret
EMAIL_PROVIDER_SMTP_ADDRESS=smtp.yourprovider.com
MY_EMAIL=your_email@example.com
MY_PASSWORD=your_email_password
TWILIO_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_VIRTUAL_NUMBER=your_twilio_virtual_number
MY_PHONE_NUMBER=your_phone_number
```
---
## Usage
1. Setup Flight Data in Google Sheets:
  - Populate the sheet with cities and empty IATA codes.
  - Use DataManager to retrieve and update destination IATA codes.
2. Track Flight Deals:
  - Run main.py to check for deals between your origin city and destination cities.
  - If a lower-priced flight is available, users are notified.
3. Notification Management:
  - Notifications are sent based on user preference (SMS, WhatsApp, or email).
  - Customize NotificationManager to adjust notification methods.
---
## Acknowledgments
This project utilizes the following services:
- Amadeus API for flight data.
- Sheety API for Google Sheets integration.
- Twilio API for SMS and WhatsApp notifications.
