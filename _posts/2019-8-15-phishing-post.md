---
categories: ['welcome']
published: false
---

Hello, there! This is Alex, I'm a cyber security analyst and this is my blog. I'm going to be rambling about technical things and exploring ideas here.

For my first post, I wanted to take a deep dive into the inner workings of a phishing attack.

In order to bypass email filters that many enterprises have deployed in 2019, attackers frequently will use sites like Dropbox, Google Drive, One Drive, or Sharepoint as the URL sent in an email. The reason this bypasses filter systems is that a lot of email security systems in use in 2019 scan URLs for malicious content, newly seen domains, and domains with known bad reputation. With URLs to trusted domains such as those for Google Drive or One Drive, the email system can be tricked because no malware is uncovered in the scan, and these companies are known and trusted. Another thing that makes phishing attacks so difficult to defend against is the fact that your end users many times may need to access Drop Box or Google Drive links to do their jobs. Additionally, these solutions, such as Box and One Drive, have Enterprise Subscriptions which many times are used by enterprises as their authorized file transfer platform. How is your end user supposed to know the different between a Box link sent from Betty in accounting vs a Box link sent from an attacker?

This post I will dive deep into the HTTP protocol to see how one of these attacks works.

