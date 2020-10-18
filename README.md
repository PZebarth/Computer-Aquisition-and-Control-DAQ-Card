# Computer-Aquisition-and-Control-DAQ-Card
## Project Description
LabVIEW 2016 was used to develop a Virtual Instrument (VI) using a Data Acquisition (DAQ) card. This VI supplies and sources AC voltage to low pass, high pass, and notch filter circuits chosen from Horowitz and Hill: The Art of Electronics. The VI’s purpose was to take a user defined frequency range and analyze the circuits response over those frequencies. 
## Project Design Considerations
This VI is designed to output a voltage at a user defined frequency, so low, high and notch filter circuits can sweep over their 3 dB frequency values. Using the device specifications of NI 6259, the program can be designed within the limitations of its operation. The relevant information considered in the design is; the analog output impedance of 0.2 Ohms, the analog input impedance between input and ground (AI+ to AI GND) which is >10 GOhms and the output current drive of +/- 5 mA (National Instruments, 2016). In addition, through testing, the analog output maximum frequency was determined to be 50kHz, with smooth sine waves, this VI uses frequencies of ≤20 kHZ. <br>
<br>
The frequency was limited by the number of samples the analog output wrote. The number of samples was chosen to be 100, which is enough to create smooth data points over the range of frequencies considered. The limitation is imposed by the loop that the DAQ Assistant is written in. Increasing the samples written requires the iterations to slow down because it increases the amount of data the analog inputs have to read. Within the parameters of the NI PCI-3259 DAQ card, the circuits were designed to be analyzed at an optimal 3dB frequency (approximately 3-7 kHz). However, this VI can be used to analyze circuits up to a 3dB frequency of <9kHz. When designing a notch filter to analyze using this program, remember to consider the low input impedance, which would result in the voltage source of the DAQ card to be affected by the current change in the circuit. The program shows the ratio of the output and input voltages, and therefore this effect of the change in current is cancelled and not shown. <br>
<br>
The program iterates a loop, changing the lower frequency to the upper frequency in steps of 100 Hz. The iteration step size was chosen because the circuits need to be analyzed over a large frequency and a smaller step size is not needed for smooth data plots. The iterations were restricted to every two seconds to allow the VI time to write the analog output samples (voltage sine wave) and read the two input samples (voltage sine wave). You can increase the step size, time delay between iterations, written samples, and read samples manually if computing time is not an issue. The analog output voltage was set at an amplitude of 1V due to the fact that only the ratios matter for analysis. This VI completes the task with sufficient data in reasonable time. <br>
## File Descriptions
> DAQ Project Report.docx - Report outlining requirements, program design, and user interface
> DAQ Project VI.vi - Virtual Instrument file for analyzing low pass, high pass, and notch filter circuits
## Using the Virtual Instrument
> 1.	Define an upper frequency less than 20000 Hz and greater than the lower frequency <br>
> 2.	Define a lower frequency less than 19000 Hz and less that the upper frequency <br>
> 3.	Choose a file name and path directory to save your file <br>
> 4.	Run the VI <br>
> 5.	User option to use cursor to retrieve values from gathered data, simply use your mouse to drag cursor around the graph, values are outputted to cursor table <br>
> 6.	A dialog box will open and ask if you want to save your file <br>
> 7.	Repeat steps 1-5 with different file names for different circuits <br>
