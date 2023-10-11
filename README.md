## Installation
* [Arduino IDE](https://www.arduino.cc/en/software)
* [Microsoft Excel](https://www.microsoft.com/id-id/microsoft-365/excel) - for monitoring with Data Streamer
* Python 3.10 or above
* Python Notebook ([Jupyter Notebook](https://jupyter.org/), etc)

## Operation
### a. Arduino
1. Download .ino [here](https://github.com/dhiteory/glucometer/blob/main/non-invasive-code.ino)
2. Open the file with Arduino IDE and connect the NIR device
3. On Arduino IDE, adjust the Board and Port (in Tools). Board: Arduino Uno
4. After the device has connected, click 'Upload'
### b. Excel
1. Download .xlsm [here](https://github.com/dhiteory/glucometer/blob/main/PPG5000.xlsm)
2. Open the file with Arduino IDE
3. Activate the Data Streamer in Excel (File > Options > Add-ins > Manage: COM Add-ins > Go) Check on Microsoft Data Streamer for Excel, OK.
4. Go to Data Streamer tab, Connect a Device.
5. On the 'Plot' tab, right-click the 'SAVE TO CSV' button, select 'Assign Macro...' and then click 'Edit.' A VBA (Visual Basic for Applications) window will appear. Modify the 'Path = "C: ..." to match the CSV file's destination address that you want to save in a specific folder.
6. Save Excel file
7. Start Data
The signal should appear like a photoplethysmograph (PPG) signal. If not, try adjusting the values in the .ino file at lines 9 and 10 (It needs to be uploaded again, of course).
7. If you feel that all the data has been filled, click 'Stop Data'.
8. Click SAVE TO CSV

### c. Train and Test
1. Download .ipynb [here](https://github.com/dhiteory/glucometer/blob/main/Glucose.ipynb)
2. Open the file with Python notebooks (for example with Jupyter Notebook)
3. Separate the .csv files for training and testing into different folders named 'train' and 'test'. Make sure the .ipynb file is in the same location as the 'train' and 'test' folders.
In the Python Notebook file, 'Run All' In the Neural Network section, you will find 'clf = MLP...' Adjust the number of hidden layers and activation type as needed. You can find information about the library [here](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html). The 'Simpan NN' section (means: Save Neural Network) indicated by the '#' symbol is currently inactive. Above it, there is a table of training results. If the results are not satisfactory, try adjusting the test-train data ratio, the number of neurons and layers, the activation type, and train repeatedly for better results. When you feel the results are good, activate 'Simpan NN' and then run that section (change the name 'ann_005' to match the name you want to save for training). The file should be saved in the same folder. Don't forget to deactivate 'Simpan NN' with '#' to prevent overwriting new training results.

To display the saved training results, go to the 'Muat NN' section (means: Load Neural Network) and change 'ann_004' to the name of the training file you specified. Run only this cell.
<p align="center">
  <img width="300" src="https://github.com/dhiteory/glucometer/assets/23611802/54e2f384-25ee-4321-beaa-29bbdea1df8a">
  <br>Example of Directory
</p>
