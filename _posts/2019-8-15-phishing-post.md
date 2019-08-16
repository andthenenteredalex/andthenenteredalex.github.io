---
categories: ['welcome']
published: true
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

![useful image1]({{ site.url }}/-phish-this-is-an-image-for-first-page.png)

Notice the URL in the window. It used to be the advice to users was to look for the lock. But this is based around a fundamental misunderstanding for how digital certificates are used. All the lock really means is that your connection is encrypted, and, if you don't see any red or errors, depending on yours browser, it means that the person or organization in control of the server on the other end has been certified to be who they say they are, as vouched for by a neutral 3rd party who your computer OS manufacturer also trusts. That's it. See the loophole? The certificate is certified by a neutral party to belong to the person who is using it on the other end. Do you trust that they're who they say they are? Of course they're who they say they are! Why would they not be? You can see mismatched errors, for example in using the certificate with a domain that is not listed on the certificate.

But the other thing to note, the initial certificate is given to Microsoft. Microsoft's name is on the certificate. Do you trust Microsoft? Well, here's where the email security system likely got confused. This is a platform that allows people to upload their own content. This page is likely clean from malware, and is hosted on a Microsoft Sharepoint server. So..... that means it's safe? Wrong!




After clicking the Review Document link for the PDF, I'm taken to this page. A rather generic, unflashy page. You will never see a webpage on the up and up which gives you so many sign-in options, especially not a generic 'other'.

![useful image2]({{ site.url }}/phish-image-page-second.png)

Again, notice the URL in the window. And the fact that we see the lock... That means that our connection is encrypted and that whoever is in control of wordpress1968310[.]home[.]pl is who they say they are, as vouched for by a neutral entity which your OS manuacturer trusts.

I'm going to click all three, "Login with Office 365", "Login with Outlook", and "Login with Other Mail" just because I'm curious and want to see where these go.

After clicking the Login with Office 365 link, a new window pops up, also with an encrypted connection. This seriously looks sketchy... And check out that URL in the address bar.
![useful image3]({{ site.url }}/images/page3-after-clicking-login-with-office-365.PNG)

Similar idea for the Outlook window. 
![useful image4]({{ site.url }}/images/page4-after-clicking-login-with-outlook.PNG)

The Other Email link, this one just cracks me up...
![useful image5]({{ site.url }}/images/page-5-after clicking-login-with-other-email.PNG)

Evidently, no matter what you use to receive email, it will work to authenticate to this server and allow you to access their imaginary document.




NOW comes the fun part. If you're anything like me, you're always asking the exciting questions. Like, how does this attacker know these credentials I enter are valid? Does this person make me retype them if I enter them incorrectly, or is everything accepted as valid?

In some more advanced attacks, I've seen links on these pages for Resetting Your Account Password actually take you to the real Microsoft page. I've also seen some which require you to re-enter a password if it doesn't think it matched, or re-type a username if they can't find an account that matches what you entered. In this case, neither is true. The Can't Access Your Account? and Sign In with a Single-Use Code are not text or links at all and are built into the image on that site.


The quest begins: Where do my username and password go if I enter them here? I think it's pretty obvious that they're being shipped off to some space controlled by the attacker and either emailed or logged in a file or in a database for later retrieval. There is an inherent delay in the way these attacks work. If you suspect you have falled for one, the best thing you can do is change your password immediately and check for any changes made to your account to make sure that you made them. For this reason, sites like Facebook are now very good about showing you the changes made to your account in a convenient log form so that you can know if someone else has been making changes to your account with your login credentials.



In this case, let's look to the session information from Fiddler. After I enteed a bogus username and password into the Outlook fake sign-in page we can see my credentials being sent to the site hosted at the initial wordpress domain. These username and password are passed beautifully in an HTTP post request and no errors were received. We know without a dubt that this is not a valid username and password pair as I just ran my hands across the keyboard to create random gibberish.

![useful image6]({{ site.url }}/images/page7-username-and-password-being-passed-in-POST-to-wordpress.PNG)


For the same POST request, in the RAW data you can see the credentials URL-encoded with the creative parameter name of 'email'.
![useful image7]({{ site.url }}/images/page8-username+password-POST-rquest.PNG)

This request redirected (you can see the HTTP 302 response code) to a landing page that had been taken down. I'm not sure what that would have, or might have been. I was dumped out at a generic hosting company's advertisement, which often means the domain is parked or available.

Some of the social engineering pages associated with this kind of attack are taken down quickly. It used to be that domains were registered and then immediately used in an attack, but many security tools are aware of this and are now incorporting protection for newly seen domains, or, domains that haven't been around very long. Therefore, attacks can register names far in advance of their pplanned attack, or purchase already registered domains so to not trigger these alarms.

In some more advanced social engineering attacks of this kind, I've seen a page that looked identical to a Microsoft or Dropbox login page in which, after passing in bogus credentials, you are taken to a legitimate Microsoft page and told that you entered invald credentials. At the time of this writing, in late summer of 2019, this is as deep as I've dug into these. But I now have a test Outlook email account I intend to compromise in any site that looks like it passes, or could potentially pass credentials to Microsoft for verification, and will uncover the depth these go. I will be digging into this in the future.

I have two theories: one, the simple one, is that the initial page takes the credentials you entered, assumes that they are valid, and just accepts that risk  that they may not be valid, and then drops you off at a Microsoft login page asking for you to re-enter your username and password. In this scenario, the user assumes that they must have mistyped it, and they proceed to carefully type it, and then when they are successfully logged into Microsoft, they don't recognize that they were phished at all and get distracted by the fact that they are now logged into Microft. This is typically Office 365 in these kinds of attacks against enterprises because of the wide use of O365.

The other theory, significantly more difficult to pull off, is that these advanced attacks send the credentials to Microsoft to test them and for validity, then successfully log you in so that the user never realizes what happened.  

I'm going to dig into this in the future and consider this simple attack to have been a sort of warm up exersise for the real study. You can expect this in the future, with my conclusions.

In the mean time, because of the state of security in 2019, set up MFA, preferably hardware keys, on all accounts. Just assume your passwords are all in the hands of baddies, along with all your credit cards and social security numbers.

Tootles.

Alex

