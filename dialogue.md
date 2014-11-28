---
layout: default
title: Personal Certificates - a dialogue in 4 acts.
permalink: /dialogue.html
---

# Alice and Bob go public.

## Dramatis Personae

Alice and Bob

## Scene 1, where Alice explains to Bob what a public key is and what it is used for.

*Bob has asked Alice to drop by. He has something important to give to her.*

Hey Bob, you wanted to see me?

> Hi Alice! Yeah, I wanted to give you this note.

Thanks. What is it?

> It's your password for my document share.

Ah, nice. But why didn't you just send it to me by email?

> Well duh! Don't you know sending sensitive information by email is unsafe? It can easily be intercepted by just about anyone!

Well, if you encrypt your email they can't!

> Encrypt my email? How can I do that?

Just install a personal [certificate][x509] and click the lock on the message before you send it.

> A personal certificate? What's that?

It's a digital statement that you are the owner of a public key.

> Uhh... a what?

A public key. It's the digital equivalent of a padlock key. You use it to "lock" a message so that noone can look inside.

> Right. Except for the recipient, I assume?

Of course.

> So, If I want to send you an encrypted message, I "lock" it with your public key so that it cannot be snooped while in transit. And once you have receive it, you "unlock" or decrypt it with your key so you can read it?

Yes, uhm, no, not exactly. I would use my private key instead.

> Wait. Private key? Where did that come from?

Well, there's two keys. They come in pairs. You create a key pair, consisting of a private key and a public key. The public key is used for encryption, the private key for decryption. They are devised such that what is encrypted with the public key, can only be decrypted with the corresponding private key.

> Sounds complicated. Why not just use a single key, and use that for both locking and unlocking? Just as with the key to my locker?

That could work, but then we both would need to have the same key.

> Yes, so what?

Well, for exchanging encrypted, sorry, "locked" messages  with several people, I would need to share a separate key with everyone.

> Hmmm. I see. You wouldn't want to use the same key with different people. They would be able to read each other's messages.

Exactly!

> But how does using public and private keys change this?

Well, because the public key is used for encryption only, the public key can be shared by anyone. They can all use the same key for encrypting messages to the same recipient. Remember, it's a public key!

> Makes sense. And the private key is kept secret, right?

Right. That's why it's called private.

> So, let me get this straight. Public and private keys are like a pair of keys for my locker, where I can use the public one to lock it, and I need the private one to open it again. I can give the public key to anyone, so they can put something valuable in it and lock it. And I will be the only one who can get to this valuable because I am the only one with the private key?

You got it! Isn't that beautiful? It's called [public key cryptography][pkc].

## Scene 2, where Alice explains that you also need signatures.

*Alice and Bob set down behind Bob's laptop. Bob is starting his mail client.*

> So, let's get started. I'll send you an encrypted message. Give me your public key!

Okay, it's (9007, 114381625757888867669235779976146612010218296721242362562561842935706935245733897830597123563958705058989075147599290026879543541)

> Uh, that's a public key?!

Yes, a public key is just two numbers (and so is a private key), crafted in a very specific way. But that's irrelevant. You store those keys in a file for instance and let software use those keys for encryption and decryption.

> Good. Maybe you better send me your public key in an email then.

Unfortunately, I can't do that yet.

> Why not?

Because sending you my public key by email without protection is not safe.

> Wait a minute! You just said that anyone can know the public key. Why does it need protection?

Well, it doesn't need *encryption*, but it needs authentication!

> Now you lost me.

Listen, if I send you my public key by email so you can use that public key to encrypt messages you send to me with, you better make sure that this public key belongs to me, right?

> Of course. But I know it's your public key: you're the one I got it from!

How can you be sure? Remember, email is not secure: anyone could have sent that message with that public key.

> So?

well, someone may have sent you *their* public key, pretending to be me. If you encrypt a message intended for me with that public key, that someone will be able to decrypt it! Remember, a public key is just two numbers. There's nothing in a public key stating who's key it is.

