---
title: "Deterministic Password Generator"
description: "An alternative to password keepers such as 1Password."
date: "2014-05-04"
categories: 
    - "Cryptography"
    - "Passwords"
    - "Login"
    - "Project"
---

The heartbleed exploit made  me thing of my own way of keeping passwords which relies on 1Password. What was painfull with 1Password was having to regenerate every single password I have over again. That is a lot of work. The second problem because all my passwords are too hard to remember, I am screwed if I ever lose my encrypted database of passwords. So I also make paper copies, but they have to be made secure as well, so they can not be used directly in their paper form.

So this has left me with desirng a better solution. Deterministic password generators seem attractive, but there is no one program that works exactly how I want it to work. But there are a of neat ideas out there. 

### Enigma

[Enigma][enigma] looks pretty cool, but they had horrible customer support and have trouble with basic english. So not the kind of people I want to entrust with generating my passwords. Should I get a problem with their solution I need crystal clear communication. Also any solution should be open source, so you know exactly how the passwords are made and which makes it possible for you to roll your own solution should the company go belly up.

### Generator without Single Point of failure

John Metta has some interesting [ideas][singlepoint] on how to do this, but he doesn't have a product yet that he can vouch for. Anyway I'll keep my eye on his progress.

### Pronouncable Passwords
 
I kind of like pronounable passwords because they are far easier to remember. [PassKool][passkool] is a python script which uses this approach. However I have to check how safe this is. Making them pronounable of course reduces the search space for a hacker. [Passphrase FAQ][passphrasefaq] might be the place to learn how to do it.

# What I want in a Solution

1. Open source
2. Based on well established standards which are can be verified to be safe without being a crypto expert.
3. Should be very easy to recreate the code for generating the passwords, should the original program get lost.
4. On multiple platforms. I want the tool accessible from my phone, desktop, browser and command line.
5. Stores a list of sites or places I have made passwords for and settings used, so I don't forget that I actually have a password already for said site. I actually often forget that.
6. Should be easy to use. So I should mostly have to write a really easy password.
7. Paper backups. Should be easy to print out a piece of paper from the app containing key information. E.g. by using QR codes so it is really easy to restore a backup.
8. Should be secure, so that hackers can't easily break my master password once they get hold of one of my passwords.

(6) and (8) are obviously at odds with each other. My approach here would be to rely on certain assumptions:

* An attacker will most likely attack me online.
* He will not break into my house.

So my current idea for a solution relies on the following:

1. One simple password whic his what is mostly asked of me.
2. A hard to guess completely random component which I can not hope to remember. This will be stored on paper and will remain in memory for a limited amount of time. So occasionally it will need to be brought back using a QR code scanner e.g. Or if no camera is present with manual typing.
3. The on paper is encrypted with my simple password so that should somebody accidentally get hold of my paper backup then can't use it unless they know something about hacking.

The security of the individual points can be tweaked. The assumption here is that ultimately nothing is completely secure. It is all about making it really inconveient for the hacker. If you don't have important secrets or are not an important or wealthy person, we can assume that less security is needed, so that people may e.g. chose themselves whether the paper data should be encrypted and e.g. for how long the hard passwords should remain valid in memory. If your security needs are lower you could let the password stay indefintitly in memory. You could even store it permanently on disk.

There should be a lot of options to make sure the generator works for everyones needs.

[enigma]: https://itunes.apple.com/us/app/enigma/id527555438?mt=12
[singlepoint]: http://mettadore.com/ruby/secure-password-generator-as-manager-without-single-point-failure/
[passkool]: http://passkool.sourceforge.net
[passphrasefaq]: http://www.iusmentis.com/security/passphrasefaq/