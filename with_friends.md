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

As far as Javascript knowlege goes you should feel comfortable invoking functions, passing arguments to functions and using the 'new' operator in Javascript. You should also feel ok with some concepts of working with arrays.

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

And you want to send this to your friend so only they can open your safe. It's a bad idea to send this message as it is, since anyone who can read English can read this message and open your safe. It's a much better idea to somehow make it readable to only your friend. Whatever process we use, we in general refer to it as 'Encryption', though techincally the term encryption refers to using specific algortihms to generate a secret message with a key. 

Before encryption, A really common thing people did is just shuffle the characters a bit, so every time you see the letter 'a' replace it with a 'b', and every time you see a 'b' replace it with a 'c' and so on. For each number, add 1 to it.

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

Then if they're smart, they'll realize they don't even need to bother decrypting most of the message, all they should decrypt is the 4-letter blocks:

    TBGF DPEF 5723

And after a few tries, they find that the message is:

    SAFE CODE 4612

And that's really all they need! 

So this is our first big lesson in Crypto: Attackers are clever, and it's not enough to just change the characters of your message, but also change how long your secret message is and how it is presented. 

What if instead, you could change your message of:

    THE SAFE CODE IS 4612

To this:

    hQIMA1WMoy9b0Iy8AQ//cQFpUNNuombyP5dKSoZd7jXdzvV6usfmI95amqmWPEOW
    tATRVrN9qF7N4wxLniqgmQ4eSYfyzs05rWUCmyoioxQsjTp1jzfn9KiuMfXpX0i1
    n3QEz6cNj1s+dvIr5U3ngi+/CRWX8ZPKa/7Wq7+z0Ajhmf7iQqssfDCBcu99nqYT
    7cZUKjX6i/maEuMfTuMyjI9503zCDaYeo6AdiNy1lvgMYAKBZJ67UaTpMHSp9ME/
    3olrtIIJo4Oe/HGizA3ZqCvt7dmqsRAfzf7Uik6AgEhnjS2YdGSl5YhUwS0M+vCT
    rBsqy12CMaqR0lq4+sylPtWp40uGXP476zL4fkMipSdgypfNo5dyIFFUZsUBSBXF
    fJGB8Jp4r6XNNWXkBS70Nd3fSnCcfte3yzCTflb1WquVGasCvEgeoYJrd6s49SAJ
    bt1vxhgZqX6AoWOLlhWgJhLjfVf+WApCTtK7+Zb3uVE8sOyMb3tS3KHK+/48PC/O
    R5ao3NgekL1j//0diXMsCj9ySEy/8tcIDo0oYKXss1jDdHn1Ewwl8PbIjiUC3o/0
    AksuwmOrGvFECxml75IodIsHy+xcY2kS7KnDhrcSksB5FvVkY8XTlksR6r25RRCe
    aC+zmA8udDMhX5Vzjo+ujuW1zsmKUV1Zx3RQcxvbihwN2AC07dEO+CQWeGfyQsLS
    UAE1L8DDImFl1e8ZVeBV7fFAfb+YxEjW/BaI9oSxjwvKEZ+767kNFN9NU3D6gYdf
    4VBCPXXk4nLKB1zEbesF+Ga7HIquWGcMjgmIT4sMVThs
    =CJ4X

Wow! This secret message is way different. This is not like our first attempt where we just shifted the message by one character. This messag is encrypted, and only the intended recipient can decrypt it. Also notice that this message is gigantic, and reads as gibberish, and gives a person reading it no idea what the intent of the original message was. This message is now really a secret. 

### 2. Encoding (which is not encrypting) ###

##### Discussion #####

The first step to understanding the world of crypto is understanding encoding. You can encode a message, send it to your friend and they can decode the message. Nothing about encoding is secret! Whoever gets a hold of your encoded message can decode it, provided they know what encoding was used.

For example, our message above of

    THE SAFE CODE IS 4612

Can be base64 encoded to

    VEhFIFNBRkUgQ09ERSBJUyA0NjEy

