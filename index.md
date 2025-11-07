# Smart companion web application
## First Entry 26/09


For the purposes of helping you study

### Brainstorm

    - monitor noise data not raw audio to detect distractions
    - Allows you to set a timer to distract, time might be able to be hidden to also reduce distractions.
    - Could have multiple modes (would need to research what people find less distracting to give users a choice about the websites perception and actions)
    - Could help setup schedules, (this means getting a time api to help set reminders)
    - Could be made to be a source of mood lighting based on time.
    - Could give warning about studying or staying up late.

More features:
    - Have a login section tied to a redis database or something similar.
    - This would make it so schedules could be tied to an account and wouldnt have to be remade
    - would need some form of hashing to make it so the database is secure given that users 



## Second Entry 02/09

Breakdown of features necessary.
How does this project qualify to be a responsive technology prototype.

This project aims to be context-aware with the ability to respond to the context it is in. This is achieved through a measurement of audio waves through dB as well as being knowledgeable of the current time of the user.


Most Important:
    - Audio File Raw Data analysis
    - having it not spike often, this means alerts hopefully wont be sporradic and instead contained if consistent noise is persistent.
    - having it interact with the site dynamically.

How would i begin to achieve this?
 I would not be able to use python to do this.

 I would have to use JavaScripts web audio API. This means that the data collection code would be front-end. I do not have much experience with java-script so i am going to have to learn about what i need to do fo rthis project.


However if i want to run backend, i may want to use flask and connect it to something like redis. This nosql system could make it so I could capture login information and hash and store it. Connected to this form of account, it would mean that a user would be able to then create a form of schedule for studying.


## Third Entry 09/09
What i want to know
Investigation into similar projects
Investigation into how load an environment has to be before it could be a distraction
would it be good ot have a setting to set level of distraction in dB?

### Interesting study
https://crl.acrl.org/index.php/crl/article/view/24743/33322  Talks about the effectiveness library use by students. The reason the study is interesting for this project is that libraries are typically quiet learning environments which are highlighted by the fact that they have few distractions.




## Fourth Entry 11/09
### Similar Projects
#### https://www.stayinsession.com/ : Session
This is a web application on macos and IOS which aims to block distracting apps and set 25 minute timers to dedicate time to study.
However, in order to use session, you must pay a subscription which may exclude large social populations of users from benefitting from such technology.
This is a timer app which follows the Pomodoro Technique: https://www.coursera.org/articles/pomodoro-study-method

Breakdown on the pomodoro study method:
    - Choose a task to complete
    - set a timer for 25 minutes
    - work uninterrupted until the timer goes off
    - take a short break. approx 5 mins
    - After repeating four times, take a larger break.
This technique is used to maximise focus on tasks in productive time managed method.

How my project is similar:
    - the use of timers to incentivise dedicated times of focus to put towards studying/work
    - The optional use of scheduling to ensure consistent studying/working

How my project differs:
    - For one, my project is responsive, it utilises information gathered from the users surroundings (dB) to find distractions
    - This difference should provide a more effective way of detering distractions then the optional disabling of apps on a computer/ phone used in session.
    - My project would be open source/ free.


### Research into when an environment is too loud to work effectivley in
This is a key aspect of what needs to be researched in order to be able to not only identify distracting environments when i move forward to implementation. This could also be expanded between multiple modes for stricter silence and lack of distractions to allowing for a minor distraction filled environment if the user cannot find a quiter place.

"The results of this study showed that as a stressor, noise affects cognitive performance and brain signals. Also, noise pressure level is an important factor regarding impairment of cognitive function and power spectral density of the brain, meaning that low levels noise is not as effective compared to high levels of noise. It can be said that the results of this study are in agreement with the proposal that a relationship exists between low performance and high levels noise"
From an study: https://pmc.ncbi.nlm.nih.gov/articles/PMC6901841/ 

Jafari, M. J., Khosrowabadi, R., Khodakarim, S., & Mohammadian, F. (2019). The Effect of Noise Exposure on Cognitive Performance and Brain Activity Patterns. Open access Macedonian journal of medical sciences, 7(17), 2924–2931. https://doi.org/10.3889/oamjms.2019.742

This study is quite interesting as it delves into the effect of sound acting environmental stressors and its ties to cognitive function.



### Looking into the Web audio API
While a web application could be the most effective which I am going to discuss. There might have to be swift overhauls to an application through something like TKInter in python if certain features become unavailable to be developed. This process would be quite annoying as the process which utilises Web Audio APIs 

