Crypto With Friends
============

Contents:

1. Introduction
2. References
3. With Friends
4. Exercises


## 1. Introduction ##

Crypto with friends is a lab based introduction to cryptography that is solely targeted at the beginner. There are a TON of resources out there for learning crypto, but the most common ones often come up pretty short in explaining what concept you're actually studying and how it fits into the bigger picture of cryptography. This series was inspired by Matasano's CryptoPals challenges, and while they are very informative, they are very dense. While doing those challenges it can be hard to figure out what you're doing and why. For programmers of less experience, attempting them will likely cause some frustration as they butt their ahead against both entirely new crypto concepts and also new parts of their langauge they are encountering. No doubt that is a recipe for growth as a programmer, but, why can't the growth come without the frustration? What if a series framed the crypto concepts more clearly, then budding crypto learner could move quicker, isn't that better? A second reason for this series is that most challenges online are for one person to do alone, which is strange because Crypto is inherently meant for two people (even if you're only encrypting your personal files, the second person is you in some months when you decrypt those files). Therefore the labs in this series will be for two people to do together.

## 2. References ##

This series will reference a few sources, they are all freely available online.

    Crypto101 - https://www.crypto101.io/ 
    CryptoPals - https://cryptopals.com/

## 3. With Friends ##

This series is meant to be done with a friend. All exercises are for two people, and will be based around sending messages to each other. If you're on your own, you can be the second person, but the most fun will be had if you're sending messages to another computer and receiving messages from another computer. If you don't have someone to do these with, my advice is to find someone and ask them to join you! You'd be surprised how many people will be into the idea of learning beginner friendly Crypto!

## 4. Exercises ##

No need for anymore fuss, let's start the exercises.

### 1. Making our first secret ###

#### Explanation ####

Let's say you have a message:

    THE SAFE CODE IS 4612

And you want to send this to your friend so only they can open your safe. It's a bad idea to send this message as it is, since anyone who can read English can read this message and open your safe. It's a much better idea to somehow make it readable to only your friend. Whatever process we use, we in general refer to it as 'Encryption', though techincally the term encryption refers to using specific algortihms to generate a secret message. 

A really common thing people do is just shuffle the characters a bit, so every time you see the letter 'a' replace it with a 'b', and every time you see a 'b' replace it with a 'c' and so on. For each number, add 1 to it.

So let's try this now:

#### Exercise ####

Both of you shift the message one letter over, so the message above looks like this:

    UIF TBGF DPEF JT 5723

Don't just read this, get pen and paper and do it by hand! Then share this with your friend, and 'decrypt' the message by moving each letter one back, and getting back the original text of: 

    THE SAFE CODE IS 4612

Now that you've done this with my message, I want you to write your own secret messages for each other, and this time, shift each letter by 2 over, so 'A' becomes 'C', 'B' becomes 'D', and at the end of the alphabet, 'Y' becomes 'A' and 'Z' becomes 'B'.

Time to Complete: 10 minutes

Cool, you've just encrypted your first message! But the downside is, it's not a strong encryption, all someone has to do is know how many characters back to shift your secret message, and they'll have your safe code!

But now let's think about something else. Let's say someone Googles the model of your safe, and they find out that this model of safe takes only a 4-digit code. All they want is your safe code, not the message itself, so if they see this message:

    UIF TBGF DPEF JT 5723

Then if they're smart, they'll realize they don't even need to bother decrypting most of the message, all they should decrypt is:

    TBGF DPEF 5723

And after a few tries, they find that the message is:

    SAFE CODE 4612

And that's really all they need! 

So this is our first big lesson in Crypto: Attackers are clever, and it's not enough to just change the characters of your message, but also change how long your secret message is. What if instead you could change your message of:

    THE SAFE CODE IS 4612

To this:

    VEhFIFNBRkUgQ09ERSBJUyA0NjEy

Wow! This secret message is much more secure than above, and guess what, it's not even encrypted, it's actually just encoded! Which is what we'll go over in the next challenge. But now an attacker can't guess which part is the safe code and which part is the text. They also are thrown for another loop, in that some characters are capitalized and some are lower case. An attacker who studies this messge will have a much harder time than the attacker above!*

*Ok you got me, any true crypto attacker won't have a hard time, but what if the attacker is new to crypto like you!


