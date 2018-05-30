# DatGudgudRepo
Week 8
# Project 8 - Pentesting Live Targets

Time spent: **7** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits and their corresponding sites are:
* Username Enumeration - **Red**
* Insecure Direct Object Reference (IDOR) - **Red**
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS) - **Green**
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation - **Green**

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: ATTEMPTED|FAILED
**SQLi** was deemed inneffective on the contact and login pages. These are the main two pages that have input fields. Also, attempting various SQLi in the URL also left no results. Some friends suggested using a tool like SQL map, however I do not have the skillset nor the time to take on learning another tool right now. That will be my next stepping stone in attempts if I ever get back to this task. 

![](https://i.giphy.com/media/A1SxC5HRrD3MY/giphy.gif)

Vulnerability #2: ATTEMPTED|FAILED
**CSRF** was a failed endeavor on these sites. Take the point of view of a non-logged-in user, I could not find any effective leaks on information with which to change headers or requests. From what I understand, many classmates used information they acquired while logged in, but I did not think that made sense. Is CSRF only effective if hackers have gained login access? If so, why bother the CSRF. All attempts to modify requests yielded no interesting results.

![](https://i.giphy.com/media/A1SxC5HRrD3MY/giphy.gif)


## Green

Vulnerability #1: Session Hijacking
![](https://raw.githubusercontent.com/trezzan/DatGudgudRepo/master/GreenHijack.gif)


Vulnerability #2: Stored XSS
![](https://raw.githubusercontent.com/trezzan/DatGudgudRepo/master/GreenXSS.gif)

## Red

Vulnerability #1: User Enumeration
![](https://raw.githubusercontent.com/trezzan/DatGudgudRepo/master/RedEnum.gif)

Vulnerability #2: IDOR
![](https://raw.githubusercontent.com/trezzan/DatGudgudRepo/master/RedIdor.gif)

## Concept Review

![] Which attacks were easiest to execute? Which were the most difficult?
* The user enumeration and IDOR were the easiest. SQLi has been a dead end mostly because I have exhausted places to inject. 

 ![] What is a good rule of thumb which would prevent accidentally username enumeration vulnerabilities like the one created here?
 * Users being enumerated in an ascending order is a bit simple. Also, making the userId an object and openly referencing it is a no-no.

![] Since you should be somewhat familiar with the CMS and how it was coded, can you think of another resource which could be made vulnerable to an Insecure Direct Object Reference? What code could be removed which would expose it? (Hint: It was also the answer to the first bonus objective to the Weekly Assignment for week 3.)
* I am not, yet. 

![] Many SQL Injections use OR as part of the injected code. (For example: ' OR 1=1 --'.) Could AND work just as well in place of OR? (For example: ' AND 1=1 --'.) Why or why not?
* No, the boolean for AND implies that both are true. Since we are purposefully ignoring the first part of the SQL statement, it should not be included. Using OR allows us to ignore it. 

![] A stored XSS attack requires patience because it could be stored for months before being triggered. Because of this, what important ingredient would an attacker most likely include in a stored XSS attack script?
* I am not sure. I am going to guess a trigger that makes the admin want to navigate to the stored XSS.

![]  Imagine that one of your classmates is an authorized admin for the site's CMS and you are not. How would you get them to visit the self-submitting, hidden form page you created in Objective #5 (CSRF)?
* Maybe sending an IM with a link?

![]  Compare session hijacking and session fixation. Which attack do you think is easier for an attacker to execute? Why? One of them is much easier to defend against than the other. Which one and why?
* Session Hijacking is easier to pull off because the SID can be grabbed passively via wireshark. Session fixation requires some sort of access to the victim's computer to plant. Encrypting traffic on all levels will make session hijacking very difficult if not impossible to achieve. 

## Notes

Describe any challenges encountered while doing the work

