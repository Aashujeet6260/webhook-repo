# 🚀 GitHub Webhook Receiver

This project is a simple **GitHub Webhook Receiver** built with **Flask**, **MongoDB**, and **ngrok**.

It listens for GitHub events (**Push**, **Pull Request**, and **Merge**) from your `action-repo`, stores them in a local MongoDB database, and displays them via an API or UI.

---

## 📌 Features

✅ Receives GitHub webhook events (push, pull request, merge)\
✅ Saves each event’s **author**, **branches involved**, **action type**, and **timestamp** in MongoDB\
✅ Uses **Flask** as the backend server\
✅ Uses **MongoDB Compass** to inspect saved data\
✅ Uses **ngrok** to expose your local server to GitHub

---

## ⚙️ Requirements

- Python 3.x
- Flask
- PyMongo
- MongoDB Community Server (running locally)
- [ngrok](https://ngrok.com) (to expose your local Flask server)

---

## 🚀 Getting Started

### 1️⃣ Clone this repository

```bash
git clone https://github.com/YOUR-USERNAME/webhook-repo.git
cd webhook-repo
```

---

### 2️⃣ Create and activate a virtual environment

```bash
# Create
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Install requirements
pip install -r requirements.txt
```

---

### 3️⃣ Make sure MongoDB is running

✅ If you installed MongoDB as a Windows Service, it runs automatically.\
✅ Or start it manually:

```bash
mongod
```

Use **MongoDB Compass** to verify you can connect to:

```
mongodb://localhost:27017
```

---

### 4️⃣ Run the Flask server

```bash
python app.py
```

By default, the server runs at:

```
http://127.0.0.1:5000
```

---

### 5️⃣ Start ngrok (new terminal)

Expose your local server:

```bash
ngrok http 5000
```

Copy your generated **ngrok URL**, for example:

```
https://abc123.ngrok-free.app
```

---

### 6️⃣ Update your GitHub `action-repo` Webhook

In your **GitHub repository settings**:

- Go to **Settings → Webhooks**
- Set the **Payload URL** to:
  ```
  https://abc123.ngrok-free.app/webhook
  ```
- Content type: `application/json`
- Select individual events: ✅ Push, ✅ Pull Requests

---

### 7️⃣ Test it!

- Make a push or open a pull request in your `action-repo`.
- GitHub will send the webhook to your Flask server.
- Flask saves it to MongoDB.
- Open **MongoDB Compass**, connect to `localhost:27017`, and find the `webhook_db` → `events` collection to see your data.

---

## 📊 Example Event Formats

- **Push:** `{author} pushed to {to_branch} on {timestamp}`
- **Pull Request:** `{author} submitted a pull request from {from_branch} to {to_branch} on {timestamp}`
- **Merge:** `{author} merged branch {from_branch} to {to_branch} on {timestamp}`

---

## 🧑‍💻 Project Structure

```plaintext
webhook-repo/
 ├── app.py
 ├── requirements.txt
 └── templates/
      └── index.html (optional if you have a simple UI)
```

---

## 📚 Tech Stack

- **Flask** — Python web framework
- **PyMongo** — MongoDB client for Python
- **MongoDB** — Local database
- **MongoDB Compass** — GUI for your database
- **ngrok** — Secure tunnel to localhost

---

## ✅ Author

Built as part of a developer task to demonstrate backend integration, database storage, and webhook handling using open source tools.

---

## 🔗 Useful Links

- [MongoDB Download](https://www.mongodb.com/try/download/community)
- [MongoDB Compass](https://www.mongodb.com/products/compass)
- [ngrok](https://ngrok.com/)

---

Happy Coding! 🚀
