# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Sue Guo

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?

**count** means  number of total rentals so it can't be negative values. we gotta replace all negative preditions with 0 but luckily none of my models predition has negative results.

### What was the top ranked model that performed?

![zrDCUc](https://testksj.oss-cn-beijing.aliyuncs.com/uPic/zrDCUc.png)

![x7pLy9](https://testksj.oss-cn-beijing.aliyuncs.com/uPic/x7pLy9.png)

![Wex2Yd](https://testksj.oss-cn-beijing.aliyuncs.com/uPic/Wex2Yd.png)

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
-   Exstract new columns "date,"hour","weekDay","month" from "datetime"  and delete the `datetime` column.
-   Coerce the datatype of      `hour`, `weekday`, `week`, `month`, `season`, `year`, `weather` to category.

### How much better did your model preform after adding additional features and why do you think that is?

First, these new features allow the model to take into account the temporal nature of the data. By including information about the specific hour, day, week, month, and year of each bike rental, the model can better understand patterns and trends in demand that may vary by time of day, day of the week, or season.

Second, these new features also allow the model to capture cyclical patterns in the data. For example, demand for bike rentals may be higher on weekends or during summer months, and these patterns may be captured by the new features.

Finally, these new features can also provide more information to the model, which can be used to make more accurate predictions. With more data to work with, the model can learn more complex relationships between the input features and the target variable, which may lead to better performance.

Overall, extracting new features from datetime data can be a powerful way to improve model performance by providing more information and capturing temporal and cyclical patterns.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?

Actually the score is worse after hyper parameter tuning so I think the default AutoGluon setting is much better than me.

### If you were given more time with this dataset, where do you think you would spend more time?

Here is what I explored with the dataset and the final score ranks top 1%

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
| model        | hpo1                               | hpo2                   | hpo3                 | score   |
| ------------ | ---------------------------------- | ---------------------- | -------------------- | ------- |
| initial      | default_vals                       | default_vals           | default_vals         | 1.80696 |
| add_features | default_vals                       | default_vals           | default_vals         | 0.42236 |
| hpo          | num_leaves: lower=1000, upper=1500 | dropout_prob: 0.0, 0.5 | num_boost_round: 100 | 0.52473 |

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score](https://testksj.oss-cn-beijing.aliyuncs.com/uPic/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score](https://testksj.oss-cn-beijing.aliyuncs.com/uPic/model_test_score.png)

## Summary
During this project, I learned
* How to set up Amazon SageMaker Studio
* How to use AutoGluon in Amazon SageMaker Studio
* How to do hyper parameter tuning in AutoGluon
