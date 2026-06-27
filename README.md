import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("WorldPopulationByAge2020.csv")

age_distribution = df.groupby("AgeGrp")["PopTotal"].sum()

colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA726']

plt.figure(figsize=(10,6))

bars = plt.bar(
    age_distribution.index,
    age_distribution.values,
    color=colors,
    edgecolor='black'
)

plt.title(" World Population Distribution by Age Group (2020)",
          fontsize=15,
          fontweight='bold')

plt.xlabel("Age Group")
plt.ylabel("Population")

plt.grid(axis='y', linestyle='--', alpha=0)

plt.show()

#Now create a barchart basis on  Calculate Total Male and Female Population
male_population = df["PopMale"].sum()
female_population = df["PopFemale"].sum()

print("Male Population:", male_population)
print("Female Population:", female_population)
#Now create  a  bar chart
gender = ["Male", "Female"]
population = [male_population, female_population]

plt.figure(figsize=(6,5))
plt.bar(gender, population)

plt.title("World Population Distribution by Gender (2020)")
plt.xlabel("Gender")
plt.ylabel("Population")

plt.show()

#Now show  Distribution using Create Histogram
plt.figure(figsize=(8,5))

plt.hist(df["PopTotal"],bins=20)

plt.title("Distribution of Population (2020)")
plt.xlabel("Population")
plt.ylabel("Frequency")
plt.show()
