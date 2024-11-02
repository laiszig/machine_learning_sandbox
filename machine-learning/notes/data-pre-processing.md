Machine Learning 2 - Data Analysis and Pre-processing

Supervised Learning Paradigm
- Guided by an external "teacher"
- The teacher knows about the task
- Represented by a set of pairs (x, d)
- The algorithm generates a model to reproduce the teacher's behavior.
- Model parameters are adjusted by successsive presentations of the pairs (x,d) - Training Phase
- After treining, the system performance must be tested with unseen data - Testing Phase

What is data?
- An abstraction of a real world entity.
- Information is data that was processed, stuctured or contextualized, so as to have meaning to humans.
- Variable, Feature and Attribute are terms indistinctively used to indicate an individual abstraction.

- Each entity is typically described by a number of attributes.
- A dataset consists in related data to a collection of entitites. 
Each entity is described in terms of a list of attributes.

What is a Dataset?
- Matrix n*m where n = number of lines (objects) and m = number of columns (attributes)
- We choose attributes that are going to compose the dataset, it is the result of our problem and what we believe is relevant to it.
- More attributes means more cost. To collect and also performance costs.

Data, info, knowledge and wisdom/intelligence
- Data is created from abstractions or real world measurements 
- Information is data that was processed, stuctured or contextualized, so as to have meaning to humans.
- Knowledge is infor already interpreted and understood by a human so it can act as necessary.
- Wisdom/Intelligence is acting accordingly as per the knowledge.

Values for attributes
- Attribute values are numbers of symbols attributed to an attribute
- Difference between attribute and value: the same attribute can be mapped with different values e.g. height in m or ft
- Different attributes can be mapped to the same value set.
- The way we measure an attribute cannot coicide with its properties.

Dataset
- Lines (N)
	- Instances
	- Objects
	- Examples
	- Tuples
	- Samples
	- Cases
	- Records
	- Feature vector
- Columns (m)
	- Attributes
	- Features
	- Field
	- Variable
	- Dimention
	
Attributes can be qualitative or quantitative.
Target attribute - class, label, dependent variable

TYpes of attribute (traslate to the propper english terminology)
- Nominal (qualitative) - simple different names. They contain only enough information to distinguish one instance from another. (accepted operations: equal or different)
- Ordinal (qualitative) - enough information to distinguis and order instances (equal, different, > or <)
- Intervalar (quantitative) - attributes where the difference between values makes sense. There is a unit of measurement with zero arbitrary reference. (accepted operations: equal, different, > or <, + or -)
- Racional (quantitative) - not only the difference between values makes sense, but also the reason between values (zero is absolute). (accepted operations: equal, different, > or <, + or -, * and /)

---------

Data Preparation

Types of attributes:
- Continuous attribute: assumes an uncountable quantity of values
	- real numbers (temperature, weight, distance)
- Discrete attribute: assume a countable value (finite or infinite)
	- seasons of the year, elementary colors, postal code, etc
	- Binary attributes: 0 or 1, V or F, S or N...
		- Assymetric binary attributes: assumes 2 values, but only one is relevant (indicating the instance has a determined characteristic)
		(add example here) - text mining is a classical scenario
		
- Preliminary data exploration
	- Facilitates the undestanding of its characteristics.
	- Helps select the best technique of pre-processing or learning
	- Uses: descriptive statistics and visualization
	
- Descriptive Statistic
	- Allows to capture: data frequency, localização ou tendencia central, dispersão ou espalhamento, distribuição ou formato (user proper english terms here)
	
Frequency
	- Times an attribute assumes a data value
		- Frequently used for categorical attribute analysis

Location Measurements
- Categorical data 
	- Mode
- Numerical data
	- Mean
	- Median
	- Percentile
	
Mean:
- sensible to outliers
- Good indicator of the center of the dataset values when they are simetrically distributed.

Median
- Less sensible to outliers
- Necessary to order the values
	- Complexity bigger than linear in worst case scenario
- Indicates a better center if distribution is skewed and/or there are outliers.

Weighted average
- "Trimmed mean"
- Minimizes the issues with the mean, by discarting values from the extremities.
			- Percentage p of values are eliminated
			- Data is ordered
			- Eliminates p/2% of values in each extremity.
			
Quartiles
- Median devides the data in half.
- Other measures use different division points.
	- Quartiles (in fourths)
		- First quartile (Q1) is the sample where 25% of values are inferior to it.
		- Also known as the 25th percentile.
		- Second quartile Q2 = median. 50th percentile.
		
Boxplot
- Summary of informations from quartiles to be presented in a graph called boxplot.

Percentile: The p percentile is a value of x when p% values observed are less than that value.

