# Why giving talks at Postgres conferences matters

**Pino:** Welcome everyone. We're here to talk about why giving talks at Postgres conferences matters. This is Path to Scon, episode three. Our producers are Carol Smith and Erin wlan. I'm Pino DeCandia. And I'm Claire Giana. If you're attending live, we would like to remind you that you can join our text chat in the Ciis Con channel under the path to Ciis Con E zero three, thread in Discord.

Okay, so I'm, let's introduce our two guests. I'm honored to introduce Alvaro Herra. Alvaro has been a Postgres Committer since 2002 and works at E DB formerly second quadrant. Alfredo is a promoter of free and open source software in Chile in general, and he was the organizer of P G A Chile in 2019.

Hi, Alro. 

**Alvaro:** Hello. I'm honored to be here. 

**Pino:** Well, really glad to have 

**Claire:** you. And before we go too far into jumping into a discussion, I also wanna introduce Bo. Hi. Who is a senior solution architect at edb. He volunteers and organizes conferences in Europe and coordinates the Postgres user group in Belgium. More recently, Boris was a speaker at Scon, an event for Postgres, which happened just a couple of weeks ago now.

And his talk was called Postgres, storytelling Support in the Darkest Hour, which I highly recommend people watch. Obviously I'm a big fan of many of the talks that the incredible cast of speakers gave at Satcon. But there was something very unique about Bois's storytelling talk. And I think it's a super interesting way to teach people and I hope we, we unpack it a little bit and explore how that came about.

Welcome, 

**Boriss:** Boris. Thank you very much, Claire, and thanks for the invitation. Super happy to be here, especially sharing with Alvaro. Once at this stages we, we've been friends for. For a very long time and things last century actually. And super happy to, to be with him. 

**Claire:** Yeah. Well, the, the two of you went, the two of you went to grad school together, right?

Yes. In Chile? 

**Boriss:** Yeah, in university, in Chi, in Chile. In Santiago, yeah. 

**Claire:** Okay. And is that when you both began your careers in Postgres? Yes. Yeah. Actually, 

**Boriss:** yeah, go ahead. We had a, a summer project and Alro was in charge of doing all the, the background part. And he, he decided to use Postgres after a, a very serious analysis of what was, was available at the time.

2001 was this, and then he needed a, a front-end developer, so he contacted me and then we started to work together. So that was my first project with the Postgres as well. And actually it's, it's, it's good to see, because we were discussing a few weeks ago that one of the founders of that company at the time, there were like four people only.

He was like celebrating like 22 years in the company. So we said, oh, wow. It's been a long time since, since that project that we did together at that time. Yeah. Yeah. I wanna continue working with Postgres immediately after that. So I, I decided to go in a different path. I went to academia and did some research, but also related to, to databases anyway, so.

**Claire:** Okay. And then eventually you came back to 

**Boriss:** Postgres? Absolutely, yeah. Yeah. Once I was doing the PhD, I started to do some research on, on implementations of two face commit actually. And at that time I, I read the code of Postgres and said, wow, I should be doing this stuff again. I, it's, it's really robust software.

And, and then, and then I started to work again with Postgres. Yep. 

**Claire:** So before we dive into the high level question that we're here to talk about today, which is why giving talks at Postgres Conferences matters, or frankly, you could insert any Open Source conference, open source developer conference there.

I actually do wanna unpack your site con talk for just a second. Postgres storytelling support in the, the Darkest Hour. And I, I'm curious, Al Alvar, did you get a chance to watch that yet? I know the recording is available as part of the live stream, but it hasn't been published yet. Not till next Monday as an individual talks, so maybe you have not yet seen it.

I have not. I'm sorry. Okay. But other, so I have, oh, go ahead. Yeah, 

**Boriss:** but this is Monica Devi stories. You know, Monica, right? Oh, right, yeah. I've seen that one as some one talk of those. 

**Claire:** So, so first of all, shout out to the artist. So for people, for people in the audience who are not familiar with what I'm talking about in, in this talk, instead of trying to teach technical concepts with the traditional techniques that we use, like demos and code blocks and screenshots of that, show people not just tell people what to do, tell people how to solve a problem, but show them how to solve a problem.

What Boice did is he did a storytelling technique. Maybe somebody can drop the, the link to the, that bookmark place in the live stream so people can go watch it later if they want. But he, he used illustrations that were absolutely drop dead gorgeous, and walked us through the story of this.

She's not a real person. Is she Monica, d b a 

**Boriss:** I. I'll keep that information without disclosing anything, so, okay. I prefer so. She 

**Claire:** may or may not, she may or may not be a real person. I, the reason I thought that is the last name is D B A, which I thought was a, a made up name because it sounds like D b A, the, the, yeah.

So anyway, and, and it talks through the problems that she's having with her system in the dark of the night after everybody has left the office and something's going wrong. And it's, I think it's the transaction id wraparound problem that she's struggling with. And it, it's just super cool to, to learn by, by storytelling.

So, and I'd like to chime in. Most people 

**Pino:** do that. I'll just chime in and say, I watched the talk last week and I, and I really loved it. The the live stream was during EU hours and, and too late for me, so I watched the recording. But it occurred to me both that it was a great change in pace in terms of how we watch technical content, especially if you're watching many, many com excuse me, presentations in a row.

And so it engages, engages you differently. Storytelling. The storytelling technique is really great. Bo I really liked your pacing in it. And then the story's engaging, you know Monica goes to get to the pub to have beer with, with, with her colleague. And then, and they discuss transaction IDs and, and the wraparound problem.

And then Monica ends up having to debug that having to, to deal with problems related to transac, to monitoring and and preventing transaction Id wraparound the next day and I thought I cap was captivating. So immediately I was wondering, wow, you've done, have you done this before? What made you think of that?

Where'd you get that that idea? 

**Boriss:** Well, thank you for, for the feedback. I mean, this is one of the things that I was. Wanted to have feedback on this type of presenting material because it is still new to me. This is the third presentation that I give in this format. The first two were also online talks.

