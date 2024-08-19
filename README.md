# practical-web-application-security-assessments-using-ZAP

### **Title**  
**Security Assessment Using OWASP ZAP on Google Gruyere: Vulnerabilities, Injection Attacks, and Authentication Testing**

### **Introduction**
The aim of this project was to perform security assessments on a target web application using the ZAP application. Our target web application was “Google Gruyere”.
This report outlines the security tests conducted on the Google Gruyere web application using OWASP ZAP. 
The goal was to identify security vulnerabilities, perform injection attacks, and evaluate the application’s authentication mechanisms to determine its resilience against common web application threats.
 

### **Methodology**

- **Tools Used**: 
  - OWASP ZAP: A security-testing tool used to identify and exploit vulnerabilities.
  - Browser: Firefox; Configured to route traffic through OWASP ZAP.
  - Google Gruyere: A vulnerable web application designed for educational purposes.
  - Testing Environment: Kali Linux VM.

## Setup

1. Install [OWASP ZAP](https://www.zaproxy.org/download/) on your machine.


- **Testing Process**: 
  The testing process involved identifying vulnerable input points across Google Gruyere using ZAP’s spidering and scanning tools. Injection attacks was performed on fields such as login forms, while authentication mechanisms were evaluated by attempting to bypass security controls using SQL Injection techniques.

### **Step-by-Step Walkthrough**

#### **Step 1: Setup OWASP ZAP and Google Gruyere**
- **Description**: 
  OWASP ZAP was configured to intercept traffic from the browser accessing Google Gruyere. The testing began by ensuring that all user input points were captured by ZAP for analysis, including the login form and search fields.
   
  

#### **Step 2: Identifying Vulnerabilities with Spidering**
- **Description**: 
  The Spider tool in ZAP was used to crawl through Google Gruyere’s pages to discover potential vulnerabilities. This allowed us to map out all user inputs, including forms and URL parameters that could be exploited.
  
  

#### **Step 3: Injection Attack Testing on Google Gruyere**
- **Description**: 
  Injection attacks was performed by manually submitting SQL Injection payloads into various input fields across the application. For example, in the search field and login form, payloads such as `' OR '1'='1` were used to manipulate queries and bypass authentication.
 
#### **Step 4: Active Scan for Vulnerabilities**
- **Description**: 
  An active scan was initiated to automate the process of injecting attack payloads into input fields. ZAP tested Google Gruyere for a variety of vulnerabilities, including injection flaws and weak authentication mechanisms.
  

#### **Step 5: Evaluating Authentication Mechanisms**
- **Description**: 
  The login mechanism of Google Gruyere was evaluated by testing whether SQL injection could be used to bypass authentication. Attempts were made to manipulate the login query with SQL payloads, and ZAP’s alerts helped confirm weaknesses in the application’s authentication process.
  
 

### **Conclusion and Recommendations**
The security tests conducted on Google Gruyere revealed serious vulnerabilities in both input validation and authentication mechanisms. The following steps are recommended to mitigate these risks:

1. **Strengthen Authentication**: Implement proper SQL query handling in the login mechanism, using parameterized queries to prevent injection attacks.
2. **Input Validation**: Ensure all user inputs are sanitized and validated before being processed by the application.
3. **Security Testing**: Conduct regular security assessments using tools like OWASP ZAP to identify and fix vulnerabilities.
 
