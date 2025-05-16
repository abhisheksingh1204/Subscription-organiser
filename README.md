# Subscription-organiser
[![Docker](https://img.shields.io/docker/pulls/dh1011/subscription-manager.svg)](https://hub.docker.com/r/dh1011/subscription-manager)

This single-page web application lets you keep track of and manage your subscriptions. You can add, edit, delete, and view subscriptions all in one place. You can set up notifications for each subscription using NTFY. The app provides a general summary of all your subscriptions and a detailed summary for each payment account, all within a single, intuitive interface.

## Demo
https://github.com/user-attachments/assets/9e7830e1-3c3c-474a-8f48-93ee8f5e440d

## Features
- ➕ Add, edit, and delete subscriptions
- 🗓️ View subscriptions on a calendar
- 💰 Calculate weekly, monthly, and yearly totals
- 📊 Detailed summaries per payment account
- 🖼️ Easy to add icons for each subscription
- 🔔 Notification system integration with NTFY
- 💱 Support for multiple currencies

## Tech Stack

- ⚛️ React
- 🚂 Express
- 🗄️ SQLite
- 🐳 Docker
- 🎨 Iconify

## Setup

### Using Docker Compose

1. Create a `docker-compose.yml` file with the following content:

   ```yaml
   version: "3.9"
   services:
   backend:
      image: dh1011/subscription-manager-backend:2.0.0
      ports:
         - "5000:5000"
      volumes:
         - ./data:/app/data
      restart: unless-stopped

   frontend:
      image: dh1011/subscription-manager-frontend:2.0.0
      ports:
         - "3000:3000"
      environment:
         - REACT_APP_API_URL=http://your_id_address:5000
      depends_on:
         - backend
      restart: unless-stopped
   ```

2. Replace `your_ip_address` in the `REACT_APP_API_URL` environment variable with:
   - Your local machine's IP address, or
   - The server's IP address where the backend will run.

3. Run Docker Compose:
   ```bash
   docker-compose up -d
   ```

4. The app will be available at `http://your_ip_address:3000`.

---

### Manual Setup

#### Backend
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/subscription-manager.git
   cd subscription-manager/backend
   ```

2. Create a Python virtual environment and activate it:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Start the backend server:
   ```bash
   uvicorn app:app --host 0.0.0.0 --port 5000
   ```

#### Frontend
1. Navigate to the frontend directory:
   ```bash
   cd ../frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set the environment variable for the API URL:
   ```bash
   export REACT_APP_API_URL=http://your_ip_address:5000
   ```

4. Start the development server:
   ```bash
   npm start
   ```

5. The app will be available at `http://localhost:3000`.

## Adding Icons

This app uses Iconify icons. To add an icon to your subscription, use the icon name from the [Iconify icon library](https://icon-sets.iconify.design/).

## Notifications

The app integrates with NTFY for sending notifications. To set up notifications:

1. Go to the Settings page
2. Enter your NTFY topic
3. Save the settings

You'll receive notifications for upcoming subscription payments.
