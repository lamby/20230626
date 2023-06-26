# Why giving talks at Postgres conferences matters

**Pino:** Welcome everyone. We're here to talk about why giving talks at Postgres conferences matters. This is Path to Citus Con Episode Three. Our producers are Carol Smith and Aaron Wislang. I'm Pino De Candia. And I'm Claire Giordano. If you're attending live, we would like to remind you that you can join our text chat in the Citus Con channel under the "Path to Citus Con E03" thread in Discord.

Okay, so I'm, let's introduce our two guests. I'm honored to introduce Álvaro Hererra. Álvaro has been a Postgres Committer since 2002 and works at EDB, formerly 2ndQuadrant. Álvaro is a promoter of free and open source software in Chile in general, and he was the organizer of PGDay Chile in 2019.

Hi, Álvaro.

**Álvaro:** Hello. I'm honored to be here. 

**Pino:** Well, really glad to have you.

**Claire:**  And before we go too far into jumping into a discussion, I also want to introduce Boriss Mejías, who is a senior solution architect at EDB. He volunteers and organizes conferences in Europe and coordinates the Postgres user group in Belgium. More recently, Boriss was a speaker at Citus Con, an event for Postgres, which happened just a couple of weeks ago now and his talk was called "Postgres Storytelling Support in the Darkest Hour", which I highly recommend people watch. Obviously I'm a big fan of many of the talks that the incredible cast of speakers gave at Citus Con but there was something very unique about Boriss's storytelling talk, and I think it's a super interesting way to teach people and I hope we unpack it a little bit and explore how that came about.

Welcome, Boriss.

**Boriss:** Thank you very much, Claire, and thanks for the invitation. Super happy to be here, especially sharing with Álvaro. Once at this stage we, we've been friends for a very long time, I think last century, actually, and super happy to be with him. 

**Claire:** Yeah. Well, the two of you went, the two of you went to grad school together, right?

**Boriss:** Yes. In Chile? Yeah, in university, in Chile. In Santiago, yeah. 

**Claire:** Okay. And is that when you both began your careers in Postgres?  

**Boriss:** Yes. Yeah. Actually, we had a summer project, and Álvaro was in charge of doing all the background part and he decided to use Postgres after a very serious analysis of what was available at the time. 2001 was this, and then he needed a front-end developer so he contacted me, and then we started to work together. So that was my first project with the Postgres as well. And, actually, it's good to see, because we were discussing a few weeks ago that one of the founders of that company at the time, there were like four people only. He was like celebrating, like, 22 years in the company. So we said, "oh, wow. it's been a long time since that project that we did together at that time". Yeah, I went to continue working with Postgres immediately after that. So I decided to go in a different path; I went to academia and did some research, but also related to databases anyway, so.

**Claire:** Okay. And then eventually you came back to Postgres?

**Boriss:** Absolutely, yeah, yeah. Once I was doing the PhD, I started to do some research on implementations of two-phase commit, actually. And at that time I read the code of Postgres, and said, wow, I should be doing this stuff again. It's really robust software. And then I started to work again with Postgres. Yep.

**Claire:** So, before we dive into the high level question that we're here to talk about today, which is why giving talks at Postgres Conferences matters (or frankly, you could insert any Open Source conference / open source developer conference there) I actually do want to unpack your Citus Con talk for just a second, "Postgres Storytelling Support in the Darkest Hour". And I'm curious, Álvaro, did you get a chance to watch that yet? I know the recording is available as part of the live stream, but it hasn't been published yet; not till next Monday as an individual talk, so maybe you have not yet seen it?

**Álvaro:** I have not, I'm sorry.

**Claire:** So I have… Oh, go ahead.

**Boriss:** But this is Monica DeBea. You know Monica, right? 

**Álvaro:** Oh right, yeah, I've seen that one talk of those...

**Claire:** So, first of all: shout out to the artist. So, for people in the audience who are not familiar with what I'm talking about, in this talk, instead of trying to teach technical concepts with the traditional techniques that we use (like demos and code blocks and screenshots),  that show people not just tell people what to do, tell people how to solve a problem, but show them how to solve a problem. What Boriss did is he did a storytelling technique. Maybe somebody can drop the link to that bookmark place in the live stream so people can go watch it later if they want. But he used illustrations that were absolutely drop dead gorgeous and walked us through the story of this... She's not a real person, is she, Monica DeBea?

**Boriss:** I'll keep that information without disclosing anything, so..

**Claire:** So she may or may not be a real person. The reason I thought that is the last name is "DeBea", which I thought was a made up name because it sounds like DBA. So anyway, and it talks through the problems that she's having with her system in the dark of the night after everybody has left the office and something's going wrong. And I think it's the transaction ID wraparound problem that she's struggling with? And it's just super cool to learn by storytelling, so ...

**Pino:** I'd like to chime in. Most people do that. I'll just chime in and say I watched the talk last week and I really loved it. The live stream was during EU hours and too late for me so I watched the recording. But it occurred to me both that it was a great change in pace in terms of how we watch technical content especially if you're watching many presentations in a row. And so it engages you differently, storytelling. The storytelling technique is really great. Boriss, I really liked your pacing in it, and then the story's engaging. You know, Monica goes to get to the pub to have beer with her colleague and then they discuss transaction IDs and the wraparound problem, and then Monica ends up having to debug that, having to deal with problems related to transaction monitoring, and preventing transaction ID wraparound the next day. And I thought: that was captivating. So immediately I was wondering: wow, you've done, have you done this before? What made you think of that? Where'd you get that idea?

