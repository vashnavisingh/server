# SEPIa
SEPIa package: installation and usage
Installation: Unpack SEPIa.tar using “tar -xvf SEPIa_soft.tar”. The package contains all the necessary information, data, scripts and executables for prediction of immunogenic regions on protein sequences.
Dependencies: Tested to work under: Python 3, scipy(>=0.17.0), numpy(>=1.10.4), pandas(>=0.18), scikit-learn(>=0.17.1), PsiBlast
Usage: Enter the working directory SEPIa and follow the intersections below.
Firstly, the users have to precompute all the features for the predicted chain: Use the instructions of how to calculate all the features in the folder “Features”. For every feature there is a separate text file with information. Prepare a cvs file with all the features. Add all the values in the given template “features.csv” file. In the column “State” add the value 99 for all the residues of your sequence (for your help see the example.csv file or the .csv file in the test folder).

Prepare the features in a sequence window of size 9 residues centered on the targeted residue:

Move the prepared features.csv file in the folder “window”, and execute the python script file: python createWindow.py features.csv
After, in the folder window/features execute the script “run”: ./run
The created .csv file with the name “features_w9.csv” is ready to use for the prediction. (Please note due to the creation of the window of size 9, the first four and the last four residues are not predicted)
Prediction Insert the paths inside the epitope_prediction.py file:
MyTestFile = pd.read_csv('/yourpath/SEPIa/window/features/features_w9.csv', sep=',') and
model = joblib.load('/yourpath/SEPIa/models/model1/model.pkl')
run the .py prediction file: python epitope_prediction.py
Output: The output will be displayed in the folder “prediction”. You will find a cvs file with the epitope prediction, where: Epitope residues = 1 and Non-epitope residues = 0