And I was thinking like, I mean, in the time of the pand, we were all doing kind of webinars, let's say webinars and, and, and online conferences. And we would try to emulate a real in-person conference, and it was super tiring and it was difficult to get feedback from the people because you don't see the audience.

So it's completely different stuff. And then I saying, okay, if I'm going to do something online, I should probably do something that I cannot do in person. So to really have an added value of doing it online. Otherwise we're just emulating what we want to do in person. And then I said, okay, what, what, what are the ideas that I have that could work in this?

And I was having this idea for a long time to tell stories. And actually came after I read a book the Phoenix Project that I thought was really good in terms of storytelling about called C I C D techniques. And I wanted to do something like that for, for Postgres. And then it came out, the idea with Monica db.

I remember I was in Milan and I was talking with my colleagues for, from support and Anna, they, they're super good. And I said, okay, maybe, maybe this should be something that that I could tell people. Like, I mean, what is the work of support? Because I've, I've done support as well. And, and that's how I came into it.

Now, I discover also there is this book A Curious Moon, which that's kind of the same. And I would really like to get to that level. I mean, try to write stories. I mean, not just giving a presentation but kind of put it in the format that people can read about it. And luckily I have the, the, the log to, to work with With Scarlet Riggs.

She's as, as Claire was saying, she's an incredible talented illustrator. And I remember that I, I didn't give a description of Monica to her. I, she asked me to describe her. I said, well, I don't know. I mean, I will tell you her personality and the things that she does and all these kind of things.

And she came up with the drawings that, that I thought that were really, really amazing. And then every time I have a new idea for a talk, I, I discuss a little bit with her and she understands immediately the technical part. And then she makes the illustration super nice. The previous one was about idling transaction, and this is when she came up with the elephant inside an hourglass.

She's super cool. So I really, I really like, I mean, I, I'm, I'm lucky to, to work with talented people as well. So that's how, this is what Monica, the BA is. Is about, and yeah, get, you, get, you get some, some feedback from people. So, so maybe I will do more of those. Yeah. You, 

**Claire:** you could argue that you can tell a good story without beautiful, magical illustrations, right?

Because your voice and the words you choose and even the, the pauses in your story can entrench people. But having that, those magical illustrations by Scarlet Riggs really added like a whole nother level. And I mean, there's no reason learning can't be fun, and you made it, I think, more fun. So I appreciated it.

Oh, thanks. All right. And then I just wanna shout out the book that you mentioned, A Curious Moon. Hopefully I, I can drop a link in later and maybe Aaron can now. I think that Rob Connery is the author of that and he is not on my direct team here at Microsoft, but he does, he does work in the cloud dev, dev advocacy group here at Microsoft, and I'm a big fan of that book as well.

It's pretty awesome. Okay, I agree. So we're here to talk about why giving talks at Postgres conferences matters. A Aldo, why don't, why don't we start with you? I would love to kind of hear your, your high level answer to that question. 

**Boriss:** Well, I think the main reason is that giving talks gives us the opportunity to grow the Post Christ community.

And growing the Postgres user community means we also grow the Postgres development community both directly because some of those users become eventually developers and also indirectly because those users as they interact with the software, provide very useful feedback for what should we do next and how to evolve the software in a way that serves everybody.

So these talks, so I, I think the, to. Sorts of conferences that are slightly different. We have Posts conference proper where posts users come and, and learn about things. And there's also the conferences of other types, like gen general open source conferences, or I dunno container conferences or database conferences where we expand the world of posts to people who don't currently use posts.

So the type of talk that we give to either of those substances gives different benefits to the Postgres community. So as we grow the, the, the community to new users, obviously we gain the input of people who has, who is working from up for up. Without their databases. And those have different ideas of how a database should work.

So that's another thing we get, 

**Claire:** have you, have you ever had trouble, like prioritizing the time that it takes? I mean, these conference talks don't just happen. They take a lot of work behind the scenes to conceptualize 'em, create 'em, practice 'em. Right. And then travel sometimes when it's in person to deliver them.

Is it, is it hard to make it a priority for you or 

**Pino:** not? Well I, 

**Boriss:** I have a family, so I have limited how, how to say that a limited amount of. Time that I give for conferences. I don't like to travel more than say, two or three times per year. So that limits how many talks I'm willing to give.

And of course, the preparation, the time for, to prepare for each conference is I know is 

**Pino:** high. 

**Boriss:** I, I don't like doing talks where I spend just a little to prepare slides and, and, and material. So to be honest, I don't limit myself. I just do as much as needed. And because I don't do many, then that that is what becomes the limit.

Got it. Oh, lemme come back. Oh, sorry. Sorry. I'm sorry. One last point. One last point is that I don't repeat talks. Some people will give the, give the same talks over and over. So that means you, you only have to spend the time to prepare the talk once and then give it me times. I, for some reason, I don't like to do that.

So that also also becomes summate a limit. Okay. Pino, 

**Pino:** I was gonna come back to, to your point Vera, about different communities that you give talks to. You're thinking about the audience and it needs a different approach. How do you go through that process and, and do you set a goal for not just what the, what the audience will take away, but what you'll take away given that the audience, especially in the case where the audience isn't, may maybe not familiar, as familiar with Postgres?

**Boriss:** I don't think so. I mean in my first presentations many years ago, I just tried to present what the, the, the topic at hand without thinking too much about. What the audience was going to get. Then at some point I realized that that was a waste of their time and my time because they, they, many people were listening to a talk and weren't getting too much value.

So I realized that I had to think very carefully about what value would I, would the audience get from my talk. And that means I, my approach to the talk becomes completely different, different depending on whether the audience is technical guys developers or decision makers. So that, that comes by direct experience because I gave a very deep talk about left sorry, outer joints to a bunch of company CTOs.

And that was a complete failure. But I do not think about what I am getting from the talk. 

