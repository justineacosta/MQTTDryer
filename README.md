# MQTTDryer

A Node.js/Express web app for monitoring and controlling an MQTT-connected dryer. It
combines real-time sensor data (over MQTT and Socket.IO) with a MongoDB-backed dashboard for
starting/stopping drying cycles, viewing temperature history, and generating PDF reports.

## Features

- **Live dashboard** — real-time temperature/sensor readings pushed over Socket.IO
- **Drying control** — start and finish drying cycles (`/StartDrying`, `/FinishDrying`)
- **History** — temperature logs at multiple granularities (per-minute, five-minute) stored
  in MongoDB
- **User accounts** — session-based login, with admin user management (add/edit/delete users)
- **PDF reports** — per-cycle and bulk report generation/download via `pdfkit`, `puppeteer`,
  and `docxtemplater`

## Tech stack

Express, MongoDB (Mongoose), MQTT.js, Socket.IO, EJS/Pug views, Bootstrap.

## Getting started

### Prerequisites

- Node.js
- A MongoDB instance
- An MQTT broker

### Setup

```bash
npm install
```

Create a `.env` file in the project root with:

```env
DATABASE_URL=your-mongodb-connection-string
MQTT_HOST=your-mqtt-broker-host
MQTT_PORT=your-mqtt-broker-port
MQTT_PROTOCOL=mqtts
```

### Run

```bash
npm start        # node server.js
npm run devStart  # nodemon server.js, for development
```

The server listens on port `10000` by default.

## Project structure

```text
server.js       # Express app, MQTT client, Socket.IO, all routes
Details/        # Mongoose models (sensor data, temperature logs, users, activity log)
routes/         # Express route modules
views/          # EJS/Pug templates — Dashboard, Control, History, Login, Profile
public/         # Static assets
uploads/        # Uploaded files
```
