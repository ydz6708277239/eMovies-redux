# eMovies-redux
A modern-day reimaging of the eMovies data model(s) in erwin DM.

In my overhaul of the eMovies data models, I've preserved the fundamental core assets from the previous iteration and added new objects/concepts to help eMovies acclimate with the times.

First, let's go over several Points of Interest (POI) in the CDM changes/updates:

- Payment methods are now classified into either CC or ePayment to normalize logical model.

![alt text](https://github.com/wuda20/eMovies-redux/blob/emovies-dev/images/POI_customer-rentals.png?raw=true)

- Customers can now opt into rental tiers (default is "Basic") to receive rewards benefits. In addition, each movie rental purchase is now associated with CDN for online rentals and delivery providers for warehouse purchases. This information will be useful in gauging the transition from brick-and-mortar to completely online viewing trends.

- Brick-and-mortar stores have been repurposed into warehouses, where fulfillment robots will now perform fulfillment duties alongside human workers.

- To confidently assess viewing demographics and trends for the future, the movies schema has been vastly expanded, with new tables for actors, genres, languages, directors. 
