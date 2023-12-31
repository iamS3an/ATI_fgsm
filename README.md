# Attack Tendency Index based Adversarial Training Model for Defending Intrusion Detection Against Gradient based Adversarial Attacks

 A repository for our research on "Adversarial Training for Network Intrusion Detection." This repository provides code and resources related to our work aimed at defending against adversarial attacks in neural network-based intrusion detection systems.  

### Experiment process record (2023/9/26): [Here](https://drive.google.com/file/d/1Rscp5CSS1KwQIVxskUlUuwoMs-IhNGMa/view?usp=sharing) 

## Dataset Selection:

### IOT23 Dataset:

### Download Link: [Here](https://drive.google.com/file/d/1T1pCAKYZYwzPH_8fL0Rz4gYrO0NPzif4/view?usp=sharing)  

### Combination:

Combine all files from the official website.  

Select 13 features.  

> Note: The "tunnel_parents" feature was not used in the experiments.  

* Benign:  

Select all records with less than 100,000 entries.  

For files with more than 100,000 entries:  

Randomly select 90,000 entries from each of the 4 files.  

Total benign records: 531,346.  

* Malicious:  

Select all records with less than 100,000 entries.  

For files with more than 100,000 entries:  

Randomly select 36,000 entries from each of the 14 files.  

Total malicious records: 533,506.

* All: 1,064,852.  

Approximately maintaining a 1:1 ratio between benign and malicious records.  

### CICIDS2017 Dataset:

### Download Link: [Here](https://drive.google.com/drive/folders/14KaYkeGKWTrW7f0AR5cOAUEVT-51DDFV?usp=drive_link)  

### Combination:

Select files: `Wednesday-workingHours.pcap_ISCX.csv`, `Friday-WorkingHours-Afternoon-PortScan.pcap_ISCX.csv`, and `Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv`.  

### Data Preprocessing:

Run `preprocess_raw.py` to generate `CIC_data.csv` and `CIC_label.csv`.  

Run `normalize.py` to generate `CIC_normalize.csv`.

## Package Requirement

* Keras
* TensorFlow
* Numpy
* Pandas
* Scikit-learn

## Getting Started

### 1. Initialization:

Run `norm_split_train_test.py`.  

First, it will create folders that will be used later in the program execution.

The files to be splited are the ones that have just been normalized. 

This will generate `train.csv` and `test.csv` in the "origin" directory.  

### 2. Generating Adversarial Samples:

Use `main_seq.py` to generate adversarial samples.  

The output files will be in various "eps" value folders within the "origin" directory.  

If you set the status parameter in `main_seq.py` to "ATI," files will be generated in the "ATI" directory.  

Ensure that you have previously calculated ATI values for the "origin" dataset and placed them in the "ATI" directory before running.  

### 3. Adversarial Sample Detection:

Execute `adv_det_seq.py` to load the original and generated adversarial samples.  

It will perform training and detection.  

### 4. Recovery:  

After generating adversarial samples and calculating their ATI values, you can execute `recovery.py`.  

### 5. Adversarial Training to Distinguish Original Labels:   

> Note: This experiment wasn't conducted in the part of CICIDS2017.

Execute `atk_eval_seq.py` to load the original and generated adversarial samples with their original labels.  

It will perform training and evaluating the original labels.  

### 6. How to conduct the part of ATI experiment:

Run `preCT_adv_det_seq.py` to generate files in the "adv_det_preATI" directory.  

Calculate ATI values for these files and place them in the "adv_det_doneATI" directory.  

Finally, execute the corresponding files named with "_ATI" for both adversarial detection and training.

## Contact
Feel free to contact me at:  

Huan Cheng Lin (Sean Lin) - seanlin12345@gmail.com

