# practical-web-application-security-assessments-using-ZAP
 
**Security Assessment Using OWASP ZAP on Google Gruyere: Vulnerabilities, Injection Attacks, and Authentication Testing**

### **Introduction**
The aim of this project was to perform security assessments on a target web application using the ZAP application. Our target web application was “Google Gruyere”.
This report outlines the security tests conducted on the Google Gruyere web application using OWASP ZAP. 
The goal was to identify security vulnerabilities, perform injection attacks, and evaluate the application’s authentication mechanisms to determine its resilience against common web application threats.
 
![1](https://github.com/user-attachments/assets/3083f46a-0e66-4105-9f6e-544e1a5bf667)

### **Methodology**

- **Tools Used**: 
  - OWASP ZAP: A security-testing tool used to identify and exploit vulnerabilities.
  - Browser: Firefox; Configured to route traffic through OWASP ZAP.
  - Google Gruyere: A vulnerable web application designed for educational purposes.
  - Testing Environment: Kali Linux VM.

- **Testing Process**: 
  The testing process involved identifying vulnerable input points across Google Gruyere using ZAP’s spidering and scanning tools.
  Injection attacks was performed on fields such as login forms, while authentication mechanisms were evaluated by attempting to bypass security controls using SQL Injection techniques.

### **Step-by-Step Walkthrough**

#### **Step 1: Setup OWASP ZAP and Google Gruyere**
- **Description**: 
  OWASP ZAP was configured to intercept traffic from the browser accessing Google Gruyere.

The testing began by ensuring that all user input points were captured by ZAP for analysis, including the login form and search fields.

-Launch ZAP on your Kali Linux VM by running the command "zaproxy &" on your terminal

-Access Google Gruyere by opening your browser and navigating to: https://google-gruyere.appspot.com/

-Ensure your browser traffic is routed through ZAP’s proxy (usually set to 127.0.0.1:8080).

-In ZAP, ensure Google Gruyere is listed in the Sites tree after you’ve browsed the application.

   
  ![2](https://github.com/user-attachments/assets/5459de6c-bcf2-44a8-af24-9519553bdef9)

![3](https://github.com/user-attachments/assets/30f3e4b9-6ad7-461d-8d58-f34184fa170a)

![4](https://github.com/user-attachments/assets/9e036215-58b5-4baa-899e-108aa8d48268)

#### **Step 2: Identifying Vulnerabilities with Spidering**
2. Crawling Google Gruyere (Spidering)
- **Description**: 
  The Spider tool in ZAP was used to crawl through Google Gruyere’s pages to discover potential vulnerabilities.
  This allowed us to map out all user inputs, including forms and URL parameters that could be exploited.

   -Right-click on the Google Gruyere URL in the Sites tree and select Attack > Spider.

  -Configure the spider settings (optional) and click Start Scan.

   -ZAP will crawl the site and populate the Sites tree with discovered pages and inputs.

  -As the scan progresses, you can monitor the Alerts tab in ZAP.

-Vulnerabilities will be flagged here with severity levels (e.g., High, Medium, Low).

-For each alert, you can click on it to view more details, including the vulnerability type (e.g., SQL Injection), affected parameters, and suggestions for remediation.

  ![5](https://github.com/user-attachments/assets/09282475-ec40-4977-bbe6-b83ce583b265)

![6](https://github.com/user-attachments/assets/56ef3e9f-4523-49a3-9cc2-b8d22a744841)

#### **Step 3: Injection Attack Testing on Google Gruyere**
- **Description**:
- An active scan was conducted to automatically inject SQL payloads into all discovered input fields and parameters.
- The scan revealed potential SQL injection vulnerabilities, which were further investigated manually.
  Injection attacks was performed by manually submitting SQL Injection payloads into various input fields across the application.
  For example, in the search field and login form, payloads such as `' OR '1'='1` were used to manipulate queries and bypass authentication.

![7](https://github.com/user-attachments/assets/3fdeca20-2762-4da2-a050-b3226f8da86c)

#### **Step 4: Active Scan for Vulnerabilities**
- **Description**: 
  An active scan was initiated to automate the process of injecting attack payloads into input fields. ZAP tested Google Gruyere for a variety of vulnerabilities, including injection flaws and weak authentication mechanisms.

  ![8](https://github.com/user-attachments/assets/ee66ba5f-4abd-423b-a9cf-95b1dfa7fffc)

![9](https://github.com/user-attachments/assets/12410624-3e6b-49ee-8b12-fe3cb9530537)


#### **Step 5: Evaluating Authentication Mechanisms**
- **Description**: 
  The login mechanism of Google Gruyere was evaluated by testing whether SQL injection could be used to bypass authentication. Attempts were made to manipulate the login query with SQL payloads, and ZAP’s alerts helped confirm weaknesses in the application’s authentication process.
  
 ![6](https://github.com/user-attachments/assets/e8a6fdef-4792-4966-afa4-e42e2b02c3d3)


### **Conclusion and Recommendations**
The security tests conducted on Google Gruyere revealed serious vulnerabilities in both input validation and authentication mechanisms. The following steps are recommended to mitigate these risks:

1. **Strengthen Authentication**: Implement proper SQL query handling in the login mechanism, using parameterized queries to prevent injection attacks.
2. **Input Validation**: Ensure all user inputs are sanitized and validated before being processed by the application.
3. **Security Testing**: Conduct regular security assessments using tools like OWASP ZAP to identify and fix vulnerabilities.
 
