# Recommendations with IBM

[IBM Watson Studio](https://www.ibm.com/cloud/watson-studio) is a software platform for data science. The platform contains articles that provide useful information such as tutorials for users, summaries of developments in the field of data science, and much more. In this project, I have built out several different methods for making article recommendations to users of IBM Watson Studio, including rank-based, user-user-based collaborative filtering, content-based, and matrix factorization techniques. The data provided by IBM contains details about which articles users have interacted with, as well as the content of each article on the platform.

# Requirements

- pandas
- NumPy
- Matplotlib
- pickle
- re
- nltk
- scikit-learn
- warnings

# Files

- Recommendations_with_IBM.ipynb - contains code for creating recommendation systems
- data
  - user-item-interactions.csv - data for user-article interactions
  - articles_community.csv - data about article content
- project_tests.py - test scripts provided by Udacity
- top_5.p, top_10.p, top_20.p - supplemental pickle files used in the test scripts
- user_item_matrix.p.zip - saved user-item matrix as a pickle file
- base.yaml - contains the environment used in this project

To get the Jupyter Notebook running, execute the following in the command line and select Recommendations_with_IBM.ipynb from the Jupyter Notebook dashboard. Be sure to also unzip user_item_matrix.p.zip. The conda environment setup is optional.

```
$ git clone https://github.com/evanchen13/ibm-recommendations.git
$ cd ibm-recommendations
$ conda env create -f base.yaml
$ jupyter notebook
```

# Summary of Recommendation Methods

## Rank-Based

Rank-based systems provide recommendations based on the highest popularity, whether that is measured by ratings, frequency of use, or some other metric. Because the data provided by IBM does not have user ratings, the popularity of an article can really only be based on how often an article was interacted with. To provide the rank-based recommendations, I have written functions that return a certain number of top articles ordered with most interactions as the top.

## User-User-Based Collaborative Filtering

Collaborative filtering systems use the interactions between users and products to provide recommendations. For the user-user-based collaborative filtering, I have created a matrix, with users as the rows and articles as the columns, that shows whether a user has interacted with an article. I have taken the dot product of this matrix with its transpose to find the similarity between users. Then, to make recommendations for a given user, I have found the most similar users and recommended the articles that those users have interacted with that the given user has not seen.

## Content-Based

Content-based systems provide recommendations based on information about users or products. I have implemented this by finding the similarity between articles based on their content, similar to what was done with users in the user-user-based collaborative filtering. I have taken the article descriptions and used TFIDF to create a matrix with articles as the rows and tokens as the columns. Then I have taken the dot product of this matrix with its transpose to get the similarity between articles and recommended those with the highest similarity.

## Matrix Factorization

Matrix factorization uses latent features to make recommendations. Latent features are features implied by data, but not explicitly observed. By looking at the relationship between users and latent features, latent features and products, and the importance of each latent feature, I have used matrix factorization to predict how a user and product will interact.

# Acknowledgements

Special thanks to IBM for providing the data and the [Udacity Data Scientist Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025) for providing the Jupyter Notebook template and test code.

# License

The contents of this repository are covered under the [GNU General Public License v3.0](https://github.com/evanchen13/ibm-recommendations/blob/main/LICENSE).