**Claire:** So I think that's a really good point that, that learning of focusing on the audience and what they need and where they're coming from and having empathy for you know, the fact that they're probably not as expert as you or don't know what you know is, is super important.

And oh, you've, you've said so many things. I mean, there's also the notion of failure. Every good conference speaker has a couple of failed conference presentations in their background, right? Like you, it's just absolutely naturally you gotta be willing to fail. Okay, so we've got a bunch of things we need to circle back on that a veto has touched on here, but I wanna.

Cut over to Boice for a second and ask you the high level question. Why do you think giving talks at Postgres conferences matters or frankly, any open source developer conference? Why, why spend the time? 

**Boriss:** Yeah. First of all, I don't think it's part of our, any of our job description, neither for Alor or for myself.

So that's why Alvarez was mentioning his limited time with the family because he has done the extra time apart from all the job that he, he does. And then it's not my, my description of work either. I think we need to do a little bit of a. Advocating, but it's not real. Like you have to give up that many talks per year.

No, we, we do as many as, as we can, and it is important in the sense that, for instance, Alvaro, the fact that he's a core developer, it gives the community the sense that the core developers are close to the people that are using the software. It's not just about we release the software that we are developing in our, in our home, and, and then you use it or you, you will, no, Alberta does it because he wants to hear how people is using the software.

And, and, and I think that's super important because, I mean, for many other software that we use, we never know who is developing that stuff. And the fact that you go to Postgres conferences and you meet the core developers, if you go to Foster Themm, you meet plenty of core developers. It's super nice. So that's, that's a, that's very important that in conferences you can meet the, the real workers of the, of the software itself, so it builds the community.

That's one thing. In my case that I don't develop Postgres, but I do work a lot with project with customers that are using Postgres. It is a way of extracting all those different cases that we see that people have troubled with or have had some patterns of solving things, and then present them to the broader community and say like, look, if you have this type of problem, then this is one way of solving it.

And, and it enhances the, the, the entire knowledge of the entire community. And, and for instance, getting back to, to other communities, when, when you, you were saying Claire, that this is not about post any open source project. I remember that when I was working with Alfresco, which is a kind of commercial open source stuff, and they were stopping the developers conferences, the community itself organized and we created the order of the b.

With the intention that we wanted to share the knowledge between us. So sharing knowledge is something that comes automatically with people that works in open source and free software, because that's one part of the core values of having open source, that you can learn things and share that knowledge with all the people.

So there's lots of things. I mean, my, my case is also to, to abstract patterns and understanding how things are being solved for, for, for many people and get feedback about whether that's, there are better ways of solving the same problem or not. Yeah. I do repeat talks, by the way. I don't have the same approach as algorithm, but I, it is never, never exactly the same talk.

Like, I mean, they talk about table partitioning. I think I've given it like three times and it's it's always different. I, I localize it a little bit depending on the conference that I'm giving and I, I get feedback from people and I try to improve that and the next time they give the talk, 

**Claire:** yeah. I, I actually do the same thing.

I will give the same talk again, but I improve it each time. I try to incorporate the feedback I got from the previous version. And I don't know Alvaro if you disagree, but you know, some of the smaller Postgres conferences, like a lot of the p pg days, for example, they don't videotape or record the conference, so it's only valuable to the 200 people who were in the room.

And so I find giving it again, makes that knowledge more accessible to more people. It basically shares it more broadly. Now, if it's been videotaped and it's a high quality video recording, then you could argue it would make more sense for me to create a new talk. And so sometimes I do. Yeah, 

**Pino:** I, I agree. 

**Boriss:** I I'm not saying that it is valueless.

I'm just saying that I don't feel comfortable doing it. Maybe it, it, it's I should be doing. The way both of you described, which is to improve the talk and give it again, because then eventually a very good quality version of the talk becomes videotaped and then that is valuable for the whole 

**Pino:** world.

It seems to be, there's something interesting about the roles each of you play as, as, as a committer Aldo, perhaps your time is best spent talking about different topics that you can go very deep on. And then others can that, that are trying to focus more on sharing knowledge and propagating the knowledge.

Can repeat, can repeat talks because there's always a more audience that didn't get a chance to watch it previously. And, and it's always more fun to watch live, or it's often more fun to watch live. Mm. 

**Boriss:** I hadn't thought about giving talks. To other speakers rather than directly to users. So lately I've been finding I've, I've had a hard, a hard time finding good topics to speak about.

Cause my work is normally stuff that is down deep into the bowels of the, of the system. So I think, well, who cares about this? So I don't give talks about that. Maybe that's a mistake. I dunno. I can, I can give you plenty of ideas. We talk. 

**Claire:** Can you throw out some ideas right now? Bo can I put you on the spot?

**Boriss:** Ah, right now, I mean, well there are plenty of stuff of the, of the improvements in, in vacuum, for instance, all the parameters to explain what the parameters do actually. And in each release there's one thing that is added or something like that. That was one thing. Other things are like parallel executions and those kind of things.

Well, you also know a lot about the brain index, which you have talked already about the brain index, but maybe Right. Explain some, some use case because it's still, people don't, don't use it enough. I think So those are at least three topics that you could be talking about. Yeah. Right. But you see brain indexes were done in version 9.5, so that was like 10 years ago about six years ago.

So at this point, who cares? Right? That, that's, I mean, that's my, that that's what I'm thinking about. Yeah. That's, that's your point of view. Exactly. Yeah. No, but I mean, for instance, I, I, I even sometimes watch the same talk twice because I discovered something different the second time that I, that I watched the talk.

And that's for me something that I mean, or, or because just, just the talk is fun. Right. That could also be another reason to watch the talk for the second time. Yep. 

**Claire:** I think the other thing to keep in mind too is even features that are in maybe new to Postgres 10, for example, or 9.2, and in the case of Bryn indexes, like the user may not be familiar with them yet.

Like they may not have been around, they may not have been using Postgres. Right. You know, back then. And so what's, what's old to you can be new to your audience. Yeah. 

