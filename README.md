<h1>U.S. Medical Insurance</h1>
<p>In this project, a CSV file with medical insurance costs was investigated using Python skills. The goal of this project was to analyze various attributes within insurance.csv to learn more about the patient information in the file and gain insight into potential use cases for the dataset.</p>

<h2>Installation</h2>
<p>Due to the project being completed using Jupyter Notebook, there is no need to install my project on your machine. If you want to explore the code and its outputs a little bit more in-depth click on U.S. Medical Insurance.ipynb file in the repository and there you can find code blocks with their outputs.</p>


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

```
print(average_age(ages))
```

<p>The average age is 39.21 years old.</p>

```
print(average_bmi(bmis))
```

<p>The average BMI is 30.66.</p>

```
print(average_children(children))
```

<p>The average number of children per person is 1.09.</p>

```
print(average_cost(insurance_charges))
```

<p>The average insurance charge is $13270.42.</p>

```
number_of_males = 0
number_of_females = 0

for sex in sexes:
    if sex == 'male':
        number_of_males += 1
    else:
        number_of_females += 1
    
percent_male = (number_of_males /  len(sexes)) * 100

percent_female = (number_of_females / len(sexes)) * 100

print('The percent of the people identifying as male is ' + str(round(percent_male,2)) +'% a total of '+ str(number_of_males) +' males in dataset.' )
print('The percent of people identifying as female is '+ str(round(percent_female,2))+'% a total of ' + str(number_of_females) +' females in dataset.')
```

<p>Finds percentage of males and females, as well as, how many are actually in insurance.csv.</p>
<p>insurance.csv is 50.52% male and 49.48% female, a total of 676 males and 662 females. There are more males in the dataset than females.</p>

```
number_of_smokers = 0
number_of_nonsmokers = 0

for status in smoker_statuses:
    if status == 'yes':
        number_of_smokers += 1
    else:
        number_of_nonsmokers += 1
            
percent_smoker = (number_of_smokers / len(smoker_statuses)) * 100
percent_nonsmoker = (number_of_nonsmokers / len(smoker_statuses)) * 100

print('The percent of the people who identify as a smoker is ' + str(round(percent_smoker,2))+"%, there are a total of "+ str(number_of_smokers)+ " smokers.")
print('The percent of the people who identify as a nonsmoker is '+ str(round(percent_nonsmoker,2))+'%, there are a total of ' + str(number_of_nonsmokers) + " nonsmokers.")
```

<p>Finds percentage of nonsmokers and smokers, as well as, how many are actually in insurance.csv.</p>
<p>insurance.csv is 79.52% nonsmokers and 20.48% smokers, a total of 1064 nonsmokers and 274 smokers.</p>

```
region_dict = {}
for region in regions:
    count = 0
    for place in region_dict.keys():
        if region == place: 
            count += 1
    if count == 0:
        region_dict[region] = 0

print(region_dict)  
```

<p>Creates dictionary showing the 4 regions: northeast, northwest, southeast, and southwest</p>

```
for region in region_dict.keys():
    count = 0
    for place in regions:
        if region == place:
            count+=1
    region_dict[region] = count
    
print(region_dict)

for region in region_dict.keys():
    print(region + " has " + str(region_dict[region]) + " people in this dataset.")

```

<p>Loads the dictionary with number of people for each region and prints it out.</p>
<p>325 people from southwest, 364 people from southeast, 325 people from northwest, and 324 people from northeast</p>

```
insurance_master_list = list(zip(ages,sexes,bmis,children,smoker_statuses,regions,insurance_charges))
print(insurance_master_list)
```

<p>Creates master patient list for further analysis.</p>

```
sex_cost = {}
sex_cost.update({'male':[],'female':[]})
print(sex_cost)

for patient in insurance_master_list:
    if patient[1] == 'female':
        sex_cost[patient[1]].append(patient[-1])
    else:
        sex_cost[patient[1]].append(patient[-1])

print(sex_cost)
```

<p>Makes a sex/cost dictionary where each key represents a list of costs.</p>

```
smoker_cost = {}
smoker_cost.update({'yes':[],'no':[]})
print(smoker_cost)

for patient in insurance_master_list:
    if patient[4] == 'yes':
        smoker_cost[patient[4]].append(patient[-1])
    else:
        smoker_cost[patient[4]].append(patient[-1])
print(smoker_cost)
```

<p>Makes smoker status/cost dictionary where each key represents a list of costs.</p>

```
male_total_cost = 0
female_total_cost = 0

for sex in sex_cost.keys():
    for cost in sex_cost[sex]:
        if sex == 'female':
            female_total_cost += float(cost)
        else:
            male_total_cost += float(cost)
            
male_average = male_total_cost / len(sex_cost['male'])
female_average = female_total_cost / len(sex_cost['female'])

print("The average insurance cost for male patients is "+ str(round(male_average,2))+'.')
print('The average insurance cost for female patients is ' + str(round(female_average,2))+'.')
```

<p>Finds the average cost of insurance charges for males and females.</p>
<p>The average male cost is $13956.75 and the average female cost is $12569.58. On average, according to the insurance.csv dataset, males pay more than females.</p>

```
smoker_total_cost = 0
nonsmoker_total_cost = 0

#ident refers to identity as in smoker or not(yes or no).
for ident in smoker_cost.keys():
    for cost in smoker_cost[ident]:
        if ident == 'yes':
            smoker_total_cost += float(cost)
        else:
            nonsmoker_total_cost += float(cost)
            
smoker_average = male_total_cost / len(smoker_cost['yes'])
nonsmoker_average = female_total_cost / len(smoker_cost['no'])

print("The average insurance cost for smoker patients is "+ str(round(smoker_average,2))+'.')
print('The average insurance cost for nonsmoker patients is ' + str(round(nonsmoker_average,2))+'.')
```

<p>Finds the average cost of insurance charges for smokers and nonsmokers.</p>
<p>The average nonsmoker cost is $7820.55 and the average smoker cost is $34433.55. On average, according to the insurance.csv dataset, smokers pay more than nonsmokers.</p>

```
for region in region_dict:
    total_cost = 0
    count = 0
    for patient in insurance_master_list:
        if patient[-2] == region:
            total_cost += float(patient[-1])
            count += 1
            
    average = total_cost / count
    print('The average insurance cost for the ' + region + ' region is '+ str(round(average,2))+'.')
```


<p>Finds the average insurance charge for each region.</p>
<p>The average insurance cost for southwest is $12346.94, southeast is $14735.41, northwest is $12417.58, and northeast is $13406.38. There does not appear to be too much of a difference between each region in terms of insurance costs. But, on average, according to insurance.csv, the southeast pays the most and the southwest pays the least.</p>



