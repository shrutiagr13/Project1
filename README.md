
# Hospitality-Dashboard

### Dashboard Link : 

## Problem Statement

This dashboard helps the hospitality industry understand their customers better. It helps the hospitality industry know if their customers are satisfied with their services. Through different ratings, they get to know their improvement area, & thus they can improve their services by identifying these area. It also lets them know the average revenue and bookings, thus since by using this dashboard they have identified this problem, they can further work on factors to regain their market share and revenue




### Steps followed 

Step 1 - Get the data from the folder, the source dataset are multiple excel files. 

Step 2 -To transform the data, will go to power query page.Power Query is basically a part of power bi and it is used for data transformation and data cleaning.

Step 3 - we will duplicate the input file, so that we can save each table separattely.

Step 4 - then will open one excel file so it will connect to the source, navigate to the folder fetch data, promote the header.

Step 5 -will rename the input file then then we can get the tables listed out, we can check on if the first row is promoted as header or not, if some column is not required we can just remove the column and its a best practice to rename the step as Removed Column: Column Name 

Step 6 - So this all done for the power query, we can close and apply this the we will be back to the power bi desktop with our cleaned and transformed data set. 

Step 7 - Then comes in picture data modelling.
In data modelling we establish relationship among the tables, some times in default we have some relationship already there just by the column name, we can view all that in manage relationship tab, if we want to delete we can delete that.

Step 8 - then we can starting connecting same column in different tables to create a relationship, One to many relationship can also be created, ex: for one date there are multiple bookings. 

Step 9 - Then we have DAX(Data Analytics expression), by this we can create new columns and new measures, it has as all the formula in built which help to extract the data fom the column that we want.Here we have created so many measures which can help us creating a meainngful dashboard,below listed are the measures that we have created.

    Revenue
    Total Bookings
    Total Capacity
    Total Succesful Bookings
    Occupancy %
    Average Rating
    No of days
    Total cancelled bookings
    Cancellation %
    Total Checked Out
    Total no show bookings
    No Show rate %
    Booking % by Platform
    Booking % by Room class
    ADR 
    Realisation %
    RevPAR
    DBRN
    DSRN 
    DURN
    Revenue WoW change %
    Occupancy WoW change %
    ADR WoW change %
    Revpar WoW change %
    Realisation WoW change %
    DSRN WoW change %



Some of the DAX Formula that is used to create these measures are:

DAX FORMULA

Revenue 

    Revenue = SUM(fact_bookings[revenue_realized])

Total Succesful Bookings


    Total Succesful Bookings = SUM(fact_aggregated_bookings[successful_bookings])

Occupancy %

    Occupancy % = DIVIDE([Total Succesful Bookings],[Total Capacity],0)

Cancellation % 

    Cancellation % = DIVIDE([Total cancelled bookings],[Total Bookings])

Booking % by Room class

    Booking % by Room class = DIVIDE([TotalBookings],
    CALCULATE([Total Bookings], 
    ALL(dim_rooms[room_class])
    ))*100"

RevPAR 

    RevPAR = DIVIDE([Revenue],[Total Capacity])

DBRN

    DBRN = DIVIDE([Total Bookings], [No of days])

DSRN

    DSRN = DIVIDE([Total Capacity], [No of days])

DURN

    DURN = DIVIDE([Total Checked Out],[No of days])

Revenue WoW change %

    Revenue WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([Revenue],dim_date[wn]= selv)
    var revpw = CALCULATE([Revenue],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

    return


    DIVIDE(revcw,revpw,0)-1

Occupancy WoW change %

    "Occupancy WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([Occupancy %],dim_date[wn]= selv)
    var revpw =  CALCULATE([Occupancy %],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

    return


    DIVIDE(revcw,revpw,0)-1"

ADR WoW change %

    "ADR WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([ADR],dim_date[wn]= selv)
    var revpw =  CALCULATE([ADR],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

    return


    DIVIDE(revcw,revpw,0)-1"

Revpar WoW change %

    "Revpar WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([RevPAR],dim_date[wn]= selv)
    var revpw =  CALCULATE([RevPAR],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

    return


    DIVIDE(revcw,revpw,0)-1"

Realisation WoW change %

    "Realisation WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([Realisation %],dim_date[wn]= selv)
    var revpw =  CALCULATE([Realisation %],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

    return


    DIVIDE(revcw,revpw,0)-1"

DSRN WoW change %

    "DSRN WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([DSRN],dim_date[wn]= selv)
    var revpw =  CALCULATE([DSRN],FILTER(ALL(dim_date),dim_date[wn]= selv-1))

    return


    DIVIDE(revcw,revpw,0)-1"

Step 10 - After creating the measures, we can starting building visuals for our final dashborad.

Some of the visuals that we have used in the dash boards are:

    Card Visuals
    Donut Chart Visuals
    Table Visuals
    Line Chart
    Line Stacked Columns




  
