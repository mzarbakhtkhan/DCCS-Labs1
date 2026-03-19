# DCCS-Labs1
LabNo 27. Password Policies_lab
Objectives
Understand the importance of password policies in enhancing system security.
Learn to view and modify current password policies on a Linux system.
Implement password expiry and complexity requirements.
Prerequisites
Basic understanding of Linux command-line operations.
Access to a Linux system with user privileges (sudo access is preferable).
Familiarity with Linux configuration files.
Lab Tasks
Check Current Password Policy using chage Command

chage -l ubuntu
Output:

Explanation:

chage: A command to change the user's password expiry information.
The -l option displays the current settings.
Modify Password Expiry Options with chage

Objective: Modify password expiry options to enhance security.

Example: To set a password to expire every 60 days and give a warning 7 days before expiry, use:

sudo chage -M 60 -W 7 [username]
-M 60: Sets maximum days before password expiry to 60.
-W 7: Sets the warning days before password expiry to 7.
Subtask: Verify changes

Re-run the chage -l [username] command to verify the updated settings.
Enforce Password Complexity in /etc/login.defs (Optional)

Objective: Strengthen password security by enforcing complexity requirements.

Step 1: Open the /etc/login.defs file in your preferred text editor.

sudo nano /etc/login.defs
Step 2: Add or modify the following lines to enforce complexity:

PASS_MIN_LEN 8  # Minimum number of characters in a password.
PASS_MAX_DAYS 90  # Maximum number of days a password may be used.
Explanation:

PASS_MIN_LEN: This sets the minimum length of the password.
PASS_MAX_DAYS: Sets the maximum period before a password must be changed.
Consideration: Password complexity can also be managed using PAM (Pluggable Authentication Modules) for more advanced requirements, such as enforcing character types.

Example configuration in /etc/pam.d/common-password:
password requisite pam_pwquality.so retry=3 minlen=8
Relevance:

These settings ensure passwords are not easily guessable or crackable, reducing the risk of unauthorized access.
Conclusion
Completing this lab provides foundational knowledge in managing password policies, a critical aspect of maintaining a secure Linux environment. You have learned how to check and modify password expiry using chage, and optionally, how to enforce password complexity. These configurations are essential for safeguarding user accounts and data against unauthorized access, ensuring compliance with security policies. Regularly revisiting and refining these settings can significantly enhance the security posture of your systems.