> Oops. Yes, I see. So sending public keys by email is a no-go.

Correct.

> So how *do* I get your public key?

There's several ways.  I could give it to you in person on a USB drive for example, ...

> Hmm. Yes, I guess that way I would be sure it's your key. But wait a minute, that sounds silly!  All I wanted to do was send you a password. If we need to meet in person, I might as well put the password on the drive instead of the public key. I'm not sure your public key stuff is very useful.

Well, wait, there's more. First of all, you only need to exchange public keys once. From then on, you can encrypt many messages.

> Ok, but what if I want to encrypt a message to someone in another country? Do I need to take a plane to meet this person first?

No, you don't. You just need to authenticate the public key.

> Right. How do I do that?

Using public key crypto!

> What? That sounds like a catch-22!

It's not. There's more magic in public key crypto. You see, It can be used to encrypt messages, but it can also be used to *sign* messages!

> You mean like signing a letter?

Exactly! A signature is used to protect messages from forgery. The message cannot be manipulated if it is signed, and it is impossible to create someone else's signature.

> And all that can be done with public key crypto?

Yes! Suppose I want to send you a message, and I want to sign it so you can be absolutely sure that it is coming from me, and that no-one changed the message while in transit.

> Sounds like a pleasant feature of a messaging system...

Yes, and I can achieve this by "encrypting" my message with my private key.

> Uhm. Your private key? You mean your public key! Encryption is done with a public key, right?

No, I mean my private key. Look, I am not trying to hide my message from eavesdroppers. I am trying to prove authenticity.

> And how is your private key going to help you with that?

Think about it. The public and private keys are inverses of each other. What is encrypted with one, can be decrypted with the other, and vice versa. The only difference between the two is that I choose to keep one secret, and the other one not.

> Ok. But I still don't see why you would encrypt your message with your private key when everyone has the public key to decrypt it.

But that's precisely the point. I *want* everyone to decrypt it. Remember, the message is not secret. I just want people to be able to verify that it's my message.

> Ok, so how would I do that?

Simple. What I send to you are a message plus a signature. The signature is nothing but an private-key-encrypted version of the message. If you use my public key to decrypt the signature, you obtain the original message. By comparing the message with the decrypted signature you can authenticate the message.

> Wow. I'm starting to see what you mean. The message and the decrypted signature should be the same, right?

Right!
If they are not, you know that something is wrong. Either the message was changed after signing, or someone tried to forge the signature.
But if they are, you know for sure that the message is authentic, and that the signature was made with the private key corresponding to the public key.

> Wonderful! I think I get it!

## Scene 3, where Alice explains what a certificate is

**

> So, Alice. I have been thinking about those digital signatures. Does this mean you *can* send me your public key in an email, provided you sign it with your private key?

Unfortunately, no. There *is* a catch-22 here. The problem is that I need to know your public key to verify your signatures. If you sign your own public key, I end up in a chicken-or-egg situation.

> I see. So were back to square one? Back to meeting everyone we want to communicate with in person?

No, we can help each other with that!

> What do you mean?

Well, let's say I meet Carol in person somewhere.

> You mean my colleague Carol?

Yes. We both know Carol and let's say I'm having lunch with her. We can exchange keys in person during lunch. It she meets you later you can do the same.

> We'll let Carol do the work of distributing our keys?

We could, but it can be more efficient. She doesn't have to carry our public keys around. Instead, she can sign them.

> Huh? Sign our public keys? What for?

Think about it. You want to know my public key, right? And you trust Carol, right? Well, if Carol signs my public key, and she knows it's my public key because we met in person, and you know Carol's public key because you exchanged keys in person, I can simply send you my public key, together with Carol's signature on it in an email. You can authenticate my public key simply by verifying Carol's signature, using the public key of Carol, which you already have.

