## Fall 2015 CIPI Acq*Knowledge* File Structure

The exported files should be `.txt` files, each with hundreds of thousands of lines. Each line is a single sample of the data, representing $\frac{1}{2000}$ of a second, since data were recorded at a sample rate of 2 kHz.  

The data will look something like this:  
```
0.0209045	10.788	0	71.2589  
0.0157166	10.7895	5	71.2589  
0.010376	10.7895	5	71.2589  
0.00549316	10.791	5	71.2589  
0.000305176	10.791	5	71.2589  
-0.0050354	10.788	5	71.2589  
```

Each of these columns represents a "channel" in the data, and is separated from the next column by a `tab` character.

The first column represents the ECG data in millivolts, and should alternate between positive and negative values roughly twice per second (every 1000 lines).

The second column represents EDA data in microsiemens, and should always be positive, usually between 3 and 20.

The third column consists of digital input from the SuperLab stimulus, via the Stim**Tracker**. This column should contain no values but `0` and `5`. `0` represents no input, and `5` represents active input. After the onset and end of each stimulus, there is a burst of input roughly 10 milliseconds long.  
There ought to be 14 bursts of `5`s in each file. The first pair of bursts bookend the first video, the second pair the second, etc., through the sixth. The seventh pair represent the beginning and end of the discussion stimulus. The individual components of the discussion stimulus are not marked by bursts, so it will be necessary to separate them by their times. The first text stimulus, telling the participant that there will be a discussion, is 30 seconds long (60000 lines). The second, giving them information on their discussion parter, is also 30 seconds. The third and final text, telling them the topics and asking them to prepare, is 2 minutes 30 seconds (300000 lines).  
For the first 6 participants (`409604`, `288092`, `614365`, `728490`, `378959`, `589338`), the SuperLab channel will be different. Unfortunately, in these files, there will be only 7 bursts, marking the beginning of each stimulus. The bursts are each 10 seconds (20000 lines) long. There is no burst at the end of each stimulus in these files.

The fourth column represents heart rate in beats per minute, calculated from the ECG data in the first column. Values should only include reasonable heart-rates, excluding artifacts in the data, including participant movement. This value will only change every heart beat, once or twice per second.
