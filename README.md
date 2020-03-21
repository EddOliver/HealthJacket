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

https://youtu.be/93hzYOjMHio

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

<img src="https://hackster.imgix.net/uploads/attachments/1089132/image_dxk7BqgvO2.png?auto=compress%2Cformat&w=740&h=555&fit=max">

As you can see we have trhe configuration for our application on the bottom, now lets try and do a broadcast.
https://www.youtube.com/watch?v=b26adihn4I0&feature=emb_title

And on the cloud side you should get something along these lines:

<img src="https://hackster.imgix.net/uploads/attachments/1089133/image_GkyuEOfIxo.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Now that we have everything online its time to do some dashboards, analytics, gather data and actuate on that data, by heating our jacket.

THE most important thing of that setup is to GET THE TOPIC. With the topic now we can follow through.

## 3.- Gather the data and display it with Node-Red
If you are completely neww using Node-RED follow this guide here:

https://github.com/EddOliver/AgroJetson/tree/master/IBM%20cloud%20Agrojetson

That is a guide for the absolute beginner, but taking a look at our flow we can see several instances of what we are doing. For the next steps we roccomend installing the Dashboard node and the Particle node:

https://nodered.org/docs/user-guide/runtime/adding-nodes

<img src="https://hackster.imgix.net/uploads/attachments/1089135/image_CarUDx9p33.png?auto=compress%2Cformat&w=740&h=555&fit=max">

By using the MQTT node, we will sync it to CloudMqtt.com which is a freemium message broker for the internet of things, our two "things" have to be setup to this broker, but that part has to be manually done.

In the case you are using another broker than m12.cloudmqtt.com, you might be needing more information and will need to change the broker.

Now we will go ahead and explain the configuration of the nodes which is very easy.

By taking both the "start" and "end" MQTT nodes we will form a messaging "bridge" so the Dashboard can "hear" the messages on Cloudmqtt. Grab the end node, go to server and then click on the edit icon to configure this part of the node.

<img src="https://hackster.imgix.net/uploads/attachments/1089136/image_eWP2KgYVr2.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Now input your credentials from the MQTT broker of your choice, here is done with Cloudmqtt.

Then grab the "start" node and set it up like so:

<img src="https://hackster.imgix.net/uploads/attachments/1089138/image_gVcwtQUqH1.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Notice the Topic, it is set up according to the topic of the sensors you will be using.

Now, remember the topic you grabbed from the cloud Websocket? In my case it was something along the lines of:

from_76920t529843041c
Now that you have it, configure it with your MQTT nodes and now you can gather all the data needed.

Just configure the Function nodes like so to parse the information incomming:

<img src="https://hackster.imgix.net/uploads/attachments/1089417/image_kaSNYF3elW.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Also notice the limit on the messages.

Let's test my node Red UI and the cloud connectivity that we have done so far:
https://www.youtube.com/watch?v=0DbBJHDAZ_I&feature=emb_title

## 4.- Controlling the heat pad (a lot of hardware assembly and crafts)
For that we will need a 5V powered heatpad like this one:

You can find one at: https://www.amazon.com/Heating-3-Shift-Electric-Element-Abdomen/dp/B078LVHX47/ref=sr_1_5?dchild=1&keywords=heat+pad+usb&qid=1584762590&sr=8-5&swrs=802B5CEC2DDECAB69F0B5EAF123C7B82

And we will make the following circuit:

<img src="https://hackster.imgix.net/uploads/attachments/1089368/heatpadscheme_hY2LHBklVc.png?auto=compress%2Cformat&w=740&h=555&fit=max">

The materials for making that one are:

A TIP120 Darlington transistor
A 1N4007 Diode
Particle Photon microcontroller
and a USB extension Cable.
Also I reccomend a Soldering iron and Wire to get everything into a protoboard.
Now, let's start with the usb extension cable. This will serve to connect everything to the Powerbank and the heating pad later.

Get one like this (the cheaper the better, as you will take it apart):

<img src="https://hackster.imgix.net/uploads/attachments/1089374/image_4wAFcKHGjp.png?auto=compress%2Cformat&w=740&h=555&fit=max">

And....tear it apart haha. Just kidding just peel the external plastic.

<img src="https://hackster.imgix.net/uploads/attachments/1089377/image_MoI7SQvLDs.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Then cut the cables but remember the red and the black one are the important ones for our application, green and white are just for data.

<img src="https://hackster.imgix.net/uploads/attachments/1089380/image_JQM15dsxb5.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Now cut then open and peel the red and black cables on both sides.

<img src="https://hackster.imgix.net/uploads/attachments/1089383/image_zdn45p6ros.png?auto=compress%2Cformat&w=740&h=555&fit=max">

With that now we can assemble the circuit:

Here is my own device after soldering and setting up everything:

<img src="https://hackster.imgix.net/uploads/attachments/1089382/image_PqHcbAEngF.png?auto=compress%2Cformat&w=740&h=555&fit=max">

Notice the Photon, the darlington transistor and how the USB is soldered and used on one side for the power bank and on the other side for the heatpad.

Here is a little bit of the construction process:
https://www.youtube.com/watch?v=BOql4WcVqZU&feature=emb_title

## 5.- Controlling the heatpad through the cloud
Go to your Particle IDE and paste the code for the Photon.

