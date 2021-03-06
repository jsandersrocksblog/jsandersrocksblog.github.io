If you are not using the Self-Serve option of Azure Active Directory premium, an email is sent to unblock the user account.&nbsp; Where does that email come from?&nbsp; I could not find it documented anywhere.

## Solution

With the help of my friend Florin Chiva in Azure AD support he helped me understand this.

In Azure Active Directory/O365 only Password admins, User management admins and Global admins can receive the password reset request notification emails.&nbsp; The priority for receiving the password reset request notification emails is:&nbsp;&nbsp; Password admins > User management admins > Global admins. 

For example:&nbsp; If you have all the three types of admins in your organization, then only the Password admins will receive the notification emails.&nbsp; If you only have User management admins and Global admins, then only the User management admins will receive the notification emails.&nbsp; If you only have Global admins, then the Global admins or alternate email address of the Global Admins will receive the notification emails. 

If you want to change the notification email, all you need to do is to create or use an existing account and assign the Password Administrator role or User Management role, set the email address that you need on this account, and the notifications will be redirected to this email instead of the Global Administrators (step by step procedure below). 

<a href="https://support.office.com/en-us/article/Assign-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504?ui=en-US&rs=en-US&ad=US&fromAR=1" target="_blank">Assign admin roles in Office 365</a> 

## Conclusion

Although simple, this is not easy to find documented.&nbsp; Again thanks to Florin for this information!

Drop us a note if you found this useful!