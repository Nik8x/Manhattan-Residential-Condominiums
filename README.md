# Manhattan-Residential-Condominiums
Filtering Investment Opportunities  in Manhattan Residential Condominiums
I collected the data from NYC Department of Finances website. They also have archive of historical data. 
I used R as my primary tool for the analysis. 
Here are the criterias I used to screen investment opportunities:
- Must be condominium (not co-op or condop) and Elevator or walk-up
- Price: less than $3,500,000
- Price per square foot: less than $2,000
- Distance from Manhattan south of 96th Street
- Rental yield of 2% or more (I was not sure about the calculation over here)

The database can be stored on Amazon AWS or similar services and can be updated with SQL query every week. And this R code will generate a new list, if any, every week.
