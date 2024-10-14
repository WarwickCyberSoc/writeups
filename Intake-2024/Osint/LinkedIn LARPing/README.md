## LinkedIn LARPing
You can view the source code for this challenge at: https://github.com/peterw18/Intake24

### Introduction
An OSINT challenge involving collecting the information for several security questions from innocuous social media posts and a touch of social engineering! However, it is (although not viable in the time given) also possible to bruteforce the password for the website.

The given website has an *about-us* page, which identifies four members of staff. Using any search engine, only one tends to have hits: Maxwell Mitchell.

It should be possible to discover three different social media accounts for Maxwell, either through searching or by finding his Facebook and then viewing the linked accounts. All accounts contain arbitrary, irrelevant posts that contain no useful information and hidden among them: at least one relevant piece of data.

```
Facebook: https://www.facebook.com/profile.php?id=61564581215016
LinkedIn: https://www.linkedin.com/in/max-mitch/
X: https://x.com/MaxMitch68

# annoyingly, both LinkedIn and X require you to have an account to view the content 👎
```

### Solving the Security Questions
#### What is your mother's maiden name?
The answer to this is on the Facebook account, where Maxwell wishes his mother a happy birthday but includes her full name. In this, he uses the word "née" which is French for "born" - a way of specifying maiden names.

#### What high school did you attend?
This information is available on Facebook, in the life information panel, or on the LinkedIn, in the education history. The website accepts either just the name or the name followed by "high school".

#### What is the name of your favourite pet?
This is available through X (formerly Twitter). Maxwell gets into an argument about age and memory with a random account and ends up posting both a photo and a retelling of his favourite memory with his pet dragon (?!)

#### What was your childhood best friend's nickname?
This information is available on LinkedIn, where Maxwell recounts fond memories of playing with his best friend "before computers were invented", and the importance of friends and people who can support you.

#### One-time Passcode
This is the tricky one! It says in one of the LinkedIn posts that Maxwell would only give away his MFA token to Barry Langton, his head of IT support, and only if he contacted him directly and could verify his identity.
The aim of this section was to contact Maxwell, either through Facebook Messenger, LinkedIn, or X and impersonate Barry to get Maxwell to give up his MFA token. This required stating who you were, fabricating a realistic context, and providing a fake id for Barry. For anyone wishing to attempt this challenge, the OTP is 266466.

#### Logging In
You must then attempt to reset the password with all the information, including the email given for Maxwell on the website, to receive the flag.