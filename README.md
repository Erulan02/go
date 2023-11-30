import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


data = {
     'Vaccination status': ['Unvaccinated', 'Vaccination refusal', 'Med. contraindications', 'Not reaching vaccination age', 'Other reasons', 'Unknown'],
     'Number of cases': [3006, 1714, 572, 648, 72, 772]
}

df = pd.DataFrame(data)


total_cases = 4306
cases_children = 3581
percent_children = (cases_children / total_cases) * 100


plt.figure(figsize=(15, 8))


plt.subplot(1, 2, 1)
sns.barplot(x='Vaccination status', y='Number of cases', data=df, palette='viridis')
plt.title('Distribution of cases of infection by vaccination status')
plt.xlabel('Vaccination status')
plt.ylabel('Number of cases')


plt.subplot(1, 2, 2)
plt.pie([percent_children, 100 - percent_children], labels=['Children under 14', 'Others'], autopct='%1.1f%%', colors=['lightcoral', 'lightblue'])
plt.title('Proportion of cases affecting children under 14 years of age')

plt.show()


print(f"Total measles cases: {total_cases}")
print(f"Children under 14 make up {percent_children:.2f}% of total cases.")


refusal_reasons = {
     'Vaccination refusal': 1714,
     'Honey. contraindications': 572,
     'Not reaching vaccination age': 648,
     'Other reasons': 72
}

plt.figure(figsize=(10, 6))
sns.barplot(x=list(refusal_reasons.keys()), y=list(refusal_reasons.values()), palette='magma')
plt.title('Reasons for refusing vaccination')
plt.xlabel('Reason')
plt.ylabel('Number of cases')

plt.show()


for reason, count in refusal_reasons.items():
     print(f"Reason: {reason}")
     print(f"Number of cases: {count}")
     print(f"Percentage of total cases: {count / total_cases * 100:.2f}%")
     print("="*40)
