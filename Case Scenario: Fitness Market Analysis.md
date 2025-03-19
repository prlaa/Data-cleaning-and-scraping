## Case Scenario: Fitness Market Analysis
You are a product manager for a fitness studio and are interested in understanding the current demand for digital fitness classes. You plan to conduct a market analysis in Python to gauge demand and identify potential areas for growth of digital products and services.

## The Data
You are provided with a number of CSV files in the "Files/data" folder, which offer international and national-level data on Google Trends keyword searches related to fitness and related products. Column & Description are named per csv file.

#### 1. workout.csv
- 'month'	Month when the data was measured.
- 'workout_worldwide'	Index representing the popularity of the keyword 'workout', on a scale of 0 to 100.
  
#### 2. three_keywords.csv
- 'month'	Month when the data was measured.
- 'home_workout_worldwide'	Index representing the popularity of the keyword 'home workout', on a scale of 0 to 100.
- 'gym_workout_worldwide'	Index representing the popularity of the keyword 'gym workout', on a scale of 0 to 100.
- 'home_gym_worldwide'	Index representing the popularity of the keyword 'home gym', on a scale of 0 to 100.

#### 3. workout_geo.csv
- 'country'	Country where the data was measured.
- 'workout_2018_2023'	Index representing the popularity of the keyword 'workout' during the 5 year period.

#### 4.three_keywords_geo.csv
- 'country'	Country where the data was measured.
- 'home_workout_2018_2023'	Index representing the popularity of the keyword 'home workout' during the 5 year period.
- 'gym_workout_2018_2023'	Index representing the popularity of the keyword 'gym workout' during the 5 year period.
- 'home_gym_2018_2023'	Index representing the popularity of the keyword 'home gym' during the 5 year period.

## ----------- CODE -----------
import pandas as pd
##### #When was the global search for 'workout' at its peak? Save the year of peak interest as a string named year_str in the format "yyyy".
df= pd.read_csv(r'data/workout.csv')
print(df)
max_value = df['workout_worldwide'].max()
print('Max search value was:', max_value)
index_max = df.loc[[df['workout_worldwide'].idxmax()]]
print('Index of max value is:',index_max)
year_str = str(df.iloc[25, 0])[:4]
print('Year of max search was:',year_str)

##### #Of the keywords available, what was the most popular during the covid pandemic, and what is the most popular now? Save your answers as variables called peak_covid and current respectively.
df= pd.read_csv(r'data/three_keywords.csv')
#Change 'month' column to datetime format
df['month'] = pd.to_datetime(df['month'], format='%Y-%m')
#Filter data for COVID-19 period
covid_df = df[(df['month'] >= '2020-01-01') & (df['month'] <= '2021-12-31')]
#Find the most popular keyword during the COVID-19 period
peak_covid = covid_df[['home_workout_worldwide', 'gym_workout_worldwide', 'home_gym_worldwide']].max().idxmax()
#Filter data for current period 
current_df = df[df['month'] >= '2023-01-01']
#Find the most popular keyword in the current period
current = current_df[['home_workout_worldwide', 'gym_workout_worldwide', 'home_gym_worldwide']].max().idxmax()
#Print the results
print(f"Peak COVID Keyword: {peak_covid}")
print(f"Current Most Popular Keyword: {current}")

##### #What country has the highest interest for workouts among the following: United States, Australia, or Japan? Save your answer as top_country.
df=pd.read_csv(r'data/workout_geo.csv')
print(df)
countries_data = df[df['country'].isin(['United States', 'Japan', 'Australia'])]
print(countries_data)
top_country = countries_data.loc[countries_data['workout_2018_2023'].idxmax()]['country']
print(top_country)

##### #You'd be interested in expanding your virtual home workouts offering to either the Philippines or Malaysia. Which of the two countries has the highest interest in home workouts? Identify the country and save it as home_workout_geo.

df=pd.read_csv(r'data/three_keywords_geo.csv')
print(df.head())
#Select and print values for countries: Philippines and Malaysia
phi_mal = df[df['Country'].isin(['Phillipines', 'Malaysia'])]
print(phi_mal)
#Selects the country with the highest index value in the 'home_workout_2018_2023' column from the phi_mal DataFrame and prints the name of that country.
home_workout_geo = phi_mal.loc[phi_mal['home_workout_2018_2023'].idxmax()]['Country']
print(home_workout_geo)
