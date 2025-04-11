# H1: The Analysis
## 1. What are the most demanded skills for the top 3 most popular data roles ?
To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role am targetting.

View my notebook with detailed steps here: [2_Skill_Demand.ipynb](Project\2_Skill_Demand.ipynb)

### Visualize Data
```python
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)
    # remove the x-axis tick labels for better readability
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])

    # label the percentage on the bars
    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=.8)
plt.show()
```
### Results
![Visualization for Top Skills for Data Nerds](Assets\skill_demand_all_data_roles.png)

### Insights
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists(72%) and Data Engineers(36%).
- SQL is the most requeted skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers Python is the most sought-after skill (AWS, Azure, Spark) come ine second.
- Data Engineers require more ..
