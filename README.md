# eMovies-redux
A modern-day reimaging of the eMovies data model(s) in erwin DM.

In my overhaul of the eMovies data models, I've preserved the fundamental core assets from the previous iteration and added new objects/concepts to help eMovies acclimate with the times.

First, let's go over several Points of Interest (POI) in the CDM changes/updates:

- Payment methods are now classified into either CC or ePayment to normalize logical model.

![alt text](https://github.com/wuda20/eMovies-redux/blob/emovies-dev/images/POI_payments.png?raw=true)

- Customers can now opt into rental tiers (default is "Basic") to receive rewards benefits (such as faster delivery and more robust content servers). In addition, each movie rental purchase is now associated with CDN for online rentals and delivery providers for warehouse purchases. This information will be useful in gauging the transition from brick-and-mortar to completely online viewing trends.

![alt text](https://github.com/wuda20/eMovies-redux/blob/emovies-dev/images/POI_customer-rentals.png?raw=true)

- Brick-and-mortar stores have been repurposed into warehouses, where fulfillment robots will now perform fulfillment duties alongside human workers.

![alt text](https://github.com/wuda20/eMovies-redux/blob/emovies-dev/images/POI_logistics.png?raw=true)

- To confidently assess viewing demographics and trends for the future, we've expanded our Movies aspect of the data model to include Stars (actors and directors), Nationality, and Genres . 

![alt text](https://github.com/wuda20/eMovies-redux/blob/emovies-dev/images/POI_movies.png?raw=true)

Next, let's have a closer look at additions and updates to the logical model:

- In the customer-related schema, there is now a prominent Tier entity with non-identifying relationships to the Customer, DeliveryProvider, and CDNProvider tables. 

- Payment entity has been normalized with the introduction of CCPayment and EPayment subtypes.

- Turning to Movies, I've included new Star, Nationality, and Genre entities and have settled on a many-many cardinality that will best serve the Movie-Star and Movie-Genre relationships, to better assist with eventual queries for film-related data.

- Speaking of robots, as warehouse robots now work alongside humans in warehouses, they are represented via a Robot entity class in the Employee portion of the schema.

And lastly, we'll dig into the changes to the physical data model.

- Another optimization involved lookup tables to reduce storage requirements for certain columns that previously had varchar datatypes: some examples were Robot.Condition, MovieCopy.Format, MovieCopy.Condition, MovieRentalRecord.RentalStatus, MovieRentalRecord, Star.StarNationality, etc. Replacing this attribute with an int will greatly speed lookup and centralize additions and deletions of lookup datatypes. Non-varchar columns, notably address-related columns in Customer, Employee, and Warehouse tables, also now reference lookup tables as well.

- Columns pertaining to financial information were replaced with money datatypes to better deal with potential precision issues.

- In the Movie table, Rating is now numeric and MovieClip is now a varchar(4000) of its associated Youtube trailer (should one exist).

- Link tables galore: link tables have been added to make tangible the many-many relationship between the Movies-Star and Movies-Genre tables, to assist with queries for such data. We anticipate the addition of more link tables as data engineers mine our data for more viewer insights. 

More changes to come in the pipeline. 
Thank you for your time.