**Boriss:** Well, thank you for the feedback. I mean, this is one of the things that I wanted to have feedback on this type of presenting material because it is still new to me: this is the third presentation that I give in this format. The first two were also online talks and I was thinking like, I mean, in the time of the pandemic, we were all doing kind of webinars, let's say webinars and online conferences. And we would try to emulate a real in-person conference, and it was super tiring, and it was difficult to get feedback from the people because you don't see the audience.

So it's completely different stuff. And then I saying: okay, if I'm going to do something online, I should probably do something that I cannot do in person. So to really have an added value of doing it online, otherwise we're just emulating what we want to do in person. And then I said: okay, what are the ideas that I have that could work in this?

And I was having this idea for a long time to tell stories. And actually came after I read a book, "The Phoenix Project", that I thought was really good in terms of storytelling about CI/CD techniques. And I wanted to do something like that for Postgres, and then it came out, the idea with Monica DeBea.

I remember I was in Milan and I was talking with my colleagues from support, and Anna: they're super good. And I said, okay, maybe mmayvbe this should be something that I could tell people. Like, I mean, what is the work of support? Because I've done support as well. And that's how I came into it.

Now, I discover also there is this book "A Curious Moon", which that's kind of it's name, and I would really like to get to that level. I mean, try to write stories. I mean, not just giving a presentation, but kind of put it in the format that people can read about it. And luckily I have the luck to work with with Scarlett Riggs.

She's, as Claire was saying, she's an incredible talented illustrator. And I remember that I didn't give a description of Monica to her, she asked me to describe her. I said, "well, I don't know. I mean, I will tell you her personality and the things that she does and all these kind of things."

And she came up with the drawings that I thought that were really, really amazing. And then every time I have a new idea for a talk, I discuss a little bit with her, and she understands immediately the technical part. And then she makes the illustration super nice. The previous one was about "Idle In Transaction", and this is when she came up with the elephant inside an hourglass.

She's super cool. So I really like, I mean, I'm lucky to work with talented people as well. So that's how, this is what Monica DeBea is about, and yeah,  you get  some feedback from people. So, maybe I will do more of those.

**Claire:** You could argue that you can tell a good story without beautiful, magical illustrations, right, because your voice and the words you choose and even the pauses in your story can entrance people. But, having those magical illustrations by Scarlett Riggs really added like a whole other level. And I mean, there's no reason learning can't be fun and you made it, I think, more fun. So, I appreciated it.

*Boriss:* Oh, thanks.

**Claire:** All right, and then I just want to shout out the book that you mentioned, "A Curious Moon". Hopefully... I can drop a link in later and maybe Aaron can now? I think that Rob Conery is the author of that, and he is not on my direct team here at Microsoft, but he does work in the Cloud Dev Advocacy group here at Microsoft, and I'm a big fan of that book as well.

It's pretty, awesome.

**Boriss**: (I agree.)

**Claire:** So, we're here to talk about why giving talks at Postgres conferences matters. Álvaro, why don't we start with you? I would love to kind of hear your high level answer to that question. 

**Álvaro:** Well, I think the main reason is that giving talks gives us the opportunity to grow the Postgres community.

And growing the Postgres user community means we also grow the Postgres development community, both directly because some of those users become eventually developers, and also indirectly because those users as they interact with the software, provide very useful feedback for what should we do next and how to evolve the software in a way that serves everybody.

So these talks... Two sorts of conferences that are slightly different. We have Postgres conference proper where Postgres users come and learn about things. And there's also the conferences of other types, like general open source conferences, or, I dunno, container conferences or database conferences where we expand the world of Postgres to people who don't currently use Postgres.

So, the type of talk that we give to either of those conferences gives different benefits to the Postgres community. So as we grow the community to new users, obviously we gain the input of people who is working with other databases. And those have different ideas of how a database should work. So that's another thing we get.

**Claire:** Have you ever had trouble, like prioritizing the time that it takes? I mean, these conference talks don't just happen. They take a lot of work behind the scenes to conceptualize them, create them, practice them, right? And then travel sometimes, when it's in person, to deliver them.

Is it hard to make it a priority for you, or not?

**Álvaro:** Well, um, I have a family, so I have limited, how to say that, a limited amount time that I give for conferences. I don't like to travel more than, say, two or three times per year. So that limits how many talks I'm willing to give.

And of course, the preparation, the time to prepare for each conference is, I know, is high.

I don't like doing talks where I spend just a little to prepare slides and material. So, to be honest, I don't limit myself. I just do as much as needed. And, because I don't do many, then that is what becomes the limit.

**Claire:** Got it.

**Álvaro:** Sorry, sorry. One last point. One last point is that I don't repeat talks. Some people will give the same talks over and over, so that means you only have to spend the time to prepare the talk once and then give it many times. I, for some reason, I don't like to do that so that also becomes a limit. Okay. Pino?

**Pino:** I was gonna come back to your point, Álvaro, about different communities that you give talks to. You're thinking about the audience and it needs a different approach. How do you go through that process, and do you set a goal for, not just what the audience will take away, but what you'll take away given that the audience, especially in the case where the audience isn't, maybe not as familiar with Postgres?

**Álvaro:** I don't think so. I mean, in my first presentations many years ago I just tried to present what the topic at hand without thinking too much about what the audience was going to get. Then, at some point I realized that was a waste of their time and my time, because many people were listening to a talk and weren't getting too much value.

So I realized that I had to think very carefully about what value would the audience get from my talk. And that means my approach to the talk becomes completely different depending on whether the audience is technical guys or developers or decision makers. So, that comes by direct experience because I gave a very deep talk about LEFT, sorry, OUTER JOINS to a bunch of company CTOs and that was a complete failure. But, I do not think about what I am getting from the talk.

**Claire:** So, I think that's a really good point that learning, of focusing on the audience and what they need, and where they're coming from and having empathy for, you know, the fact that they're probably not as expert as you, or don't know what you know is super important.

