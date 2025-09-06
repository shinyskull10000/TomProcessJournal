# Smart companion web application
## First Entry 26/09


For the purposes of helping you study

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

How would i begin to achieve this?
 I would not be able to use python to do this.

 I would have to use JavaScripts web audio API

However if i want to run aackend, i may want to use flask and connect it to something like redis. This nosql system could make it so I could capture login information and hash and store it. Connected to this form of account, it would mean that a user would be able to then create a form of schedule for studying. whether this be