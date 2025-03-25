# Network Analysis on MOOC platform 
*This research project is a part of my submission to Project 3 from MITx MicroMaster program, in which I am challenged to analyze any sociology networks for further understandings.*

# Research Topics - What are the bottlenecks for the students on MOOC platforms?

## Abstract
Massive Open Online Courses (MOOCs) provide accessible education to learners worldwide. However, optimizing the platforms for better student engagement remains a critical challenge. This study examines student interactions within a MOOC platform, leveraging network analysis to identify activities that encourage or discourage student retention. By analyzing user-activity engagement patterns, this paper uncovers key insights into how certain activities contribute to student disengagement. The findings suggest that activities requiring repeated attempts before completion correlate with increased dropout likelihood. To elevate learning experience, smart interventions such as enhanced guidance and adaptive learning mechanisms should be considered.

## Introduction
MOOCs have transformed education by providing flexible learning opportunities. Consequently, strategies to enhance the learning experience for students on these platforms are in high demand. This study aims to answer: What activities encourage or discourage students from studying on MOOC platforms? By constructing and analyzing a bipartite graph of student interactions, I identify activities with high dropout risk and propose potential improvements.

## Methodology
### Dataset Description
The dataset consists of user interactions with various activities on a MOOC platform from SNAP Stanford (https://snap.stanford.edu/data/act-mooc.html). It is composed of three files:

mooc_actions.tsv (Tab-separated format):
* ACTIONID: Unique identifier for each action.
* USERID: Unique identifier for each user.
* TARGETID: Unique identifier for each target activity.
* TIMESTAMP: Timestamp of the action in seconds from the beginning.

mooc_action_features.tsv (Tab-separated format):
* ACTIONID: Unique identifier for each action.
* FEATURE0, FEATURE1, FEATURE2, FEATURE4: A 4-dimensional feature vector associated with the action.

mooc_action_labels.tsv (Tab-separated format):
* ACTIONID: Unique identifier for each action.
* LABEL: Binary label indicating whether the student drops out after the action (1 for dropout, 0 otherwise).

## Methodology
To investigate student engagement and dropout patterns, I constructed a bipartite network where users interact with various course activities. The three datasets were merged into a single data frame containing interaction records and dropout labels. By modeling this dataframe as a network, I analyzed engagement patterns and identified factors contributing to student dropout.

First, I tested whether the network's degree distributions follow a power-law distribution to guide further quantitative analysis. Next, I compared network density across dropout and non-dropout subgraphs to assess whether dropout behavior correlates with connectivity. Additionally, I computed degree centrality to evaluate whether highly influential activities contribute to disengagement. Lastly, I analyzed interaction frequency before dropout to determine if repeated failed attempts correlated with disengagement.

## Analysis and Results
### Network Structure and Statistics
I plotted and tested whether the degree distributions of users and activities follow a power-law distribution. While the graphs suggest there could be power law distribution, the power law test results could not confirm power-law strictly.
> Please refer to the notebook for visualization

Instead of relying on degree-distribution, I will use degree centrality, how many times students interacted with them, to rank the importance of 97 activities. Activities with high degree centrality indicate either high student interaction or multiple 

> Please refer to the notebook for table data

### Bottleneck Activities
To understand which activities contribute most to dropout behavior, I analyzed the top activities by dropout rate and the last actions performed before disengagement.
> Please refer to the notebook for table data

Out of 4,066 dropout record actions, the most common last interactions before dropout involved activities 13, 16, 15, 8, and 9. Notably, activities 13 had high degree centrality (Table 2), making it a critical point of engagement.
To assess whether these activities are genuinely discouraging, I examined the number of attempts before dropout compared to non-dropout students.

> Please refer to the notebook for visualization

Non-Dropout Students seem to have an easy transition to the next activity (1.02 attempts on average) and Dropout Students dropouts after an average of 2.19 attempts. 

For students that churned at Activity 13, they had slightly higher attempts (1.68) than the non-dropout benchmark. This result suggests that activity 13 high degree centrality is mostly attributed to its high number of students interacting. Hence, it is crucial in the learning journey for students; however, with high dropout rate, this activity is also discouraging for students to move on to the next activity.

## Discussion
The analysis revealed that students struggling with specific activities are significantly more likely to drop out, particularly if they fail within their first few attempts. Surprisingly, network connectivity alone does not serve as a strong predictor of dropout behavior. Instead, dropout patterns are more closely tied to engagement with particular activities, suggesting that course design and individual activity structure play a more critical role than mere connectivity.

To address these challenges, I propose several interventions. Implementing adaptive feedback mechanisms, such as real-time hints and scaffolding strategies, could help students navigate difficult activities and improve completion rates. Additionally, an early warning system could identify at-risk students based on repeated failed attempts, allowing for timely and personalized support. Encouraging peer-assisted learning through discussion forums and community engagement may also enhance student persistence, particularly in challenging course modules.
Despite these insights, our study has some limitations. The dataset does not account for external factors such as student motivation, prior knowledge, or course difficulty, all of which may influence engagement levels. Furthermore, while we focused on interaction patterns within the MOOC platform, we did not assess the quality of instructional materials or teaching methods. Future research could integrate qualitative data to provide a more holistic understanding of student dropout behavior and refine intervention strategies accordingly.

## Conclusion
This study highlights key activities that contribute to student dropout in MOOCs. By applying network analysis, I identified activities where students disengage and proposed targeted interventions to improve retention. The findings suggest that early interventions in difficult activities and adaptive feedback mechanisms could significantly enhance student engagement and reduce dropout rates.

## Citation
Kumar, S., Zhang, X., & Leskovec, J. (2019). Predicting dynamic embedding trajectory in temporal interaction networks. Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, 1269-1278. ACM.
