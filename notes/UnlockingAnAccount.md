# Unlocking an Active Directory Account

## Overview
When a user account is locked due to incorrect login attempts, follow these steps to unlock it. *(Screenshots are available for reference)*

## Account Lockout Policy
- Accounts lock automatically based on your domain's **Account Lockout Policy**
- Check your policy settings before attempting to unlock accounts

## Steps to Unlock an Account

1. **Identify the locked account**
   - Verify the account is actually locked based on your domain's lockout policy

2. **Open Active Directory Users and Computers**
   - Launch the AD management tool

3. **Locate and select the account**
   - Find the locked account in the directory

4. **Access account properties**
   - Right-click on the account and select **Properties**
   - Navigate to the **Account** tab

5. **Unlock the account**
   - Click the **"Unlock account"** button
   - Click **Apply** and **OK**

6. **Notify the user**
   - The user can now attempt to log in again

## Tips
- Document when and why you unlocked an account for audit purposes
- Consider resetting the password if multiple failed attempts were made