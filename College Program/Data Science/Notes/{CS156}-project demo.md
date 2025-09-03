---
create date: 2024-07-09
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
https://docs.google.com/presentation/d/17LpJTreNXhJPdASQOvZLZJaa-Wj4K_S1hbMg5_Kvx0s/edit#slide=id.p

---
# Review List
>[! abstract] 
>Good afternoon, everyone. Here is **Team Jun-Jia** and my name is Jiahao. Today I and my teammate Wong are going to introduce our dataset "WISDM-51" . 
>First, let me have a brief introduction to the dataset. The dataset describes biometric factors from basic daily activities over 51 subjects. The research team collected data from the accelerometer and gyroscope sensors of a smartphone and smartwatch as 51 subjects performed 18 diverse activities of daily living and our dataset covers all of those phone's records. Each of those activities was performed for 3 minutes, in a rate of 20 Hz for each record, so that each subject contributed 54 minutes of data.
>
>As everyone can see, the 18 kinds of activities described in the dataset cover various types of low-intense activity through daily living. By researching on this dataset, it can be used for building and evaluating biometrics models, or activity recognition models.
>
>Next, let us focus on some details of this dataset and each records. As I mentioned before, there were 51 subjects who contributed to this. So the dataset contains all records for them in 51 csv files and each record consists of 6 columns: the subject id(1600-1650), the activity code representing the 18 types of activites, the timestamp which is a Linux time format count and the sensor's reading raw record in the XYZ dimension. Here I give a example of one sample record. As everyone can see, it represents the first subject (whose id was 1600), did a activity "A", which refers to walking at a specific timestamp, following is the sensor reading for X Y and Z. Since each activity was holding for 3 min with a rate of 20 Hz in recording. There will be 3,600 records for each activity. Generally, the dataset contains 15,630,426 raw measurements in total.
>
>Now let my teammate Wong to give everyone  a more clear image for what kind of description those records can draw.


>[!Abstract] 
>Good afternoon, everyone. Here is Jiahao. Today I and my teammate are going to briefly take a view about our dataset.
> First, before we actually go to the data view. Please let me review the dataset.
> We use Numpy and pandas for data manipulation, matplotlib and seaborn for mapping and draw the histogram and scatter diagrams, and we used sklearn and scipy for preprocessing the data.
> 
> Let us have a look to the overview of the dataset. From the right table we can see 18 different types of activities. 
> 
> The 3 histograms above describe the frequency of all the activities for X, Y and Z axis of the accelerometer sensors' records. 
> 
> The 3 Scatters below them show the comparison in X vs Y, Y vs. Z and X vs. Z for all records. 
> 
> As you can see, there are some noise in the dataset, which makes the histogram a little bit scrappy. Also, we can somehow get some information and relationship between the different records in those diagrams such as some activities' records are more concentrated in each axis like the purple one on the scatter, which represent R and S referring to  "clapping" and "folding clothes" from the table and some activities like jogging looks having broader range than others.
> 
> To make sure the real relationship between those activities, and decline the noise. We do some preprocessing to our dataset.
> 
> After check the missing value, we found the dataset is complete, with no missing values. Then we use the filter to handle the noise.
> 
> Meanwhile, the activities could be grouped into 3 groups. 
> 
> Then we can visualize the data in each group. Just as it present, the non-hand-oriented activities show the most broader range in both axis. On the contrast, the records of only hand-oriented activities mostly fall into a smaller range which is very clearly in the middle column. 
> Finally, the group 3 has intermediate range of the three. 
> 
> These diagram reflect the range of human's body movement in different activities: the outdoor activities usually need more frequently move and the indoor activities like typing, writing only cause small movement, and the eating activities come in between the two, probably because people feel more freedom and casual when eating. Therefore, we can model upon these and predict which kind of group of a new activities could be if we get a new record.
> 
> Now we've taken a overview of the whole picture, but how about the single activity in the same group? Now let my teammate to illustrate what a single, specialized activity will look like.
> 









---
# In-Class Problems

Non-hand-oriented activities: 
{walking, jogging, stairs, standing, kicking} -A, B, C, D, E, M

Hand-oriented activities (General): 
{dribbling, playing catch, typing, writing, clapping, brushing teeth, folding clothes} - P, O, F, Q, R, G, S

Hand-oriented activities (eating):
{eating pasta, eating soup, eating sandwich, eating chips, drinking}- J, H, L, I, K


---

# Flash Cards
