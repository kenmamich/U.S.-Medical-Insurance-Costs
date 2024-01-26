<h1>U.S. Medical Insurance</h1>
<p>In this project, a CSV file with medical insurance costs was investigated using Python skills. The goal of this project was to analyze various attributes within insurance.csv to learn more about the patient information in the file and gain insight into potential use cases for the dataset.</p>


<h2>Documentation</h2>
<h3>Library</h3>

<p>To start, all necessary libraries must be imported. For this project, the only library needed is the `CSV` library to work with the insurance.csv data. Other potential libraries could help with this project; however, for this analysis, using just the `CSV` library will suffice.</p>

```
import csv
```

<h3>Getting Started</h3>
<p>Next step is to thoroughly look through the data set looking for the following:</p>
<ul>
  <li>Names of the columns and rows</li>
  <li>Any noticeable missing data</li>
  <li>Types of data values (Categorical or Numerical)</li>
</ul>
<p>The code below initially inspects the entire dataset by printing each line out. The data set has 7 columns: age, sex, BMI, children, smoker, region, and charges. There appear to be no missing data values and sex(Male, Female), smoker(Yes, No), and region(Northeast, Northwest, Southeast, Southwest) are categorical values and age, BMI, children, and charges are all numerical. </p>

 ```
with open('insurance.csv') as insurance_data:
    print(insurance_data.read())
 ```

<p>Lists for each column.</p>

 ```
ages = []
sexes = []
bmis = []
children = []
smoker_statuses=[]
regions = []
insurance_charges = []
 ```

<p>Function for loading each list with their respective values.</p>

```
def list_loader(lst,file,column_name):
    with open('insurance.csv') as insurance_data:
        csv_dict = csv.DictReader(insurance_data)
        for row in csv_dict:
            lst.append(row[column_name])
        return lst
```

<p>Offically loads each list with the analyst defined list_loader function.</p>

```
ages = list_loader(ages,'insurance.csv','age')
sexes = list_loader(sexes,'insurance.csv','sex')
bmis = list_loader(bmis,'insurance.csv','bmi')
children = list_loader(children,'insurance.csv','children')
smoker_statues = list_loader(smoker_statuses,'insurance.csv','smoker')
regions = list_loader(regions,'insurance.csv','region')
insurance_charges = list_loader(insurance_charges,'insurance.csv','charges')
```

<p>Prints out each list.</p>

```
print('Age list: ' + str(ages))
print('Sex list: ' + str(sexes))
print('Bmi list: ' + str(bmis))
print('Number of children list: '+ str(children))
print('Smoker status list: '+str(smoker_statuses))
print('Regions list:' + str(regions))
print('Insurance charges list : '+ str(insurance_charges))
```

<h3>Functions</h3>
<p>Developer defined function for finding average age.</p>

```
def average_age(ages):
    total_age = 0
    for age in ages:
        total_age += int(age)
    
    average_age = total_age / len(ages)
   
    return 'The average age is ' + str(round(average_age,2)) + ' years old.'
```

<p>Developer defined function for finding average BMI.</p>

```
def average_bmi(bmis):
    total_bmi = 0
    for bmi in bmis:
        total_bmi += float(bmi)

    average_bmi = total_bmi / len(bmis)

    return 'The average BMI is ' + str(round(average_bmi,2)) + '.'
```
<p>Developer defined function for finding the average number of children per person.</p>

```
def average_children(children):
    total_number_of_children = 0
    for num in children:
        total_number_of_children += int(num) 

    average_number_of_children = total_number_of_children / len(children)

    return 'The average number of children per person is '+ str(round(average_number_of_children,2))+'.'
```

<p>Developer defined function for finding the average cost.</p>

```
def average_cost(insurance_charges):
    total_insurance_cost = 0

    for charge in insurance_charges:
        total_insurance_cost += float(charge)
    
    average_charge = total_insurance_cost / len(insurance_charges)
    return 'The average insurance charge for the people represented in the dataset is $'+ str(round(average_charge,2))+'.'

```

<h3>Analysis</h3>
