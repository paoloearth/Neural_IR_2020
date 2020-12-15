

---

Link to get the whole project, containing also the data and the pre-trained embeddings: [HERE]( https://drive.google.com/file/d/17E9fIbZPk7zkwopqEt47g7fDJ4H2fVz7/view?usp=sharing)

---



# Neural IR 2020

**Hello!** Welcome to the the companions notebooks for the 2020 IR project on Neural IR: I  promise this will be fast.

To match the more theoretical part of the work (Report + Presentation) I decided to get my hands dirty by developing a demonstration application of the Doc2Vec framework.

The  3-notebooks project is split in 3 jupyter files:

- `0_Preprocess.ipynb`

- `1_Doc2Vec_Movies.ipynb`

- `2_PlayGround.ipynb`

All these will be used during the live presentation as a support to the theoretical material.

---

In addition to the notebooks, 3 folders: `data`, `models`, `preprocessed` will be present. The first will contains the movies dataset, used during the course, with its companion file which contains the plots of the movies. 

The `models` folder will contained the pretrained model that was created for the task

Finally, the `preprocessed` will contain a transformation of the original dataset into a more functional one.

---

The **libraries** used  by the code are:

- `Seaborn` and `matplotlib` for plotting

- `pandas, json, numpy, sklearn, string` for data manipulation

- `nltk` for text preprocessing, stemming

- `gensim` for the creation of the Doc2Vec model

- `cython` is suggested to speed up `gensim`

- `pickle` to serialize and deserialize objects

---

**Efficiency** (performance) of the code was taken into account: I tried to use vectorized functions as much as possible and avoid loops, making use of the built-in functions of pandas and numpy.

---

**KISS** (Keep It Simple Stupid) principle was adopted, trying to breakdown in short, easy to maintain and reusable functions the code.

Nevertheless, repetitions  are omnipresent but on purpose for easy and fast lookup. This is still a toy example and building a library would not  be usefull. 

All the functions are commented.

---

Lets briefly break down the notebooks:

### ` 0_Preprocess.ipynb`

This is, as the name suggests, a preprocessing notebook.

Here I firstly merge the data (`pandas`), discard the unusefull columns and apply the following text transformations(`string,nltk`):

- tokenization

- stopword removal

- stemming

- lemmatization

Only documents with a plot of more than 1000 words were kept.

After the preprocessing is finished, the " clean "  pandas dataframe is serialized into a pickle object.

### `1_Doc2Vec_Movies.ipynb`

In notebook 2 the protagonist is the training of the Doc2Vec model (`gensim`).

After reading the dataframe from the previous step the model is trained on the corpus and saved to the preprocessed library for future use.

At the end of the notebook a "sanity check" is performed, that is, I query a random selection of documents (seed can be set for reproducibility) with the model and check if the most similar document returned are the query documents themselves.

### `2_PlayGround.ipynb`

This is where the model is "tested". Since the dataset is not labelled, the test is only based on my human judgement.  (more of this during the presentation)

Query can be performed by the custom function `query`, which takes strings.When querying the number of documents to retrieve can be easily set by the second parameter.

Movies can be inspected via the `describe_movie` function to investigate wheter the relation found by the model makes sense.

To make it easy to find a wanted movie, the function `get_movies_from_title` will return the  partial matches (of title) of the dataframe, as a dataframe.

Once we have the code/index of a movie, we can call the function `get_neighbours` which will return the k closest movie to the one indexed by the code passed.

> Positively, when queried with the plot of a "star wars"  movie, the model return the other star wars movie.
> 
> The same is true for "the lord of the rings" (as can be seen directly from the notebook.)

Finally, a visualization tool is provided. Since the vectors of embeddings have size 100, i used  [sklearn TSNE](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html) to squeeze them down to 2 dimension. 

Unfortunately, the results where not magnificent. 

---

That was it. Thanks for the time dedicated to the reading.

For any question, hit me at paoloearth@gmail.com

Cheers,

Paolo.
