# POTENTIOMETRIC DIGITAL-TO-ANALOG CONVERTER
The project aims at designing a `potentiometric digital-to-analog converter` using end-to-end `open-source EDA` tools. The key idea is to design the IP to achieve specifications similar to the target specifications using `osu180nm`.

# Why digital-to-analog converter?
A computer is designed to work in a digital domain.In today's world, the existence of digital electronics is boundless.Despite such advancement,the world is yet analogous and this seems to be inevitable. Hence,there is a need for a bridge between the digital and analog domains.On that account,there comes a need for digital-to-analog and analog-to-digital converters. 

# Quick glance of the IP
With the advent of high performance digital circuits,the need for data converters with high speed and accuracy for a wide range of applications has drawn the attention of scientists and researchers worldwide.In this project we tried to design a potentiometric digital-to-analog converter.This repository consists of all the details required to design a potentiometric dac and know its characteristics. Digital to Analog converter(DAC) is a device that converts the digital signals to analog signals. It reconstructs the sampled data into an analog signal . The digital data might be produced from Field programmable gate array(FPGA) or a microprocessor or Application specific integrated circuit(ASIC) but in order to interact with the real world, the data requires conversion to analog signal.DAC converter have various architectures like Kelvin divider (String DAC), Segmented string DAC and Digital potentiometer (slightly modified Kelvin DAC).The slightly modified version of Kelvin DAC is the potentiometric DAC. The key idea is to design a `10 bit potentiometric DAC` with 3.3v analog voltage, 1.8v digital voltage and 1 off-chip external voltage reference using osu180nm tech node. To develop an insight into the project and its specifications, download the `pdac_IP` pdf document uploaded in this repository. Also, to get better understanding of the IP read the ```potentiometric DAC``` file uploaded above.The dimentions of the designed IP are 333umX150um (widtheXheight).

# Device in action
![symbol](https://user-images.githubusercontent.com/68046197/87008502-77353700-c1e1-11ea-8298-f75e5a0534a6.jpg)
# Terminal Functions
| Name | No. | I/O  | Description | 
| :---:  | :-: | :-: | :-: |
| D[0:9] | 1-10 | I | Digital inputs |
| EN | 11 | I | Enable pin |
| VDD | 12 | I | Digital power supply(1.8) |
| VSS | 13 | I |  Digital ground|
| OUT| 14 | O | DAC analog voltage output|
| VDDA| 15 | I | Analog voltage supply (3.3) |
| VSSA | 16 | I | Analog ground |
| VREFH | 17 | I | Reference voltage high for DAC|
| VREFL | 18 | I | Reference voltage low for DAC|

# Parameters

| Parameter| Description| Min | Type | Max | Unit | Condition |
| :---:  | :-: | :-: | :-: | :---:  | :-: | :-: |
|RL|Load resistance| 50|||Mohm|T=-40 to 85C|
|CL|Load capacitance|||1|pF|T=-40 to 85C|
|VDDA|Analog supply| |3.3||V|T=-40 to 85C|
|VDD|Digital supply voltage||1.8||V|T=-40 to 85C|
|VREFH|Reference voltage high|||3.3|V|T=-40 to 85C|
|VREFL|Reference voltage low|0|||V|T=-40 to 85C|
|RES|Resolution| |10||bit|T=27C|
|INL|Integral Non-linearity||9.6||LSB|T=27C|
|DNL|Differential non-linearity||-1.6 to +0.6||LSB|T=27C|

1) Integral nonlinearity (INL), also referred to as linearity error, is the maximum deviation of the output from the line between zero and full scale excluding the effects of zero code and full-scale errors. The INL is calculated for code 0-63. 
2) The differential nonlinearity (DNL), sometimes referred to as differential error, is the difference between the measured and ideal 1LSB amplitude change of any two adjacent codes. The DNL is calculated for code 0-63. 


# Future work
1) The target dimensions of the IP are 195.58X117.45 (widthXheight). The achieved dimensions are greater than the expected. We are looking into other ways of designing the layout like lclayout to give better results in terms of size.
2) Due to the complexity of the circuit, the runtime is huge. Hence, for now INL and DNL are calculated for digital code 0-63. The values will be updated as and when they are found through simulation.
3) The layout has to be verified in openroad to check the compatibilty of the designed IP.
4) PNR is pending.
5) Few parameters are yet to be updated.
# Open Source EDA Tools used to design the IP
``` LTSpice XVII ```-LTspice® is a high performance SPICE simulation software, schematic capture and waveform viewer with enhancements and models for easing the simulation of analog circuits.

``` Ngspice ```-ngspice is the open source spice simulator for electric and electronic circuits. Such a circuit may comprise of JFETs, bipolar and MOS transistors, passive elements like R, L, or C, diodes, transmission lines and other devices, all interconnected in a netlist. 