And oh, you've said so many things. I mean, there's also the notion of failure. Every good conference speaker has a couple of failed conference presentations in their background, right? Like you, it's just absolutely naturally you got to be willing to fail. Okay, so we've got a bunch of things we need to circle back on that Álvaro has touched on here, but I want to cut over to Boriss for a second and ask you the high level question: Why do you think giving talks at Postgres conferences matters or, frankly, any open source developer conference? Why spend the time?

**Boriss:** First of all, I don't think it's part of any of our job description, neither for Álvaro or for myself.

So that's why Álvaro was mentioning his limited time with the family because he has done the extra time apart from all the job that he does. And then it's not my description of work, either. I think we need to do a little bit of advocating, but it's not really like you have to give "that" many talks per year.

No, we, we do as many as we can. And it is important in the sense that, for instance, Álvaro, the fact that he's a core developer, it gives the community the sense that the core developers are close to the people that are using the software. It's not just about, "we release the software that we are developing in in our home and then you use it how you will". No. Álvaro does it because he wants to hear how people is using the software.

And I think that's super important, because, I mean, for many other software that we use, we never know who is developing that stuff and the fact that you go to Postgres conferences and you meet the core developers; if you go to FOSDEM, you meet plenty of core developers. It's super nice. So that's very important that in conferences you can meet the real workers of the software itself, so it builds the community.

That's one thing. In my case, (that) I don't develop Postgres, but I do work a lot with project with customers that are using Postgres. It is a way of extracting all those different cases that we see that people have trouble with or have had some patterns of solving things, and then present them to the broader community and say like, "look, if you have this type of problem, then this is one way of solving it".

And it enhances the entire knowledge of the entire community. And, for instance, getting back to other communities, when you were saying Claire, that this is not about just any open source project. I remember that when I was working with Alfresco, which is a kind of commercial open source stuff, and they were stopping the developers conferences [so] the community itself organized and we created the "Order of the Bee" with the intention that we wanted to share the knowledge between us. So, sharing knowledge is something that comes automatically with people that work in open source and free software because that's one part of the core values of having open source: that you can learn things and share that knowledge with all the people.

So there's lots of things. I mean, my case is also to abstract patterns and understanding how things are being solved for many people and get feedback about whether there are better ways of solving the same problem or not. Yeah. I do repeat talks, by the way: I don't have the same approach as Álvaro. But it is never exactly the same talk.

Like, I mean, I talk about table partitioning. I think I've given it like three times and it's always different. I localize it a little bit depending on the conference that I'm giving, and I get feedback from people and I try to improve that and the next time I give the talk.

**Claire:** Yeah. I actually do the same thing. I will give the same talk again but I improve it each time. I try to incorporate the feedback I got from the previous version. And, I don't know, Álvaro, if you disagree but, you know, some of the smaller Postgres conferences, like a lot of the PGDays for example, they don't videotape or record the conference, so it's only valuable to the 200 people who were in the room.

And so I find giving it again makes that knowledge more accessible to more people. It basically shares it more broadly. Now, if it's been videotaped and it's a high quality video recording, then you could argue it would make more sense for me to create a new talk. And so sometimes I do.

**Álvaro:** Yeah, I agree. I'm not saying that it is valueless, I'm just saying that I don't feel comfortable doing it. Maybe it's [something] I should be doing, the way both of you described, which is to improve the talk and give it again because then eventually a very good quality version of the talk becomes videotaped and then that is valuable for the whole world.

**Pino:** It seems to me, there's something interesting about the roles each of you play. As a committer, Álvaro, perhaps your time is best spent talking about different topics that you can go very deep on. And then others that are trying to focus more on sharing knowledge and propagating the knowledge can repeat talks because there's always a more audience that didn't get a chance to watch it previously. And it's always more fun to watch live. Or it's often more fun to watch live...

**Álvaro:** Mm, I hadn't thought about giving talks to other speakers rather than directly to users. So, lately, I've been finding I've had a hard time finding good topics to speak about because my work is normally stuff that is down deep into the bowels of the system. So, I think, "well, who cares about this?" So I don't give talks about that. Maybe that's a mistake, I dunno.

**Boriss:** I can give you plenty of ideas. We talk....

**Claire:** Can you throw out some ideas right now, Boriss? Can I put you on the spot?

**Boriss:** Ah, right now... I mean, well there are plenty of stuff [on] the improvements in VACUUM, for instance: all the parameters to explain what the parameters do, actually and in each release there's one thing that is added or something like that. That was one thing. Other things are like parallel executions and those kind of things.

Well, you also know a lot about the BRIN index, which you have talked already about the BRIN index, but maybe, right, explain some use case because it's... still, people don't use it enough. I think those are at least three topics that you could be talking about. Yeah.

**Álvaro:** Right. But you see, BRIN indexes were done in version 9.5, so that was like ten years ago... about six years ago.

So at this point, who cares, right? That's, I mean, that's what I'm thinking about.

**Boriss:** Yeah. That's your point of view, exactly. 

**Álvaro:** No, but I mean, for instance, I even sometimes watch the same talk twice because I discovered something different the second time that I watched the talk.

And that's for me something that, I mean. Or because just the talk is fun, right? That could also be another reason to watch the talk for the second time, yep. 

**Claire:** I think the other thing to keep in mind too is even features that are, maybe, new to Postgres 10, for example, or 9.2, and in the case of BRIN indexes, like, the user may not be familiar with them yet.

Like they may not have been around, they may not have been using Postgres.

**Álvaro:** Right.

**Claire:** You know, back then. And so, what's old to you can be new to your audience. Yeah.

**Álvaro:** Yeah glad we're having these conversations,because I'm discovering also so many things that I am wrong about. 

**Claire:** No, no, no, no, no. We are not here to tell you you were wrong!

