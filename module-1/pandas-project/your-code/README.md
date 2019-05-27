# Demonstration of Data Cleaning and Manipulation with Pandas

## Data cleaning processes (Steps)

Start with importing the data set (CSV file)
 
Create a copy of the original dataframe to modify it safely

Examine the data : there are unnamed columns, columns containing links and others containing numbers that refer to number cases.
Since those don't give any relevant information, we delete them from the start

Clean the names of the remaining columns, drop all the spaces and return lowercase strings

Dropping columns with high pencentage of NaN values

We noticed that the columns 'name', 'sex' and 'age' won't give any relevant information, since the shark attack is not related the the age and sex people. So we dropped these columns.

Drop the rows containing NAN values.

After cleaning the data set in a summary way, let's dive into each columns and try to figure out how we can group their values.
WE choosed to clean the columns : "fatalyn", "time", "injury","country", "type"

** Attribute "fatalyn" : we only keep the two values "Y" and "N", and transform the " N" to "N" by deleting the space.
Result: 

N    1433
Y     263
Name: fatalyn, dtype: int64

**Attribute "time"
The time is given by the approximative hour when the incident happened and by the parts of the day( morning, late evening etc...)
The better way we think we can group those column values is to transform all the hours to names of the parts of the day.
So we created 9 hours intervals, each is corresponding witha specific par of the day. Then update the dataframe with the new column.

Result:
earlyafternoon    392
morning           352
afternoon         147
earlymorning      139
latemorning       130
lateafternoon     101
earlyevening       92
evening            21
night              19
Name: time, dtype: int64

**Attribute "injury"

Clusterize the column "injury" values into 5 cases: "death", "no injury", "provoked", "injury", "amputation". Then make a list of the words that apprear in the column "injury" values the make them correspond with the 5 cases..Then update the new column.

Result: 

injury        813
death         515
provoked       34
amputation     18
no injury      13
Name: injury, dtype: int64

**Attribute "country"

We create a list of all the countries and territories contained in each ocean worldwild and put every country written in the "country" column into the right ocean. The localisation is very important to analyse the incidence of sharks attacks around the world. Then update the new column.

Result:

atlantic ocean    988
pacific ocean     376
indian ocean       29
Name: country, dtype: int64

** Attribute "type"

We find "invalid" value in the column, we don't know to which type of attack it refers so we dropped all these values.
The types: Boat, Sea disaster, Boating, can be considered as Unprovoked to simplify the column.

The most relevant columns were cleaned so we can export our new cleaned data set to a CSV file. 