**Pino:** I, I, I'm 

**Boriss:** glad we're having these conversations because I'm discovering also so many things that I am wrong about. 

**Claire:** No, no, no, no, no. We are not here to tell you you were wrong.

Oh my goodness. No. Uhoh 

**Pino:** we're 

**Boriss:** gonna give bad reputation. No, it's just about repeating the topic. For instance I saw Claire's talk about how to make posts and, and make your, your, your communication like more visible to people in, in Berlin. And then I saw it again in Stom in Brussels. And the second time that I saw it, I said like, oh.

I didn't realize that this was also in the presentation. It was something that I discovered the second time that I watched the talk. So I think it's impossible to get the, the entire talk. Like once when you see it, the second time that you see it, you learn something. It's like watching a movie again. I don't know, not all the movies are worse, watching twice, of course.

But some of them it's like, ah, I didn't realize this. 

**Claire:** Oh my gosh. So you're telling me my talk was worth watching twice? 

**Boriss:** Well, yeah, it, it, it was absolutely. 

**Pino:** Yeah. I'll also add that I think people are doing interesting things with, with, with recordings. We have so many recordings now, so much content.

Of course, new content is always very welcome. And again, people appreciate live attending live. But what I've started doing with folks on my team is we watch recorded talks together because there'll always be someone who knows a little bit more about the topic. And if we, we can stop the video.

Take questions. Started again. So the recorded talks definitely are huge value. Of course, people have always been listening to them. You can see the watch, your watch count increases, you know, in whatever platform. But, but, but we can, we can reinject a little bit of a live show experience by watching together.

**Claire:** So wait, you watch together all in the same room, or? I, I know the answer to that is no, because your team is distributed, right? You're all in different places. 

**Pino:** That's right. So I, I'm sure other other platforms have the same feature, but on, on Microsoft teams, we can share the video in the meeting and that way we're all listening to the same audio at the same time.

And and that creates a great experience. So, and, and I can share controls so that anyone it's a, you know, we usually this in a small group, and so anyone can stop the video and say, excuse me for a second. I just didn't understand that part. Does anyone know what that meant? Huh? Nice. And it creates a nice interaction.

**Claire:** I know Discord supports that as well. I've been on the general stage here with Aaron and we popped up something from YouTube and we were watching it together at one point. So it's, it's a nice capability to have multiple people watching. 

**Pino:** Could I ask a question? I want to come back to something that Bodhi said about the importance of sharing knowledge for a an open source community and.

And Alberto touched on this as well the aspect of how much knowledge sharing do you need? And it seems like there's always so much to do, whether it's development tasks reviewing other folks code our own projects, whatever that that work is. And then knowledge sharing. Blogs, presentations.

Do you have a sense of how you can ca how you calibrate that? And not just at a personal level, but do you have a sense of whether you take into account the Postgres community needs more of the Postgres community needs to do more of this, and perhaps there was a time when it wasn't and now it is. Or how much does that influence your participation and how much you ask others to participate in this way?

And I, I didn't, either one of you, Alad or Bo.

**Boriss:** Oh, well in my case, I mean, I try to kind of pay attention to the questions that are being asked by the customers. And when I do training, I also try to get the, the, the questions that are come over and over and I say, okay, maybe this is something that was talking in a conference, the kind of explain this like a, a broader audience.

And that's how I try to identify topics for, for giving talks that the needs come from, from there, from what I see on the fields. If I want to, if you want to say like like that. So yeah. Experience with, with users mostly. Yeah. That would be my way of trying to identify which kind of knowledge have to be shared.

But for instance, last, last, last episode, you were discussing about people having trouble with host-based authentication. I thought that was, that that problem was already solved like many years ago. But now I realize that some people are using all the databases just because they cannot get around this host-based authentication.

But then giving a talk about that, it's kind of difficult because no call for papers committee is going to accept a talk on host based authentication, but that means that we can do kind of a juju video or, or something different to explain that again, because people are still having troubles with that.

So I think, I mean, the need for, for knowledge sharing comes from trying to listen to what people are asking about and, and then go there. Yeah. That, that's how I do it. Mm, right. So when I was working for Second Quadrant, I mean before the acquisition, I had plenty of involvement with customers. In, in like for professional services like, like Boris.

And that was a very productive mechanism to know what, what features, what Postgres features to work on. Nowadays, I don't do that too much anymore. So I kind of feel like I've lost a bit touch with that. I still get that from the community mailing list and that once a feature is done, of course I can make conference talk about the, the new feature.

But my current professional work with Postgres at EDB seems to relate more to fixing bug and. Those, I don't think give too, too many conference interesting conference top topics as much as new features or future 

**Pino:** expansions. 

**Claire:** I feel like you can go either way. I, I, I, when I try to have empathy for people in the audience, obviously they wanna know and understand how to use the new things, the new features.

So that's obvious, like content for future conference talks. But there are also pain points or things that are complicated that maybe they don't fully understand yet. And that also gives fodder and that, that goes back to what Bodice was saying a few minutes ago about, you know, listening to whether it's users or people in customer support.

Right? The inspiration for Monica Deia. Like, what, what are those trouble spots? What are those pain points? Where do people get stuck? And then of course there's also getting started, like anybody new, you know, they're starting from a blank sheet of paper, or maybe they're starting from knowledge of another database, right?

And so they've got a whole bunch of things they need to learn. And so those introductory talks, I feel like are always useful. What, what else? So new features, pain points, getting started. Are there other obvious categories of useful talk content out there? 

**Boriss:** Well, obviously how to become a Postgres hacker is very good talk.

Yes. And how to view patches and stuff like that. Yeah, I, I am thinking about stuff that revolves around Postgres development rather than Postgres usage.

Yeah. Yeah, exactly. And, and I gave, for instance, a talk in, which is the other spectrum. I think we, we, we compliment each other a lot. Albert, the, in Nordic PD day, I gave a talk about Jason usage and what I did is I went to Stack Overflow and I searched for the top 10 questions and I answered those questions and in the talk, but I didn't go like one question after the other.

