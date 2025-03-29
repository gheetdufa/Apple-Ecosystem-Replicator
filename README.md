# Apple-Ecosystem-Replicator

I should preface this by saying, 99% of people in this situation should just buy an Iphone, this process is complicated, expensive, and time intensive however for me the result was worth it. I wanted to put this up just incase anyone else wanted to completley replicate the Apple Ecosystem on an Android phone.

# Important Links / Credit

There are many important components to this, but the main ones are:
1. https://bluebubbles.app/
2. https://openbubbles.app/
3. https://github.com/versionDefect/findmy-mqtt/tree/main
4. https://www.home-assistant.io/

# Cost

This project will run you around 300$ for a good reliable setup, you can definetley do it with cheaper Iphones and a Mac Mini, but for me I got really lucky on facebook Marketplace/Ebay so Ill break down the cost.

> [!IMPORTANT]  
> The Mac Mini / Iphone need to be specific versions, specifically MacOS Ventura+ and a version of an Iphone that can be jailbroken.

### Components

1. Mac Mini 2020 32GB - 200$
2. Iphone X 256gb (SIM locked) - 50$
3. Iphone 8 256gb (Unlocked) - 30$
4. Domain - 20$

# Setup


### Mac Mini Setup
> [!WARNING]  
> You technically dont need BlueBubbles, or even a Mac Mini at all for this however it makes the process much more streamlined and much more consistent. If you plan on using iMessage on multiple devices, you could get friends computer banned so having your own really helps because you can add up to 20 devices.

1. The first step is to set up the Mac Mini, and there are a couple of things that you need to install for this to work. First, install Bluebubbles, set up Home Assistant, and install Chrome Remote Desktop (optional but really helps later on). Verify all of these work and then move to part 2.
2. Step to is to set up Openbubbles. Openbubbles is built off the BlueBubbles API, and they are really similar however Openbubbles has FindMy, FaceTime, and constant connectivity regardless of your Mac Mini status.
3. Your Mac Mini should work! Bluebubbles is a really reliable solution just incase Openbubbles fails, so I like to have both just incase. Also, make sure this Mac has good stable internet, it'll save you headaches and troubleshooting steps later on.

### Home Assistant Setup
> [!WARNING]  
> You dont need Home Assistant for this setup at all, however it is the solution I used because I deemed it the most reliable and consistent. Initially when I did this, I used tasker as a replacment however but more on that later.

1. There are countless guides for this online already, but I'll link the ones that I used to set up HomeAssistant as of March 2025: https://www.home-assistant.io/getting-started/
2. You then need to get external access setup, while this may seem like an odd choice, this makes it so that you can access Home Assistant regardless of where you are in the world. I reccomend following this video: https://www.youtube.com/watch?v=JGAKzzOmvxg.
3. Set up the mqtt broker, and set up an automation (if you havent done this before look it up) but I set up "trigger 10 seconds of every hour" and "mqtt publish" using the payload from versionDefect's github.
4. Download Home Assistant on your primary phone (the android) and make it some easy identifier like pixel_8 and replace that with the payload markers and you should be good to go. You can test this out in the mqtt add on settings, it should give you your phones location every 10s. 

### Iphone(s) Setup
1. You do NOT need 2 iphones for this at all, you can definetley suffice with one but I found often found issues with phone number deregistration that I just didnt want to deal with.
2. Once you have your jailbroken iPhones, follow https://openbubbles.app/docs/pnr.html and set up the relay on one phone. This phone is going to be on 24/7 and should always be connected consistently.
3. With the other iPhone, jailbreak it and set up the https://github.com/versionDefect/findmy-mqtt/tree/main, but instead of using that version of code use the one I provided called forwardLoc.py
5. As it stands right now, the github repo will not work unless you are locally on the same network as your Home Assistant, so if you do not care about having the second Iphone with you all the time then this step is irrelavent, just leave it in the same room and connect it to eachother and it should work fine. However if you do want the phone with you (better faceTime, Imessage games, sharing location without going to your mac, etc) then you need a site to site vpn. You could also use TailScale, but I was facing some issues when I tried.
