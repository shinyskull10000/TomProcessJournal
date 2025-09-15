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