Oh my goodness. No. Uh-oh! We're going to get a bad reputation!

**Álvaro:** No, it's just about repeating the topic. For instance, I saw Claire's talk about how to make Postgres and make your communication, like, more visible to people in Berlin. And then I saw it again in FOSDEM in Brussels. And the second time that I saw it, I said, like, "Oh, I didn't realize that this was also in the presentation". It was something that I discovered the second time that I watched the talk. So I think it's impossible to get the entire talk, like, once when you see it. The second time that you see it: you learn something. It's like watching a movie again. I don't know, not all the movies are worse, watching twice, of course. But some of them it's like: "ah, I didn't realize this".

**Claire:** Oh my gosh. So you're telling me my talk was worth watching twice? 

**Álvaro:** Well, yeah, it was absolutely. 

**Pino:** Yeah. I'll also add that I think people are doing interesting things with recordings. We have so many recordings now, so much content.

Of course, new content is always very welcome. And again, people appreciate attending live. But what I've started doing with folks on my team is we watch recorded talks together because there'll always be someone who knows a little bit more about the topic. And if we can stop the video, take questions, start it again... So the recorded talks definitely are huge value. Of course, people have always been listening to them. You can see your watch count increases, you know, in whatever platform. But we can, we can reinject a little bit of a live show experience by watching together.

**Claire:** So wait, you watch together all in the same room, or? I know the answer to that is "no", because your team is distributed, right? You're all in different places. 

**Pino:** That's right. So I'm sure other other platforms have the same feature, but on Microsoft teams, we can share the video in the meeting and that way we're all listening to the same audio at the same time and that creates a great experience. So I can share controls so that anyone... you know, we usually this in a small group, and so anyone can stop the video and say. "excuse me for a second, I just didn't understand that part. Does anyone know what that meant? Huh, nice." and it creates a nice interaction.

**Claire:** I know Discord supports that as well. I've been on the general stage here with Aaron and we popped up something from YouTube and we were watching it together at one point. So it's a nice capability to have multiple people watching. 

**Pino:** Could I ask a question? I want to come back to something that Boriss said about the importance of sharing knowledge for an open source community and Álvaro touched on this as well: the aspect of how much knowledge sharing do you need? And it seems like there's always so much to do, whether it's development tasks, reviewing other folks code, our own projects... whatever that work is. And then knowledge sharing; blogs, presentations..

Do you have a sense of how you can ca how you calibrate that? And not just at a personal level, but do you have a sense of whether you take into account [that the] Postgres community needs to do more of this, and perhaps there was a time when it wasn't and now it is? Or: how much does that influence your participation, and how much you ask others to participate in this way?

And I didn't... either one of you: Álvaro or Boriss.

**Boriss:** Oh, well in my case, I mean, I try to kind of pay attention to the questions that are being asked by the customers. And when I do training I also try to get the questions that come up over and over, and I say, "okay, maybe this is something that worth talking in a conference", the kind of explain this, like, to a broader audience.

And that's how I try to identify topics for giving talks: the needs come from there, from what I see on the fields, if you want to say like like that. So yeah, experience with users mostly, yeah. That would be my way of trying to identify which kind of knowledge has to be shared.

But, for instance, last episode, you were discussing about people having trouble with host-based authentication. I thought, "that problem was already solved like many years ago". But now I realize that some people are using all the [other] databases just because they cannot get around this host-based authentication.

But then giving a talk about that? It's kind of difficult because no Call for Papers committee is going to accept a talk on host based authentication. But that means that we can do kind of a juju (?) video or something different to explain that again, because people are still having trouble with that.

So, I think, I mean, the need for knowledge sharing comes from trying to listen to what people are asking about and then go, "there, yeah. that's how I do it".

**Álvaro:** Mm, right. So when I was working for Second Quadrant, I mean before the acquisition, I had plenty of involvement with customers. In, like, for professional services like, like Boris is.

And that was a very productive mechanism to know what Postgres features to work on. Nowadays, I don't do that too much anymore. So I kind of feel like I've lost a bit touch with that. I still get that from the community mailing list, and that, once a feature is done, of course, I can make conference talk about the new feature.

But my current professional work with Postgres at EDB seems to relate more to fixing bug and, those... I don't think give too many interesting conference topics as much as new features or future expansions.

**Claire:** I feel like you can go either way. When I try to have empathy for people in the audience, obviously they want to know and understand how to use the new things, the new features.

So that's obvious, like, content for future conference talks. But there are also pain points, or things that are complicated that maybe they don't fully understand yet. And that also gives fodder. And that goes back to what Boriss was saying a few minutes ago, about, you know, listening to whether its users or people in customer support, right, the inspiration for Monica DeBea, like: What are those trouble spots? What are those pain points? Where do people get stuck? And then, of course, there's also "getting started", Like, anybody new, you know, they're starting from a blank sheet of paper, or maybe they're starting from knowledge of another database, right?

And so they've got a whole bunch of things they need to learn. And so, those introductory talks, I feel like are always useful. What else? So: new features; pain points; getting started. Are there other obvious categories of useful talk content out there? 

**Boriss:** Well, obviously "How to become a Postgres hacker" is a very good talk.

**Claire:** Yes.

**Boriss:** And how to view patches and stuff like that. Yeah, I am thinking about stuff that revolves around Postgres development rather than Postgres usage.

**Álvaro:** Yeah, exactly. And I gave, for instance, a talk in, which is the other spectrum, I think we compliment each other a lot. In the Nordic PGDay I gave a talk about JSON usage, and what I did is I went to Stack Overflow and I searched for the top 10 questions and I answered those questions in the talk. But I didn't go, like, one question after the other.