##### This is idea for javascipt implemented into html is asssisted by the use of chatgpt as a walkthrough for how this application may be possible
This is build first by capturing microphone audio (this is necessary for having the application to be able to be responsive):
const stream = await navigator.mediaDevices.getUserMedia({ audio: true });

This gives a mediastream stored as a const variable to be used to be plugged into webAPIS

Utilising Audio Context, Media Stream Source and Analyser Node

AudioContext is a way to interface with audio with nodes and allows for audio processing and or decoding.
MediaStream SOurce is a method of audio context, it 

const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const source = audioCtx.createMediaStreamSource(stream);
const analyser = audioCtx.createAnalyser();

The analyser allows for code to be used on the analyed raw audio to produce dbFS.

An important distinction to make between the two types of decibel measurements:
dBFS
dBSPL

dBSPL is the absolute value which represents sound pressure created by soundwaves while dBFS which is more relative and measures of the amplitude of a digital audio signal.
While human hearing is highly related to dBSPL, it is possible for dBFS to still detect distraction throughs spikes in audio or consistently loud sounds where dBFS is near -10 to 0. 
It may take tinkering to discover a recommended balance between loud noises of human hearing vs what the computer hears and can calculate.


## Fifth Entry 12/09

Chosing Name for the project.

Decided to go with either QuietMind or HushStudy

QuietMind would most likely be the chosen option as it seems a bit more friendly due to how Hush has some negative connotations. This is further explored for when a user wanting to use the app would most likely not be the one making the noise as background sound would be the cause of distractions. 


## Sixth Entry 14/09

### Understanding Possible Realisations
With the focus of the website being made on surrounding the basis that it is responsive to the audio the computer can here to determine if the environment is far too distracting, it may be difficult to implment other features.
This concern majorly stems from the idea of implementing a savable schedule feature. This would require the use of a database to store information so that it can be accessed depending on the user. 
This means that it would require for me to implement a secure login system which hides the backend features (such as database keys and login information) as well as encrypting user passwords as they are stored.

## Seventh Entry 15/09

### Experimenting with the APIs
I created as simple web application to explore how the use of the APIs discussed earlier could be utilised to make this project.
The link for the github pages is this: https://shinyskull10000.github.io/WorkingWithSoundAPIS/
The website shows both the dBFS of the user microphone as well as the average over time. How dBFS works is that it is a negative scale which as it approaches 0, the louder the sound it registers is. This website also has a trigger when the sound average is too loud, the background of the website turns red. This is currently set to a trigger at average -20 dBFS as that it would require quite a loud/ distracting environment, perfect for what I am looking to achieve with quiet mind.  

While these are important steps for the process of development for QuietMind, it is important to configure as well as understand what the limits in dBFS should be to determine a loud environment. Ways I might figure this out could be testing with myself as well as testing with other people. I could also try and find new ways to record sound pressure at the time as i record the dBFS to try and find correlation for fine tuning.



## Eighth Entry 7/10

### Consideration of having a whitenoise generator in the application of well, to avoid total silence but to not have an overly loud environment.

This would be for the purpose of minimizing the impact of sharp crashing inconsistent sounds for the user. This is too solve for an issue the app would be designed to address.


### The use of Chatgpt to assist in app creation
The use of chatgpt to create a prototype of my app. This prototype consists of a way to measure and represent the microphone data. The prototype also includes a session feature which takes notes of interruptions (every second which the noise average is louder then the set threshold) and creates a json document surrounding the history and information it gathered around the session.

### Problems I have with the prototype
When the incident occurs, it sends a notification from the website about how the environment is too loud. The problem with this is how it is currently set up is that it will spam notifications every second the sound is louder than the threshold. This can be deeply annoying and most likely would have to be fixed by having the alert trigger only once per peak reached. 


## Ninth Entry 14/10
### Implementation of White noise generator
added a part to the index.html of the quietmind project which enables the the use of the of a quiet mind generator. Uses the Noise node to generate whitenoise through gain.
### The next steps with whitenoise generator. 
#### Ideas
If there are large consistent spikes of noise, for it to be automatically turned on. 
If there are a large consistent spikes of noise, it asks if the user wants to turn on the white noise monitor
For when doing sound calibration, would it be possible to also calibrate an appropriate white noise level suited for the desired sound level measured in -db.
Say when it is enabled, it is tied to the -db measurement, so when the average would be around -50 the environment is quite quiet so a low whitenoise would be important. but when the average is set around e.g -15, a loud whitenoise may be necessary 
All of this should be subject to testing to determine what is effective.
Maybe add a question to the user when first running the app or a toggle depending if the user has a headset/headphones and microphone plugged in to their audio or not. 
A measure of uneveness. Use entropy to detect unpredictable sounds and increase the whitenoise sound. The higher the entropy the higher the whitenoise. This should be the most effective solution when regarding the use of responsive whitenoise for the quiet mind web application

