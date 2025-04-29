<p align="center">
  <img src="https://media.giphy.com/media/LmNwrBhejkK9EFP504/giphy.gif" />
</p>

# Simulating and Analyzing PowerShell Commands for SOC Challenge

For my first task in the **60 Days of SOC Challenge**, I decided to simulate and analyze PowerShell commands, and learn how they can be monitored using the **Event Viewer**.  
Here’s a full breakdown of what I did, step-by-step, in a clear and beginner-friendly way.

---

## Step 1: Enabling PowerShell Logging in Local Group Policy

First, we need to **enable PowerShell logging**, because by default, Windows doesn't log every PowerShell command.

To do this:

- Press `Win + R`, type `gpedit.msc`, and hit **Enter** to open the **Local Group Policy Editor**.
- In the editor, navigate to:  
  **Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell**

At first, you’ll notice the PowerShell logging settings are **disabled**. Here's how it looks:  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/Screenshot_2025-04-28_13-30-46.png" alt="Disabled PowerShell Logging" />
</p>

Now, to enable logging:

- Double-click on **Turn on Module Logging** and **Turn on PowerShell Script Block Logging** one by one.
- Select **Enabled** and **Apply** the settings.

While enabling, the screen will look like this:  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/Screenshot_2025-04-28_13-31-51.png" alt="Enabling PowerShell Logging" />
</p>

Once both options are enabled, the settings will now look active:  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/Screenshot_2025-04-28_13-34-54.png" alt="Enabled PowerShell Logging" />
</p>

🔵 **Quick Note:**  
Without enabling logging, PowerShell activities will not appear in the Event Viewer — so this step is super important for analysis!

---

## Step 2: Running a Test PowerShell Command

Now that logging is enabled, let’s create an event that we can later catch.

Here’s what I did:

- Press `Win + X` and open **Windows PowerShell (Admin)**.
- Run this simple test command:

```powershell
Write-Output "Hi, I am Fazi, and I am writing this so it can be detected in Event Viewer"
```

Here’s a snapshot of me running the command:  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/Screenshot_2025-04-28_13-51-29.png" alt="PowerShell Command Execution" />
</p>

✅ **Goal:** Generate an activity that gets logged, so we can track it.

---

## Step 3: Checking Event Viewer for PowerShell Logs

Now it's time to check if our command got logged!

Here’s how to do it:

- Press `Win + R`, type `eventvwr.msc`, and hit **Enter** to open the **Event Viewer**.
- In the Event Viewer, navigate to:  
  **Applications and Services Logs > Microsoft > Windows > PowerShell > Operational**

Inside the **Operational** log, I found the event that captured my PowerShell command! 🎯

Here’s what it looked like:  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/Screenshot_2025-04-28_13-52-48.png" alt="Event Viewer Log Details" />
</p>

🔵 **Tip:**  
If you don't see any events, make sure:
- The correct logging policies were enabled.
- You ran the PowerShell command **after** enabling logging.

---

## Key Takeaways

- **PowerShell logging** needs to be manually enabled for better visibility and threat hunting.
- **Testing** your setup with a simple command is an easy way to validate that logging is working.
- **Event Viewer** provides detailed information about PowerShell activity, which is crucial for SOC analysts when investigating suspicious behavior.

This small project helped me build a solid foundation for understanding **PowerShell monitoring**, and how important it is for real-world security operations.  
Excited for the next challenges ahead! 🚀
`
