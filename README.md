# CS5265_Project1

This project will investigate how well nutrition facts can be approximated from product branding and the ingredients list. A successful model could be used to impute historical data missing from official sources and provide a preliminary data source of product nutrients before official test results are made available. Understanding product nutrition details is critical for many applications, especially in healthcare, so building tooling to fill in data gaps could be quite valuable in these areas.

## Performance Metrics

The two goals of this project - low-fat classification and calorie regression - have two different performance metrics. For the initial goal of binary low-fat classification, an appropriate performance metric is simple percent accuracy.
Computed from a simple confusion matrix (TN, TP, FN, FP), accuracy is computed like so:
$$Accuracy = \frac{TP+TN}{TP+TN+FP+FN}$$
If accuracy is low, precision and recall will be useful metrics to determine any bias in the error.
$$Precision = \frac{TP}{TP+FP}$$
$$Recall = \frac{TP}{TP+FN}$$
If classes are heavily unbalanced (e.g. there are relatively few low-fat products) it may be appropriate to use an accuracy metric that reflects both precision and recall, like F1 score.

$$F1 = \frac{2*TP}{2*TP+FP+FN}$$

From a business value standpoint, we will care much more about maximizing precision (ensuring that when we say something is low-fat, it actually is) than about maximizing recall (ensuring that we don't fail to identify low-fat products).
This is because if we call a product low-fat when it actually isn't, there may be regulatory implications or health problems for our customers, and we may be sued.
Maximizing recall is still important, however, as being able to correctly identify as many low-fat products as possible makes them more marketable, increasing sales. False negatives pose less of an existential risk to our business, however.

A test for fat content in food costs around $199.00 (Source: Medallion Labs). If technology like this allowed food manufacturers to expedite or bypass this process for a large number of products (assuming successful coordination with the relevant regulators), there could be significant savings over a large product catalog. Even without using this tool to skip regulatory steps, it could be used as a valuable pre-screening option to determine if the product is likely to meet nutritional specifications before subjecting it to expensive nutritional tests.

For the goal of calorie regression, the primary metric is MAE (Mean Absolute Error), which describes the average number of calories by which the predicted value varies from the actual value.
The formula is given below where x is the actual value, y is the predicted value, and D is the number of data points being evaluated.
$$\sum_{i=1}^{D}|x_i-y_i|$$

From a business value standpoint, we may also want to consider percentage error, where we additionally divide the error by the true value (x) so the metric is more interpretable for low-calorie items.
Accurate calorie tests are actually substantially cheaper, as they simply involve burning the food to heat water and measuring the temperature, and many labs will give them out for free. For some applications, however, like reconstructing nutrition for incomplete historical data where samples to burn are inaccessible, the business value may be substantial and harder to quantify.



