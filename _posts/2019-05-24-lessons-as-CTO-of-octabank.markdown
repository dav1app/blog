---
layout: post
title:  "Lessons I've learned as a CTO of blockchain based bank."
image: /assets/images/octabank-logo.png
---
Four months ago I left the role as a CTO and founder of Octabank, an investment bank that tries to use almost every safety and decentralization feature on its process.

It has some nice technical characteristics, like:

- It uses public and private key hashes as signatures, using the same elliptical curve - secp256k1 - and almost the same hash techniques - 2- layer SHA256 - as Bitcoin. Practically speaking, you log into your account using a JWT, encrypted through symmetric scheme (login and password) that you open locally inside your browser (like My Ether Wallet).

- You store your own private key and you are able to check your account for any types of wrongdoing. All the transactions are open and we were prototyping a block explorer soo anyone can audit it. We were planning to implement a button labeled 'Audit Everything' with an open JavaScript file that you can use to check the operations locally.

- It supports some P2P operation, and we are planning to create a serverless cash transaction using browsers WebRTC and WebCrypto API. If you are interested in how it works, I highly recommend you search for a cryptocurrency called Nimiq. We didn't know about this project, and by sheer coincidence, the code has some extraordinary similarities.

- We register every daily balance into the Bitcoin's Blockchain via Opentimestamps. We also provided a hash link between all the operations in a single day.
Strong terms for not selling clients data or using software that doesn't have explicit terms for that. We use ProtonMail as our main e-mail service, and everything has an MFA.

Everything from the logo to the contracts was carefully crafted from scratch. We were trying to reduce the friction between those who already invest in traditional assets, based on the principles of safety and transparency.

Pretty cool, right? Well, not everyone thought this way.

Here are the 9 lessons that I took for that project.

## 1. Very few people actually care about safety.
Yep. The topic is self-explanatory. And yes, many people wrote about this in the past. And yes, I am one of those tin foil hats guys.

And if I can give an advice for those paranoid developers and CTOs: Never go safety-first on anything. And most of the safety-first guys make some concessions on the financial world due to practicality - unless, of course, they are doing something wrong and don't wanna get caught.

Even roller coaster builders don't go safety first. They go fun first, but apply several safety measures to keep it fun. Remember that.

## 2. People on the financial market tends to remove responsibilities from technology.
When you are a victim of fraud on your traditional bank account, the bank runs a simple equation to see if your case worth changing the process inside the company: how often does this happen and how much it is damaging the institutional image? Most case scenario, they just refund you with no questions asked.

This is an example of how to remove responsibility from IT sectors using money. The financial executives don't mind if your system is broken unless the equation starts to sum up.

## 3. Clients feel happier if they see their money grows in smaller steps than if they get rich and loses it all.
Imagine two different scenarios:

*Client A has $10, then it grows to $11, and then to $12.*

*Client B has $10, then it grows to $1,232 and then back to $12.*

Who will think that you did a great job as a financial advisor?

On the second case, there is a high possibility that the client will ask you "why you did not stop when it hits $1,232?". And the answer has some technically and practically arguments that won't fit for the client.

And this could happen even if you don't have it written anywhere. Even some spikes on your graph can lead to this.

## 4. Meetings with financial professionals are basically worthless.
I got trapped into SO MANY useless meetings that I started wondering how much those financial guys earn hourly. I found out it is better to be rude and break an 30 min worthless meeting than wasting 2 hours of your day and become a mentally wasted zombie afterward.

Good investors know that you have the stuff to do and they won't stop you from doing it. And they are starting to know how important IT is for their ecosystem.

## 5. Clients seek human touch and your job is to take it away.
During the time we spent trying to sell our investment solution - called Galt, a multi cryptocurrency investment fund - we built a sales method that we can use every time we had the benefit of physical presence. It was called High Touch Method It was based on some powerful selling methods combined and we achieved some percentages as high as 88% of conversion over this method. I will probably write about it in the future.

The problem was simple: it did not scale. Unless we can manage to have a sales team, what we never had, this method takes a lot of time and money to work.
Some of the newer banks use the concept of "Digital Human Touch" - when you interact with something 'human' over a digital channel. We never had the opportunity to fully try it because we fail some steps earlier on the process. Probably this method works for companies that have a huge investment in other types of propaganda, what we never had.

## 6. Good marketing is the one that makes your bank looks like a different bank.
Now a little story.

When we started to plan what Octabank will be, we chose to be a bank that looks like a solid bank. The name octa is a reference to the carbon atoms that gets more stable with 8 electrons, and I personally crafted the logo that resembles a diamond.

This was the logo that I made.The problem of identity, however, started to rise when we position ourselves against the fun and young startup that rules the scenario today. We even chose to not call ourselves a startup, because we were focused on building a robust structure before scaling. Here in Brazil, the laws that preserve the oligopoly of financial markets are strong, and we don't wanna get in trouble before we had some money to afford some good lawyers.

And during the whole 2 years after creating it, we discovered that this solid and safe image was a problem, not a solution.

The person that buys things from startups is different than the one that buys things from banks. As said before, the average consumer of bank products doesn't care about how your algorithms are running, but they care about how much money you have to pay them back in case of fraud.

So what the fintechs are doing most of the time is either creating new markets for their bank (normally from younger and middle-class people - and I have a pleasure to meet some extraordinary projects during that period that fit on this category) or focusing on the very rich customer.

We didn't have the time to reach the young, nor the money to reach the rich.

## 7. Only worth to try if you have money and plan to start big.
This one sounds half obvious.

The obvious part is that…well, it is a bank. It needs money to sustain its operation.

The not so obvious part is that…well, it is a startup. It runs differently than a bank.

But think about it: when it was the last time that you see a bank+startup that runs with almost no money? Because regardless of how awesome your tech is, it doesn't mean that you won't need a lawyer. In fact, the biggest bank+startup that we have here in Brazil did it by having some serious lawyers.

So my advice is: find the investor before investing your time because it will take a lot. And forget about the smaller investors, because they can help you with knowledge, but they won't sustain your operation.

## 8. Bureaucracy is the most precious thing inside a bank.
If you ever entered a large bank and thought that at least half of that people could be fired and replaced by some OCR and Selenium, you are not alone. But there is something more upon those people that I didn't realize during the process.

They are the most precious thing that the bank has. And not only them, but also the stupid amount of signatures, papers, documents, and unnecessarily complex process that they do. Here in Brazil, you even need a license to work as one of those guys.

But hey, IT guys can get hired e without those.

And that is a reason for that: lobby. I bet the financial lobby is the strongest one on earth and they make sure that nobody gets in or out without the certifications, contracts, licenses, and signatures needed.

## 9. Everybody will try to use you for money laundry or tax evasion.

And the final one. If you mention Bitcoin 4 times in front of a mirror, a rich person shows up and asks about sending money to his friend in China without paying the huge amount of money (it can get high up to 30%) to the government.

---
Despite every painful lesson that I learned, the experience of trying to build a bank was simply one of the best things that I've ever had. Banks are everywhere, and soon we will experience a revolution in its way of work. 

I'm also extremely thankful for every single person that helped me through this journey. Some of them from the inside, like my partners an those who worked for us, some of them from the side, like the mentors and seed investors, and some from the outside, like my fiance, friends, and clients that made us go this far. 
