Crypto With Friends
============

Contents:

1. Introduction
2. With Friends!
3. What You Both Will Learn
4. Pre-requisites
5. Disclaimer, This Is Not Secure!
6. References
7. Exercises


## 1. Introduction ##

Crypto with friends is a lab based introduction to cryptography that is solely targeted at the beginner. There are a TON of resources out there for learning crypto, but the most common ones often come up pretty short in explaining what concept you're actually studying and how it fits into the bigger picture of cryptography. 

This series was inspired by my attempts at doing Matasano's CryptoPals challenges. While they are very informative, they are very dense. When attempting those challenges it can be hard to figure out what you're doing and why. For programmers of less experience, attempting them will likely cause some frustration as they butt their ahead against both entirely new crypto concepts and also new parts of their langauge they are encountering. No doubt that is a recipe for growth as a programmer, but why can't the growth come without the frustration? What if a series framed the crypto concepts more clearly, then budding crypto learner could move quicker, isn't that better? I think so, which is why I'm writing this. 

A second reason for this series is that most challenges online are for one person to do alone, which is strange because Crypto is inherently meant for two people (even if you're only encrypting your personal files, the second person is you in some months when you decrypt those files). Therefore the labs in this series will be for two people to do together.

## 2. With Friends! ##

This series is meant to be done with a friend. All exercises are for two people, and will be based around sending messages to each other. If you're on your own, you can be the second person, but the most fun will be had if you're sending messages to another computer and receiving messages from another computer. If you don't have someone to do these with, my advice is to find someone and ask them to join you! You'd be surprised how many people will be into the idea of learning beginner friendly Crypto!

## 3. What you Both Will Learn ##

You'll learn three basic concepts:

1. Encoding messages (which is not encryption)
2. Encrypting messages (which is encryption)
3. What hashing is.

## 4. Pre-requisites ##

To do these exercises you'll need to have Node.js installed on your computer as we'll do these exercises in Javascript. Node.js is a program you can download on to your computer from https://nodejs.org/en/ I recommend getting version 4.4.5 LTS or later. 

After that, you'll just need to be comfortable using your command line, and doing some Javascript via the Node command on it. If you need a command line introduction, I have one I recorded myself at: https://www.youtube.com/watch?v=KP0b0iaZiWk

## 5. Disclaimer, This Is Not Secure! ##

I have to point out here, that what you'll learn in these exercises is not meant for securing messages in real life! Everything you make here can be broken by trivially by most anyone! Use these to learn ony! I make no promise of any security with these exercises. I do make a promise of fun.

## 6. References ##

This series will reference a few sources, they are all freely available online.

    Crypto101 - https://www.crypto101.io/ 
    CryptoPals - https://cryptopals.com/

## 7. Exercises ##

No need for anymore fuss, let's start the exercises.

### 1. Making our first secret ###

##### Explanation #####

Let's say you have a message:

    THE SAFE CODE IS 4612

And you want to send this to your friend so only they can open your safe. It's a bad idea to send this message as it is, since anyone who can read English can read this message and open your safe. It's a much better idea to somehow make it readable to only your friend. Whatever process we use, we in general refer to it as 'Encryption', though techincally the term encryption refers to using specific algortihms to generate a secret message. 

A really common thing people do is just shuffle the characters a bit, so every time you see the letter 'a' replace it with a 'b', and every time you see a 'b' replace it with a 'c' and so on. For each number, add 1 to it.

So let's try this now:

##### Exercise #####

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

Wow! This secret message is way different, and guess what, it's not even encrypted, it's actually just encoded! Which is what we'll go over in the next challenge. But now an attacker can't guess which part is the safe code and which part is the text. They also are thrown for another loop, in that some characters are capitalized and some are lower case. An attacker who studies this messge will have a much harder time than the attacker above!*

*Ok you got me, any true crypto attacker won't have a hard time, but what if the attacker is new to crypto like you!

### 2. Encoding (which is not encrypting) ###

##### Discussion #####

The first step to understanding the world of crypto is understanding encoding. You can encode a message, send it to your friend and they can decode the message. Nothing about encoding is secret! Whoever gets a hold of your encoded message can decode it, provided they know what encoding was used.

Some encoding you're likely familiar with:

    - Morse Code, i.e. turning your message into dots and dashes
    - Binary, i.e. turning your message 0's and 1's

Other encoding you'll probably learn here:

    - ASCII
    - Base 64
    - Hex

When you encode a message using one of the encodings above, everyone else will know how to decode it. Why, because encoding is not meant to make messages secret, but make them easy to transmit. 

Think about Morse Code: When it it was invented, all they knew was that they could send electrical signals over a wire, so they had find a way to turn english letters into electrical signals, and once those electrical signals were sent to the other person, they needed to turn those signals back into letters. Hence Morse Code, a way of doing just that.

Morse Code turns

    Hi

Into

    .... ..

And

    SAFE CODE 4612

Into

    ... .- ..-. . / -.-. --- -.. . / ....- -.... .---- ..---

Morse Code is not a secret in any way whatsoever, it's completely public knowledge. If someone trying to listen in on you and your friend talking in Morse Code knows that you're using Morse Code, they can read your messages. The only security you have is that maybe the person reading it has no clue what Morse Code is and what it looks like, BUT, if they're reading my other series Stealing Secrets With Friends(TM), then they'll quickly find out!*

*This is not a real series I'm writing, sorry!

We're going to skip Morse Code and instead encode messages into Binary

But to do that, we have to understand how a computer really thinks about letters, and the answer is that a computer doesn't think in letters at all. Computers only know numbers deep down, specifically numbers of base 2 (binary) kind, e.g. 1001, 0110, etc.

So to really get a feel for crypto, you need a feel for turning your message of:

    hello

into:

    01101000 01100101 01101100 01101100 01101111

Let's take a look at this example, we have 'hello' and in binary it's '01101000 01100101 01101100 01101100 01101111'

Notice that 'hello' has 5 characters ('h', 'e', 'l', 'l', 'o'). And notice that our binary has 5 chunks. Furthermore, notice that the two chunks where the letter l's are the same, this means that each character of the word hello has the same 8-bit representation. 

A single bit is just a 0 or 1, so we if we put eight in a row, we have 8-bits, or 1-byte. So each letter is 1-byte.

So now we have to ask our second question, of, why does each letter correspond to exactly this binary number? As in, why does lowercase 'h' correspond to 01101000 and not 01101111 or 10101010 (can you tell I just typed 10 four times?). And why does 'h' always correspond to 01101000 and not 10101010 sometimes and 01010101 other times?

This was basically just a design decision made a long time (The 60's) ago when some engineers created ASCII, which is one of the earliest text to binary encodings. They decided that certain characters in the english language would corresond to a certain number, so if you look at an ASCII table entry for lowercase 'h':

Decimal value: 104 
Hex value    : 68  
Binary value : 01101000
Displays as  : h

Decimal 104 in binary is 01101000, and decimal 104 in hex is 68, these are all equivalent values

##### Exercises #####

So, finally, we get to exercise 1, let's convert the decimal value of 104 to Binary, and then convert it to hexidecimal (also just called 'hex'), and you should get a decimal value of 01101000 and a hex value of 68. Here's where a better book would go over how to convert from decimal (base 10) to binary (base 2) or hex (base 16), but this is not a better book, so Google it! (Google: 'method for converting to binary' and 'convert decimal to hex' to find some ways).

Then I want you to look up an ASCII table online (Google: 'ASCII table') and then find the decimal values for 'e', 'l' and 'o' and convert them to both binary and hex. One of you should convert 'h' and 'e' and the other person should convert 'l' and 'o', then combine them to get 'hello' in both binary and hex. Your answers should look like this:

    01101000 01100101 01101100 01101100 01101111
    68       65       6C       6C       6F   

Note, if you didn't get results like mine, check and make sure you weren't using the decimal values 

Time to Complete: 15 minutes

Now you've converted your plain-text message, via the ASCII encoding, into binary that your computer can natively understand. While this is definitely not encryption, it is encoding that might enough to prevent your dad or teacher from decoding your messages. But remember, they can just as easily Google 'Binary to text' and figure it out!

Let's do one more exercise, and this time I want you and your partner to pick a small phrase like:

    The car is red.

And one of you encode it in binary, and the other in hex, then I want you to switch and decode each other's message. So if you turned it into binary, you'll get some hex to decode back into English. Remember, capital letters have different ASCII values than lower case ones and puncutation like a period or exclamation point will have their own decimal values too. Also a ' ' has it's own encoding value too. 

    01010100 01101000 01100101 00100000 01100011 01100001 01110010 00100000 01101001 01110011 00100000 01110010 01100101 01100100 00101110 

    54 68 65 20 63 61 72 20 69 73 20 72 65 64 2e

Time to Complete: 20-30 minutes, if at 20 minutes you haven't gotten the full message decoded yet, no worries, you got the idea, feel free to stop!






    

