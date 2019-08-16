---
categories: ['welcome']
published: false
---

Hello, there! This is Alex, I'm a cyber security analyst and this is my blog. I'm going to be rambling about technical things and exploring ideas here.

# Introduction
For my first post, I wanted to take a deep dive into the inner workings of a phishing attack.

In order to bypass email filters that many enterprises have deployed in 2019, attackers frequently will use sites like Dropbox, Google Drive, One Drive, or Sharepoint as the URL sent in an email. The reason this bypasses filter systems is that a lot of email security systems in use in 2019 scan URLs for malicious content, newly seen domains, and domains with known bad reputation. With URLs to trusted domains such as those for Google Drive or One Drive, the email system can be tricked because no malware is uncovered in the scan, and these companies are known and trusted. Another thing that makes phishing attacks so difficult to defend against is the fact that your end users many times may need to access Drop Box or Google Drive links to do their jobs. Additionally, these solutions, such as Box and One Drive, have Enterprise Subscriptions which many times are used by enterprises as their authorized file transfer platform. How is your end user supposed to know the different between a Box link sent from Betty in accounting vs a Box link sent from an attacker?

In this post I will dive deep into the HTTP protocol to see how one of these attacks works.

# The attack

ATTENTION: Be careful if you choose to open untrusted URLs, I am opening this in a safe lab and tested this out in a sandbox to see which processes spawned and what was dropped. I am not responsible if anyone chooses to follow along or open experiment with their own risky URLs.

I opened a phishing URL I found and have a tool called Fiddler running in the background which is capturing the protocol information. 

After clicking the link, here is the landing page. It is likely that this was sent out in emails to enterprises with a message along the lines of "Here is the document you asked for. Kindly respond with feedback at your earliest convenience." There is generally a sense of urgency, and it is common to see misspellings in emails as well. 

![useful image]({{ site.url }}/images/Page1.png)

Notice the URL in the window. It used to be the advice to users was to look for the lock. But this is based around a fundamental misunderstanding for how digital certificates are used. All the lock really means is that your connection is encrypted, and, if you don't see any red or errors, depending on yours browser, it means that the person or organization in control of the server on the other end has been certified to be who they say they are, as vouched for by a neutral 3rd party who your computer OS manufacturer also trusts. That's it. See the loophole? The certificate is certified by a neutral party to belong to the person who is using it on the other end. Do you trust that they're who they say they are? Of course they're who they say they are! Why would they not be? You can see mismatched errors, for example in using the certificate with a domain that is not listed on the certificate.

But the other thing to note, the initial certificate is given to Microsoft. Microsoft's name is on the certificate. Do you trust Microsoft? Well, here's where the email security system likely got confused. This is a platform that allows people to upload their own content. This page is likely clean from malware, and is hosted on a Microsoft Sharepoint server. So..... that means it's safe? Wrong!




After clicking the Review Document link for the PDF, I'm taken to this page. A rather generic, unflashy page. You will never see a webpage on the up and up which gives you so many sign-in options, especially not a generic 'other'.

![useful image]({{ site.url }}/images/Page2.png)

Again, notice the URL in the window. And the fact that we see the lock... That means that our connection is encrypted and that whoever is in control of wordpress1968310[.]home[.]pl is who they say they are, as vouched for by a neutral entity which your OS manuacturer trusts.

I'm going to click all three, "Login with Office 365", "Login with Outlook", and "Login with Other Mail" just because I'm curious and want to see where these go.

After clicking the Login with Office 365 link, a new window pops up, also with an encrypted connection. This seriously looks sketchy... And check out that URL in the address bar.
![useful image]({{ site.url }}/images/page3-after-clicking-login-with-office-365)

Similar idea for the Outlook window. 
![useful image]({{ site.url }}/images/page4-after-clicking-login-with-outlook)

The Other Email link, this one just cracks me up...
![useful image]({{ site.url }}/images/page-5-after clicking-login-with-other-email)

Evidently, no matter what you use to receive email, it will work to authenticate to this server and allow you to access their imaginary document.




NOW comes the fun part. If you're anything like me, you're always asking the exciting questions. Like, how does this attacker know these credentials I enter are valid? Does this person make me retype them if I enter them incorrectly, or is everything accepted as valid?

In some more advanced attacks, I've seen links on these pages for Resetting Your Account Password actually take you to the real Microsoft page. I've also seen some which require you to re-enter a password if it doesn't think it matched, or re-type a username if they can't find an account that matches what you entered. In this case, neither is true. The Can't Access Your Account? and Sign In with a Single-Use Code are not text or links at all and are built into the image on that site.


The quest begins: Where do my username and password go if I enter them here? I think it's pretty obvious that they're being shipped off to some space controlled by the attacker and either emailed or logged in a file or in a database for later retrieval. There is an inherent delay in the way these attacks work. If you suspect you have falled for one, the best thing you can do is change your password immediately and check for any changes made to your account to make sure that you made them. For this reason, sites like Facebook are now very good about showing you the changes made to your account in a convenient log form so that you can know if someone else has been making changes to your account with your login credentials.



In this case, let's look to the session information from Fiddler. 







I have two theories: one, the simple one, is to take the credentials you entered, assume that they are valid, and just accept that risk if they are not, and then drop you off at a Microsoft login page asking you to re-enter your username and password. In this scenario, the user assumes that they must have mistyped it, and they proceed to carefully type it, and then when they are successfully logged into Microsoft, they don't recognize that they were phished at all and get distracted by the fact that they are now logged into Microft, typically Office 365 in these kinds of attacks against enterprises because of the wide adoption of O365.

The other theory, significantly more difficult to pull off, is that these advanced attacks patch the credentials into Microsoft to test them and then successfully log you in so that you never realized what happened. (This would not work if MFA was enabled on the account, which, at the time of this writing is optional on outlook email accounts.)

This also would not work depending on the way the Referrer headers are accepted on Microsoft login pagesMy next post will attempt to determine what exactly happens in a more sophisticated social engineering attack. 

