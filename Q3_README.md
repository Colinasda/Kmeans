- [Q3 Specific Process](#q3-specific-process)
  - [Step1.  Read the csv file](#step1--read-the-csv-file)
  - [Step2.  Calculate the distance](#step2--calculate-the-distance)
  - [Step3.  10 episode training](#step3--10-episode-training)
  - [Step4.  Print the new central points](#step4--print-the-new-central-points)

> Note: The environment is jupyter notebook (python).

## Q3 Specific Process

### Step1.  Read the csv file

We use the pandas to read the csv file "Points.csv" and set the header for the dataset. Besides, we use some functions to check the basic information of dataset, like there are totally 90 records in the dataset. Then we can better draw the scatter plot by these description information.

![](https://tva1.sinaimg.cn/large/008eGmZEgy1gpkqtiuohjj305t06qq38.jpg)

In order to have a better view of dataset, we use the matplotlib to draw a scatter plot for each record.The plot is shown below.(The green '+' represent each record and the red triangles represent the initial centers.)

![](https://tva1.sinaimg.cn/large/008eGmZEgy1gpkjov6uubj30ao06ywem.jpg)



### Step2.  Calculate the distance

Iterator all points and put them into the nearest central points.

```python
points_set = {key: [] for key in range(K)}
for p in p_list:
    nearest_index = np.argmin(np.sum((centeroid - p) ** 2, axis=1) ** 0.5)
    points_set[nearest_index].append(p)
```

Then we can draw the first iteration result of clustering. The scatter plot is shown below.

![](https://tva1.sinaimg.cn/large/008eGmZEgy1gpkr085724j30aa06pweo.jpg)



### Step3.  10 episode training

Use the for loop to do 10 episode training, the process is very similar with above, then we can find that the clustering results become more and more stable according to the scatter plot.

The following picture shows the clustering result after 10 episode.

> The complete 10 scatter plots are in the jupyter notebook file.

![](https://tva1.sinaimg.cn/large/008eGmZEgy1gpkr1s6p52j30af06o0sy.jpg)



### Step4.  Print the new central points

After 10 episode, we can get three new central points, which are 

```python
[[ 58  60]
 [ 20 121]
 [120  21]]
```



