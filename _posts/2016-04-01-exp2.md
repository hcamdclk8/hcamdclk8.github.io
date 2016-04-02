---
layout: post
title: Air Quality Meter - A Developer's Diary
---

## Designing and Testing Air Quality Meter ##

My [previous](http://hcamdclk8.github.io/capstone/) post detailed why I chose Alexa to build final Bloc project and rational why I picked air quality meter as my skill to work on. With this post, I will share the 'how' - what went on as I built and tested this skill. The prevailing approach and guiding principle I utilized was K.I.S.S. - Keep It Simple Stupid which is a life philosophy that I adhere to.

1. Choose a service - there are several services such as communicating to database (i.e DynamoDB) or sending email that can be incorporated with Alexa. I chose API service for two reasons. The first is it is widely used by web apps to exchange data so it is relevant in the workplace. Second, since data management/data processing is a strong suit of mine prior to becoming a developer, its just was a natural choice.

2. Define user stories or core user requirements - for this stage, I went the scrappy route. By this I mean I went back to old school paper and pen to list it down using the complimentary notebook that Bloc provided to their students. This is what I came up with :

  - It will use a one shot model instead of dialog.
  - Alexa will provide air quality rating when user provides a 5 digit zip code. 
  - API service must have good and easy to follow documentation that is up-to-date.

3. Designing the skill - for this step, I had to do research and study other Alexa skills to determine the best way to develop this. I'm not one to re-invent the wheel so this stage is common for me in my development approach. I focused on two samples, the one provided by Amazon called [Tide Pooler] (https://github.com/amzn/alexa-skills-kit-js/tree/master/samples/tidePooler) and another from fellow Bloc student Henry Schaumburger called [Area Code](https://github.com/per4mnce/area-code.git). The latter becoming my go-to reference as I built this out.

4. Develop and code - this is where the fun begins. Being organized, process oriented and methodological thinker that I am; comes very handy in this stage. I like to break things in smaller chunks. Most modern codes are built in modules or by functionality that is then distributed for development to different developers to work on. Here's I how broke down which code to work on :

  - Procure token from the API service, in this case Breezeometer.
  - Work on getting the API string to work so Alexa can communicate with Breezemeter. Some developers would probably tackle    this head on by going right down to solve the full functionality (i.e. getting Alexa to recognize user input and send this   to Breezeometer). I saved that for later and focus on the basic goal which is to get Alexa to connect and get a response     back. I tested this by hard coding the zip code in the string and tested with a web browser. My rational is if it works for   one city, then the code will work for any city since this step was merely to test request-response round trip was occuring.
  - Once successful connection was established, I then coded to parse the JSON so that I only store the info that I needed     which in this case was air quality rating.
  - Then I proceeded to think about coding for error handling which will then come handy later as I already had that as one    of my test cases.
  - I then proceeded to tackle the end to end functionality which is to have Alexa recognize the zip code provided by user,    store it, construct the API string, perform the `HTTP.get`, process the response and have Alexa speak out the response       correctly.
  - Wrap up work on sample utterances, index.js, custom slots and intent schema.

5. Unit testing - this is where I tested the code for syntax errors or to see if the code would break, I did this by running node.js on the command line.
  
6. Draft testing plan - this is where I drafted the test cases or scenarios I want to execute as part of functional testing. So some of the questions I asked myself were :
  
  - What will the code do if web service is down ?
  - What will the code do if user provided a valid 5 digit number but not a valid US zip code ?
  - What will the code do if user provided only one or 4 digit zip code ?
  - What will the code do if user provided a valid 5 digit zip code ?

  Here's a sampling of test cases I wrote :

  - user provided 2 digit zip code
  - user provided a bogus 5 digit zip code
  - user provided a valid 5 digit zip code
  - test the sample utterances work
  - test by listening how Alexa was speaking out text properly
  - test the intents

  I enjoyed drafting the test plan as it allowed me to find vulnerabilities in my code, think about how it functions and     best of all, I get to switch roles and put myself as if I was the user. Ultimately, testing is to ensure we make user        experience delightful by preventing bugs to go into Production.

7. Prepare test data - I got exposed to this due to my experience working with testers and involved intimately with the entire SDLC. Sometimes its good to test with mock up data but at times, its important to test with Production data. During this step, I was digging into granular level of defining the data set. Not only is it important to say one would like to test with a valid zip could but actually define what valid zip code to use. 

  Since testing is a very iterative process, by writing out the test data itself, it allowed me to be more efficient during    functional testing. More on this on the next stage in the process.

8. Functional testing - As mentioned previously about testing being iterative by nature, writing out the test data came useful at this stage. Since I was using the AWS dev console to test, it was easier to cut and paste utterances, invocation and zip codes on the site. This also avoided typos and allowed me to not get distracted on typing but rather on the testing. Finally, being time efficient is important as testing repeatedly is required to hit certain test scenario and perform end-to-end testing.

9. Final code clean up - this step involves removing/adding additionals comments, formatting in terms of indentions or spacing to make it more reader friendly for other developers during code reviews and is performed before final check-in to GitHub and AWS.

10. Documentation - this stage involves finalizing the README.md, user documentation for use in the skill card, icons and information needed for certification process by Amazon.

11. Submit skill for Certification - the reward and crowning moment comes here when I submitted skill for review and certifcation. Though there is no guarantee Amazon will not come back with modifications, it is still a milestone achieved.

This entire process was definitely enriching and satifying. It helped to reinforce the decision I made to switch careers to become a developer was not only justified but is a natural progression of my growth.


