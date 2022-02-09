# Detachable-Keys-Piano
Note: For Demo and Download section, scroll down to end.

## Table of Contents
- [ABSTRACT](#1-abstract)
- [METHODOLOGY](#2-methodology)
- [THEORY](#3-theory)
- [DESIGN AND IMPLEMENTATION](#4-design-and-implementation)
- [DEMO](#5-demo)
- [DOWNLOAD](#6-download)
- [ABOUT TOOLS USED](#7-about-tools-used)
- [ACKNOWLEDGEMENT](#8-acknowledgement)


## 1. ABSTRACT
Like all other fields, technology plays a crucial role in the musical world. 
Piano being one of the undetachable members of this world has to improve for the dynamic growth of the field. 
But it's abiding nature, difficulties in portability and increasing demand for the interconnection along with the virtual world (digital media) have given space for technophiles for development. 
‘DETACHABLE PIANO KEYS WITH DUPLEX TUTOR’ is an instrument that overcomes all these limitations by providing a set of keys which can be attached or detached as per the requirement of the user. 
So that the same instrument can cover a domain ranging from the novice to the trained and experienced musicians. 
The number of keys is decided by the user as per their requirement, so that they can be modified with ease by the user whenever their requirement is not met. 
Along with that after one set the keys based on their requirement, can be connected to digital media where on the other side the teacher will mentor all musical notes played by the students.
Below are the objectives for this work:
- To build an adjustable piano with its keys detachable/attachable.
- To transmit real time data from piano with recording option.
- To create a virtual music tutorial platform connected to ‘dynamic keys piano’.
- To develop and fabricate the detachable key piano circuit at affordable cost

Different frequency sounds can be produced with the help of a capacitor connected to a transistor based on charging/discharging time constants. 
By making stretchable cylindrical rods as base of a piano and making a combined pack of particular resistor, capacitor and transistor, to be fixable on the cylindrical rods, piano keys can be made attachable/detachable. 
The base of the piano consists of 3 main rods i.e. for power supplies and audio output, and 8-bit bus rods for transmitting data to cloud or any external devices.
The core of each key consists of 2 transistors, 8 resistors and 4 capacitors to adjust frequency along with a clipping mechanism to fit on base rods. 
8-bit unique binary sequence is provided for each key package. 
When we press the key, respective data is sent to the cloud via a controller (Node MCU ESP8266) along with its notation info, real-time with recording. Using this data in a graphical way, learners as well as composers can learn in duplex communication.


## 2. METHODOLOGY
<p align="center">
  <a href="https://ibb.co/rMVt0Rd"><img src="https://i.ibb.co/y5rRPc4/image.png" alt="image"><br> <em>Fig.1 Methodology</em> </a>
</p>

- Different frequency sounds can be produced with the help of a capacitor connected to a transistor based on charging/discharging time constants. 
- By making stretchable cylindrical rods as base of a piano and making a combined pack of particular resistor, capacitor and transistor, to be fixable on the cylindrical rods, piano keys can be made attachable/detachable. 
- The base of the piano consists of 3 main rods i.e., for power supplies and audio output, and 8-bit bus rods for transmitting data to cloud or any external devices. 
- The core of each key consists of 2 transistors, 8 resistors and 4 capacitors to adjust frequency along with a clipping mechanism to fit on base rods. 
- 8-bit unique binary sequence is provided for each key package. 
- When we press the key, respective data is sent to the cloud via a controller (Node MCU ESP8266) along with its notation info, real-time with recording. 
- Using this data in a graphical way, learners as well as composers can learn in duplex communication.

## 3. THEORY
Detachable keys piano duplex tutor can be mainly divided into following sub-modules.
1. **Oscillator Circuit:** This is responsible for the different frequency sound generation. Here 2 transistor oscillator models produce the variable, stable frequency output based on the value of the variable capacitance which acts as a time constant controller for the oscillator. The output of this oscillatory circuit is mainly taken out as local sound output. This circuit is an element of a key package
2. **Bus rod connected Switching Key Package (BSKP):** This forms the hardware base for the piano. Here the keys made with the help of different frequency oscillators are packed to form a key package with U clip hold mechanism. Here 2 in-out ports form the power supply for the key package, and 8 output ports form the binary data output from the package, which will be used for cloud data transmission. U clip hold arrangement ensures keys to fit on the base of the piano, i.e., cylindrical rods which includes 8 rods as data bus and 2 rods for power and 1 as output rod.
3. **Opamp amplifier:** The initial output from the piano is of lower amplitude which is barely audible. So, there we use an opamp which is connected with the output from the piano and the final output is the amplitude enhanced signal, resulting in loud and audible sound. Opamp based amplifiers ensure the gain of around 200. 
4. **Cloud Data Uploader:** This module connects the local piano output to the internet. Here the binary data obtained from the key package parallelly is converted to serial data and uploaded to cloud storage along with the conversion data from binary bit to musical notes. It forms the data backend for the duplex tutor platform. 
5. **Real Time Virtual Analyzer:** The notes played by the trainee should be monitored by the trainer, so that the learner could get the best output for his efforts. So, whenever the note that is played by the student is wrong, the mentor can correct it then and there and the student can rectify the problem without any delay. This kind of virtual analyser does not require high bandwidth to transmit the binary data. So, it solves time lag problems that have been observed through digital media for teaching.

## 4. DESIGN AND IMPLEMENTATION
The complete design of this detachable keys piano can be subdivided into physical-hardware piano construction and the digital hardware connected duplex tutor. 

1. ### Detachable Keys Piano Base:
<p align="center">
 <a href="https://ibb.co/cCyb4Rc"><img src="https://i.ibb.co/X3Wyc6Z/image.png" alt="image"><br> <em>Fig.2 Detachable Keys Piano Base</em> </a>
</p>
    
    - It mainly consists of the following: 
      - 8 bus rods for binary data transmission (B0 to B7)
      - Diode for each rod to prevent reverse flow of current back to the key package
      - 3 rods for:
        - Output
        - VCC
        - Ground
      - These are the cylindrical rods with a diameter of 0.5cm. 
      - These rods can be stretched or compressed based on the requirement of the size of the piano.
      - These rods act as the base for the key package which has to be placed on it through the clip arrangement. 
2. ### Key Package
<p align="center">
 <a href="https://ibb.co/yNN1W7d"><img src="https://i.ibb.co/511yBwG/image.png" alt="image"><br> <em>Fig.3 Key Package designed using Esim-KiCad</em> </a>
</p>

    - The Key Package forms individual buttons of the piano. 
    - This has to be attached to the base through the clip-hold arrangement. 
    - This package takes the power supply from the base rods and on the switch press, it will generate the frequency signals. 
    - These frequency signals again pass through the base rod called “out” of the piano which is connected to the speaker via amplifier. 
    - Each key package even outs the binary bit data which is unique for a key. Each key package consists of the following:
      - Pair of NMOS
      - Resistors - 120k,10k(3),6k,1k(2),6.8k
      - Capacitors - 100n,0.5n,5.1n, variable
     
    - Here, the transistors M9 and M10 form the oscillator circuit, and its oscillation frequency is controlled by the charging constant of the capacitor C5. 
    - C3 is kept constant to maintain the M10 transistor in the saturation region. 
    - Output is taken across the voltage divider junction at a node between R4 and R5. 
    - Based upon the value of the capacitor C5, the oscillation frequency changes. 

- _DC Analysis_ of the oscillator key package ensures that, to keep the transistor in oscillatory phase and to maintain in saturation, 5v is sufficient.
- While carrying out DC Analysis of BJT circuits,
    - Capacitors act like an open circuit. (f=0, XC=∞)
    - Inductors act like a short circuit (f=0, XL=0)

- Below waveform shows the _Transient Analysis_ of the circuit for variable capacitor value of 120nF. 
- The frequency of the generated waveform is around 440 Hz with amplitude of around 200mV for 5 volt input supply by using nmos pair (sky130pdk) and around 36mv by using bc547bp transistors pair in place of nmos

     - #### Construction and Simulation using **Esim and Sky130 pdk**
            - Construction of this key package is done using Esim and Sky130 pdk is used for it's components.
            - Simulation is done using ngspice
          - <p align="center"><a href="https://imgbb.com/"><img src="https://i.ibb.co/D7GfBHN/safl-oscillator-ngspice.png" alt="safl-oscillator - transient analysis -ngspice"><br> <em>Fig.4 oscillator - transient analysis -ngspice</em> </a></p>
          -  <p align="center"><a href="https://imgbb.com/"><img src="https://i.ibb.co/NCVQgbS/safl-oscillator-transient.png" alt="safl-oscillator-transient"><br> <em>Fig.5 oscillator - transient analysis report -ngspice</em> </a></p>
  
 - _Spectrum analysis_ of the output is done using proteus
            - <p align="center"><a href="https://ibb.co/sstJS8Y"><img src="https://i.ibb.co/xz38vxT/image.png" alt="safl-oscillator -spectrum analysis -proteus"><br> <em>Fig.6 oscillator - spectrum analysis -proteus</em> </a></p>

3. ### Opamp Amplifier
<p align="center">
 <a href="https://ibb.co/xLp9x4V"><img src="https://i.ibb.co/54Npb7q/image.png" alt="image" ><br> <em>Fig.7 Opamp Amplifier designed using Esim-KiCad</em> </a>
</p>

    - To amplify the output of oscillator circuit, a Two Stage CMOS Op-erational Amplifier using SkyWater 130nm Technology is used
    - It has a NMOS differential amplifier followed by a PMOS Common Source Amplifier to provide gain of aroud 40dB. 
    - The output from the differential pair is taken as single ended. 
    - This single ended output is fed to PMOS common source amplifier
    - This opamp is biased using constant current source of 10uA.


```
* /home/rohitlinux/eSim-Workspace/opamp5.cir
.lib "skywater-pdk-libs-sky130_fd_pr/models/sky130.lib.spice" tt

*oscillator
xM9  Net-_C3-Pad2_ Net-_M9-Pad2_ Net-_C4-Pad1_ Net-_C4-Pad1_ sky130_fd_pr__nfet_01v8 L=1 W=20
xM10  vdd Net-_C3-Pad2_ Net-_C5-Pad1_ Net-_C5-Pad1_ sky130_fd_pr__nfet_01v8 L=1 W=20


R3  vdd Net-_C3-Pad2_ 10k	
R6  Net-_C4-Pad1_ Net-_C6-Pad1_ 1k		
R7  Net-_C6-Pad1_ GND 10k
R8  Net-_C5-Pad1_ GND 6.8k
R4  Net-_C4-Pad2_ out1 6k
R5  out1 GND 1k
R1  vdd Net-_M9-Pad2_ 33k
R2  Net-_M9-Pad2_ GND 10k	

C3  vdd Net-_C3-Pad2_ 5.1n	
C5  Net-_C5-Pad1_ Net-_C4-Pad1_ 110n	
C4  Net-_C4-Pad1_ Net-_C4-Pad2_ 100n
C6  Net-_C6-Pad1_ GND 0.5n		


*Opamp
xM1  Net-_M1-Pad1_ out1 Net-_M1-Pad3_ Net-_M1-Pad3_ sky130_fd_pr__nfet_01v8 l=1 w=1.79	
xM2  Net-_C1-Pad2_ in2 Net-_M1-Pad3_ Net-_M1-Pad3_ sky130_fd_pr__nfet_01v8 l=1 w=1.79			
xM3  Net-_M1-Pad1_ Net-_M1-Pad1_ vdd_op vdd_op sky130_fd_pr__pfet_01v8 l=1 w=10	
xM4  Net-_C1-Pad2_ Net-_M1-Pad1_ vdd_op vdd_op sky130_fd_pr__pfet_01v8 l=1 w=10		
xM5  Net-_M1-Pad3_ Net-_I1-Pad1_ vss_op vss_op sky130_fd_pr__nfet_01v8 l=1 w=20
xM6  Net-_I1-Pad1_ Net-_I1-Pad1_ vss_op vss_op sky130_fd_pr__nfet_01v8 l=1 w=20
		
I1  Net-_I1-Pad1_ vdd_op dc	10u
	
xM7  out2 out2 vdd_op vdd_op sky130_fd_pr__pfet_01v8 l=1 w=62.83	
xM8  out2 Net-_I1-Pad1_ vss_op vss_op sky130_fd_pr__nfet_01v8 l=1 w=62.83

C1  out2 Net-_C1-Pad2_ 2p		
C2  out2 GND 10p		

v1  vdd GND DC 5		
v5  in2 GND 0	
v3  vdd_op GND DC 4		
v4  vss_op GND DC -4	

*Simulation Command
.tran 0.1us 25500us

* ngspice control statements
.control

run

*For Transient Analysis
*Oscillator Out
plot v(out1)
*Opamp out
plot v(out2)

.endc
.end
```

4. ### Binary Data Handler
  - Key package along with the data produces the binary information which is unique for each key. 
  - For an 8-bit data bus, the total number of unique binary patterns will be 2^8 - 1. i.e., 255 unique combinations exist excluding 0000_0000 which represents no key is pressed.
  - These parallel bit data are uploaded to firebase real time database using an esp8266 Wi-Fi module (node MCU). Binary data bits are converted to the corresponding musical notations.

5. ### Duplex Tutor Platform
  - This is the digital web interface of the hardware piano from the real time database. 
  - Buttons pressed on the hardware piano will directly reflect here. 
  - There will be a separate channel for a predefined set of detachable keys piano and a duplex tutor. 
  - It helps in advance learning of the piano for beginners. 
  - Both the learners and composers can interact in the most efficient way. 
  - For each individual duplex piano platform, there will be login credentials, learners and composers have to login to this portal along with the specified hardware. On successful login, the user will be redirected to the learning platform.
    - <p align="center"><a href="https://ibb.co/W6DF11Z"><img src="https://i.ibb.co/1LsKxx1/image.png" alt="image" ><br> <em>Fig.8.Learning Platform</em> </a>
</p>


## 5. DEMO
  - For demo proteus is used since it requires Internet connection to upload data from circuit to the cloud.

https://user-images.githubusercontent.com/44223447/152941079-f98747d9-9041-4570-9a5d-3cf15a5f7998.mp4

(In this video, specific transistors are used, in the schematic download files, these are replaced by NMOS)

## 6. DOWNLOAD
Files | Download
--- | --- 
**eSim: Schematic File** |  <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/esim_oscillator_and_opamp.zip"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**ngspice: Spice Code using Sky130pdk File** |  <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/ngspice%20simulation%20files.zip"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**LtSpice Files** | <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/LtSpice_files.zip"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**Proteus File** |  <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/proteus_files.zip"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**Node MCU, and Arduino Data Uploader Files** |   <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/arduino_nodemcu_codes.zip"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**Literature survey** | <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/Detachable%20Keys%20Piano%20-%20oscillator%2C%20audio%20amplifier.pdf"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**Report** |   <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/report-auto_genereted.pdf"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**Demo Video** |   <a href="https://github.com/ROHITDH/Detachable-Keys-Piano/raw/main/Detachable%20keys%20Piano%20-%20demo.mp4"><img src="https://img.icons8.com/officel/40/000000/download--v1.png"/> </a>
**WebApp Interface** |   <a href="https://dvrblacktech.pythonanywhere.com/detachablekeyspiano/greenleaves/">Requires Hardware/Proteus Files</a>

## 7. TOOLS USED
TOOLS | DESCRIPTION | DOWNLOAD
--- | --- | ---
**eSim EDA Tool** |  <a href="https://esim.fossee.in/home">Description</a> |  <a href="https://esim.fossee.in/downloads">Download</a>
**SkyWater SKY130 PDK** |  <a href="https://skywater-pdk.readthedocs.io/en/main/">Description</a> |  <a href="https://github.com/google/skywater-pdk-libs-sky130_fd_pr/archive/f62031a1be9aefe902d6d54cddd6f59b57627436.zip">Download</a>
**LTspice** |  <a href="https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html">Description</a> |  <a href="https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html">Download</a> 
**ngspice** |  <a href="http://ngspice.sourceforge.net/">Description</a> |  <a href="http://ngspice.sourceforge.net/download.html">Download</a>

## 8. ACKNOWLEDGEMENT

[Kunal Ghosh](https://github.com/kunalg123), Co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd.
[Sumanto Kar](https://www.linkedin.com/in/sumanto-kar-0424391a9), Sr. Project Technical Assistant, IITB
