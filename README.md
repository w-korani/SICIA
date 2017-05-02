# SICIA: Seed Infection Coverage and Intensity Analyzer
Image processing software for analyzing seed coverage infection,

the program was designed mainly for analyze peanut seeds which infected by GFP-Aspergillus-flavus strain.

However, it is suitable for a large application, for other species and other methods of infection.

# Citation: the paper will be publish soon.

The folder containing seed images and GFP-images (or infected images) are set in 'INPUT' panel.

Note, the images in the GFP-folder and seeds images SHOULD HAVE THE SAME ID AND SHOULB BE IN jpg FORMAT. if the number of the files in the two folder not equall, the program will trigger an error.

The output folder and csv file are set in 'OUTPUT' panel.

Number of seeds to be analyzed can be set, the default is 1 to be analyze one seed. if you analyze multiple seeds, you have to set the number.

'Background' panel is used to set the best cutoff for seed normalization, the value should <1 and >0, the user can test different values using 'Test' button.

'GFP' panel is used to set the best cutoff for infection normalization, the value should <1 and >0, the user can test different values using 'Test' button.

'Scale' panel is used to set the best cutoff for the scale, the value should <1 and >0, the user can test different values using 'Test' button.

scale should be in the upper left corner of the infected seed images, if the user does not have a scale in the images, the scale checkbox is unchecked. However, some values will not be calculated.

Once all parameters are set, 'Apply>>>' botton is pressed, the images will be processed in the sequence of input folders.

The output folder contains:
    
    1. The orginal seed image
    2. The normalized seed image
    3. The original infected image
    4. The normalized infected image
    5. the alignment of the normalized infected seed image to the normalized seed image

![23-5_github](https://cloud.githubusercontent.com/assets/21265433/25634815/35ec7e86-2f39-11e7-9553-859a37d6c437.png)

The output file is a CSV spread sheet file contains the following fields

    1. The image ID
    2. The seed size (in mm2)
    3. The infection size (in mm2)
    4. The outer infection size: is the infection that is outside the scope of the seed.
    5. The coverage infection size: is the infection that is inside the scope of the seed.
    6. The coverage percentage of the coverage infection to the seed scope
    7. The intensity of the infection
    8. The number of pixels included in the infection
    9. The average intensity: normalizing the intensity to the number of pixels included in the infection

note: if the user unchecks the 'scale' checkbox, fields 2, 3, 4, 5 will not be generated in the csv file.

![image](https://cloud.githubusercontent.com/assets/21265433/25634888/74b3663e-2f39-11e7-9000-359ad11ae951.png)

Testing the program:
A set of input files are available in the 'program files' folder of the windows under the following path \UGA\SICIA_v.1.0\application\testing_data

the testing data is run fine with the following paramters:

    background_cutoff = 0.3, GFP_cutoff = 0.6, Scale_cutoff = 0.28
