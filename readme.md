# Google QUEST Q&A Labeling

![img](https://storage.googleapis.com/kaggle-media/competitions/google-research/human_computable_dimensions_1.png)

- 使用从近70个网站收集来的question-answer pairs数据集，建立针对问答的不同主观方面的预测算法
  - (for different subjective aspects of question-an4swering)

The training data contains rows with some duplicated questions (but with different answers). The test data does not contain any duplicated questions.

This is not a binary prediction challenge. Target labels are aggregated from multiple raters, and can have continuous values in the range [0,1]. Therefore, predictions must also be in that range.

## Submission Evaluation

- 使用mean column-wise Spearman's correlation coefficient
- 对每个目标行计算spearman相关系数，再对它们求mean。
- 提交文件：
  - 对测试集中的每个`qa_id`，需要对其每个目标值预测一个prob
  - 其格式如下：

| qa_id | question_asker_intent_understanding | ...  | answer_well_written |
| ----- | ----------------------------------- | ---- | ------------------- |
| 6     | 0.0                                 | ...  | 0.5                 |
| 8     | 0.5                                 | ...  | 0.1                 |
| 18    | 1.0                                 | ...  | 0.0                 |