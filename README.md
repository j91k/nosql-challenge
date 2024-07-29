# Project : Evaluating Food Hygiene Ratings
## Introduction
The UK Food Standards Agency evaluated various establishments across the United Kingdom and assigned them food hygiene ratings. To assist the journalists and food critics of *Eat Safe, Love* magazine in analyzing these ratings for their future articles, exploratory analysis was required.
## Part 1: Database and Jupyter Notebook Setup
1. **Database Import**:
    
    Imported the data from establishments.json into MongoDB using the provided Terminal commands. Named the database uk_food and the collection establishments.

2. **Library Imports**:

    In your Jupyter Notebook, imported the necessary libraries: PyMongo and Pretty Print (pprint).

3. **MongoDB Client Setup** : 

    Created an instance of **MongoClient** to connect to your MongoDB server.

4. **Database Verification**:

    - Listed all databases to confirm that uk_food was present.
    - Listed all collections within the uk_food database to ensure that the establishments collection existed.
    - Retrieved and displayed one document from the establishments collection using find_one and formatted the output with pprint.

## Part 2: Update the Database
1. **Add New Restaurant**
    - Inserted a new record for a halal restaurant located in Greenwich that hadn't been rated yet.
    - Retrieved the BusinessTypeID for "Restaurant/Cafe/Canteen" and updated the new restaurant record with this BusinessTypeID.
    
2. **Remove Establishments in Dover**:
    - Counted and removed all documents with the LocalAuthorityName of Dover from the database.
    - Verified the deletion by counting the number of remaining documents.
    
3. **Data Type Correction**:
    - Converted latitude and longitude values stored as strings to decimal numbers.
    - Converted RatingValue from strings to integers, ensuring that non-numeric values were handled appropriately.
    
## Part 3: Exploratory Analysis
1. **Hygiene Score Analysis**:

    - Identified establishments with a hygiene score of 20.
    - Used count_documents to display the number of such documents.
    - Converted the results to a Pandas DataFrame, printed the number of rows, and displayed the first 10 rows.
    
2. **London Rating Value Analysis**:

    - Found establishments in London with a RatingValue greater than or equal to 4. Noted that London’s Local Authority name may have contained more than just "London".
    - Used `$regex` to match the full Local Authority name.
    - Used count_documents to get the number of such documents, and converted results to a Pandas DataFrame.

3. **Top Establishments by Rating and Proximity**:

    - Determined the top 5 establishments with a RatingValue of 5, sorted by the lowest hygiene score, and located nearest to the new restaurant "Penang Flavours".
    - Searched within a 0.01 degree range around the latitude and longitude of "Penang Flavours".
    - Used geospatial queries to find and sort these establishments.

4. **Local Authority Hygiene Score Analysis**:

    - Found how many establishments in each Local Authority area had a hygiene score of 0.
    - Sorted the results from highest to lowest and limited to the top 10 Local Authority areas.
    - Converted the results to a Pandas DataFrame and printed out the top 5 rows.

