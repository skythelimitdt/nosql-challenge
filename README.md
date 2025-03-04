#### The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

### Part 1: Database and Jupyter Notebook Set Up
Used [NoSQL_setup_starter.ipynb](https://github.com/skythelimitdt/nosql-challenge/blob/main/NoSQL_setup_starter.ipynb)
 for this section of the challenge.

1. Imported the data provided in the establishments.json file from your Terminal.
2. Named the database 'uk_food' and the collection 'establishments'. 
3. Within the notebook, imported the libraries I needed: PyMongo and Pretty Print (pprint).
4. Created an instance of the Mongo Client.
5. Confirmed that I created the database and loaded the data properly.
6. Assigned the 'establishments' collection to a variable to prepare the collection for use.

### Part 2: Update the Database
Used [NoSQL_setup_starter.ipynb](https://github.com/skythelimitdt/nosql-challenge/blob/main/NoSQL_setup_starter.ipynb) for this section of the challenge.

The magazine editors have some requested modifications for the database before I could perform any queries or analysis for them. I made the following changes to the establishments collection:

1. An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the information to the database.
2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.
3. Update the new restaurant with the BusinessTypeID you found.
4. The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.
5. Some of the number values are stored as strings, when they should be stored as numbers.
    6. Use update_many to convert latitude and longitude to decimal numbers.
    7. Use update_many to convert RatingValue to integer numbers.

### Part 3: Exploratory Analysis
Eat Safe, Love has specific questions they want me to answer, which will help them find the locations they wish to visit and avoid.

Used [NoSQL_analysis_starter.ipynb](https://github.com/skythelimitdt/nosql-challenge/blob/main/NoSQL_analysis_starter.ipynb)
 for this section of the challenge.

Some notes to be aware of while you are exploring the dataset:

- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

**Some questions to answer:**
1. Which establishments have a hygiene score equal to 20?
2. Which establishments in London have a RatingValue greater than or equal to 4?
3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

#### References
chatgpt: Query assistance on this query: query = {
    'RatingValue': 5,
    'geocode.latitude': {'$gte': latitude - degree_search, '$lte': latitude + degree_search},
    'geocode.longitude': {'$gte': longitude - degree_search, '$lte': longitude + degree_search}
