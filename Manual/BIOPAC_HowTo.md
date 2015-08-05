
# SNaPP Lab Biopac Manual

Created 5 August 2015 by Edward Hernández  
Last modified 5 August 2015 by Edward Hernández  

Original version "Biopac How-To" created 23 July 2013 by Drew Englehardt  
Based on YouTube tutorials created by [BIOPAC Systems](https://www.youtube.com/user/BiopacSystems)

## About this Manual

This manual is meant to document the practices currently used by student researchers in the College of William & Mary's Social Networks and Political Psychology Lab. This document makes no claim to be authoritative in any way. If you would like more information about why these particular steps or taken or about the decisions which lead to this set-up, [contact Edward Hernández](mailto:ehernandez@email.wm.edu).

## Setting up the Hardware

1. Connect the MP150, STP-100C, four PPGED-R units, UIM100C, and four ECG100C units together, in that order. When completed, the units should look like this.  
![Assembled MP150][MP150assembled]
2. Take one of the yellow Ethernet cables and connect it to the back of the MP150 unit. Connect the other end to the BOX in slot 1. Take the other yellow Ethernet cable and connect it to slot 8. This cable will connect to the computer running AcqKnowledge.  
![Attached cords][AT-FS708]
3. To set up the BIONOMADIX, connect the lead for the heart rate measurement to the PPG input. Connect the leads for the EDA electrodes to the EDA input. 

## Setting up Channels

1. Turn off the Wifi via the "Network" System Preferences tab.
2. Open Acq*Knowledge* 4.4
3. If the following drop down menu appears, select whatever option appears. If no options appear except "No MP150 Hardware" click the "Refresh Now" key until there one appears.  
![MP150 Selection][MP150selection]
4. Open a blank file (Acq*Knowledge* calls all its files "graphs"), by selecting "Create and/or Record a new experiment" and Create empty graph."  
![AcqKnowledge Blank Graph Creation][BlankGraphCreation]
5. This should yield a window that looks something like this.  
![Blank Graph][BlankGraph]
6. Select the MP150 dropdown

## Collecting Data in AcqKnowledge

1. Open Acq*Knowledge*.
2. Make sure the MP150 unit is turned on and connected. Select the relevant MP150 unit and click OK. If the module does not appear you may need to click the REFRESH button a couple of times.
3. We now need to create the file for our data collection. Make sure “Create and/or Record a new experiment” and “create empty graph” are selected.  
Now you have an empty workspace within which you’ll collect the data.
4. The next step is to set up the data collection channels. To do so, click MP150 on the top menu, and select “set up channels”. A new window will open titled “Input channels setup…” Click “Add New Module, ” scroll down to PPGED-R and select this module. This will bring up an additional window. Match the button configuration to the PPGED-R unit.  
Read through the directions on the screens that appear after clicking OK. It will make sure that you have the BIONOMADIX unit turned on and that you have the electrode leads connected to the BIONOMADIX device. You do not need to have the electrodes themselves connected to anything at this time. After reading through these screens, the window should look like the following.
5. In step 4 we created channels for EDA measurement (default channel A13) and PPG, or photoplethysmograph, a measure of blood flow (default channel A1). This can be seen by clicking the “View Channels…” button in the “Set Up Channels” window. We now need to create a channel to measure heart rate. To do so, click on the “Calculation” tab. Then click “Acquire,” “Plot,” and “Value” on channel C0. Next, with C0 still selected, click “Setup”  
On the new window that appears, make sure that A1 is selected as the source channel. We are using the data collection from A1 to also calculate heart rate.  
Match the settings on the setup channel to the ones in the image and click OK. These should be the default options. We now have our three data collection channels created and we’re ready to go. Close out of the channel set up window and return to the data collection screen. While the channels have been created, they won’t appear until data are collected.
6. When you’re ready to begin data collection, press START in the data collection window. You will now see the channels you created separately gathering the physiological data in real time.


## Data Analysis using AcqKnowledge

1. To analyze EDA data, first filter any high frequency noise. Select Transform on the top menu, then filter, FIR, low pass. I’ve used the following settings to define the filter.
2. To count the number of EDA events, first create a copy of the EDA channel by going to Edit, then “Duplicate Waveform”.
3. Next, select the duplicate EDA waveform. Select transform, from the top menu, math functions, threshold. For the “lower threshold” input 0.05, and for the “upper threshold” input 0.051. These settings will detect events that are 0.05 microsiemens or larger and will display the result as a series of spikes that meet the response criteria of being 0.05 microsiemens or larger. 
4. Then, go to “Analysis” and select “Find Rate.”  
Use the following criteria to count the number of peaks (i.e. EDA events) in the transformed waveform. Function: Find Rate. Threshold level: 0.05.  
This creates a new waveform that is a count of the number of EDA events in the collected data. If you compare it to the waveform created in step 3, the count will increase by one at the end of each marked event.
5. AcqKnowledge also has an automated procedure to determine EDA events. To access it go to the Analysis tab, click on Electrodermal activity, and Locate SCRs.
6. Make sure the EDA channel is selected, and hit ok.
7. Finally, the EDA events are marked as below. The beginning and end of the SCR event are marked by ( and ) respectively. The peak event response is marked by a water droplet, like below.

[MP150assembled]: .Pictures/MP150assembled.png
[AT-FS708]: .Pictures/AT-FS708.png
[MP150selection]: .Pictures/MP150selection.png
[BlankGraphCreation]: .Pictures/BlankGraphCreation.png
[BlankGraph]: .Pictures/BlankGraph.png
[MenuBar]: .Pictures/MenuBar.png