So, again, I tried to build up a "use case" and within the use case I was answering the questions, and, of course, talking about metal music which is one of my favorite topics. So it's... I tried to mix "Jason" sounds like really "metal" stuff. I sounds like a killer character in a movie or something: "here's Jason".

**Claire:** I know that one of my teammates gave a talk at PGConf.EU about, going back to what Álvaro was saying about "How to become a Postgres hacker", and it was him sharing his story about the first six months of becoming a Postgres hacker. And then he gave that talk again at PGDay Paris a few months later.

So that's kind of another category of, like, not quite "Today I Learned", but, you know, "What I learned as I was doing X for the first time". And I think people always appreciate those as well, right? Because a lot of people, whether they're expert or beginners, have empathy for those kind of, you know, first experiences and sharing their observations as a newcomer.

**Boriss:** That was a very good talk. I saw it also in PGDay Paris. I was there. Yeah, very interesting stuff.

**Claire:** Oh, I wish I was there. Other categories of really useful Postgres conference talks? We've got pain points, new features, how to get started, how to become a Postgres hacker... how to create Postgres patches.

**Boriss:** Something that I would like to see a little bit more, and I cannot do it personally, it's like, people having their experience with Postgres: like people who are not working with Postgres as the main thing but they are doing something else and they use Postgres. Even just sharing their failure that could be also something very interesting. Like, "we tried to implement logical replication, but we failed on this and that: please help us to understand why"... that will be a very useful talk. Maybe meetups will be a better place instead of conferences?

I'm not thinking about what I would like to see, I'm just thinking about what the Call for Papers committee is going to accept, because I would like to see that in a conference, like use cases: "we try it and we failed" or "we tried and we were successful, but we still need to do these other steps". So people just using Postgres, I'm just saying. Like "we implemented, I don't know, pharmacy software, and this is how we use Postgres". I really would love to see that. More, more of that.

**Álvaro:** Oh, I definitely agree that user success stories are a good topic because it shows other users that Postgres can really do whatever.

**Claire:** There was a talk at FOSDEM PG day... I'm looking up the schedule right now: it was Nick's talk. Remind me what the title was? I'm trying to look it up. Oh, "LFMF: how a CREATE INDEX CONCURRENTLY led to a 6 hour downtime" and it was by Nick Bluth. And what does LFMF stand for?

**Boriss:** I have no idea but the story was super good. I saw it in Nordic PGDay as well. 

**Pino:** Probably something about laughing a lot.

**Claire:** Okay. I think it was "Failure"? I think one of those F's stands for "Failure". So, and I do think failure stories are really appealing. I mean, some people don't like to share them because it makes them feel vulnerable or like they might be judged.

But when you kind of are willing to be vulnerable in that way people can learn a lot from your failure story. And it's actually quite a generous gift, right, to share it. And there was a lot of laughter actually in the room during that presentation, because you could kind of feel his pain as he was reliving it.

So as I scribble notes here, Boriss, I took your suggestion just now to "people having their experience using Postgres" as one category, but then "sharing your failures trying to do this and it didn't work" as another category that's super useful, too.

**Boriss:** So, LFMF means Learn From My Failure, right?

**Claire:** Oh okay. Cool, oh.

**Álvaro:** Yeah, right now. So, the first two times that I gave Monica DeBea talk, I was doing kind of an audiobook. So I wrote the script and I read the script, I was yet to record it. But then you convinced me to do it like talking to somebody, and I was saying like: "you know, I cannot do this. I cannot do this." And then I saw Nick doing this in Nordic PGDay and he was really doing storytelling live and said: "wow". And I was wondering like, how this to him. And then I was wondering, while he was presenting this stuff, I said: "oh, wow, maybe I can do this for Citus Con". So yeah, thank you, Nick, for giving that presentation because it convinced me that your idea, Claire, was very good.

And that's how I managed to present it in the way I did in Citus Con. Otherwise, I was just going to try to do the scripted thing again. But I think this one works really well. It's a very good, yeah.

**Pino:** I... Oh, sorry Claire, go ahead.

**Claire:** I was just gonna say I really liked on the Citus Con recording being able to see your face as you were telling the story. And you told me that the inspiration for the storytelling technique was that your daughters had been growing older and you had all these fond memories of reading them stories. Right, telling them stories as a Dad and you thought, "well, maybe I can do this with Postgres to other people now?" And so, just like when you're reading a story to somebody else, a young child in your family, they can see your face and that's part of it. It's not just your voice, so I was really happy that you did both, right? 

**Álvaro:** Thanks for the suggestion. That was good. 

**Pino:** I was gonna ask since we're talking about getting ideas from other speakers who are your favorite speakers on the circuit and why? In Postgres in particular?

**Boriss:** No, I do have a favorite one.

So I was making, so somebody asked me this before and said, okay, there are plenty of names that are very good. And I said, well, if I have the "Top 10" speakers in a conference and they're all presenting at the same time, which one will be the one that I don't want to miss? And that for me is Thomas Vondra.

He is such a good speaker because he's is the same level of knowledge as Álvaro and he adds a little bit more jokes. And this is what I really like, because his jokes are so dry. He comes up with, with these kind of things that make you think a lot with with his presentations.

Every time that I see one of his talks, he's like, "well, I need to check this stuff when I get back home and I need to see these slides again and then try all this stuff...". And he doesn't overdo it in terms of trying to be funny. No, he just is Thomas presenting. And then he's super dry and I really enjoy watching him.

That's [a] speaker that I never want to miss. If he's in a lineup for presentation, I want to see his talks. That's, yeah, because it's a very good combination of knowledge and then bringing it in a funny way as well. 

**Pino:** Yeah. And I guess humor is an important part. I mean, not all speakers try to get humor in, in their presentation. 

