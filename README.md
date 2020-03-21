# HealthJacket
A jacket that tracks temperature and some vitals and adjust its temperature. Powered by the RSL10-SENSE-DB-GEVK dev kit by ON.

### Things used in this project

Hardware components
RSL10-SENSE-DB-GEVK	
ON Semiconductor RSL10-SENSE-DB-GEVK
×	1	
heat pad
×	1	
Jacket
×	1	
Darlington High Power Transistor	
Darlington High Power Transistor
×	1	
1N4007 – High Voltage, High Current Rated Diode	
1N4007 – High Voltage, High Current Rated Diode
×	1	
Resistor 1k ohm	
Resistor 1k ohm
×	1	
Photon	
Particle Photon
×	1	
USB extension
×	1	

Software apps and online services
Strata Developer Studio	
ON Semiconductor Strata Developer Studio
Node-RED	
CloudMQTT
RSL10 application

Hand tools and fabrication machines
Plier, Needle Nose	
sewing needle
Soldering iron (generic)	
Solder Wire, Lead Free	
3D Printer (generic)	

Story
DISCLAIMER: This application is used for demonstrative and illustrative purposes only and does not constitute an offering that has gone through regulatory review. It is not intended to serve as a medical application. There is no representation as to the accuracy of the output of this application and it is presented without warranty.

For this contest I decided to change it up a little bit. This time instead of something theoretical or unproven, the end product has to be something designed for daily use and more related to current events. Without further ado..

If you have little time, watch the video:
https://drive.google.com/drive/folders/1O4SuGFKH5aUyah2biGQ7E5RRfrHUFdAj?usp=sharing

Introduction
We live in perilous times, it seems 2020 has brought the worst it can be, hitting us with a Pandemic and the following economic impact that will probably lead us to a global economic recession. The COVID19 led pandemic has thaught us a lot, more on the side of personal higiene and taking care of our health. But, it seems people forget that the seasonal flu has similar impact in terms of healthcare and lives taken thatn this new disease. It took quarintines, a hit to the global economy and a new strain for people to activate an act. Even when experts warned us about the impact a Pandemic would have:

https://www.youtube.com/watch?v=as9JRKed7Cs&feature=emb_title

Despite the billions that are spent on healthcare annually almost everything goes into curative care and most of that is related to Chronic diseases, yes, the ones that are caused by poor preventive care. Among the money spent on Preventive medicine a very small percentage is destined to prepare and potentially combat these pandemics. We just have to take a look to what happened few months ago when the Trump administration fired its pandemic research team.

<img src="https://hackster.imgix.net/uploads/attachments/1089102/image_u1NrGzjK8v.png?auto=compress%2Cformat&w=740&h=555&fit=max">

And then there's the seasonal flu which kills each year more than perhaps this Coronavirus will (It's not going away btw).
COVID19 takes all the media attention at the moment but we have to take some numbers into consideration. We just had one of the worst decades in relation to children mortality regarding the seasonal flu:

https://weather.com/health/cold-flu/news/2020-02-14-worst-flu-season-for-children-in-a-decade

And we have to remember that the flu is PREVENTABLE, with a simple flu shot you have a high degree of immunity and probability of not taking it even during the coldest months of the year. And that takes us to my next point.

<img src="https://hackster.imgix.net/uploads/attachments/1089106/image_S7vlJUEmB9.png?auto=compress%2Cformat&w=740&h=555&fit=max">

There are several key indicators to battle a disease such as the flu, one is that the virus is weak during the warmer months because of the lipid structure of its membrane:

"The outer membrane of the influenza virus is made chiefly of molecules known as lipids. Lipids—which include oils, fats, waxes and cholesterol—don't mix with water. The NIH researchers used a sophisticated technique called magic angle spinning nuclear magnetic resonance, which was developed and previously tested in NIAAA's laboratories, to investigate how the virus's outer membrane responds to variations in temperature."

Their findings were published online on March 2, 2008, in Nature Chemical Biology.

Other aspects, written by Harvard Medical School are:

1) During the winter, people spend more time indoors with the windows sealed, so they are more likely to breathe the same air as someone who has the flu and thus contract the virus (3).

2) Days are shorter during the winter, and lack of sunlight leads to low levels of vitamin D and melatonin, both of which require sunlight for their generation. This compromises our immune systems, which in turn decreases ability to fight the virus (3).

3) The influenza virus may survive better in colder, drier climates, and therefore be able to infect more people (3).

So the old adage of "wearing your winter clothes and keep warm" becomes much more important it seems as a way to prevent this seasonal disease.