Spread measures
- measure the dispersion (or spread degree) of a dataset
- indicate if an attribute is
	- widely spread
	- relatively concentrated in a specific point( ex: mean)
	- common measures: range, variance, standard deviation
	
Range: calculates the maximum spread. largest value minus the smallest value. It is not resistant, because changing just one datum can make it arbitrarily large.

Variance (σ²): A preferred measure of spread (dispersion) in data analysis.
Denominator (N-1): Known as Bessel's correction, which adjusts the calculation for a better estimate of the true variance in a sample.
Second central moment: Variance is defined as the second central moment of the data distribution.
Standard Deviation (σ): The square root of the variance, often used alongside variance to interpret data spread in the original units of measurement.

Skewness
Definition: Measures the symmetry of a distribution around its mean.
Scale Independence: Division by σ³ (the standard deviation cubed) makes this measure independent of scale.
Third Central Moment: Skewness is the standardized third central moment of the distribution.
Kurtosis
Definition: Measures the shape (flatness or peakedness) of a distribution.
Fourth Central Moment: Kurtosis is the standardized fourth central moment of the distribution.
Normal Distribution Reference: For a standard normal distribution, kurtosis is 3. Often, excess kurtosis is used, which is β(x)−3, so a standard normal distribution has an excess kurtosis of 0.

Histogram

Definition: A histogram is a graphical tool used to display the distribution of a dataset by showing the frequency of data points within specified ranges or "bins."
Usage: It is especially useful for visualizing kurtosis (shape or flatness) and skewness (symmetry or asymmetry) of the distribution. The shape of the histogram can reveal whether the data has:
High kurtosis (sharp peak) or low kurtosis (flatter distribution).
Positive skew (long tail on the right) or negative skew (long tail on the left).

Multivariate data:
Univariate data: Examines a single variable or data feature to draw conclusions
Multivariate data: Examines multiple variables to understand the complex relationships and interactions between them 
We acquire each attribute separately, and aggregate after.
- Spread of a dataset can be captured by a covariance matrix. Each element is the covariance of a pair of attributes
- Covariance doesn't really indicates clearly the relationship between pairs of attributes.
	- We can use correlation. It indicates a linear relationship between two variables
	- It is preferred to explore data, instead of covariance.
	
Correlation (Pearson)
- Varies from -1 to 1
- Vector magnitude are ignored when normalized by deviation.
	- ignores mean and variability
- Correlation of 1 or -1 means xj and xk have a perfect linear relationship (positive or negative)
- Correlation of 0 means there is no linear relationship.

Data Transformation
- Conversion from symbolic to numerical values
- Conversion from numerical to symbolic values

Conversion of Categorical Values
Many machine learning (ML) algorithms, such as Neural Networks and Support Vector Machines (SVM), work only with numerical variables.
Categorical variables must be converted to numerical form. The conversion approach depends on whether there is an inherent order in the categories:
Nominal variables: Conversion often uses one-hot encoding, where each category is represented by a binary vector.
Ordinal variables: Conversion typically uses integer encoding or target encoding, preserving the order for the model.

Ordinal Value Conversion
Maintaining Order: For ordinal variables, the order of values should be preserved in some way.
	-  Assign increasing integer values to represent the order (e.g., {cold, warm, hot} = {1, 2, 3}).
Potential Issues: This method may introduce distortions in the relative differences between categories, as differences are subjective and may not truly reflect the distances between concepts.

Nominal Value Conversion
Nominal attributes lack an inherent order.
	- Conversion Method: Typically handled through binarization, using either one-hot encoding (1-of-n encoding) or integer-binary encoding.

One-Hot Encoding (1-of-n Encoding)
Assigns a unique binary attribute for each category, with one attribute set to 1 and all others to 0.
Example: Encoding {yellow, red, green, blue, orange, white} results in a binary vector for each color.
Dimensionality Drawback: This can produce a large number of attributes, leading to the curse of dimensionality.
Advantages:
Equidistance: Maintains equal distances between any two binary vectors.
Independence: Binary attributes are uncorrelated.
Asymmetry: Binary attributes are asymmetric, which is required for some ML algorithms.
Mode Representation: The mode of a nominal attribute corresponds to the binary attribute with the most 1s.

Integer-Binary Encoding
Method: Each nominal value is first assigned an integer, then converted to binary representation.
Advantages: Requires fewer binary attributes (log₂(n)).
Disadvantages:
Non-uniform Differences: Differences between values are not the same in integer or binary representations, which can introduce correlations between attributes.
Algorithm Compatibility: Can perform poorly with certain ML algorithms due to induced correlations and unequal distances between categories.