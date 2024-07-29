# Project : Evaluating Food Hygiene Ratings
## Introduction
The UK Food Standards Agency evaluates various establishments across the United Kingdom and assigns them food hygiene ratings. To assist the journalists and food critics of *Eat Safe, Love*  magazine's in analyzing these ratings for their future articles, exploratory analysis is required.
## Part 1: Database and Jupyter Notebook Setup
1. **Database Import**:
    
    Import the data from establishments.json into MongoDB using the provided Terminal commands. Name the database uk_food and the collection establishments.

2. **Library Imports**:

    In your Jupyter Notebook, import the necessary libraries: PyMongo and Pretty Print (pprint).

3. **MongoDB Client Setup** : 

    Create an instance of **MongoClient** to connect to your MongoDB server.

4. **Database Verification**:

    - List all databases to confirm that uk_food is present.
    - List all collections within the uk_food database to ensure that the establishments collection exists.
    - Retrieve and display one document from the establishments collection using find_one and format the output with pprint.

## Part 2: Update the Database
1. **Add New Restaurant**
    - Insert a new record for a halal restaurant located in Greenwich that hasn't been rated yet.
    - Retrieve the BusinessTypeID for "Restaurant/Cafe/Canteen" and update the new restaurant record with this BusinessTypeID.
    
2. **Remove Establishments in Dover**:
    - Count and remove all documents with the LocalAuthorityName of Dover from the database.
    - Verify the deletion by counting the number of remaining documents.
    
3. **Data Type Correction**:
    - Convert latitude and longitude values stored as strings to decimal numbers.
    - Convert RatingValue from strings to integers, ensuring that non-numeric values are handled appropriately.
    
## Part 3: Exploratory Analysis
1. **Hygiene Score Analysis**:

    - Identify establishments with a hygiene score of 20.
    - Use count_documents to display the number of such documents.
    - Convert the results to a Pandas DataFrame, print the number of rows, and display the first 10 rows.
    
2. **London Rating Value Analysis**:

    - Find establishments in London with a RatingValue greater than or equal to 4. Note that London’s Local Authority name may contain more than just "London".
    - Use `$regex` to match the full Local Authority name.
    - Use count_documents to get the number of such documents, and convert results to a Pandas DataFrame.

3. **Top Establishments by Rating and Proximity**:

    - Determine the top 5 establishments with a RatingValue of 5, sorted by the lowest hygiene score, and located nearest to the new restaurant "Penang Flavours".
    - Search within a 0.01 degree range around the latitude and longitude of "Penang Flavours".
    - Use geospatial queries to find and sort these establishments.

4. **Local Authority Hygiene Score Analysis**:

    - Find how many establishments in each Local Authority area have a hygiene score of 0.
    - Sort the results from highest to lowest and limit to the top 10 Local Authority areas.
    - Convert the results to a Pandas DataFrame and print out the top 5 rows.