Don't get me wrong, that is just our context, but we have to take preventable and easy to implement solutions seriously, at least in the US the amount of GDP destined to healthcare is reaching 20% which is unsustainable. We have to take seriously preventive medicine (which is the cheapest medicine) and come up with new solutions to help ourselves. Maybe even using the constantly improving and constantly cheaper computational power and the benefits of the cloud.

## Solution
By re-engineering clinically validated technologies with new and out of the box IoT technologies like the RSL10-SENSE-DB-GEVK dev kit (Will now be called just Dev kit) , the device will measure temperature mainly but will make use of humidity and air quality for its analytic component. The wearable will be powered by its own little battery and will wirelessly transmit health data to a central monitoring application which will help the user.

The RSL10-SENSE-DB-GEVK will be the bridge between the sensors and the cloud. It'll be connected via Bluetooth with the user's cellphone to local WiFi or GSM/BLE module. We will have the sensors connected to the kit and then the information will be processed in the cloud with Machine learning algorithms in order to determine if the jacket needs to be heated or just idle, and it will learn from the data.

<img src="https://hackster.imgix.net/uploads/attachments/1089389/image_2tsD4Fl5ZG.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Our main purpose will be then to keep the user warm during variations of temperature, notify of the pe performance of the system and all around keep a record that we can later improve on and generate valuable insight and predictions about the user's health state.

Here is the architecture of our solution:

<img src="https://hackster.imgix.net/uploads/attachments/1089387/image_1yVg9gndQY.png?auto=compress%2Cformat&w=740&h=555&fit=max">

## Now let's build it step by step:
## 1.- Setting up the Dev kit
This is perhaps the easier step, as the Dev kit already comes pre programmed with the necesary feed of its sensors to the App. We just have to connect it and put in the battery.

<img src="https://hackster.imgix.net/uploads/attachments/1089112/image_MYpjd1oeGr.png?auto=compress%2Cformat&w=740&h=555&fit=max">

To correctly configure the dev kit, download the official ON Semiconductor IDE.

IDE Link: https://www.onsemi.com/PowerSolutions/gatedDocument.do?method=getGatedDocument&docId=1172113

And here is the manual to set up your computer:

Link: https://www.onsemi.com/pub/Collateral/EVBUM2614-D.PDF

Remember those are only if for some reason, you cannot link the device to the APP out of the box.

Now we have to continue by setting up the application.

Install the APP through these links:

iOS:https://apps.apple.com/us/app/rsl10-sense-and-control/id1451974010

Android:https://play.google.com/store/apps/details?id=com.onsemi.rsl10senseandcontrol&hl=es_VE

Or via search:

<img src="https://hackster.imgix.net/uploads/attachments/1089114/image_bWQX7ksXKp.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Should be only this one.

<img src="https://hackster.imgix.net/uploads/attachments/1089115/image_8kxHMlAhQI.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Open the app and wait for it to scan on devices. Whenever you see yours then click on it.

<img src="https://hackster.imgix.net/uploads/attachments/1089116/image_EMiQ3Vq2KU.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Choose your desired sensors (in my case they were these). And name your application:

<img src="https://hackster.imgix.net/uploads/attachments/1089117/image_P6ofq7YkFa.png?auto=compress%2Cformat&w=740&h=555&fit=max">

If everything is correct you should see your sensors gathering data:

<img src="https://hackster.imgix.net/uploads/attachments/1089123/image_KVphzTi4lH.png?auto=compress%2Cformat&w=740&h=555&fit=max">

We have finished this step now let's go to connect it to our chosen cloud.

## 2.- Connecting it to the Cloud
Go to the gear symbol on the upper right.

<img src="https://hackster.imgix.net/uploads/attachments/1089122/image_PPSzv5lI5R.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Then swipe on enable broadcast.

<img src="https://hackster.imgix.net/uploads/attachments/1089124/image_E2KK1g1Yev.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Then go to Manage Brokers. Inside here go to the + symbol and then add broker.

<img src="https://hackster.imgix.net/uploads/attachments/1089125/image_v4TzXCVRpE.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Then inside here, select Generic broker, click next and set up the information for your broker. In this case we will use CloudMQTT.

<img src="https://hackster.imgix.net/uploads/attachments/1089131/image_0Hr88icMvC.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Note: you have to have an account on CloudMQTT, but as soon as you create an instance all this information is readily available on the home page of that instance.

Select that broker and go back to the home screen of the app.

<img src="">
<img src="">
<img src="">
<img src="">
<img src="">

<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">

<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">
<img src="">

<img src="">

