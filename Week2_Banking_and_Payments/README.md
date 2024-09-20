# Week 2

### Grading

Task #|Points|Description|
-----|:---:|----------|
[Task 1](#task-1-choose-a-or-b) | 1 | Browsers and Banking Security ***or*** Certifcates
[Task 2](#task-2-cards-and-payments) | 1 | Cards and Payments
[Task 3](#task-3-card-fraud) | 1 | Card Fraud
[Task 4](#task-4-wazuh) | ~~2~~ | SIEM Wazuh **check grading on this**

---

# Tasks

### Task 1: Choose A ***or*** B

#### Task 1A: Browsers and Banking Security

Online Banking is of the most lucrative targets for phishing and scams. How do our browsers protect us against them?

Look at the following snippets from a browsers address bar:

![Bank image 1](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/bank_1.png)

![Bank image 2](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/bank_2.png)

![Bank image 3](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/bank_3.png)

**Questions:**

- What does the "Not Secure" warning mean in the first picture and what risks does visiting sites with the warning pose?
- Why does the second site show up as "trusted" to the browser?
- What other ways are there to detect a phishing/scam site? 
    - Are there any tools available online?
- What is typosquatting and how does it relate to the pictures?
    - What is **UDRP** and how does it help with combatting typosquatting?
    - If you were to own the domain **ouspg.org** and would be running your crypto banking application at **bank.ouspg.org**, what domains could you monitor for warning signs of possible phishing attempts against your customers?


TASK 1A Answers: 
 - "Not Secure" means that the site is using HTTP and not HTTPS. The risk is that HTTP Doesn't encrypt client-to-server communications, which means that the data is sent in plain text. This means that the data stream can be intercepted and accessed by virtually anyone.

 - 2nd site is using HTTPS, so it shows up as secured. 

 - There are many ways, one is common sense. For example if you are suddenly redirected to a loginsite of, for example, facebook or microsoft, there should be some alarms going off in your head. Other is using Open source tools like URLScanner or Virustotal, which can give you information about the site and you can check its reputation if its negative or positive.

 - Typosquatting in this means making your phishing site in a way, that it relies on victims making typos. Like on danskebanks case, its fairly easy to typo danskebankk, just by doubleclicking k. 

 - UDRP(Uniform Domain-Name Dispute-Resolution Policy) Basically means that danskbank can get that fake url to shut down, since it is clearly malicious. Broadly you can have urls shut down that violate your trademark.

 - Some examples for monitoring: bank.ospg.org | bank.ouspg.com | bank.ouspg.fi | bankouspg.org |

#### Task 1B: Certificates

You have probably seen the following kind of warning when browsing the internet:

![Certificate image 1](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/certificate_1.png)

**Questions:**

- What are digital certificates used for?
    - Why are certificates important for online payments and banking security?
    - What other uses do certificates have?
- What kind of attacks does TLS mitigate and why is this important for online banking?
- How do browsers use certificates for ensuring browsing security?
    - What does the warning in the picture above mean?



ANSWERS:
- Digital certificates are yo verify the identity and integrity of websites or organizations on the internet, kinda like an ID.
    - They ensure the legitimacy and security of the online payments.
    - VPNs can use them to secure connections. 
- TLS mitigates MitM attacks by encrypting the communications between client and server, making it impossible for TA to intercept the data. With encryption it also mitigates evasedropping and data tampering, since it makes the data virtually untouchable during transit.
- Browsers use certificates by validating website identity and estabilishing secure connections.
- The picture can mean for example; Expired certificate, A not trusted certificate, mismatch between the domain and certification and revoked certificate. 





**Certificate Authorities**

Read the following entries on Certificate Authorities and Certificate Transparency and answer questions:

https://en.wikipedia.org/wiki/Certificate_authority
https://en.wikipedia.org/wiki/Certificate_Transparency
https://certificate.transparency.dev/howctworks/
https://www.ecb.europa.eu/pub/pubbydate/html/index.en.html

**Questions:**

- Why would it be bad if a trusted certificate authority was compromised?
- Why is certificate transparency important?


ANSWERS:

- If a trusted CA was compromised, it would be very dangerous because TA's could verify the authenticity of malicious websites on their own accord. 

- Transparency is important, because it addresses the issue of unauthorized or fraudulent certificates. It ensures that all issued certificates are logged in public, auditable logs. This helps people to indetifiy mis-issued of fraudulent cerificates quickly, which can mitigate a lot of harm. 

---

### Task 2: Cards and Payments

**Read the following:**

https://en.wikipedia.org/wiki/Payment_card
https://en.wikipedia.org/wiki/EMV
https://en.wikipedia.org/wiki/Multi-factor_authentication

**Questions: Payments**

- Why do modern payment cards use a chip and not a magnetic stripe?
- What are EMV Certificates and why are they relevant for payment protection?
- What attacks exist against payment cards?
    - Card-not-present?
    - Contactless payment?

**Questions: MFA**

- How is multi-factor authentication (MFA) used in banking?
- How does multi-factor authentication increase payment security?
- What MFA methods are you using in you daily life?
- What attacks exists against different forms of 2FA?
    - Time-based-one-time-password?
    - Text Message?

---

### Task 3: Card Fraud

One part of understanding payment card security is monitoring how the cards are used for frauds. The following articles are reports on card fraud by the European Central Bank and will give you an overview of how the fraud landscape has evolved between 2008-2019. Read through the articles and then answer the questions in the questions section.

**Read the following reports:**


https://www.ecb.europa.eu/pub/pdf/cardfraud/cardfraudreport201207en.pdf
https://www.ecb.europa.eu/pub/cardfraud/html/ecb.cardfraudreport202008~521edb602b.en.html
https://www.ecb.europa.eu/pub/cardfraud/html/ecb.cardfraudreport202110~cac4c418e8.en.html

**Supporting Resources:**

https://www.ecb.europa.eu/pub/pubbydate/html/index.en.html (Search: "Fraud")
https://www.ecb.europa.eu/paym/intro/mip-online/2018/html/1803_revisedpsd.en.html


**Questions:**

Write a summary (max 800 words) on "Evolution of card fraud" in which you answer at least the following questions:

- What kinds of card fraud exist?
    - How does card fraud type prevalence differ geographically?
- How has the fraud landscape changed between 2008-2019? Why?
    - What type of fraud has seen a notable increase during the last decade?
    - What technologies or regulations have had an impact on card fraud?
- How has the transaction landscape changed in the same period?
    - What kind of transactions have become increasingly popular?
    - What kind of transactions have had a high risk of being fraudulent?
        - Has this changed at all during 2008-2019?
- What effect has internet and e-commerce had on card fraud?
- Why is preventing data breaches important in preventing card fraud?
    - How does payment card tokenisation help in this?
-Anything interesting you found?

---

### Task 4: [Wazuh](https://www.wazuh.com)

---

**TODO** Update late august before course to recent version

---

Wazuh is an free and open source "unified XDR and SIEM protection for endpoints and cloud workloads." In this task we are going to focus more on the [SIEM](https://www.gartner.com/en/information-technology/glossary/security-information-and-event-management-siem) side of things. Take a look at their [website](https://wazuh.com/platform/siem/) and [github](https://github.com/wazuh/wazuh) to familiarize yourself with the capabilities and features Wazuh SIEM offers.

>**Note**
>Task has been written on Version 4.5, when going through documentation, you can switch to Version 4.5 from the top-left.

Start of with deploying the Wazuh [single-node on Docker](https://documentation.wazuh.com/current/deployment-options/docker/wazuh-container.html). You should go through the documentation to understand what's going on, but the following commands should be enough:

```console
git clone https://github.com/wazuh/wazuh-docker.git -b v4.5.1
cd wazuh-docker/single-node
docker-compose -f generate-indexer-certs.yml run --rm generator
docker-compose up -d
```

You can access the Wazuh (WUI)WebUI at your localhost, to do this go to [https://localhost](https://localhost). By default Wazuh uses self signed certs and you won't be directed to the site directly, instead click the advanced tab and find the button for "Accept the risk and continue". This will direct you to the site, and from then on you should be able to use it normally.

Next deploy atleast 2 agents with different operating systems, one on a virtual machine and one on your own OS for example. You can do this via the Wazuh WUI(Web User Interface), or when your OS is not available there, you can follow [this](https://documentation.wazuh.com/current/user-manual/agent-enrollment/index.html), the first method is recommended. The IP address is your internal ip address. This step should be straightforward.

Create a directory named integrity and add a file to it on both machines and enable FIM(File Integrity Monitoring) on both agents, you should also set the scan frequency at around 60 seconds, so you won't have to wait for the events. 

You are to trigger the FIM with atleast two different events. Then answer the questions below.

**What to return:**
1. What rule descriptions did you get?
2. What are the MITRE ATT&CK techniques(include ID) Wazuh reports for these events?
3. What is the reported MITRE techniques for deleting files or directories inside monitored directories?
4. Explain in your own words where, when and why should these systems be used.
5. Add a screenshot of your integrity monitoring events tab.

---

**TODO** *Add second part if deemed necessary*

---

### Feedback
Be sure to give feedback on these tasks. Do you feel these to be the kind of skills you might need or want?
