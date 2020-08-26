# CoincidenceMCA
A LabVIEW and M or X series data-acquisition (DAQ) card based Multi-Channel Analyser (MCA) for use in coincidence counting experiments featuring an Ortec 567 Time-To-Amplitude (TAC) converter. This is an alternative to a commercial MCA that uses one of the ADCs on board an NI DAQ card together with LabVIEW software that interfaces to the card and produces a timing spectrum in the form of a histogram.

This repository includes the MCA functional global variable (FGV) as well as two example LabVIEW programs demonstrating its usage:
1. SimpleExample_MCA_Program.vi is a bare bones program that is the minimum usable case. The data-acquisition (DAQ) card analog input hardware is set up to perform analog readings triggered by the rising edges of digital input pulses. The main loop runs continuously to check the DAQ card's first in first out buffer (FIFO) and convert any acquird voltage readings back to times as measured by the TAC. These get added to bins in a histogram to make up the continuously updated timing spectrum. Once the front panel Stop button is pressed, the analog hardware is released so it may be used by other programs, and the program stops running.
![SimpleExampleProgram.png](images/SimpleExampleProgram.png)
2. EventStructureBasedExample_MCA_Program.vi is a more fully featured program that makes use of most of the MCA FGV's functions. It uses an event structure to handle interactions with the front panel to show how to integrate the MCA FGV from within a more fully featured program.
![EventStructureDemo.png](images/EventStructureDemo.png)


## Getting Started

1. Pull the github repository to your local machine or download the zip file and unzip it. 
2. Wire up the TAC output to the chosen analog input channel.
3. Wire up the TAC Valid Conversion output to the chosen digital trigger input channel.
2. Run either of the test programs in LabVIEW.

### Prerequisites

* LabVIEW 2014 or later.
* M or X series NI DAQ card.
* TAC that features Valid Conversion digital trigger pulse output such as the Ortec 566 or 567.
* The Valid Conversion pulse's rising edge MUST take place during the peak of the TAC output pulse for the DAQ card to accurately sample the peak voltage.

## License

This project is licensed under the GPL-3.0 License - see the [LICENSE](LICENSE) file for details