So again, I tried to build up a use case and within the use case I was answering the questions and of course talking about metal music which is one of my favorite topics. So it's, I tried to mix Jason sounds like really metal stuff. I sounds like a killer character in a movie or hears. Come Jason.

**Claire:** I know that one of my teammates gave a talk at pg Comfy u about going back to what Alvaro was saying about how to become a Postgres hacker, and it was him sharing his story about the first six months of becoming a Postgres hacker. And, and then he gave that talk again at PG Day Paris a few months later.

So and that's kind of another category of like, not quite today I learned, but you know, what I learned as I was doing X for the first time. And I think people always appreciate those as well, right? Because a lot of people, whether they're expert or beginners, have empathy for those kind of, you know, first experiences and sharing their observations.

As a newcomer, 

**Boriss:** That was a very good joke. I saw it also in PDay, Paris. I was there. Yeah. Very interesting 

**Claire:** stuff. Oh, I wish I was there. Other, other categories of really useful Postgres conference docs. We've got pain points, new features, how to get started, how to become a Postgres hacker. How to create Postgres patches.

**Boriss:** Something that I would like to see a little bit more, and I cannot do it personally. It's like people having their experience with Postgres, like people who are not working with Postgres as the main thing, but they are doing something else and they use Postgres. Even, even just sharing their, their, their failure.

That could be also something very interesting. Like we try to implement logical replication, but we fail on this, this and that. Please help us to understand why that will be a very useful tool. Maybe meetups will be a better place instead of conferences. I'm, I'm not thinking about what I would like to see.

I'm just thinking about what the call for papers committee is going to accept, because the, but I would like to see that in a conference, like use cases, we try it and we failed or we tried and we were successful, but we still need to do these other steps. So people just using Postgres, I'm just saying like we implemented, I don't know how.

Pharmacy software, and this is how we use Postgres. I really would love to see that. More, more of that. Oh, I definitely agree that use use success stories are a good topic because it shows other users that Postgres can really do do whatever.

**Claire:** There was a talk at fom PG day, I'm looking up the schedule right now. It was Nick's talk. Remind me what the top the title was. I'm trying to look it up. Oh. L F M F How to create index concurrently led to a six hour downtime and it was by Nick Bluth. And what does L F M F stand for? 

**Boriss:** I have no idea, but the story was super good.

I saw it in, in Nor PD Day as well. 

**Pino:** Probably something about laughing 

**Claire:** a lot. Okay. I, I think it was failure. I think one of those f stands for failure. So, and I do think failure stories are really appealing. I mean, some people don't like to share them because it makes them feel vulnerable or like they might be judged.

But when you, when you kind of are willing to be vulnerable in that way, people can learn a lot from your failure story. And it's actually quite a generous gift Right. To, to share it. And there was a lot of laughter actually in the room. Yeah. During that presentation. Yeah. As you, cuz you could kind of feel his pain as he was reliving it.

So I. As I scribble notes here, Boris, I took your suggestion just now to people having their experience using Postgres as one category, but then failure sharing your failures tried to do this and it didn't work as another category that's super useful too. So 

**Pino:** L 

**Boriss:** F M F means learn from my failure, right?

Oh, 

**Claire:** okay. Cool. Oh, 

**Boriss:** okay. Yeah, right now. I know. No. So the first two times that I gave Monica the B talk, I was doing kind of an audiobook. So I, I wrote the script and I read the script. That was it. Yeah. To recorded it. But then you convinced me to do it, like like talking to somebody and I was saying like, you know, I cannot do this.

I cannot do this. And then I saw Nick doing this in Nordic P Day. Oh. And he was really doing storytelling live and said, wow. And I was wondering like, how, how this, this happen to him. And then I was wondering, while he was presenting this stuff, I said, oh, wow, maybe I can do this for, for Site Con. So yeah, thank you Nick, for, for giving that presentation because it convinced me that your idea Claire, was very good.

And, and that's how I, I managed to present it in the way I did in Cytocon. Otherwise I was just going to, to try to do the scripted thing again. But I think this one works really well. It's a very good, yeah. Yeah. 

**Pino:** I really liked. Oh, sorry Claire, go ahead. 

**Claire:** I was just gonna say I really liked on the cis con recording being able to see your face as you were telling the story.

And you told me that the inspiration for the storytelling technique was that your daughters had been growing older and you had all these fond memories of reading them stories, right. Telling them stories as a dad, and you thought, well, maybe I can do this with Postgres to other people now. And so just like when you're reading a story to somebody else, a young child in your family, they can see your face and that's part of it.

It's not just your voice. So I was really happy that you did both, right? 

**Pino:** Yeah. Yeah. 

**Boriss:** Thanks for the suggestion. That was good. 

**Pino:** I was gonna ask, since we're talking about getting ideas from other speakers who are your favorite speakers on the circuit and why? In Postgres in 

particular? 

**Boriss:** No, I do have a favorite one.

So I was making, so somebody asked me this before and said, okay, there are plenty of names that are very good. And I said, well, if I have the top 10 speakers in a conference and they're all presenting at the same time, which one will be the one that I don't want to miss? And that for me is Thomas vra.

He is such a good speaker because he's so, is the same level of knowledge as Alvaro, and, and he adds a little bit of more jokes. And this is what I, what I really like because his jokes are so dry that he, he comes up with, with this kind of things like make you think a lot with with his presentations.

Every time that I see one of his talks, he's like, well, I need to, I need to check this stuff when I get back home and I need to see these slides again and then try all this stuff. And, and he doesn't. Overdo it in terms of trying to be funny. No, he, he just is Thomas presenting and then he's, he's super dry and, and, and I really enjoy watching him.

It's that's, that's this speaker that I never want to miss. If he's in a lineup for presentation, I want to see his stocks. That's yeah, because it's a very good combination of knowledge and then bringing it in a, in, in a, in a funny way as well. 