> I see. So it's a multi-step process?

Indeed. And you can extend it to as many steps as you like. If you sign Carol's key, and exchange keys in person with Dave, then Dave can also verify signatures in email I send to him: he just needs your public key, Carol's public key (signed by you), and My public key (signed by Carol).

> Yes, I get it! And you and Dave never have to meet!

Precisely. As long as there's a path between people, composed of signed public keys, people can trust each other's keys.

> And that system actually works?

Yes, more or less. Of course, everyone must play by the rules and only sign keys they have verified in person. This so called Web-of-Trust model is used in a secure emailing system called _PGP_, which stands for [Pretty Good Privacy][pgp].

> And I can use it to verify the public key of anyone in the world?

It depends. You can only do that when there is a trust-path from you to that person.

> And how likely is that?

Well, it gets more likely if you exchange and sign keys with lots of people. The bigger your Web of Trust, the more likely a path exists.

> Ok. But that means I may get stuck if such a path doesn't exist?

Correct. But there's an alternative solution.

> I was afraid you were going to say that. Are you going to throw more crypto my way?

Not really. It's just that Web of Trust is not the only way to verify public keys. There's also this thing called PKI.

> PKI?

Yes, PKI stands for [Public Key Infrastructure][pki], but never mind what that means. It's just a different model for establishing trust.

> So how is it different from Web of Trust?

It is actually quite similar, except that you have a few parties called [Certification Authorities][ca] or CAs that do the key signing instead of everyone singing everybody else's keys.

> Is that better somehow?

Not better or worse, just different. The pro is that there only need to be a small number of CAs in the world. The con is that everybody needs to trust them to properly verify all the keys they sign.

> Ok, so let's assume everybody trusts them. What are the benefits then?

Well, then everybody can go to a CA of their choosing, and have their public key signed in a certificate.

> Wait, certificate? Is that another crypto feature?

Not really, its just a digital document, signed by the CA, that states that some public key belongs to some person.

> So just like Carol's signature on my public key?

Basically, yes. If Carol was a CA, she would be signing *many* people's public keys. Not just her friends, but anybody. It would be her business. That business will only be profitable if she takes her job seriously, that is by thoroughy verifying the identity of people whose public keys she signs.

> So, back to our original problem. I need to verify your public key. How does that work with a CA?

Simple. I go to the CA with my public key and some documents to prove my identity. They will  verify that I am Alice, and put my name together with my public key in a document. Then they sign this document which is called a certificate and after I pay them for their services, I obtain the certificate. I send the certificate to you, and you can verify the signature of the CA to ensure that the public key obtained in it is in fact mine.

> Eureka! And then I can finally send my secret message to you?

Yes!

> But wait, I see another catch-22: I want to know your public key, and to verify that this public key is yours I need to validate your certificate, which was signed by the CA. But boom! To verify the signature on the CA I need the CA's public key. I am back to square 1 again! How do I verify the CA's public key?

In fact: you don't. CA keys, sometimes called root keys, are contained in self-sign certificates. These certificates are issued by the CA's themselves.

> That sounds like a catch-22 in itself!

Yes, but that's what I meant when I said that the downside of a PKI is that everybody must trust the root CA's. Their self-signed certificates are often built-into communication software like browsers and mail clients. Those certificates are called *trust anchors*. This is how a PKI gets bootstrapped.

> Oookay. So no catch-22 after all?

Nope. Wonderful isn't it?

[pki]: http://en.wikipedia.org/wiki/Public_key_infrastructure
[pgp]: http://en.wikipedia.org/wiki/Pretty_Good_Privacy
[pkc]: http://en.wikipedia.org/wiki/Public-key_cryptography
[sign]: http://en.wikipedia.org/wiki/Digital_signature
[x509]: http://en.wikipedia.org/wiki/Public_key_certificate
[ca]: http://en.wikipedia.org/wiki/Certificate_authority
