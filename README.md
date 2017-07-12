# SICIA: Seed Infection Coverage and Intensity Analyzer
Image processing software for analyzing seed, leaf, stem, ... coverage infection,

the program was designed mainly for analyze peanut seeds which infected by GFP-Aspergillus-flavus strain.

However, it is suitable for a large application, for other species and other methods of infection.

# Citation, please cite to:
Korani, W. A.; Chu, Y.; Holbrook, C., Clevenger, J. and Ozias-Akins, P. (2017). Genotypic Regulation of Aflatoxin Accumulation but Not Aspergillus Fungal Growth upon Post-Harvest Infection of Peanut (Arachis hypogaea L.) Seeds. Toxins, 9(7), 218.

# SICIA version 1:

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
A set of input files are available in the 'program files' folder of the windows under the following path 
    
    \UGA\SICIA_v.1.0\application\testing_data

the testing data is run fine with the following paramters:

    background_cutoff = 0.3, GFP_cutoff = 0.6, Scale_cutoff = 0.28
    
# SICIA version 2:

The folder containing images is set in 'Input/Output' panel.

Images' types should be setting by user, the default is jpg. The analysis will done only for files having the set extenstion.

output folder and file should be set in 'Input/Output' panel.

level, noise, filter, scale and invert_image should be set for infection and background:
  it is tested by Test_cutoffs button.
  Set buttons are used to set the selected parameters to infection or backgound.
  Refresh buttons are used to allow user to re-set the parameters to infection of background

It is preferable to set the background paramaters before the infection

In some cases, when the infection pattern has colours close to the backgound of the orginal images (such as darkbrown and black), 
  Image-subtraction is used to solve the issue, it is only availabe to infection.

If the user has scale, it should be in the UPPER LEFT corner of the image and the diameter can be set in milimeters. 
  the default is 26.5 mm which is the diameter of USA 1 dollar coin.
  
  
The output folder contains:

    1. The orginal image
    2. The filter image
    3. The infection pattern
    4. the alignment of the infection to the backgound

The output file is a CSV spread sheet file contains the following fields

    1. The image ID
    2. The back size (in mm2)
    3. The infection size (in mm2)
    4. The coverage percentage of the coverage infection to the seed scope
    5. The intensity of the infection
    6. The number of objects
    7. The average intensity: normalizing the intensity to the number of objects
    
note: if the user unchecks the 'scale' checkbox, fields 2, 3, will not be generated in the csv file.

note2: paramters 6 and 7 are used to count and normalze to number of infected leaves, seeds, stem, or any plant parts used in the image,
       therfore, if the number of object is differnt than number of plant parts in the original image, 
       the user should re-analyze and use more suitable settings
       
Note3, Although, the program can deal with differnt single color background images, the black background is preferable.

Testing the program:
A set of input files are available in the 'program files' folder of the windows under the following path 
        
    \UGA\SICIA_2.0\application\input_test.

The outputs are available too.


the testing data is run fine with the following paramters:

Stem infection:

Testing image: https://www.ars.usda.gov/midwest-area/st-paul-mn/cereal-disease-lab/docs/cereal-rusts/wheat-stem-rust/

image_type: jpeg

background: levels = 0.3, noise = 1000, filter=Grey

infection: levels=0.55, noise = 1000, filter =Blue, image_substraction enabled


![wsr-it1](https://user-images.githubusercontent.com/21265433/28124268-6b974136-66e0-11e7-838e-f7169a7ce669.jpeg)
id | coverage | intinsity | object | average_intensity
-- | -- | -- | -- | --
wsr-IT1.jpeg | 40.6602 | 270882 | 9 | 30098

Single leaf infection:

Testing image: https://www.ars.usda.gov/midwest-area/st-paul-mn/cereal-disease-lab/docs/barberry/black-stem-rust-biology-and-threat-to-wheat-growers/

image_type: jpg

background: levels = 0.1, noise = 20, filter=Grey

infection: levels=0.6, noise = 20, filter =Grey


![wsr-it](https://user-images.githubusercontent.com/21265433/28124297-7adcda20-66e0-11e7-9144-8d2111303bdc.jpg)


Multi leaves infection:

Testing image: courtesy of Dr. Larissa Arrais Guimaraes 

image_type: png

background: levels = 0.33, noise = 2000, filter=Grey

infection: levels=0.39, noise = 2000, filter =Green, image_substraction enabled

![picture1](https://user-images.githubusercontent.com/21265433/28124337-9ae2a5fc-66e0-11e7-8ac0-8519cb4bba92.png)