**Álvaro**: And Boriss has a very, very good sense of humor, and that absolutely leads to the audience being very engaged with the topic of the talk.

**Claire:** You sure, Álvaro? Are you just being nice because you've known him for a long time?

**Álvaro:** No, not at all!

**Claire:** I mean, is Boriss really that funny? 

**Álvaro:** Uh, to me, I, definitely enjoy his talks very much. I also..

**Claire:** Oh my God, you thought I was serious! I'm sorry! Of course, Boriss is funny.

**Boriss:** Thank you. Yeah. No, but I've learned that humor is like salt to food. I mean, it enhances your taste of your food, light. But you can't have a plate of just salt, right, you need to have a content. Yeah, I learned this by watching all the talks, like, how to add humor. I watch a lot of talks about how to give talks, and one of these was about, I think it [was] a Ted Talk or TEDx about adding humor to your talks? And the guy explained it very well. I said like, "ah, yeah, okay, that's how it works." If you add too much it's going to be too salty, and then you mess up with the content. So you, hah, it's difficult to get that balance as...

**Pino:** So that's on one end, but what about the other end? I mean, I would imagine that some people don't think that humor is accessible to them.

They might be willing to give a talk because they feel competent about the subject, but they might not feel co comfortable with humor. Do you think it's for anyone to add humor to their talks, or it takes a certain kind of personality?

**Álvaro:** Can answer that one? I definitely think not. Cause I don't have the sense of humor that is needed to make jokes on stage, so I don't even try. My talks are, I would say, pretty much humorless. And I'm sorry for that, but I really don't know how to do that.

**Pino:** So, do you substitute with something else, Álvaro? If humor is not your "go to", is there something else that you focus on to keep the audience engaged?

**Álvaro:** I just... I think one thing is trying to make examples. For example, if I am presenting a Postgres feature, I try to make the command examples something that is a little bit alluring so that people are not bored by me talking about "SELECT foo FROM bar", which means nothing. But, I dunno, constructing something that keeps people interested, if I can add some pictures about the thing that's even better.

**Boriss** But I think the knowledge that Álvaro has is also authority. I mean, everybody knows that Álvaro knows what he's talking about. So, you have more confidence into listen to what he's saying, and you know that you can ask any questions and he's going to answer you correctly unless he doesn't know and then he's going to tell you, "I don't know", right? And then it's like, okay.

**Claire:** It's important, yeah. That it's for speakers to know that it's okay not to know. And it's really important to say, "I don't know", right. I mean, that gives you authority. I actually want to shine a light on something that Álvaro just said, which is using interesting things in your examples.

I don't know if any of you remember the talk that Louise Grandjonc gave at PGCon ["Wonderful SQL features your ORMs can use (or not)"], probably back in Milan... so what is that, pre-Covid? And she might have given a similar talk at a DjangoCon conference. And she used, like, pop music stars in her data model and in her examples. And it made it just so much more interesting than if it was "foo" and "bar" which, as you said, are meaningless.

So I do think that's a way to connect, to have those examples that kind of catch your attention. Another way to connect is just, I don't know. Do you do this, Álvaro? Do you ever ask your audience questions, like, as part of the talk? Like pause and stop. and make it less of a lecture and more of a conversation? Or even just ask, "show of hands - how many people have done X, Y, Z with this new feature?"

**Álvaro:** Yeah, I think that's a good resource and I've done it a couple of times. I learned to do that only recently so it's not very long in my story. But yeah, those are good resources.

**Claire:** Basically anything to keep people off their phones, right? Yeah, because it doesn't take that much of either boredom or not being able to follow... And, like, as soon as you can't follow the speaker, as soon as you're lost, your brain is gonna try to find something else to think about, right. And what's the closest thing? It's probably your phone on your lap. So, anything you can do to kind of keep somebody paying attention.

**Pino:** So, since we're talking... oh, I'm sorry, Claire didn't mean to cut you off.

**Claire:** No, you didn't. Go, go, go.

**Pino:** Since we're on the topic of, sort of, how [a] presenter's personality comes into play, I wanted to ask: are you an introvert or extrovert, and how does that affect how you prepare and how you give talks? Maybe Álvaro, could you take this?

**Álvaro:** Yeah, so I'm definitely an introvert and it I find it very hard to, in a normal situation outside of a talk, to engage in a conversation with people.

So when I'm at a conference it is very useful to have given a talk so that people approach me and we can speak and about my topic. And then we will ask, "what are you working on?", and then conversation from there. So that's one thing I definitely like about giving talks, which is to let me connect.

Extroverts, I think, do not have this problem about connecting with people, so they can go to a conference and connect with people without having given a talk. So, for me 

**Boriss:** So for you, it's like your icebreaker. You give a talk as an icebreaker.

**Álvaro:** Yeah. That's one way to see it. And it's best if I can give the very first talk, or, or a very early talk, so I have the rest of the time too connect.

**Claire:** It really is a wonderful icebreaker. Not only does it give you something to talk about but people will recognize you in the hallway, like you said, after you've given your talk. And they'll stop you and you'll continue to get feedback and meet new people. And maybe feel a bit more welcome, even though you would've been welcome had you not been giving a talk, but you might not feel that way, you know?

**Álvaro:** Right, yeah.

**Claire:** Boriss, are you an extrovert?

**Boriss:** I understand I am. I mean, I never understood the question, "being an introvert or extrovert", because sometimes I look at what it is to be [one] and sometimes I keep things for myself. So maybe I'm introvert as well, I don't know.

But my reason for giving talks is that also I learn a lot when I give talks. I have to prepare the talks a lot, and although I repeat some of the talks I never repeat the same slide sets. So, I try to learn while I help other people to learn. And from the feedback that I get is that because I can make jokes and all this kinda stuff, I can keep the attention of the people. And because I can keep the attention of the people I manage to pass some concept that could be either boring or complex and make it accessible to people. So when I understood this, like, "oh, my talks are really contributing to the knowledge sharing of the people". I kind of make it my own mission.