``` Magic VLSI```-Magic stands for Manhattan Artwork Generator for Integrated Circuits. It is a vlsi layout tool. As free and open-source software magic continuesto be a popular layout tool as it is easy to and expand for specilised tasks.

## Steps to install ``` LTSpice XVII ``` on LINUX
1. It's not directly supported, so we need to download ```WineHQ```. Wine is a linux software that creates windows environment and allows you to run various windows programs.
2. Copy paste the commands mentioned below one after the other in the terminal for downloading and installing.
``` 
sudo dpkg --add-architecture i386
wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ focal main'
sudo apt update
sudo apt install --install-recommends winehq-stable
```
3. Download [LTSpice](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html).
4. Click on ```Download for Windows```.
5. Install it by clicking on ``` -> next ```.
6. After installing , click on open with ```WineHQ windows program loader```.
> ```LTSpice``` is now installed and you can design the circuit```

## Steps to install ``` LTSpice XVII ``` on   WINDOWS
1. Just click on [LTSpice](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html) and go to ```Download LTSpice->Download for Windows```.
2. Now click on the application ltspice from your ```downloads``` and accept and continue.
> ```LTSpice``` is now installed and you can design the circuit by opening it.

## Steps to install ```Ngspice``` on LINUX

It’s Super Easy! simply click on Copy button to copy the command and paste into your command line terminal using built-in APT package manager.

1. Run update command to update package repositories and get latest package information ```sudo apt-get update -y```
2. Run the install command with -y flag to quickly install the packages and dependencies ```sudo apt-get install -y ngspice```
3. Check the system logs to confirm that there are no related errors.

Note: ```-y```flag means to assume yes and silently install, without asking you questions in most cases

## Steps to install ```Ngspice``` on WINDOWS

Click on [ngspice](http://ngspice.sourceforge.net/download.html) and go to ```Downloads->Download Latest Version```.

> ```ngspice``` is now downloaded and ready to use

## Steps to install ```Magic VLSI``` on LINUX
1. Download the [magic.sh file](https://drive.google.com/file/d/1F0y1xuYWIgeYEpzKnGlaCQH3urdSFc4E/view)

2. Copy paste the below commands one after another
``` 
cd Downloads/
chmod +x magic.sh
./magic.sh

