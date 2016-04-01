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

4. Develop and code - this is where the fun begins. Being organized, process oriented and methodological thinker that I am; comes very handy in this stage. I like to break things in smaller chunks. Most modern codes are built in modules or by functionality that is then distributed for development to different developers to work on. Here's how broke down which code to work on :

  - Procure token from the API service, in this case Breezeometer.
  - Work on getting the API string to work so Alexa can communicate with Breezemeter. Some developers would probably tackle this head on by going right down to solve the full functionality (i.e. getting Alexa to recognize user input and send this to Breezeometer). I saved that for later and focus on the basic goal which is to get Alexa to connect and get a response back. I tested this by hard coding the zip code in the string and tested with a web browser. My rational is if it works for one city, then the code will work for any city since this step was merely to test request-response round trip was occuring.
  - Once successful connection was established, I then coded to parse the JSON so that I only store the info that I needed which in this case was air quality rating.
  - Then I proceeded to think about coding for error handling which will then come handy later as I already had that as one of my test cases.
  - I then proceeded to tackle the end to end functionality which is to have Alexa recognize the zip code provided by user, store it, construct the API string, perform the `HTTP.get` and process the response and have Alexa speak out the response correctly.
  
5. Testing plan
3. Unit Testing
4. Prepare test data
4. Functional Testing
5. Final code clean up
6. Documentation
7. gather periphenail for AMZN cert


[Tide Pooler] (https://github.com/amzn/alexa-skills-kit-js/tree/master/samples/tidePooler)