**Pino:** Yeah. And I guess humor is an important part. I mean, not, not all speakers Absolutely.

Try to get humor in, in their presentation. Yeah. And Boris 

**Boriss:** has a very, very good sense of humor, and that absolutely leads to the audience being very engaged with the, with the topic of the dog, whatever 

**Pino:** it's, are 

**Claire:** you sure? Aldo Alda, are you just being nice because you've known him for a long time? No, not at all.

I mean, is bodice really that funny? 

**Pino:** To me, I, 

**Boriss:** I definitely enjoy his talks very much. I also, oh my God, 

**Pino:** you thought I was 

**Claire:** serious. I'm sorry. Of course. What is funny, thanks. 

**Boriss:** Yeah. No, but I, I, I've learned that humor is like salt to, to food. I mean, it enhances your, the taste of your food. Right. But you can have a, a plate, just salt, right?

You need to have a content. Yeah. I, I learned also this by watching all the talks like how to add humor. I, I, I, I watch a lot of talks about how to give talks, and one of this was about I think it's a Ted Talk or TEDx about adding humor to your talks. And the guy explained it very well. I said like, ah, yeah, okay.

That's, that's how it works. If you add too much, it's going to be too salty, and then you mess up with the content. So you ha it's difficult to get that balance as so that's on one end, 

**Pino:** but what about the other end? I mean, I, I, I would imagine that some people don't think that humor is accessible to them.

They might be willing to give a talk because they feel competent about the subject, but they might not feel co co comfortable with, with humor. Do you think it's, it's, it's for anyone to add humor to their talks or it takes a certain kind of personality? Can I 

**Boriss:** answer that one? I definitely think not.

Cause I don't have the sense of humor that is needed to make jokes on stage, so I don't even try 

**Pino:** my talks are, 

**Boriss:** I would say, pretty much humor or less. And I'm sorry for that, but I really don't know how to do that. So 

**Pino:** do you, do you substitute with something else, Al Alberto? If, if humor is not your go-to is there something else that you focus on to keep the audience engaged?

I just try 

**Boriss:** to, I think one thing is trying to make the examples. For example, if I am presenting a, a post feature, I try to make the, the command examples something that is a little bit alluring so that people are not bored by me talking about select full from bar, which means nothing. But I dunno, constructing something that keeps people interested, if I can add some pictures about the thing that's even better.

But I think the knowledge that Oliver has is also authority. I mean, everybody knows that Oliver knows what he's talking about. So, so you have more confidence into listen to what, what he's saying and, and, and you know that you can ask any questions and he's going to answer you. Correctly, unless he doesn't know and then he's going to sell, tell you, I don't know.

Right. And then it's like, okay, 

**Claire:** it's important. Yeah. That it's for speakers to know that it's okay not to know. And it's really important to say, I don't know. Right. I mean, that, that gives you authority. I actually wanna shine a light on something that Alvaro just said, which is using interesting things in your examples.

I don't know if any of you remember the talk that Louise gave at PG Con, probably back in Milan. So what is that? Pre covid? And she might have given a similar talk at a Django Con conference. And she used like pop music stars in her data model and in her examples. And it made it just so much more interesting than if it was F and bar, which as you said, are meaningless.

So I do think that's a way. To connect, to have those examples that kind of catch your attention. Another way to connect is just, I don't know, do you do this, Alvaro, do you ever ask your audience questions like, as part of the talk, like pause and stop and make it less of a lecture and more of a conversation, or even just ask, show of hands how many people have done X, y, Z with this news feature?

Yeah. Is that, is that a 

**Boriss:** Yeah, I think that's a good resource and I've done it a couple of times. I, I learned to do that only recently, so it's not very long in my story, but, but yeah. Yeah. Those are good resources, 

**Claire:** basically anything to keep people off their phones, right, right, right. Yeah. Cause it, it doesn't take that much of either boredom or not being able to follow.

And like, as soon as you can't follow the speaker, as soon as you're lost. Your brain is gonna try to find something else to think about. Right. And what's the closest thing? It's probably your phone on your lap. So anything you can do to kind of keep somebody paying attention. So, since, 

**Pino:** since we're talking, oh, I'm sorry, Claire didn't mean to cut you off.

No, you didn't. Go, go, go. Since, since we're on the topic of sort of how presenter's personality comes into play, I wanted to ask are you an introvert or extrovert and how does that affect how you prepare and how you give talks? Maybe Alvaro, could 

you 

**Boriss:** take this? Yeah. So I'm definitely an introvert and it I find it very hard to in a normal situation outside of, of a talk, to engage in a conversation with people.

So when I'm at a conference it is very useful to have given a talk so that people approach me and we can speak and about my topic, and then we will, I, I will ask, what are you working on? And then conversation go. So from, from there. So that's one thing I definitely like about giving talks, which is to let me connect.

Extroverts I think do not have this problem about connecting with people so they can go to a conference and connect with people without having given a talk. So for me it's, it's so, so for you. Yeah. Yeah. It's like your icebreaker. You give a talk as an icebreaker. Yeah. That's one way to, to, to see it.

And it's best if I can give the very first talk or, or a very early talk, so I have the rest of the time too. 

**Pino:** Connect. 

**Claire:** It really is a wonderful icebreaker. Not only does it give you something to talk about, but people will recognize you in the hallway, like you said, after you've given your talk, and they'll stop you and you'll continue to get feedback and meet new people and, and maybe feel a bit more welcome.

Even though you would've been welcome had you not been giving a talk, but you might not feel that way, you know? Right. Yeah. Boice, are you 

**Boriss:** an extrovert? I understand. I am. I mean, I, I never understood the question being an introvert or extrovert, because I, sometimes I look at what it is to be, and sometimes I keep things for myself, so maybe I'm introvert as well.

I don't know. But my, my my reason for giving talks is that also I learn a lot when I give talks. I, I have to prepare the talks a lot, and although I repeat some of the, the, the talks, I never repeat the same slide sets. So I try to, to To learn while I help other people to learn. And from the feedback that I get, is that because I can, I can make jokes and, and all this kinda stuff, I can keep the attention of the people.

