# 🐳 Django Docker App Deployed to Azure ACR & ACI (CI/CD Enabled)

This project is a **Django-based web application** structured using best practices and **fully containerized** with Docker. It is automatically deployed to **Azure Container Registry (ACR)** and **Azure Container Instances (ACI)** using **GitHub Actions**.

---

## 🚀 Live Application

🌐 **URL**:  
[http://af1ndockerdjango.f8e0evfebsezebff.centralindia.azurecontainer.io:8000](http://af1ndockerdjango.f8e0evfebsezebff.centralindia.azurecontainer.io:8000)

---

## 🛠 Tech Stack

- 🐍 Python 3.x
- 🌐 Django Framework
- 🐳 Docker
- ☁️ Azure Container Registry (ACR)
- ☁️ Azure Container Instances (ACI)
- 🔄 GitHub Actions (CI/CD Automation)

---

## 📁 Project Structure
<pre>
├── core/ # Django project settings
│ ├── init.py
│ ├── asgi.py
│ ├── settings.py
│ ├── urls.py
│ └── wsgi.py
├── main/ # Django app folder
│ ├── init.py
│ ├── admin.py
│ ├── apps.py
│ ├── urls.py
│ ├── views.py
│ └── migrations/
│ └── init.py
├── Dockerfile # Docker build instructions
├── requirements.txt # Python dependencies
├── manage.py # Django CLI runner
├── models.py # Custom models (optional)
├── .dockerignore # Ignore files during docker build
├── .gitignore # Ignore venv/pycache etc.
├── README.md # This file
└── .github/
└── workflows/
└── docker-acr-aci.yml # GitHub Actions workflow
</pre>

---

## ⚙️ How It Works (CI/CD Pipeline)

Whenever code is pushed to the `main` branch:

1. **GitHub Actions** is triggered.
2. The Docker image is built from your Django project.
3. The image is pushed to **Azure Container Registry (ACR)**.
4. The image is deployed to **Azure Container Instances (ACI)** with a public DNS.

---

## 🔐 GitHub Secrets Used

| Secret | Description |
|--------|-------------|
| `AZURE_CREDENTIALS` | JSON output from `az ad sp create-for-rbac --sdk-auth` |
| `ACR_NAME` | Name of your Azure Container Registry |
| `ACI_RG` | Resource group for your ACI |
| `ACI_NAME` | Container instance name |
| `ACI_DNS_NAME_LABEL` | DNS label for public access |
| `ACI_REGION` | Azure region (e.g., `centralindia`) |

---

## 🐳 Docker Commands (Manual Reference)

### Build Image
```bash
docker build -t dockerdjangoapp .

Run Locally
bash
Copy
Edit
docker run -p 8000:8000 dockerdjangoapp
Tag for ACR
bash
Copy
Edit
docker tag dockerdjangoapp <acr-name>.azurecr.io/dockerdjangoapp:latest
Push to ACR
bash
Copy
Edit
docker push <acr-name>.azurecr.io/dockerdjangoapp:latest
🔄 GitHub Actions Workflow Overview
Workflow file: .github/workflows/docker-acr-aci.yml

Triggers on:
    on:
  push:
    branches:
      - main

Actions:
Log in to Azure

Build Docker image

Push image to ACR

Deploy to ACI using Azure CLI

📝 License
This project is licensed under the MIT License.

🙋‍♂️ Author
Af1n
DevOps | Azure
GitHub: https://github.com/af1nzr

💬 Want to Contribute?
Feel free to fork, raise PRs, or star ⭐ this repo if it helped you.


---

Let me know if you'd like a **screenshot template**, **GitHub repo structure**, or help setting up the **GitHub Actions file** correctly. You're doing DevOps like a pro now 🚀
