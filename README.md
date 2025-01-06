# Twilio Bidirectional RND

This project demonstrates bidirectional communication using Twilio's APIs with FastAPI. It allows you to create, manage, and stream calls interactively, leveraging Twilio's Media Streams and FastAPI's asynchronous capabilities.

## 🚀 How to Run the Project

### Prerequisites

Make sure you have the following installed:
- Python 3.7 or later
- pip (Python package manager)
- [ngrok](https://ngrok.com/download) (for exposing localhost)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/twilio-bidirectional-rnd.git
   cd twilio-bidirectional-rnd
   ```

2. Install the required dependencies:
   ```bash
   pip install fastapi pydantic twilio python-dotenv
   ```

### Running the Application

1. Start the first FastAPI application for making simple calls:
   ```bash
   uvicorn simple-call-maker:app --port 8000 --reload
   ```

2. Start the bidirectional FastAPI application for media streaming:
   ```bash
   uvicorn bidirectional:app --port 5050 --reload
   ```

3. Expose the bidirectional app using ngrok:
   ```bash
   ngrok http 5050
   ```

4. Configure Twilio webhooks:
   - Add the `<ngrok_url>/media-stream` URL to the XML source in `bidirectional.py`.
   - Add the `<ngrok_url>/incoming-call` URL to `simplecaller.py`.

### Example Workflow

1. Use the **`simple-call-maker`** to initiate a call.
2. Use the **`bidirectional`** app to handle the Twilio Media Streams for real-time communication.
3. Expose the application with ngrok and connect it to Twilio's webhook system for bidirectional audio streaming.

## 🛠️ Features

- **FastAPI Integration**: High-performance Python framework for API development.
- **Twilio Media Streams**: Real-time audio streaming via Twilio's API.
- **Bidirectional Communication**: Enables two-way audio interaction.
- **Environment Variable Management**: Securely manage API credentials using `python-dotenv`.

## 🔧 Configuration

Create a `.env` file in the root directory and add the following:
```env
TWILIO_ACCOUNT_SID=<your_account_sid>
TWILIO_AUTH_TOKEN=<your_auth_token>
TWILIO_PHONE_NUMBER=<your_twilio_phone_number>
```

## 📘 Documentation

- [Twilio Media Streams Documentation](https://www.twilio.com/docs/voice/twiml/stream)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)

## ✨ Contributing

Feel free to fork this repository, make your changes, and submit a pull request. Contributions are always welcome!

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
