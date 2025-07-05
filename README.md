# Lead Generation Backend for n8n Email Automation 🚀

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white) ![Express](https://img.shields.io/badge/Express.js-404D59?style=flat-square&logo=express&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)

Welcome to the **Lead Generation Backend** repository! This project is a lightweight backend built with **Node.js** and **Express**. It handles form submissions, validates data, and forwards it to **n8n** via webhook integration. This backend acts as a bridge between your frontend application and n8n's powerful automation engine.

You can find the latest releases [here](https://github.com/webnoxin/lead-generation-BACKEND-to-send-email-through-n8n/releases).

## Table of Contents

1. [Features](#features)
2. [Installation](#installation)
3. [Usage](#usage)
4. [API Endpoints](#api-endpoints)
5. [Data Validation](#data-validation)
6. [Webhook Integration](#webhook-integration)
7. [Testing](#testing)
8. [Contributing](#contributing)
9. [License](#license)

## Features

- **Form Submission Handling**: Easily collect data from user forms.
- **Data Validation**: Ensures that the data received is valid and meets your requirements.
- **Webhook Integration**: Forwards data to n8n for automation.
- **Lightweight and Fast**: Built with efficiency in mind.
- **Easy Setup**: Simple installation process for quick deployment.

## Installation

To get started, clone this repository to your local machine:

```bash
git clone https://github.com/webnoxin/lead-generation-BACKEND-to-send-email-through-n8n.git
cd lead-generation-BACKEND-to-send-email-through-n8n
```

Next, install the necessary dependencies:

```bash
npm install
```

You can also download the latest release from the [Releases](https://github.com/webnoxin/lead-generation-BACKEND-to-send-email-through-n8n/releases) section. Look for the executable file and follow the instructions to set it up.

## Usage

To run the backend server, use the following command:

```bash
npm start
```

The server will start on the default port (3000). You can access it via `http://localhost:3000`.

### Configuration

Before using the backend, make sure to configure the following environment variables in a `.env` file:

```env
PORT=3000
N8N_WEBHOOK_URL=https://your-n8n-instance.com/webhook
```

Replace `https://your-n8n-instance.com/webhook` with your actual n8n webhook URL.

## API Endpoints

### POST /submit

This endpoint handles form submissions. It accepts JSON data and forwards it to n8n.

#### Request Body

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "message": "Hello, I am interested in your services."
}
```

#### Response

- **200 OK**: Data successfully forwarded to n8n.
- **400 Bad Request**: Validation errors.

### GET /status

This endpoint checks the status of the backend service.

#### Response

- **200 OK**: Service is running.
- **500 Internal Server Error**: Service is down.

## Data Validation

Data validation is crucial for ensuring that the data received is correct. This backend uses middleware to validate incoming requests. If the data does not meet the required criteria, the server responds with a 400 status code.

### Validation Rules

- **Name**: Required, must be a string.
- **Email**: Required, must be a valid email format.
- **Message**: Required, must be a string with a minimum length of 10 characters.

## Webhook Integration

This backend integrates seamlessly with n8n. Once the data is validated, it forwards the information to your specified n8n webhook URL. Make sure to set the correct URL in your environment variables.

### n8n Workflow

To set up a workflow in n8n:

1. Create a new workflow.
2. Add a "Webhook" node.
3. Set the HTTP Method to POST.
4. Use the same URL as specified in your backend's environment variables.

You can then add further nodes to process the data as needed.

## Testing

To test the backend, you can use tools like **Postman** or **curl**. Here’s an example using curl:

```bash
curl -X POST http://localhost:3000/submit \
-H "Content-Type: application/json" \
-d '{"name":"John Doe","email":"john@example.com","message":"Hello!"}'
```

You should receive a 200 OK response if everything is set up correctly.

## Contributing

We welcome contributions! If you would like to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes and commit them (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

Please ensure your code follows the existing style and includes appropriate tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

Feel free to explore the code, report issues, or request features. For more information, check the [Releases](https://github.com/webnoxin/lead-generation-BACKEND-to-send-email-through-n8n/releases) section for updates and improvements.

Happy coding!