It's like, "ah, I want to give more talks because I'm helping the community to learn about Postgres". And I like it, I like it a lot. So, because I learn and I know that people can learn from that so that's very good. When I was in FOSDEM, I mean last time, somebody asked (I was walking with Álvaro, actually, we were walking to the room, to the Postgres room) and somebody asked us: "Hey, you guys know where is the Postgres room?" We gave them direction, and then the guy look[ed] at me and say like, "what are you giving a talk about JSON on, on [unknown]?" I said, "well, yeah, could be me". Said, "oh, yeah, it was you". And then, "Thanks to you, now I use JSON on Postgres". "Oh wow, that's super cool." So it kind of convinced me, like, okay, I'm doing the right thing. And also I foster them: somebody came to me and said like, "ah, Boriss, your talk about table partitioning in Berlin, I used your slides to give the same talk to my colleagues in a couple... I don't remember, it was a customer. So that's kind of like making a song and somebody makes a cover of your song, yeah. Because they just pick up the slides. So that's kind of a very huge compliment because..

**Claire:** Yeah!

**Boriss:** ... my slides, they don't even have bullet points so they're not very easy to just pick them up and reuse them. It means that the guy was really paying attention to what I was saying in Berlin because he was able to just reduce the slides. So, I think that's my motivation. I mean, I'm now convinced that I can contribute to knowledge [and] that it increase the knowledge of the community, and that's why I like it. Apparently this is one of the advantage of being extroverts, probably.

**Pino** Do you feel that you get enough feedback as a presenter? You're making me think that you gave some great examples of feedback and it's enough to energize you and motivate you. And it reminded me that any open source developer community also often tells people just, "even if you don't have a bug to submit, but just let us know you're using the product. Just you know, just say something, send us an email", and that little feedback helps. How is it, as a presenter, do you feel you get enough feedback at the moment?

**Boriss:** I think, yes, I'm getting enough. It could be more, it could be more. And the good things is that people, for some reason, they are also able to tell me that was wrong, or "Why didn't you talk about this?"

So people also give me constructive feedback so that's also very positive. It can always be more, and I will appreciate a little bit more just to know, like, I was doubting a lot about this Monica DeBea thing. I mean, "is it good or not"? And then...

**Claire:** It's really good.. 

**Boriss:** Thank you. I wasn't getting enough feedback about that one because it's different. So yeah, that one you need a little bit of help to improve it and all this kind of stuff.

**Claire:** So, I think human nature... I think a lot of people like our parents mostly tried to teach us to not be selfish, but we're naturally selfish, and there's only 24 hours in the day and we have a million things to do, right?

We've gotta pay the bills and cook the food and take care of family, and, you know, we have our hobbies and work, sleep... I mean, you get it. And so there's a lot to do and it's hard to even make the one minute or two minutes it'll take to send someone a one-liner and pass that compliment along. I tried to compliment people as much as I can, and I don't think I do it enough.

I don't think I say "thank you" or I tell people, "Hey, you did this thing and it helped me". And so, I don't know. I think we should all give each other feedback more. Both positive and the constructive negative feedback too. That's my philosophy for the day!

**Boriss:** Yeah, I agree. And given that philosophy, I will publicly acknowledge then Álvaro: because of him,I'm into open source and free software.

I'm working with him in the beginning of my career in it was very, very important. So, thank you, Álvaro, for all your knowledge transfer to me..

**Álvaro:** My pleasure...

**Boriss:** ... and always good time.

**Álvaro:** Yeah, it's been a very nice long ride.

**Claire:** I remember being at FOSDEM, and I don't think it was 2020, right before Covid hit, the year I gave up my first talk at FOSDEM, I think it was the year before 2019. And Lætitia Avrot was there and she was really excited to be working on her very first patch to Postgres. And I think you were her patch reviewer Álvaro?

**Álvaro:** That's right. We sat on a freezing beer pub in Brussels and we were going over her code. But it was a nice... I didn't think too much of it at the time, but I think it was well received from her.

**Boriss:** Oh, 2017.

**Claire:** Oh, really? Okay. Really. I know I, this is a long time ago. I just wanted to give you that shout out as well, like as a Postgres committer, it's not just your job to do development on Postgres and get it integrated, but you spent a lot of time reviewing other people's patches and other people's work, giving them feedback, helping shepherd it through the process.

And so you know, we all, we all owe Aden. Thanks for that because you know, it's not your name on those features but it wouldn't happen without you. So, yeah. Yeah, 

**Pino:** it's 

**Boriss:** been a very lucky ride for me, and I'm very grateful for the all the time that I've given Postgres and Postgres, the opportunities that's working on Postgres has 

**Pino:** given me.

I thought with a question, is it too late for me to open up a quick, it could be quick. Yeah, go for it. I can run a few minutes open. I was, how, I was just reflecting on how nice it is to hear you all who have been in the Postgres community longer and you remember talks from different people like going way back and you've worked together in your case Álvaro and Boriss for a very long time.

And it's nice to hear that and it's all part of the community building. So folks that join Postgres, they find a community that's warm and welcoming and supportive. And so I wanted to ask Bo, I think it was bodies have touched on it earlier that during the pandemic conferences, in-person conferences were reduced so much and how did it affect the community?

Is it coming back or, or, or, or can we do that kind of community building through virtual events and remote events like we're doing now? Yeah. Maybe take that. In whatever direction in terms of like, you know, how how much do we struggle now? And because presentations are so much part of, and the conferences are so much part of community building.