You might be tempted to think encoding is encryption since this gibberish looks a lot like the big block of gibberish above, but it is not! I repeat, encoding is public, not secret, anyone who recognizes that this message is written in base64 can try (and will succeed in) decoding it and see the original plain text. 

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

Morse Code is not a secret in any way whatsoever, it's completely public knowledge. If someone trying to listen in on you and your friend talking in Morse Code knows that you're using Morse Code, they can read your messages. The only security you have is that maybe the person reading it has no clue what Morse Code is and what it looks like, but if they're reading my other series Stealing Secrets With Friends(TM), then they'll quickly find out!*

*This is not a real series I'm writing, sorry!

We're going to skip Morse Code and instead encode messages into Binary

But to do that, we have to understand how a computer really thinks about letters, and the answer is that a computer doesn't think in letters at all. Computers only know numbers deep down, specifically numbers of base 2 (binary) kind, e.g. 1001, 0110, etc.

So to really get a feel for crypto, you need a feel for turning your message of:

    hello

into:

    01101000 01100101 01101100 01101100 01101111

Let's take a look at this example, we have 'hello' and in binary it's '01101000 01100101 01101100 01101100 01101111'

Notice that 'hello' has 5 characters ('h', 'e', 'l', 'l', 'o'). And notice that our binary has 5 chunks. Furthermore, notice that the two chunks where the letter l's are the same, this means that each english letter has it's own uniqute 8-bit representation.

A single bit is just a 0 or 1, so we if we put eight in a row, we have 8-bits, or 1-byte. So each letter is 1-byte.

So now we have to ask our second question, of, why does each letter correspond to exactly this binary number? As in, why does lowercase 'h' correspond to 01101000 and not 01101111 or 10101010 (can you tell I just typed 10 four times?). And why does 'h' always correspond to 01101000 and not 10101010 sometimes and 01010101 other times?