```
 Magic tool will be opened with minimum technology file by default. 
 Follow below steps to open magic with osu180nm tech file.
 
3. Download the ```osu180nm.tech``` file from the uploaded files. Copy and paste the entire content in ```Text Editor``` and save it as ```osu180nm.tech```.

4. Open the Terminal and copy, paste the commands mentioned below.
```
sudo cp osu180nm.tech /usr/local/lib/magic/sys/
cd /usr/local/lib/magic/sys/
ls 
cd
clear
```
5. You have successfully added osu180nm.tech file!

6. Just open the terminal and type ```magic -T osu180nm.tech filename.mag``` to begin layout.

# Steps to clone the IP onto UNIX based systems
Cloning a github repository creates a local copy of a remote repo and this allows us to make any changes to the files locally without affecting the main repository. To clone the IP onto your system copy paste the commands given below one after the other.

```
$  sudo apt install -y git
$  git clone https://github.com/VSD-DACteam/avsddac_3v3.git
$  cd avsddac_3v3/pre-layout
```
# Pre-layout Simulations

*Note: Before you begin to simulate make sure that the model files i.e the .lib files uploaded in this respository are in the same directory that contains the .cir files.*

*All the details on how to design the schematics using LTspice have been mentioned in the README file of the folder 'pre-layout' of this repository.*

To enter the Ngspice Shell, open the terminal & type:
```
$ ngspice
```
To simulate a netlist, type:
```
ngspice 1 ->  source <filename>.cir
```
## 10 bitdac vout vs digital code graph

*note: Due to huge runtime, simulation is done for the first 64 digtal codes. This will be update as and when output for other codes is simulated.

![prelayout](https://user-images.githubusercontent.com/68046197/87139148-22ff8500-c2bd-11ea-9aa4-d45c5aa45103.jpg)

*note: The above graph is the hardcopy generated from ngspice. The staircase output is not clearly seen as the hardcopy distinguishes between various colors using dashed and dotted lines. To have a look at a better picture, please navigate to ```prelayout_plot``` uploaded in the repository.*

You can exit from the Ngspice Shell by typing:
```
ngspice 1 ->  quit
```
## To obtain Vout/Vref vs digital code characteristics @T=27C

Open your terminal and change the working directory to the folder where your netlist file is saved.
Run the netlist file using the following command.
```
$  ngspice 10bitdac.cir
```
The obtained graph shows the voltages outputs for first 64 values i.e digital code 0-62. Note down the displayed values which will be used for plotting  vout/vref vs digital code graph using a plotting software. Here, SciDavis plotting software is used. The graph appears like the one shown below:
![voutvref](https://user-images.githubusercontent.com/68046197/87396861-19ce2b00-c5d1-11ea-8c99-f35a8496c17c.JPG)

## To obtain DNL vs digital code characteristics @T=27C and VREF&VDD=3.3

The differential nonlinearity (DNL), sometimes referred to as differential error, is the difference between the measured and ideal 1LSB amplitude change of any two adjacent codes. Using the values noted earlier and the formula given below find all the DNL values. These vaues are uploaded in the repository with the name `DNL`.
```
DNL(LSB)= (Actual height- Ideal height)/1LSB
```
The DNL vs digital code graph is shown below:

![dnl](https://user-images.githubusercontent.com/68046197/87149911-bbeacc00-c2ce-11ea-95db-2c3d323362b6.JPG)

## To obtain INL vs digital code characteristics @T=27C and VREF&VDD=3.3

The relative accuracy or integral nonlinearity (INL), sometimes referred to as linearity error, is the maximum deviation of the output from
the line between zero and full scale excluding the effects of zero code and full-scale errors.
```
INL(LSB)= (Actual vout-Reference vout)/1LSB
```
The INL vs Digital code graph is shown below:
![inl](https://user-images.githubusercontent.com/68046197/87149912-bdb48f80-c2ce-11ea-8898-6aa4a859b667.JPG)
# Magic Vlsi layout design steps:

Now to open Magic and start designing the layout, paste the below command in the terminal
```
$ magic -T osu180nm.tech filename.mag
```
This creates a .mag file to design your layout. DAC requires hierarchial designing i.e we have create instances of lower level blocks to built an overall dac.
To create an instance type in the following command in the tkcon window that open along with the magic layout window.
```
getcell blockname.mag
```

After the layout is designed, it is time to save the layout. Use the below command to save layout
```
save filename.mag
```
To generate the netlist use the following commands in the magic interpreter.
```
extract all
```
```
ext2spice -cthresh -rthresh filename.ext
```
This saves a file with the extention .spice which is our required netlist.

To exit from magic, use the following command in tkcon window
```
quit
```
## 10bit layout
The picture below shows the layout of a 10bit potentiometricdigital-to-analog converter

![10bitlayoutfinal](https://user-images.githubusercontent.com/68046197/87396877-20f53900-c5d1-11ea-929f-0a4c3751fafb.JPG)

## Post-layout simulations
Once the magic file is extrated to spice, a .spice file is created. Copy the data from this file and create a separate document with .sp extention. Now, add voltage sources and transient alaysis statement and the control statements . This is now ready for simulation. Similar to what has been done with pre-layout, open ngspice and run the .sp file. Copy and paste the commands given below one by one in the terminal.

```
$ ngspice
$ source filename.sp
```

Now, note the values displayed and follow a similar process given for pre-layout simulation and plot in SciDavis.

## Vout/Vref vs digital code characteristics @T=27C

The graph below shows post-layout Vout/Vref Vs digital code chaacteristics for the 0-64.

![voutvrefpost](https://user-images.githubusercontent.com/68046197/87395672-5d279a00-c5cf-11ea-80f5-4978c9f8026c.JPG)

## DNL vs digital code characteristics @T=27C and VREF&VDD=3.3

The below graph shows the DNL values for the digital code ranging from 0-63.

![DNL post layout](https://user-images.githubusercontent.com/68046197/87395685-6284e480-c5cf-11ea-9c4b-4bc4398a52e8.JPG)

## INL vs digital code characteristics @T=27C and VREF&VDD=3.3

The plot shows the INL values for digital code ranging from 0-63.

![NewINL(0-63) (1)](https://user-images.githubusercontent.com/68046197/87395681-5f89f400-c5cf-11ea-93b8-c88036a4aa97.png)

| Parameter| pre-layout (LSB)| postlayout (LSB) |
| :---:  | :-: | :-: |
|DNL|-1.6 to +0.6|-1.5 to +0.59 |
|INL|+9.6|+9.5 |


It can been seen that both the pre-layout and post-layout characteristics for 0-63 digital code are in good match.

For any support, please contact the administrator or report in ```issues``` in Github.


# Authors
Bellana Avinash Naidu, Neelam Buddhiram Chaurasiya, Jayasri Veeravilli

# Contact information
- Bellana Avinash, B.Tech, NIT Rourkela, avinashbellana@gmail.com
- Neelam Buddhiram Chaurasiya, BE-Degree, VESIT Mumbai, chaurasiyaneelam001@gmail.com
- Jayasri Veeravilli, B.Tech, SRM University, jayasriveeravilli@gmail.com
- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com
- Philipp Gühring, Software Architect, LibreSilicon Assocation pg@futureware.at

