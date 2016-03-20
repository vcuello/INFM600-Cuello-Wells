#Description of Datasets

The dataset is a combined set of two *Pew Research Center’s Internet & American Life Project*  in association with *Princeton Survey Research Associates International* survey analysis datasets, which are a combined set of a  *2013 Library Typology*  (http://www.pewinternet.org/datasets/september-2013-library-typology/) survey analysis compiled by Research Analysist Kathryn Zickuhr, Associate Director of Research at the Pew Research Center,  Kristen Purcell, and Director of Internet Science & Technology Research at the Pew Research Center, Lee Raine ; and a  *2014 E-Reading and Gadgets*  (http://www.pewinternet.org/datasets/january-2014-e-reading-and-gadgets-omnibus/) survey analysis compiled again by Research Analysist Kathryn Zickuhr and Director of Internet Science & Technology Research at the Pew Research Center, Lee Raine.  

The  *2013 Library Typology*  dataset is comprised of information in relation to survey answer question analysis about American adults 16 years and older most common uses for public libraries, along with a report analysis on the findings published by Pew Research Centers (Zickhur, Purcell & Raine, 2014), (http://www.pewinternet.org/2014/03/13/library-engagement-typology/). 

The  *2014 E-Reading and Gadgets*  dataset consist of a survey question analysis of American adults age 16 and older frequency of use of E-reading and other electronic devices uses in public libraries, also includes a link to an analytic report of the dataset ( Zickhur & Raine, 2014) ,                                                                                                                           ( http://www.pewinternet.org/2014/01/16/e-reading-rises-as-device-ownership-jumps/).

Even though these datasets are one year apart which may lead to data miss match, it still provides relevant information based on the commonality factor of location. The one year apart between the datasets is not significant given the information we used for the joined dataset is formulated in a way that asks the individual if he/she ever used electronic devices for reading or ever visited the library making the question cumulative overtime with only a one year difference. 

From these two original datasets of the *2013 Library Typology* dataset survey response results of Q21, frequency of use of the library in the past year combined with the dataset survey results of the  *2014 E-Reading and Gadgets*   PIAL4 response to the used electronic book platforms is necessary to answering the question of; Do states whose population reported a significant percentage of reading using E-books also have a significant percentage of in person visits to public libraries ?

# Data Description

The following section describes the codification of the selected data points: 

From *2013 Library Typology*: Q21a Have you, personally, EVER Visited a public library or used a public library bookmobile IN PERSON

Options:

1.	Yes, have done this in past 12 months
2.	Yes, have done this, but not in the past 12 months
3.	No, have never done this
8.	Don’t know
9.	Refused

From  *2014 E-Reading and Gadgets* : PIAL4  When you read electronic books or e-books, do you ever read them on your... [INSERT ITEMS IN ORDER]?

a.	Tablet computer

b.	E-book reader

c.	Desktop or laptop computer

d.	Cell phone

Options:

1.	Yes, every day or almost every day
2.	Yes, a few times a week
3.	Yes, a few times a month
4.	Yes, less often
5.	No, do not read e-books on this device
6.	Can’t read e-books on device/Device not equipped for reading e-books
8.	Don’t know
9.	Refused

The dataset is released in the framework and conjugation with INFM 600, Information Environments, Spring 2016, at the University of Maryland iSchool, http://umd.edu/mim.

# Dataset Combination Process 

To join both datasets, the research team identified the common key to combine the datasets for       *2013 Library Typology*  and  *2014 E-Reading and Gadgets*  using the state key id (FIPS code). Before joining the sets, new variables were defined for each dataset to transform the data from measures taken from individuals nationally to significant state measures. 

The team used Excel to do the new variable calculations and define a new join dataset as follows:

## 2013 Library Typology 

- Identified the state identifier column
- Identified the Q21a column
- Created new variable, called Key, to signify the combination of the state identifier and the Q21a selected answer formated as; [state identifier],[Q21a codified answer]. 

## 2014 E-Reading and Gadgets 

- Identified the state identifier column
- Identified the PIAL4 columns for all 4 devices tested; PIAL4a, PIAL4b, PIAL4c and PIAL4d
- Created new variable, called Key, to signify the combination of the state key and the selected answers for PIAL4a, PIAL4b, PIAL4c and PIAL4d formated as; [state identifier],[PIAL4a answer],[PIAL4b answer],[PIAL4c answer],[PIAL4d answer]
- Created a new variable called PIAL4Calc to sum all PIAL4 answers only for options:
(1) Yes, every day or almost every day
(2) Yes, a few times a week
(3) Yes, a few times a month
(4) Yes, less often
- If the Sum PIAL4Calc  is greater than 0 this individual uses e-reading devices. For this purpose we created a new boolean variable called useEReadingDevices to hold the value of TRUE if the sum PIAL4Calc  is greater than 0, FALSE otherwise.
- Created new variable, called Key, to signify the combination of the state key and the calculated variable useEReadingDevices; [state identifier],[useEReadingDevices]

## Joined Dataset 
- Created a sheet with all possible permutations of the variables: State Identifier,  Q21a (possible answers: 1, 2, 3, 8 and 9) and useEReadingDevices (possible values: TRUE, FALSE)
- Created a Key variable to match the Key values for each dataset.
- Created variables  PercentageTypology and PercentageEreading using the COUNTIF function in Excel to count each Key value and divided by the total number of answer per state, creating a new calculated variable representing the percentage of people in that state with each answer combination (from 0 to 1). 
- Notice Alaska, Hawaii and Wyoming were not survey in the *2014 E-Reading and Gadgets*  were we got a division by zero error, those state were removed for the purpose of this study and for final analysis we used the cleansed sheet of the joined dataset.

#Dataset Graphic Representation

By using  *Bing Maps*   in  *Excel*   we filtered the cleansed sheet of the joined data for the percentages for answer 1 for Q21a (People that have visit a public library in the past 12 months) and TRUE for use E-Reading devices by state. The percentages were scaled to 0 to  100 and finally the map uses the pie chart display to make a comparison of percentages.
Notice that to be able to visualize the map the user needs to be connected to the internet and have a Microsoft account.  The user will also need to be able to zoom in and out of the map to find the best resizing format to see the whole United States Of America regions.
From the graphic representation the most noticeable feature is that the percentage of people visiting public libraries in the last 12 month is always greater or equal to those using E-Reading devices making noticeable the relevance of public libraries in all states as of 2013-2014. A tendency analysis will need to be made to see if E-Reading devices will overtake libraries  in the future.

#File

The datasets are available at Join_Library_Typology_EreadingV6.xlsx as follows:
- Sheet Sept_2013_Library_Typology: contains raw data set for * 2013 Library Typology*  with the highlighted fields selected fields and Key fields defined for the purpose of this project.
- Sheet January_2014_Ereading_Gadgets_C: contains raw data set for  * 2014 E-Reading and Gadgets* and the highlighted fields, the calculated fields and key defined for the purpose of this project.
- Sheet Join_Library_ Typology_ Ereading: contains the first iteration of the joined data; it includes the FIPS State Numeric Code, State Identifier, Library Typology Q21a Possible answers, useEReading Devices, KeyTypology, KeyEreading, PercentageTypology, and PercentageEReading.
- Sheet Clean_Join_LibTypology_Ereading: contains the cleansed data removing states with no answers such as Alaska, Hawaii and Wyoming and the final percent calculation in 0 to 100 scale. 
- Sheet Library Visit & E-Reading Map: contains a filtered set of data from the Clean_Join_LibTypology_Ereading sheet to only include Q21a 1 and Use E-Reading Devices TRUE and a graphical map representation of the filtered data.

##Variable Description

###Sept_2013_Library_Typology
- state: FIPS code	
- q21a: Answers for Q21a (1,2,3,8 or 9)
- KeyTypology: [state],[q21a]

###January_2014_Ereading_Gadgets_C.
- state: FIPS code
- Pial4a: Answers for question PIAL4a (1,2,3,4,5,6,8 or 9)
- Pial4b: Answers for question PIAL4b (1,2,3,4,5,6,8 or 9)
- Pial4c: Answers for question PIAL4c (1,2,3,4,5,6,8 or 9)
- Pial4d: Answers for question PIAL4a (1,2,3,4,5,6,8 or 9)
- Pial4Key: [state],[Pial4a],[Pial4b],[Pial4c],[Pial4d]
- Pial4calc: Sum of answers from 1 to 4	  
- useEreadingDevices: TRUE if Pial4calc>0, FALSE otherwise
- Key: [state],[useEreadingDevices]



###Join_Library_ Typology_ Ereading
- FIPS State Numeric Code: State Name
- State Identifier: FIPS Code
- Library Typology Q21a: All possible answers for q21a    
- useEReadingDevices: All possible values for useEReadingDevices
- KeyTypology   [State Identifier],[Library Typology Q21a]
- KeyEreading: [State Identifier],[useEreadingDevices]
- Percentage Typology: Number of KeyTypology occurrences for this state divided by all the answers for this state (percent from 0 to 1)	 
- PercentageEReading: Number of KeyEreading occurrences for this state divided by all the answers for this state (percent from 0 to 1)	 

###Clean_Join_LibTypology_Ereading
- FIPS State Numeric Code: State Name
- State Identifier: FIPS Code
- Library Typology Q21a: All possible answers for q21a    
- useEReadingDevices: All possible values for useEReadingDevices
- KeyTypology   [state],[Library Typology Q21a]
- KeyEreading: [state],[useEreadingDevices]
- Percentage Typology: Number of KeyTypology occurrences for this state divided by all the answers for this state (percent from 0 to 1)	 
- PercentageEReading: Number of KeyEreading occurrences for this state divided by all the answers for this state (percent from 0 to 1)	 
- Percentage Typology: Number of KeyTypology occurrences for this state divided by all the answers for this state (percent from 0 to 100)	 
- PercentageEReading: Number of KeyEreading occurrences for this state divided by all the answers for this state (percent from 0 to 100)	   

###Library Visit & E-Reading Map
- State: State Name	 
- Visit Public Libraries %	: Number of KeyTypology occurrences for this state divided by all the answers for this state (percent from 0 to 100)	
- Use E-Reading Devices %: Number of KeyEreading occurrences for this state divided by all the answers for this state (percent from 0 to 100)


#Acknowledgements

We want to thank the research groups of the  *Pew Research Center’s Internet & American Life Project*   in association with *Princeton Survey Research Associates International*   for allowing access to both master sets of datasets and survey question analysis (http://www.pewresearch.org/).  We would like to thank Aaron Smith compiler of the   *2013 Library Typology*   dataset and the compliers Kathryn Zickuhr and Lee Raine of the *2014 E-Reading and Gadgets*  dataset.  We also would like to thank *Bing Maps*  in  *Microsoft Excel 2013*   developed by the  *Microsoft Corporation*   for providing us with the geographic chart map.

#Licenses 

This  data in the INFM 600 Discovery and Analysis repository is distributed by a *Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License *                                                                          ( please read:  http://creativecommons.org/licenses/by-nc/4.0/)
The data is made available for only non-commercial use. For individuals interested in using the data in a commercial use context please contact a researcher and fill out a form at the Pew Research Center:
http://www.pewresearch.org/about/use-policy/
info@pewresearch.org.
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Dataset" property="dct:title" rel="dct:type">Joined Library Typology Ereading Uses </span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/vcuello/INFM600-Cuello-Wells" property="cc:attributionName" rel="cc:attributionURL"> Veronica Cuello and Stephen Wells</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.<br />Permissions beyond the scope of this license may be available at <a xmlns:cc="http://creativecommons.org/ns#" href="http://www.pewresearch.org/about/use-policy/" rel="cc:morePermissions">http://www.pewresearch.org/about/use-policy/</a>.

#References

When citing this data you should cite :
- Pew Research Center  Website , http://www.pewresearch.org/
- Pew Research Center Data Set :  *July 18-Sept. 30, 2013*  – *Library Typology* , http://www.pewinternet.org/datasets/september-2013-library-typology/
- Pew Research Center Data Set : *Jan. 2-5, 2014*  – *E-Reading and Gadgets*  , http://www.pewinternet.org/datasets/january-2014-e-reading-and-gadgets-omnibus/
- Pew Research Center Report : *From Distant Admirers to Library Lovers-and beyond*  , http://www.pewinternet.org/2014/03/13/library-engagement-typology/
- Pew Research Center Report: *E-Reading Rises as Device Ownership Jumps* ,    http://www.pewinternet.org/2014/01/16/e-reading-rises-as-device-ownership-jumps/                                                                             
-  *Bing Maps*  Website enabled app function in *Microsoft  Excel 2013* ,  2016 Microsoft Corporation https://www.microsoft.com/maps/Default.aspx

#Credits

This dataset was constructed by Veronica Cuello and Stephen Wells.
