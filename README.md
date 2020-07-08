# Microsoft-Azure-ML-Scholarship

_Basically convert everything into numbers_

## Scaling Data
Let's consider an example. Imagine you have an image represented as a set of RGB values ranging from 0 to 255. We can scale the range of the values from 0–255 down to a range of 0–1. This scaling process will not affect the algorithm output since every value is scaled in the same way. But it can speed up the training process, because now the algorithm only needs to handle numbers less than or equal to 1.
There are 2 approaches to it: **standardization** and **normalization**.

**Standardization _rescales data so that it has a mean of 0 and a standard deviation of 1_** 
(𝑥 − 𝜇)/𝜎   We subtract the mean (𝜇) from each value (x) and then divide by the standard deviation (𝜎)

**Normalization _rescales the data into the range [0, 1]._**
(𝑥 −𝑥𝑚𝑖𝑛)/(𝑥𝑚𝑎𝑥 −𝑥𝑚𝑖𝑛)    For each individual value, you subtract the minimum value (𝑥𝑚𝑖𝑛) for that input in the training dataset, and then divide by the range of the values in the training dataset. The range of the values is the difference between the maximum value (𝑥𝑚𝑎𝑥) and the minimum value (𝑥𝑚𝑖𝑛).



## Encoding Categorical Data
When we have categorical data, we need to encode it in some way so that it is represented numerically.

#### Ordinal Encoding
In ordinal encoding, we simply convert the categorical data into integer codes ranging from 0 to (number of categories – 1).

**drawbacks** 
This approach is that it implicitly assumes an order across the categories. In the above example, Blue (which is encoded with a value of 2) seems to be more than Red (which is encoded with a value of 1), even though this is in fact not a meaningful way of comparing those values. This is not necessarily a problem, but it is a reason to be cautious in terms of how the encoded data is used.

#### One-Hot Encoding
we transform each categorical value into a column. If there are n categorical values, n new columns are added. 

##  Image Data
If you zoom in on an image far enough, you can see that it consists of small tiles, called pixels.

- In **grayscale images**, each pixel can be represented by a single number, which typically ranges from 0 to 255. This value determines how dark the pixel appears (e.g., 0 is black, while 255 is bright white).

- In **colored images**, each pixel can be represented by a vector of three numbers (each ranging from 0 to 255) for the three primary color channels: red, green, and blue(RGB).

The _number of channels_ required to represent the color is known as the **color depth** or simply depth. With an RGB image, depth = 3, because there are three channels (Red, Green, and Blue). In contrast, a grayscale image has depth = 1, because there is only one channel.

#### Encoding an Image
We need to know the following three things about an image to reproduce it:

- Horizontal position of each pixel
- Vertical position of each pixel
- Color of each pixel

The size of the vector required for any given image would be the **height * width * depth** of that image.

#### Assumptions
We would want to ensure that the input images have a _uniform aspect ratio_ (e.g., by making sure all of the input images are square in shape) and are _normalized_ (e.g. subtract mean pixel value in a channel from each pixel value in that channel)

## Text Data

#### Normalization
One of the challenges that can come up in text analysis is that there are often multiple forms that mean the same thing. 
For example, the verb _to be_ may show up as _is, am, are_, and so on. Or a document may contain alternative spellings of a word, such as _behavior vs. behaviour_. So one step that you will sometimes conduct in processing text is normalization.

Text **normalization** is the _process of transforming a piece of text into a canonical (official) form._

**Lemmatization** is an example of normalization. A lemma is the dictionary form of a word and lemmatization is the process of reducing multiple inflections to that single dictionary form. For example, we can apply this to the is, am, are example we mentioned above:
| Original Word      | Lemmatized word |
| ----------- | ----------- |
| is     | be       |
| are   | be      |
| a |  be |

**Stop words** are high-frequency words that are unnecessary (or unwanted) during the analysis. So, remove them.

Here we have **tokenized** the text (i.e., split each string of text into a list of smaller parts or tokens), _removed_ stop words (the), and _standardized spelling_ (changing lazzy to lazy).













