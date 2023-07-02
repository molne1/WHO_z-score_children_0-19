# WHO_z-score_children_0-19

This repository stores a Jupyter Notebook, reference information and a folder with reference data from the WHO 
Function to calculate BMI z-score's for children using LMS calculation. 
Link to formulas used in the function: https://cdn.who.int/media/docs/default-source/child-growth/growth-reference-5-19-years/computation.pdf?sfvrsn=c2ff6a95_4 (also stored in information) 

HOW TO SET UP FUNCTION 
All calculations are with age(months), weight(kg), height(cm)
The WHO reference sheets will be downloaded automatically from github as needed.
You must have following columns named in the correct format "age", "sex", "weight", "height".
You must NOT have a column named "BMI" in your intial dataframe
The function will create three new columns: BMI, reference sheet used, and z-score

OPTIONS
Age in months is defualt, but if you have it in years use following argument "age_in_years = True"
Month 61 is default from 5-19 reference to change to 0-5 use following argument "month61_from_0to5_reference = True"



REFERENCE FILES:
There are two reference standards 0-5 years(Age is Days =  0-1851) and 5-19 years(Age is Months = 61-228).
Download 0-5 here: https://www.who.int/toolkits/child-growth-standards/standards/body-mass-index-for-age-bmi-for-age I used the file: Girls z-scores: expanded tables (BMI-for-age) & Boys z-scores: expanded tables (BMI-for-age)
Download 5-19 here: https://www.who.int/tools/growth-reference-data-for-5to19-years/indicators/bmi-for-age I used the file: z-scores: girls [xlsx, 27kb] & z-scores: boys [xlsx, 27kb]


PREPROCESSING OF REFERENCE FILES: 
1)Standardization for reference population
To standardize for reference population, a common " age" was needed. I choose to standardize it to "Months". This looses the granuality of days, but makes it possible to have the two references together
I used the WHO reference for the conversion: https://cdn.who.int/media/docs/default-source/child-growth/child-growth-standards/indicators/instructions-en.pdf?sfvrsn=5cec8c61_23 ( also in information ) 
1 month = 30.4375 days was the conversion I used for the 0-5 year old reference data, ending up with 61 months. Note the overlap with the 5-19 year old reference. 
2) For the 5-19 year old reference I replaced column name "Month" with "Months" to match the other reference.
