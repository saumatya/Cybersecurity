# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal Data Mapping and Minimization** |
| :----: | :--- |
| ⚠️ Personal information such as name, email, and age is collected during registration, but there's no clear documentation or centralized tracking of this data. | Have you identified all the personal data collected and processed in the system (e.g., name, email, age, username)? |
| ✅ The system only collects the essential personal data needed. | Have you ensured that only the necessary personal data is being collected (data minimization)? |
| ✅ Users under 15 years old are not allowed to register in the Booking System. | Is user age verified to ensure the person booking is over 15 years old? |

---

| **Result** | **User Registration and Management** |
| :----: | :--- |
| ⚠️ There is a checkbox for "I accept Terms of Service," but it becomes blank after clicking the terms. | Does the registration page include GDPR-compliant consent for processing personal data (e.g., acceptance of the privacy policy)? |
| ❌ No clear option for users to edit or delete their accounts. | Are users able to view, edit, and delete their personal data through their account settings? |
| ⚠️ The basic framework exists for deleting users, but the complete "right to be forgotten" functionality hasn't been fully implemented yet. | Is there a mechanism that allows administrators to delete users in compliance with the "right to be forgotten"? |
| ✅ Users under 15 cannot register or book. | Is the system preventing underage (under 15 years) registration and booking functionality? |

---

| **Result** | **Booking Visibility** |
| :----: | :--- |
| ✅ Only the resource name and booking period are visible. | Are bookings visible to non-logged-in users only at the resource level, without revealing any personal data? |
| ❌ Regular users can access other users' personal data (e.g., email), which is a violation of GDPR and requires proper access control and anonymization. | Are personal details such as names and emails kept confidential and not exposed to unauthorized users or publicly? |

---

| **Result** | **Access Control and Authorization** |
| :----: | :--- |
| ❌ Administrators lack the delete function. Users can modify other users’ bookings and resources. | Are permissions set so only administrators can add, modify, or delete resources and bookings? |
| ✅ The system clearly defines user roles. | Does the system use role-based access control (e.g., reserver vs. administrator)? |
| ⚠️ There is no audit log or safeguards regarding data use. | Are administrator permissions restricted to ensure they cannot misuse data for unauthorized purposes? |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| ❌ Administrators cannot delete data, and reservers can alter other users' bookings and resources. This is a major GDPR violation, as it allows unauthorized access to personal data and modifications to system resources. | Has Privacy by Default been implemented (e.g., collecting only necessary data)? |
| ✅ No critical errors were found. | Is the system properly logging activities without storing unnecessary personal data? |
| ⚠️ The registration and login forms only request username and password, supporting data minimization. However, passwords are transmitted via HTTP (not secure), and there are no protections against brute force attacks. | Are system components and forms designed with data protection in mind (e.g., secure login, minimal data collection)? |

---

| **Result** | **Data Security** |
| :----: | :--- |
| ❌ No CSRF token in forms. There is no mention of security protections like helmet.js. The MongoDB database lacks escaping and sanitizing. | Are protections against CSRF, XSS, and SQL injection implemented? |
| ✅ Passwords are securely hashed using bcryptjs during registration. | Are passwords securely hashed with a strong algorithm like bcrypt or Argon2? |
| ⚠️ There is no mention of backup or recovery procedures. | Are data backup and recovery processes compliant with GDPR standards? |
| ⚠️ Deployment details aren't fully specified, leaving it unclear whether GDPR-compliant data storage practices are followed. | Is personal data stored in data centers that comply with GDPR regulations (e.g., within the EU)? |

---

| **Result** | **Data Anonymization and Pseudonymization** |
| :----: | :--- |
| ❌ Personal data is stored without any anonymization or retention policy in place. | Is personal data anonymized when possible? |
| ❌ There is no evidence of pseudonymization techniques being used. | Are pseudonymization techniques employed to protect data while maintaining its usability? |

---

| **Result** | **Data Subject Rights** |
| :----: | :--- |
| ❌ There is no feature for users to download their personal data. | Can users request and download all personal data related to them (data access request)? |
| ❌ Users cannot delete their accounts, and this feature is not implemented. | Is there a way for users to request the deletion of their personal data? |
| ❌ There is no mechanism to withdraw consent. | Can users withdraw their consent for processing their personal data? |

---

| **Result** | **Documentation and Communication** |
| :----: | :--- |
| ⚠️ There is a link to the privacy policy, but it is blank. | Is a privacy policy available to users during registration and easily accessible? |
| ⚠️ It is unclear if this is included in external documentation. | Are administrators and developers provided with clear documentation on data protection practices and processing activities? |
| ❌ There is no documentation on how data breaches are handled. | Is there a documented procedure for responding to data breaches, including how to notify authorities and affected users? |

---

**Symbols used:**  
✅ Pass (can be clarified or added)  
❌ Fail (requires attention)  
⚠️ Attention needed (review and improve)
```