And because I can keep the attention of the people I manage to pass some concept that could be either boring or, or complex and make it accessible to people. So when I understood this, like oh, my talks are really contributing to the knowledge sharing of the people. I kind of make it my own mission.

It's like, ah, I want to give more talks because I, I'm, I'm helping the community to learn about Postgres. And and I like it. I like it a lot. So because I learn and, and I know that people can learn from that. So that's very good. When I was in foster, I mean last time, Somebody asked. I was working withal Alberto, actually.

We were walking to the, to the room, to the posts room and somebody asked us, Hey, you guys know where is the post room? We gave them direction and then the guy look at me and say like, what are you giving a talk about Jason on, on YouTube? I said, well, yeah, yeah, could be me. Said, oh, yeah, yeah, it was you.

And then thanks to you. Now I, I use Jason also posters. Oh wow. That's super cool. So it kind of convinced me like, okay, I'm doing the right thing. And also I foster them. Somebody came to me and said like, ah, Boris your talk about table partitioning in Berlin, I used your slides to give the same talk to my colleagues in, in a couple.

I don't remember. It was a customer. So that's like a, kind of like making a song and somebody makes a cover of your song. Yeah. Cause they just pick up the slides. So that's, that's kind of a very huge compliment because my slides, they don't even have bullet points, so they're not very easy to just pick them up and reuse them.

It means that the guy was really paying attention to what I was saying in Berlin because he was able to just reduce the slides. So, so I, I think that's, that's my motivation. I mean, I, I'm now, I'm convinced that I, that I can contribute to knowledge that it increase the knowledge of the community, and that's why I like it.

Apparently this is one of the advantage of being extroverts, probably. Yeah. Do you feel that you get 

**Pino:** enough feedback as a, as a presenter, you're, you're making me think that you gave some great examples of feedback and, and it's enough to, to, to energize you and motivate you. And it reminded me that any, any open source developer community also often tells people just even if you don't have a bug to submit, but just let us know you're using the product.

Just you know, just say something, send us an email, and that that little feedback helps. How, how is it, as a presenter, do you feel you get enough 

**Boriss:** feedback at the moment? I think. Yes, I'm getting enough. It could be more. It could be more. And the good things is that people, for some reason, they are also able to tell me that was wrong, or Why didn't you talk about this?

So people also gimme constructive feedback. So that's also very positive. It can always be more, and I will appreciate a little bit more just to know, like, like I was doubting a lot about this Monica Dbr thing. I mean, is is it good or not? And then it's really good that, that one. Thank you. I wasn't getting enough feedback about that one because it's different.

So yeah, that one you need a little bit of help to improve it and all this kind of stuff. I think so, yeah. 

**Claire:** I think human, human nature. I think a lot of people, a lot of people like our parents mostly tried to teach us to not be selfish, but we're naturally selfish and there's only 24 hours in the day and we have a million things to do, right?

We've gotta pay the bills and cook the food and take care of family and, you know, we have our hobbies and work, sleep. I mean, you get it. And so there's a lot to do and it's hard to even make the one minute or two minutes it'll take to send someone a one-liner and pass that compliment along. I, I tried to compliment people as much as I can, and I don't think I do it enough.

I don't think I, I say thank you or I tell people, Hey, you did this thing and it helped me. And so, I don't know. I think we should all give each other feedback more, both positive and the constructive negative feedback too. That's my philosophy for the day. Yeah, 

**Boriss:** I, I agree. And given that Phil philosophy, I will publicly acknowledge then Alvaro, because of because of him, I'm, I'm into open source and free software.

I'm working with him in the beginning of my career in it was very, very important. So thank you, Alvaro, for all your knowledge. Transfer to me had my pleasure and always good time. Yeah. It's been, it's been a, a very nice long ride. Yeah, 

**Claire:** I remember being at Fadim, and I don't think it was 2020 right before Covid hit the year I gave up my first talk at Fadim, I think it was the year before 2019.

And Leticia Avro was there and she was really excited to be working on her very first patch to Postgres. Yeah. And I think you were her patch reviewer Alto. That's right. 

**Boriss:** We sat on a freezing beer, beer pub in Brussels, and we were going over her coat. But it was a nice I was, I, I was, I wasn't, I didn't think too much of it at the time, but I think it was well received from her.

Oh, 2017. Oh, 

**Claire:** really? Okay. Really. I know I, this is a long time ago. I just wanted to give you that shout out as well, like as a Postgres committer, it's not just your job to do development on Postgres and get it integrated, but you spent a lot of time reviewing other people's patches and other people's work, giving them feedback, helping shepherd it through the process.

And so you know, we all, we all owe Aden. Thanks for that because you know, it's not, it's not your name on those features but it wouldn't happen without you. So, yeah. Yeah, 

**Pino:** it's 

**Boriss:** been a very lucky ride for me, and I'm very grateful for the all the time that I've given Postgres and Postgres, the, the opportunities that's working on Postgres has 

**Pino:** given me.

I thought with a question, is it, is it too late for me to open up a quick, it could be quick. Yeah, go for it. I can run a few minutes open. I was, how, I was just reflecting on how, how nice it is to hear you all who have been in the Postgres community longer and you remember talks from different people like going, going way back and you've worked together in your case Alvaro and Boris for a very long time.

And it's, it's nice to hear that and it's all part of the community building. So folks that join Postgres, they find a community that's warm and welcoming and supportive. And so I wanted to ask Bo, I think it was bodies have touched on it earlier that during the pandemic conferences, in-person conferences were, were reduced so much and how did it affect the community?

Is it coming back or, or, or, or can we do that kind of community building through virtual events and remote events like we're doing now? Yeah. Maybe take that. In whatever direction in terms of like, you know, how how much do we struggle now? And because presentations are so much part of, and the conferences are so much part of community building.

