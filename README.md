# The Analysis
## What are the most demanded skills for the top 3 most popular data roles

to find the most demanded skills for the top 3 most popular data roles.I filtered out those positions by which ones were the most popular and got the top 5 skills for these to top 3 roles.This query hightlights the most popular job_titles and their top skills,showing which skills i should pay attention to depending on the role im targeting

View m notebook of rthe detailed notes here:
[2_Skill_Demand.ipynb] (Project Side\2_Skill_Demand.ipynb)


# Visualize Data

```python

fig,ax = plt.subplots(len(job_titles),1)

for i , job_title in enumerate(job_titles):
    df_plot = df_skill_perc[df_skill_perc['job_title_short'] == job_title].head(5)

    sns.barplot(data=df_plot,x='skill_percent',y='job_skills',ax=ax[i],hue='skill_count',color='blue',palette = 'dark:b_r')
    sns.set_theme(style='ticks')
    ax[i].set_title(job_title)

    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0,78)
    ax[i].legend().set_visible(False)

    #looping through the index to show the skill perecentage
    for n ,v  in enumerate(df_plot['skill_percent']):
      ax[i].text(v + 1,n,f'{v:.0f}%', va='center')

    if i != len(job_titles) - 1:
      ax[i].set_xticks([])

      #setting the xticks to remove the x axis numbers
    ax[i].set_xticks([])
plt.tight_layout()
plt.show()
```


### Results

![visualization of TOP 10 Skills for Data Analyst](Images\output.png)

### Insights

- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%)..
- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles.
For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.

- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists, who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).