**Boriss:** In the case of the user group in Belgium, it was an opportunity to start doing online conferences because it's always so difficult to find sponsors for doing in-person events and people moving around because it not like we are big one, big city. It's like a, a small country, so people still have to move a lot to go to Amita, but when we started doing it on a regular basis online, I think it was good for the group.

So, but it's not that obvious to engage the people. You need to still give them an opportunity to react back and not just listen and then ask questions to a forum or something like that. So for larger groups, don't think it's that obvious. I think it is. Meetups and stuff like that can still benefit and build up a group like that.

That's my experience. 

**Claire:** Yep. What about you, virtual versus in person? 

**Boriss:** I think an in person conference has value that an online conference cannot ever have. I mean, a virtual conference of course, is going to have some value. But the ability to network live in person with people and not live, I mean, physically it is not replaced somewhere, so.

Okay. Personally, I've never felt motivated enough to do an online talk.

I was going to stop actually, but then Claire convinced me and forced them. That was a good idea. So thank you for that. So that was that was a cytocon. Now I'm glad that you have still this past two cycle and to continue because it means there are going to be other events. Yeah. I think that 

**Claire:** I guess I'm curious, like you haven't wanted to do a virtual conference presentation El Vado, but Boice, you just did one and your recording is gonna go live, and I expect that you will have thousands of views of that recording ultimately, right.

If you promote it, if you share it. Right. Obviously it all depends. And apparently on YouTube, the first 24 hours matters a lot, right. To the YouTube algorithms. But so, so what's your take bodies on, like, is there a place for both when you think about conferences? 

**Boriss:** Yes. My, I think it's, it is possible to have both the thing is that it's difficult is to follow because when we go to a conference, we, our colleagues, they know that we are not available.

But when you do it online, you have to jump from one meeting to the other and then try to follow one presentation. Sometimes you even have time only to give your own presentation and that's it. Yeah, that's a little bit difficult. In terms of getting time for the conference itself 

**Claire:** yeah, I actually find that same problem whenever there's a conference in my area, like when I haven't had to travel to an in-person conference and it's in San Francisco.

It's easy to get sucked back into the office. Back, you know, pre covid when I had an office, so, okay. 

**Boriss:** I think room for both, but the live presenta, the online presentation should be limited to half an hour. I think one hour is difficult to watch recordings. That's a good point. Yeah, I think 

**Pino:** that's, that's a good point.

**Claire:** Yeah, I think that's fair. Okay. One last question before we leave today. Do you remember the first Postgres conference talk you gave? I'm just curious. Bodies. 

**Boriss:** I don't think I gave the, I remember the first talk that I gave in the post risk community, which was a liking talk in t That was fun. But the first post question, probably I give it in the RESCO community, I don't remember.

But my first very first talk, it was in 1999. That one I remember it really, really well. It was with Philippe Hoffa, another friend of us. Yes. Yeah. Okay. 

**Claire:** Also should Lightning Talks are a really good way to get started. Yes, 

**Boriss:** I think. Yeah. But lightning talks have the problem that you have to be extremely funny or something.

Cause it is so easy to get next to somebody who was really funny and then present some something boring that is 

**Pino:** yeah. Anyway. I hear you. 

**Boriss:** Anyway. I was going to say, my first posts talk was in year 2000. At the event at the Linux event in Chile and Linux, the second one. And my first International Postgres conference was in Mexico in 2004.

Wow. Yeah. 

**Pino:** Yeah. 

**Claire:** All right. So you've been teaching people about Postgres for a while. Oh, yes. Fair to say. All right. Well, RO and Boiz, thank you on behalf of both Pino and myself for joining us today and exploring this. I think that, you know, I guess my question to you, going back to the first topic or the first question of the day, why giving talks at Postgres conferences matters is would you encourage people who have never given a Postgres talk, whether it's a user talk or developer talk at a Postgres conference, would you encourage them to submit?

Should they do it? Absolutely. 

**Boriss:** Is it worth it? Yeah, absolutely. Yeah. Coming from an introvert and an extrovert, both, we say immediately. Absolutely. Yeah. 

**Claire:** Even if it's a little bit scary. So as, as 

**Boriss:** definitely intimidating as an introvert, I can say that it is definitely worth overcoming the fear and doing it.

It is a challenge. It is difficult, but the benefit is enormous. Can you, in my 

**Pino:** case, sorry, but just quickly, can new presenters get help from, from the community? Can from help 

**Boriss:** if, if you want to give a talk and then you don't know how to, I offer my help. I mean, contact me. I can, I help all the peoples already.

But we don't have any, we, we should have a group kind of like help speakers. Would that be something? Right? Why not? Coaches talk. I don't know. I mean that sounds a little bit pretentious, but if somebody wants some feedback, I can always help. I'm open to to doing that. A lot 

**Claire:** of, a lot of times members of the talk selection committee sometimes are willing to answer questions as well and give feedback before people even submit their C F P proposals.

So I don't know if everybody does that. I know I have done that and I know other folks have as well. Because, you know, there are some basic tactics in terms of your C F P submission, like filling in the additional information section with, you know, your experience and what you're gonna do to prepare and practice, particularly if you're a first time speaker, like there are things you can do to make your submission stronger and to make it more likely to be accepted.

So I think there's lots of help out there. You just have to ask for it. All right, bud. Thank you so much for joining us today. Episode three. This episode has been recorded and it will be published on YouTube initially. Will drop the link in the thread and then it will also probably ultimately be published on other podcast platforms too.

**Boriss:** So thanks for the invitation. It's been really a pleasure. Yeah. Thank you, Claire. Thank you. Pinot High five boys. Thank you both so much. 

**Claire:** Yes. Yeah. Virtual high five here. Yeah. All right, and thanks to everybody on the chat as well,

cia.

