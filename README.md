# Pritunl VPN Setup on Ubuntu 22.04

This guide provides step-by-step instructions to install and set up Pritunl VPN along with MongoDB on Ubuntu 22.04.

---

## Prerequisites
Ensure your system is updated:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## Installation Steps

### 1. Add the Pritunl and MongoDB Repositories
Run the following commands to add the necessary repositories:

```bash
echo "deb [trusted=yes] https://repo.pritunl.com/stable/apt jammy main" | sudo tee /etc/apt/sources.list.d/pritunl.list
echo "deb [trusted=yes] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

### 2. Update Package List
Update the package list to include the newly added repositories:

```bash
sudo apt update
```

### 3. Install Pritunl and MongoDB
Install the required packages:

```bash
sudo apt install pritunl mongodb-org -y
```

### 4. Enable and Start Services
Enable and start the MongoDB and Pritunl services:

```bash
sudo systemctl enable mongod pritunl
sudo systemctl start mongod pritunl
```

### 5. Retrieve Setup Key
Generate the setup key required for the Pritunl setup:

```bash
sudo pritunl setup-key
```

Save the output securely as it will be needed for the initial setup.

### 6. Retrieve Default Admin Password
Get the default admin password:

```bash
sudo pritunl default-password
```

Save the default admin password. It will be used to log in to the web interface.

---

## Accessing the Pritunl Web Interface
1. Open a web browser and navigate to `https://<server-ip>`.
2. Enter the setup key and default admin credentials obtained earlier.
3. Follow the on-screen instructions to complete the setup.

---

## Notes
- Ensure port `443` is open on your firewall to allow HTTPS traffic.
- After logging in, you can change the admin password and configure your VPN server as needed.

For more details, refer to the [Pritunl Documentation](https://docs.pritunl.com/).
