# SNaPP Lab BIOPAC Manual

Created 5 August 2015 by Edward Hernández  
Last modified 5 August 2015 by Edward Hernández  

Original version [Biopac How-To][Original] created 23 July 2013 by Drew Englehardt  
Based on [YouTube tutorials](https://www.youtube.com/user/BiopacSystems) created by BIOPAC Systems

## About this Manual

This manual is meant to document the practices currently used by student researchers in the College of William & Mary's Social Networks and Political Psychology Lab. This document makes no claim to be authoritative in any way. If you would like more information about why these particular steps are taken or about the decisions which lead to this set-up, [contact Edward Hernández](mailto:ehernandez@email.wm.edu).

## Setting up the Hardware

1. Connect the MP150, STP-100C, four PPGED-R units, UIM100C, and four ECG100C units together, in that order. When completed, the units should look like this.  
![Assembled MP150][MP150assembled]
2. Connect the MP150 unit to the slot 8 of the AT-FS708 with an ethernet cable. Connect the Acq*Knowledge* computer to slot 1 using another ethernet cable and an ethernet to USB adapter.  
![Attached cords][AT-FS708]
3. Connect the leads for the EDA electrodes to the BioNomadix.
4. Attach the ECP leads to the extension cord and the extension cord the ECG100C.
5. Set the switches as pictured. PPG is intentionally turned off, as ECG is a more direct, precise, and reliable measurement of the same phenomena.
6. Turn on the MP150 and AT-FS708 units.

## Setting up Channels

1. Turn off the Wifi via the "Network" System Preferences tab.
2. If you have a graph template, open it and skip to step 14. If not, continue with step 3.
3. Open Acq*Knowledge* 4.4
4. If the following drop down menu appears, select whatever option appears. If no options appear except "No MP150 Hardware" click the "Refresh Now" key until there one appears.  
![MP150 Selection][MP150selection]
5. Open a blank file (Acq*Knowledge* calls all its files "graphs"), by selecting "Create and/or Record a new experiment" and Create empty graph."  
![AcqKnowledge Blank Graph Creation][BlankGraphCreation]
6. This should yield a window that looks something like this.  
![Blank Graph][BlankGraph]
7. Select "Set Up Channels..." from the MP150 drop down menu.  
![Set Up Channels][SetUpChannels]
8. Click the "Add New Module..." button on the popup window.  
9. Find and select the "ECG100C and ECG100C-MRI" option.
10. Select channel 1.
11. Open the "Digital" tab, and select the "Acquire," "Plot," and "Value" options on channel D8. This allows Acq*Knowledge* to recognize and incorporate signals from the Stim**Tracker** unit.
12. Open the Calculate tab, and select "Acquire," "Plot," "Value," and "Rate" for Channel C0.
13. All of the configuration up to this poing can be saved in a template file, but EDA requires per-setup calibration which prevents a template file for performing properly if it is included. Use the "Save As..." dialogue to save the graph as a .gtl template.
14. Add the PPEGED-R module with the "Add New Module" option of the "Set Up Channels" dialogue box (see steps 7 through 9 if there is any confusion).
15. Set the radio buttons as pictured.
16. Follow the instructions given by the following pop-ups.
    * 
    *
17. Acq*Knowledge* is now ready to collect data!  
Be aware that there will be additional EDA calibration prompts at the start of data collection. These will be covered in the next section.

## Collecting Data in AcqKnowledge

This section assumes that you have already set up your channels exactly as described above and that you have the graph on which they are set up open already.

1. Connect your subject. See the separate 
2. When you’re ready to begin data collection, press "Start".
2. You should be presented with a pop-up instructing you to calibrate the BioNomadix EDA sensor. Follow the instructions.
3. When you click "Calibrate," collection will begin, and you should see 4 channels separately gathering data in real time.
4. Check to make sure the waveforms look essentially like this example.
    * If the EDA graph looks like this, there is a connection problem between
    *

Test

<p><a href="https://en.wikipedia.org/wiki/File:EKG_limb_leads.png#/media/File:EKG_limb_leads.png"><img src="https://upload.wikimedia.org/wikipedia/en/f/fd/EKG_limb_leads.png" alt="EKG limb leads.png" height="1000" width="1500"></a><br>"<a href="https://en.wikipedia.org/wiki/File:EKG_limb_leads.png#/media/File:EKG_limb_leads.png">EKG limb leads</a>" by <a href="//en.wikipedia.org/wiki/User:Npatchett" title="User:Npatchett">Npatchett</a> - Created in Gimp. Licensed under <a href="http://creativecommons.org/licenses/by-sa/3.0/" title="Creative Commons Attribution-ShareAlike 3.0">CC BY-SA 3.0</a> via <a href="//en.wikipedia.org/wiki/">Wikipedia</a>.</p>



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

[Original]: Legacy/biopac_howto.docx
[MP150assembled]: .Pictures/MP150assembled.png
[AT-FS708]: .Pictures/AT-FS708.png
[MP150selection]: .Pictures/MP150selection.png
[BlankGraphCreation]: .Pictures/BlankGraphCreation.png
[BlankGraph]: .Pictures/BlankGraph.png
[SetUpChannels]: .Pictures/SetUpChannels.png