The main point of the code is understanding that it creates a function that can be accessed via the particle cloud. Whenever you input certain conditions to that functions externally, you can do some previous programmed actions.

Flash it and go back to Node-RED. If you need aditional help with the Photon go directly to www.particle.io/start for a great place to begin.

Now in Node-RED make a flow like so:

<img src="https://hackster.imgix.net/uploads/attachments/1089140/image_6iVo8vc11O.png?auto=compress%2Cformat&w=740&h=555&fit=max">

The Particle node is indeed the function node.

Double click on the Particle node and click on the pencil on "Add new particle cloud". Then fill it like so:

<img src="https://hackster.imgix.net/uploads/attachments/1089141/68747470733a2f2f696d6167652e6962622e636f2f6b79576762382f363837343734373037333361326632663639366436313637363532653639__35cb4aaec143b952b24867b813d21e92.jpeg?auto=compress%2Cformat&w=740&h=555&fit=max">

Your access token is in your particle IDE, Devices section and clicking on the current device you are using. Update and in the next screen fill it with your device name that you can get on the Particle IDE and also on "CLoud Function" input "led".

- Now your Particle Photon node is configured to get an "on" or "off" payload and do the appropriate action with it.

- To configure properly the email node you have to log in to your gmail account and then go to: http://myaccount.google.com/u/1/lesssecureapps and turn it on, if you followed this guide accordingly, you set a password and username to your Node-RED so this procedure should be safe.

Then just fill the required fields.

<img src="https://hackster.imgix.net/uploads/attachments/1089404/image_SnDmuuTylX.png?auto=compress%2Cformat&w=740&h=555&fit=max">

The function node has to be configured as shown so it may relay the information at a proper time to the Photon.

- The most important step:

Finally, you have reached the end of this part of the tutorial so you have an idea of how to do the main parts of the project. Next is to do your own and use the concepts to get to a final product like the one presented here. There is also the main Flow that we did but we strongly suggest the reader to cultivate their own so you can have a better understanding of what is happening.

If you still want to have a complete solution in the "code section" at the github of the project there is the Node Red flow used in the project. You will just have to configure the credentials for both the cloud and the particle cloud as presented before.

Just upload it to a virtual machine via cloud, or we fully recommend a service such as the Node-RED starter from IBM cloud (highly recommended):

https://cloud.ibm.com/catalog/starters/node-red-starter

## 7.- Getting the prototype into a jacket.
For this we will 3D print a small case (STL files at the bottom), and then incorporate them into a coat (any coat, hoodie or jacket is fine). This case of course will have in its interior the Devkit and it should be exposed to the elements, so on the outside of the jacket.

<img src="https://hackster.imgix.net/uploads/attachments/1089152/image_smojJLR9Ez.png?auto=compress%2Cformat&w=740&h=555&fit=max">

How to assemble it:
https://www.youtube.com/watch?v=Nne2ZALpiIU&feature=emb_title

Then we will grab the Photon-powered Heat pad and its case and also set it up in the jacket. All this has to be powered by an external power bank, and you can choose to power the photon through the powerbank or an external lithium battery (in this case I just used the same power bank):

Lets go through a video of that:

https://www.youtube.com/watch?v=0U0ryli5Px4&feature=emb_title

And this is how it looks!

https://www.youtube.com/watch?v=VWxoZBUtWKY&feature=emb_title

Showcase and Demo.
If you didn't watch the video at the start here it is again!:

https://www.youtube.com/watch?v=93hzYOjMHio&feature=emb_title

## Commentary and future rollout.
The Prototype for this application worked as intended , but of course there are some areas of opportunity. for once I thing that the part of the project done with the ON's RSL10 is almost adequate, it is very small and can be adjusted accordingly, and most of all is uses very little power. A case where you can switch the battery out easily is quite easy to imagine. For the other part the heat circuit in this case is still a little too big for the application and could be done better, (Perhaps another RSL10 devkit is in order?), but for the most part those are just problems for Design and Manufacturing and not really on the hardware or the software's backend part.

Solutions like this are in order to increase our self awareness for preventive medicine. Preventive medicine is perhaps the most important part of public health and recent events just proved that. Solutions like this one, even if they do little can in the long run have a great impact.

### References:
1. https://weather.com/health/cold-flu/news/2020-02-14-worst-flu-season-for-children-in-a-decade

2. https://weather.com/health/cold-flu/news/2020-01-09-17-things-you-probably-didnt-know-about-the-flu

3. Elert, E. 2013. FYI: Why is There a Winter Flu Season? Popular Science. <http://www.popsci.com/science/article/2013-01/fyi-why-winter-flu-season> [2 November, 2014]

4. https://www.nih.gov/news-events/nih-research-matters/flu-virus-fortified-colder-weather

5. http://sitn.hms.harvard.edu/flash/2014/the-reason-for-the-season-why-flu-strikes-in-winter/

6. https://medicalfuturist.com/ten-ways-technology-changing-healthcare/?utm_source=The%20Medical%20Futurist%20Newsletter&utm_campaign=ee5854702c-EMAIL_CAMPAIGN_2019_10_29_diabetes_companies_COPY_&utm_medium=email&utm_term=0_efd6a3cd08-ee5854702c-420575081

7. https://www.onsemi.com/pub/Collateral/EVBUM2614-D.PDF

8. https://www.onsemi.com/products/connectivity/wireless-rf-transceivers/rsl10

9. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0206808
