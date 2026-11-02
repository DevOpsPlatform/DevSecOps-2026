# Azure Cloud Learning Journey: Day 2 - Your First Hands-On Lab

Welcome to Day 2! Now that you understand what cloud computing is and what student perks you have, it is time to log into the **Azure Portal** and get your hands dirty. 

By the end of today, you will know how to navigate the portal, create your very first project container, and deploy a live web page.

---

## 1. Logging In & Understanding the Dashboard
1. Go to [portal.azure.com](https://portal.azure.com) and log in with your student account.
2. Take a look around the home screen:
   * **The Search Bar (Top):** This is your best friend. Instead of clicking through menus, you can just type what you want (e.g., "Virtual Machines" or "Storage") to find it instantly.
   * **Resource Groups:** Your home base for organizing projects.

---

## 2. Step 1: Create Your First "Resource Group"
Before building anything in Azure, you must create a Resource Group to hold it. Think of this as creating a folder on your computer desktop before saving a project inside it.

1. In the top search bar, type **Resource groups** and click on it.
2. Click the **+ Create** button.
3. Fill out the basic details:
   * **Subscription:** Select *Azure for Students*.
   * **Resource group name:** Give it a clean, simple name like `rg-myfirstproject`.
   * **Region:** Choose a region closest to where you live (e.g., *East US* or *Central India*).
4. Click **Review + create**, then click **Create**. 

---

## 3. Step 2: Deploy a Free Static Web App
Let's build a tiny "Hello World" website so you can see something live on the internet! We will use **Azure Static Web Apps**, which has a great free tier for students.

1. In the top search bar, type **Static Web Apps** and click on it.
2. Click **+ Create**.
3. Fill out the basics:
   * **Resource Group:** Select the `rg-myfirstproject` you just created.
   * **Name:** Give your app a unique name (e.g., `my-student-portfolio`).
   * **Hosting plan:** Choose **Free**.
   * **Deployment details:** For now, you can select *Other* or connect a simple GitHub repository if you already use GitHub.
4. Complete the wizard and click **Review + create** -> **Create**.
5. Once deployment is complete, go to the resource, find your **URL**, and click it to see your live site on the web!

---

## 4. Best Practice Habit: Cleaning Up
Because you are working with student credits (or free tiers), practicing clean habits early saves you headaches.

* If you test something out and no longer need it, delete the **Resource Group** (`rg-myfirstproject`). 
* Deleting a resource group automatically deletes **everything** inside it, ensuring you don't leave hidden resources running in the background.

---

## Preview for Day 3
Tomorrow, we will step into **Compute** and look at how to spin up a full Linux Virtual Machine (VM) in the cloud!
