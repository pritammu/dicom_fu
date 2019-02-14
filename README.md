# dicom_fu
Contains code for all things dicom

## dicom_exploration.py
This script is useful for summarizing metadata from dicom files. Assuming proper directory structure: patients/Studies/Series/dicom_files (mainly assumes all dicom files are in the leaf nodes) it looks for CT or MR files (at present only CT and MR are implemented), reads the dicom headers using pydicom and collects the desired fields in desired format.  
#### Usage: 
You can use the functions separately or as a script. To use as a script: 

**./dicom_exploration.py ROOT -o OUTPUT_FILE**

where ROOT (required argument) is the root directory containing the dicom files (the code recurses through subdirectories), and OUTPUT_FILE is the name of the output file (.csv) - this argument is optional, by default it is summary.csv.

##### Customization
You can change the tags of interest by changing the CT_TAGS_OF_INTEREST or MR_TAGS_OF_INTEREST variables. These are python dictionaries in the format {key1: format1, key2: format2,...} where key1, key2 are dicom tags and format1, format2 are functions which specify how to process the read dicom tags. This is useful because most tags are read as strings, which one should be converted to useful types. For example, PixelSpacing is read as a list of two strings (for 2D images), but we may want to have a numpy array of two floats, instead. 

#### Requires:
  - autopep8==1.4.3,
  - cycler==0.10.0,
  - kiwisolver==1.0.1,
  - numpy==1.16.0
  - pandas==0.24.1
  - pycodestyle==2.4.0
  - pydicom==1.2.2
  - pyparsing==2.3.1
  - python-dateutil==2.7.5
  - pytz==2018.9
  - six==1.12.0
  - tqdm==4.31.1
