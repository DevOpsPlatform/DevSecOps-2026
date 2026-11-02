# Azure Cloud Learning Journey: Day 3 - Virtual Machines (Compute)

Welcome to Day 3! On Day 1 we covered the basics, and on Day 2 we deployed a website. Today, we step into the most powerful concept in cloud computing: **Compute**. 

By the end of today, you will understand what a **Virtual Machine (VM)** is and how to spin up your very own Linux computer running inside a Microsoft data center.

---

## 1. What is a Virtual Machine (VM)?
Up until now, you've likely only used physical computers sitting on your desk or laptop. A **Virtual Machine (VM)** is a software-based emulation of a physical computer. 

* **The Cloud Advantage:** Instead of buying a new laptop just to run a server or test code, you can rent a high-powered Windows or Linux computer from Microsoft for pennies an hour (or use your student credits).
* **Remote Access:** Once it's running, you connect to it over the internet via a terminal (SSH) or remote desktop (RDP), as if it were sitting right next to you.

---

## 2. Step 1: Create a Linux Virtual Machine
Let's spin up a small, student-friendly Ubuntu Linux server.

1. Go to the [Azure Portal](https://portal.azure.com).
2. In the top search bar, type **Virtual machines** and click on it.
3. Click **+ Create** and select **Azure virtual machine**.
4. Fill out the **Basics** tab:
   * **Subscription:** Select *Azure for Students*.
   * **Resource Group:** Choose your existing `rg-myfirstproject` (or create a new one like `rg-day3-vm`).
   * **Virtual machine name:** Give it a name like `my-first-linux-vm`.
   * **Region:** Choose the same region you used before (e.g., *East US*).
   * **Image:** Select **Ubuntu Server** (choose a free-tier eligible version like Ubuntu LTS).
   * **Size:** Look for a small, budget-friendly size (e.g., `Standard_B1s` which is often covered or very cheap under student credits).
   * **Authentication type:** Choose **Password** (simpler for beginners) and set a secure username and password.

---

## 3. Step 2: Configure Network Ports (Inbound Ports)
By default, Azure blocks all outside internet traffic to your VM for security. To talk to it, you need to open a "door" (port).

1. Look for **Inbound port rules** in the same creation screen.
2. Under **Public inbound ports**, check **Allow selected ports**.
3. Select **SSH (22)**. This allows you to securely log into your Linux command line.

---

## 4. Step 3: Review and Create
1. Click **Review + create**. Azure will run a quick validation check.
2. Click **Create**. (It will take 1–3 minutes for Microsoft to provision your virtual computer).
3. Once the deployment is complete, click **Go to resource**.

---

## 5. Step 4: How to Connect to Your VM
Now that your cloud computer is running, let's log into it!

1. On your VM's overview page, look for the **Public IP address** (e.g., `20.51.x.x`). Copy this number.
2. If you are using Windows 10/11 or Mac/Linux, open your computer's local **Terminal** (or Command Prompt/PowerShell).
3. Type the following command (replace `your-username` and `your-public-ip` with your actual details):
   ```bash
   ssh your-username@your-public-ip