### Testing needed to be done
See how loud the whitenoise generated is approximately when no headphones are not plugged in. 
Is it equivalent to typing in terms of how loud device is. Only is that when typing without a proper microphone. the peaks are incredibly loud and for these.

### Implementation of Responsive Whitenoise in response to entropy
e.g. when a session is started white noise will play dependent on the entropy. It will be slightly dynamic with fixed levels it moves between. it may also be important to include fading between moving between levels of noise as jumps between levels of sound that are sharp are also distracting. 


## Tenth Entry 4/11
### Implementation of the entropy in the website.
Calculation of the entropy for the recorded microphone audio was added. The entropy is scaled from 0 to 1 where 0 to 0.3 is low entropy with predictable noise in the background e.g. a AC hum or a fan. Entropy measured from 0.4 to 0.6 is slightly more unpredictable with sudden noises occuring with some patterns. With lastly a high entropy of 0.7 to 1 where the sound is chaotic, unpredictable with high variation in sudden noises.

Includes a slider which handles smoothing. The slider goes from 1 to 20 where a each number represents a 200ms frame/window of time where entropy is calculated. This means that 20, the entropy calculater would be smooth and slower to react to loud noises as it calculates the 20 readings over a 4 second window to get the average entropy. On the other end, a 1 means that an average would be calculated after every single reading leading to a very jumpy entropy readings.

Lastly this calculation was then tied to the whitenoise to have a louder whitenoise with higher entropy and a quieter whitenoise with a lower entropy. This choice was made out of the idea that a whitenoise sound would reduce the environments overall entropy of the users environment resulting in a higher quality studying enivornment.


## Eleventh Entry 6/11
### Final Prototype Design // The exclusions 
The final prototype of QuietMind does not include being live hosted with a scheduling, login functionality. There are a few limitations when it comes to wanting to live host the website with password implementation and a database linked to save user data. This is mainly that since the current prototype has all the code within the index.html file, it means that every bit of code is exposed. If willing someone with no good intentions could look at the website with the login functionality and find the keys for the database exposed in the code. The way to get around this would be to break up the code into seperate files and live host it on a HTTPS protected domain. As these would come with additional costs and further precautioned, the the current version of the prototype will not include the schedule/ login system due to security risks

### Writing a script for pitch video for QuietMind
Introduction
    - Introduce self
    - QuietMind is a responsive web application study assisstant.
    
Purpose/use cases of QuietMind
    - Studies show studying in loud distracting environments can negatively impact the effectiveness of time spent studying
    - While loud environments can also negatively impact studying, if a place is too quiet, it could raise anxiety levels as the only things you might hear would be bodily sounds e.g. heartbeat, movement of muscles and joints. Studies of Anechoic chambers prove this theory as no person can usually last more than an hour in such an environment.
    - The last type of environment relevant to quiet are environments with sporadic and jumping noises where while the overall average sound of the environment may be good for studying, e.g. a dog barking, constructiongoing on in the background, yelling. are all things that can end up still distracting the user.

Features
    - A live noise monitor based on microphone audio that takes in audio data (doesn't record the audio) and projects it on a graph as dbFS. 
    - A noise limiter to cause a trigger when average audio is too loud. This can be calibrated based on a recorded sample of microphone audio or it can set manually to a limit that the user finds more suitable. This in combination with the noise monitor leads to a responsive experience when using QuietMind
    - An adjustable studying timer which creates a record of a session when completed.
    - These sessions are stored locally in the browser but also could be exported to json to have a backup of previous study sessions
    - A white noise feature is included in quietmind to aim to solve the second and third use cases related to having a suitable study environment. With the goal to firstly, provide some noise to not have the user of the application study in pure silence.
    - The white noise feature is also responsive as it is configured to respond to the entropy of the of the monitored microphone audio. If the entropy is higher, the white noise would be louder to compensate for the chaotic jumping audio levels in a goal to reduce the overall entropy of noise for the user. The whitenoise part of quietmind has multiple sliders including a manual volume override, entropy smoothing where a higher number of samples results in a more smooth calculation of entropy and a response sensitivity slider that determines how much impact entropy has on the volume of the whitenoise.

Conclusion
    - Thankyou for listening to my showcase of quiet mind, have a great day.