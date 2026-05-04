# BackendGPT-CICD-Project 🛠️

The core API service for the GPT-CICD project, powered by **Node.js** and **Express**. It handles data processing, OpenAI integration, and connects to a MongoDB Atlas cloud database.

## 🛠 Tech Stack
- **Runtime:** Node.js v22.x
- **Framework:** Express.js
- **Database:** MongoDB Atlas
- **Process Manager:** PM2 (Zero-downtime)
- **Infrastructure:** AWS EC2

## 🏗 Architecture & CI/CD
This backend is managed via **PM2** on a shared EC2 instance. Our GitHub Actions pipeline handles the sensitive `.env` management and restarts the service automatically.


## 🤖 CI/CD Pipeline
On every push to `main`, the following automated steps occur:
1. **Backup:** Securely backups the existing `.env` file.
2. **Sync:** Pulls the new code via GitHub Actions.
3. **Restore:** Re-applies the `.env` configuration.
4. **Deploy:** Installs dependencies and runs `pm2 restart backend`.

## 🔑 Environment Variables
Create a `.env` file with the following keys:
- `PORT=9000`

## 📋 Troubleshooting
- **PM2 Logs:** Run `pm2 logs backend` to see real-time errors.
- **DB Connection:** Ensure the EC2 IP is whitelisted in MongoDB Atlas.
- **Port Access:** Verify that Port 9000 is open in the AWS Security Group.