**Boriss:** In the case of the user group in Belgium, it was an opportunity to start doing online conferences because it's always so difficult to find sponsors for doing in-person events and people moving around because it not like we are big one, big city. It's like a, a small country, so people still have to move a lot to, to go to Amita, but when we started doing it on a regular basis online, I think it was good for the group.

So, but, but it's not that obvious to engage the people. You need to still give them an opportunity to react back and not just listen and then ask questions to a forum or something like that. So for larger groups, don't think it's that obvious. I think it is. Meetups and stuff like that can, can still benefit and, and build up a group like that.

That's my experience. 

**Claire:** Yep. What about you, virtual versus in person? 

**Boriss:** I think an in person conference has value that an online conference cannot ever have. I, I mean, a virtual conference of course, is going to have some value. But the ability to network live in person with people and not live, I mean, physically it is not replaced somewhere, so.

Okay. Personally, I've, I've never felt motivated enough to do an online talk.

I was going to stop actually, but then Claire convinced me and forced them. That was a good idea. So thank you for that. So that was that was a cytocon. Now I'm, I'm glad that you have still this past two cycle and to continue because it means there are going to be other events. Yeah. I think that 

**Claire:** I, I guess I'm, I'm curious, like you haven't wanted to do a virtual conference presentation El Vado, but Boice, you just did one and your recording is gonna go live, and I expect that you will have thousands of views of that recording ultimately, right.

If you promote it, if you share it. Right. Obviously it all depends. And apparently on YouTube, the first 24 hours matters a lot, right. To the YouTube algorithms. But so, so what's your take bodies on, like, is there, is there a place for both when you think about conferences? 

**Boriss:** Yes. My, I think, I think it's, it is possible to have both the, the, the thing is that it's difficult is to follow because when we go to a conference, we, our colleagues, they know that we are not available.

But when you do it online, you have to jump from one meeting to the other and then try to follow one presentation. Sometimes you even have time only to give your own presentation and that's it. Yeah, that's a little bit difficult. In terms of getting time for the conference itself 

**Claire:** yeah, I actually find that same problem whenever there's a conference in my, in my area, like when I haven't had to travel to an in-person conference and it's in San Francisco.

It's easy to get sucked back into the office. Back, you know, pre covid when I had an office, so, okay. 

**Boriss:** I think room for both, but the live presenta, the online presentation should be limited to half an hour. I think one hour is difficult to watch recordings. That's a good point. Yeah, I think 

**Pino:** that's, that's a good point.

**Claire:** Yeah, I think that's fair. Okay. One last question before we leave today. Do you remember the first Postgres conference talk you gave? I'm just curious. Bodies. 

**Boriss:** I, I don't think I, I gave the, I remember the first talk that I gave in the post risk community, which was a liking talk in t That was fun. But the first post question, probably I give it in the RESCO community, I don't remember.

But my first very first talk, it was in 1999. That one I remember it really, really well. It was with Philippe Hoffa, another friend of us. Yes. Yeah. Okay. 

**Claire:** Also should Lightning Talks are a really good way to get started. Yes, 

**Boriss:** I think. Yeah. But lightning talks have the problem that you have to be extremely funny or something.

Cause it is so easy to get next to somebody who was really funny and then present some something boring that is 

**Pino:** yeah. Anyway. I hear you. 

**Boriss:** Anyway. I was going to say, my first posts talk was in year 2000. At the event at the Linux event in Chile and Linux, the second one. And my first International Postgres conference was in Mexico in 2004.

Wow. Yeah. 

**Pino:** Yeah. 

**Claire:** All right. So you've been teaching people about Postgres for a while. Oh, yes. Fair to say. All right. Well, RO and Boiz, thank you on behalf of both Pino and myself for joining us today and exploring this. I think that, you know, I guess, I guess my question to you, going back to the first topic or the first question of the day, why giving talks at Postgres conferences matters is would you encourage people who have never given a Postgres talk, whether it's a user talk or developer talk at a Postgres conference, would you encourage them to submit?

Should they do it? Absolutely. 

**Boriss:** Is it worth it? Yeah, absolutely. Yeah. Coming from an introvert and an extrovert, both, we say immediately. Absolutely. Yeah. 

**Claire:** Even if it's a little bit scary. So as, as 

**Boriss:** definitely intimidating as an introvert, I can say that it is definitely worth overcoming the, the, the fear and, and, and doing it.

It is, it is a challenge. It is difficult, but the benefit is enormous. Can you, in my 

**Pino:** case, sorry, but just quickly, can new presenters get help from, from the community? Can from help 

**Boriss:** if, if you want to give a talk and then you don't know how to, I, I offer my help. I mean, contact me. I can, I help all the peoples already.

But we don't have any, we, we should have a group kind of like help speakers. Would that be something? Right? Why not? Coaches, coaches talk. I don't know. I mean that sounds a little bit pretentious, but if somebody wants some feedback, I can always help. I'm open to to, to doing that. A lot 

**Claire:** of, a lot of times members of the talk selection committee sometimes are willing to answer questions as well and give feedback before people even submit their C F P proposals.

So I don't know if everybody does that. I know I have done that and I know other, other folks have as well. Because, you know, there are some basic tactics in terms of your C F P submission, like filling in the additional information section with, you know, your experience and what you're gonna do to prepare and practice, particularly if you're a first time speaker, like there are things you can do to make your submission stronger and to make it more likely to be accepted.

So I think, I think there's lots of help out there. You just have to ask for it. All right, bud. Thank you so much for joining us today. Episode three. This episode has been recorded and it will be published on YouTube initially. Will drop the link in the thread and then it will also probably ultimately be published on other podcast platforms too.

**Boriss:** So thanks for the invitation. It's been really a pleasure. Yeah. Thank you, Claire. Thank you. Pinot High five boys. Thank you both so much. 

**Claire:** Yes. Yeah. Virtual high five here. Yeah. All right, and thanks to everybody on the chat as well,

cia.