This was basically just a design decision made a long time (The 60's) ago when some engineers created ASCII, which is one of the earliest text to binary encodings. They decided that certain characters in the english language would corresond to a certain number, so if you look at an ASCII table entry for lowercase 'h':

| Decimal | Hex | Binary   | Displays as |
|---------|-----|----------|-------------|
| 104     | 68  | 01101000 | 'h'         |

##### Exercises #####

So, finally, we get to exercise 1, let's convert the decimal value of 104 to Binary, and then convert it to hexidecimal (also just called 'hex'), and you should get a decimal value of 01101000 and a hex value of 68. Here's where a better book would go over how to convert from decimal (base 10) to binary (base 2) or hex (base 16), but this is not a better book, so Google it! (Google: 'method for converting to binary' and 'convert decimal to hex' to find some ways).

Then I want you to look up an ASCII table online (Google: 'ASCII table') and find the decimal values for 'e', 'l' and 'o' and convert them to both binary and hex. One of you should convert 'h' and 'e' and the other person should convert 'l' and 'o', then combine them to get 'hello' in both binary and hex. Your answers should look like this:

    01101000 01100101 01101100 01101100 01101111
    68       65       6C       6C       6F   

Note, if you didn't get results like mine, check and make sure you weren't using the decimal values. Also remember that lower case and uppercase letters have different values.

Time to Complete: 15 minutes

Now you've converted your plain-text message, via the ASCII encoding, into binary that your computer can natively understand. While this is definitely not encryption, it is encoding that might enough to prevent your dad or teacher from decoding your messages. But remember, they can just as easily Google 'Binary to text' and figure it out!

Let's do one more exercise, and this time I want you and your partner to pick a small phrase like:

    The car is red.

And one of you encode it in binary, and the other in hex, then I want you to switch and decode each other's message. So if you turned it into binary, you'll in turn get some hex to decode back into English. Remember, capital letters have different ASCII values than lower case ones and puncutation like a period or exclamation point will have their own decimal values too. Also a ' ' has it's own encoding value too. 

The binary value of 'The car is red.' is:

    01010100 01101000 01100101 00100000 01100011 01100001 01110010 00100000 01101001 01110011 00100000 01110010 01100101 01100100 00101110 

And its hex value is:

    54 68 65 20 63 61 72 20 69 73 20 72 65 64 2e

But hey, don't just copy me, verify it yourself!

Time to Complete: 20-30 minutes, if at 20 minutes you haven't gotten the full message decoded yet, no worries, you got the idea, feel free to stop!

### 3. More Encoding (which is still not encrypting) ###

##### Discussion #####

So now we should have a feel for taking our English message, using the ASCII character table, we have a uniform way to get our message into binary or hex, which computers natively understand. And since ASCII is a universally accepted standard, we know that most all computers are capable of understand us, we are one step closer to encryption!

Another encoding we should talk about is base64 encoding, which yes, you're correct is absolutely insane sounding. 

In ASCII, we decided that most every english character has a base 10 (decimal) value. We then convert it to binary or hex for saving in the computer's memory. We can also convert that english character to base64.

Let's look at our example of:

    The car is red.

In base64 is:

    VGhlIGNhciBpcyByZWQu

A table of the first two letters should only confuse you more...

| Letter | Decimal | Binary | Base64 value |
|--------|---------|--------|--------------|
| T      | 84      |01010100| VA==         |
| h      | 104     |01101000| aA==         |
| Th     | 84 104  |01010100| VGg=         |
|        |         |01101000|              |

What. The. Hell. So encoding 'T' and 'h' separately to base64 result in a different encoding than 'Th' together? How? Why? Nooooooo.

Well Base64 is a weirder encoding, but what you need to know is that it's taking your string, putting it into binary (which we can do like cake now), and then splitting it into 6-bit chunks and converting those:

|   T    |   h     00|
|--------|--------|--|
|010101|000110|100000|
|  21  |  6   |  32  | 
|Base64|Base64|Base64|
|  V   |  G   |  g   |

010101 is 21 in decimal and is V in base64, 000110 is 6 in decimal is G in base64 and 100000 is 32 in decimal and g in base64.

So that's how we got VGg, but what about the '='? Well that's padding, notice we added two zeroes on the end to turn 16 bits into 3 6-bit blocks we could convert (so we had to add two empty bits to get our 18 required bits).

The intricacies of converting to base64 by hand are not what you should be focusing on though! So now we're going to do our first computer assignment. We are going to convert plain-text to base64!

##### Exercises #####

We're going to convert our string:

    The car is red.

to base64 using Javascript. You'll want to go your command line and enter the Javascript repl by typing 'node' on the command line, like so:

    > node

Then once you're in, let's make a new Buffer object, a Buffer is Node's way of letting us represent hex data. So when we make a new buffer of out of our string, it's automatically storing it as Hex. Let's save the buffer as a new variable:

    > var buffer = new Buffer('The car is red.');

The if we just type in our variable name:

    > buffer
    // <Buffer 54 68 65 20 63 61 72 20 69 73 20 72 65 64 2e>

The output should loook like the <Buffer 54 68 65...> line.

So now we have a Javascript variable of raw hex data. Which you know that we can easily convert to letters via ascii, or we could transform it into base64.

So let's display the hex as base64, type the following command in:

    > buffer.toString('base64')
    // 'VGhlIGNhciBpcyByZWQu'

You should see the 'VGhlI...' string output

Now let's display it as hex

    > buffer.toString('hex');
    // 54686520636172206973207265642e

Notice that in this case, it looks exactly like the hex values in our Buffer? That's because it stores it as hex, so to output a string of it's hex values is pretty simple.

Finally let's turn it back into text:

    > buffer.toString();
    // 'The car is red.'

So there we go, we've just manipulated our data from text to hex, and then back to base64, we are encoding with speed now!

So now you and your partner should encode a few messages and send them to each other (via e-mail or IM), then you should try and decode the messages you recieve.

For instance if you get a message that looks like it's hex, try and first turn it into a Buffer like so:

    > var buffer = new Buffer('546865207361666520636f64652069732034353136', 'hex');
    // <Buffer 54 68 65 20 73 61 66 65 20 63 6f 64 65 20 69 73 20 34 35 31 36>

Then turn your hex into an ASCII string by running:

    > buffer.toString();
    // 'The safe code is 4516'

Notice above that when our input was hex, we add the 'hex' argument to the Buffer function. That told our buffer that we weren't passing in the characters of 5468... etc, but instead they were hex values representing characters. Or another way of putting, the string of '5468...' is not intended to represent the number 5468 but hex values that should be looked up in the ASCII table

If we want to take a base64 encoded value and get its raw hex bytes, we can do the following:

    > var buffer = new Buffer('VGhlIGNhciBpcyByZWQu', 'base64')
    > // <Buffer 54 68 65 20 63 61 72 20 69 73 20 72 65 64 2e>
    > buffer.toString()
    // 'The car is red.'

You and your friend should each send three messages to each other:

1 Plaintext message, 1 hex encoded message and 1 base64 encoded message, and then you should each make a buffer out of each, and get it's original text. 

Remember, encoding isn't encryption, but it sure kind of feels like it sometime!

Time to Complete: 10 minutes

Let's do one final exercise, using Node's 'fs' library. We're going to read in a file and see that it is stored as a Buffer.

First, make a file named message.txt with the contents of 'this is the message'. Here's a quick one line command line command you can use to make it.

    > echo 'this is the message' > message.txt

Now make another file that is a Javascript file called read.js (the touch command can be used to make a file)

    > touch read.js

Open read.js and put in the following:

    var fs = require('fs');
    var file = fs.readFileSync('./message.txt');
    console.log(file);

Save the file and now run it on your command line by doing the following:

    > node read.js
    // <Buffer 74 68 69 73 20 69 73 20 74 68 65 20 6d 65 73 73 61 67 65 0a>

And your output should be the Buffer object shown. 

Beware of this big gotcha: If the contents of your file is encoded, then you must specify that in your readFileSync call, e.g.

    > var file = fs.readFileSync('./hexEncodedMessage.txt', 'hex')

Otherwise it will think the file is literal English and give you the hex values of your hex values, which is a mess, and will cause you a headache when you're encrypting/decrypting!

So now, let's take stock of what we've done:

1. You should realize that encoding is not encrypting, and encoded messages are not secret in any way whatsoever.
2. You should be able to use Javascript to encode and decode strings.
3. You can also get the raw data of files you read in, and you're careful to specify if they are encoded or not.
4. You should have a sense of how your computer thinks of string data as numbers.

If you feel like you're clear on those concepts. Let's move on to some basic encryption!

### 4. The almighty XOR ###

##### Discussion #####

Now we're going to get into our first notions of encrypting with computers. We could spend more time doing encryption by hand, but there are lots of good books that start by doing that. I want to instead spend some time demystifying the first computer based encryption tool you'll use: XOR.

First off, it's pronounced "Ex Or", in two syllables. Not "Zor" or "Shor" or "Tom Petty", but "Ex Or".

An xor is like a math operation, just like you can "add 7 to 8 to get 15", you can "xor 8 with 7 to get 15".

And that's not a coincidence that "xor 8 with 7" results in 15, just like addition. At its core, xor is very close to addition.

That last statement is totally mathematically sound, you can prove it by xor'ing in Node. Open up Node and let's do the xor command, which maybe you've never done before:

    > 8 ^ 7
    // 15

Instead of '8 + 7', we wrote '8 ^ 7'. Which means "xor 8 with 7". 

Like addition, order does not matter, so try this:

    > 7 ^ 8
    // 15

They both result in 15! (Did that merit an exclamation point? You decide!)

This is handy, because when we use an xor to encrypt, what we do is "xor our message text with our key, to produce a our encrypted message" And it'll be nice to know that we can do it an any order.

There's one more handy thing about xor, it's reversible. Notice in both cases above we got 15 as a result? (We did). So now if you xor 15 with 8 you'll get 7, and if you xor 15 with 7 you'll get 8. So the three numbers are intimately related. Try it out in node:

    > 15 ^ 7
    // 8
    > 7 ^ 15
    // 8
    > 15 ^ 8
    // 7
    > 8 ^ 15
    // 7

This type of relationship is exactly what we want for cryptography!

If we have some plaintext message 'm', and some key 'k' that only you and your friend know, then we can xor m with k and get a secret 'c'. And when we xor 'c' with 'k', we'll get back our original message 'm'.

If you're not seeing how this is encryption yet, don't worry, you shouldn't be because we haven't done an example yet! Let's do one now!

To do it we have to go back to ASCII encoding. Let's say that we want to encrypt the word 'cat'. Well what are the numerical values in the ASCII table for 'c', 'a' and 't'?

|  'c'  |  'a'  |  't'  |
|-------|-------|-------|
|  99   |  97   |  116  |

Now we can pick a secret key we'll call k, which can be any number we can feel like, let's pick a number at random, oh say... 21.

Ok, now let's xor each number with k.

|   |  99  |  97  |  116  |
|---|------|------|-------|
|xor|  21  |  21  |  21   |
|   |  118 |  116 |  97   |

But do this in Node:

    > 99  ^ 21
    > 97  ^ 21
    > 116 ^ 21

So we get back '118', '116' and '97', but what are those values in ASCII so we can display them?

|  118  |  116  |  97   |
|-------|-------|-------|
|  'v'  |  't'  |  'a'  |

So we just did encryption! We encrypted the string 'cat' against a numerical key of 21, and we get this encrypted message of 'vta'! Awesome!

Now you can send the message of 'vta' along with the key of 21 to your friend, and they can decrypt the message.

Now comes the million dollar question, how can we keep our key a secret too? 

Well, turns out that's a really big question, and it's solved by a system called "Public Key Cryptography". Which this guide might never even get to (at that point you can just read a big crypto book).

For now we just to assume that we can somehow meet up in person, or talk via phone, and securely exhcnage the key. Once we've done that, we can send any amount of encrypted messages publicly, because after all, who would guess that 'vta' means 'cat'? It could mean 'car' or 'run' or 'yay', or '500', we just dont' know!

So now that we've encrypted to 'vta', let's decrypt with our key.

|   |  118  |  116  |  97  |
|---|-------|-------|------|
|xor|  21   |  21   |  21  |
|   |  99   |  97   |  116 |

    > 118 ^ 21
    > 116 ^ 21
    > 97  ^ 21

And we should have our original message of 'cat'!

If you think about it, the second ASCII conversion, (where we make our secret message 'vta') is actually kind of optional. For instnace what if we just transmitted our code as:

118.116.97?

We could even make up a system, where we sent these as fake IP addresses:

    Hey friend, check out this site at http://118.116.7.0!

And your friend could reply:
    
    Meow!

That's not a perfect example (for instance what if your fake IP addres starts with 0, someone will notice something fishy!), but it should give you a sense of what you can do with a simple xor operation.

##### Exercises #####

Now let's try this out!

You and your friend should agree on a numerical key, it can be any number! Then each of you pick a message and xor it like above and send the encrypted messages to each other to decrypt. 

If you choose too large a key number, you'll notice that maybe the resultant number has no ASCII character, in which case you'll need to just send the number itself. 

For instance, if you xor 'cat' with 2500, then you'll have to do:

    > 99  ^ 2500 
    // the 'c' character, which becomes 2471
    > 97  ^ 2500
    // 2469
    > 116 ^ 2500
    // 2480

And 2471, 2469 and 2480 are too large for ASCII, so you'd send your code as: 2471.2469.2480

So go ahead, each of you agree on a key number, encrypt a message and send it to the other, and then decrypt the message you've been given with your key.

Time To Complete: 20 mins.