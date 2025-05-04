The Move from Coal to Renewable Electricity
The data we will be using records the total number of terawatt hours (TWh) of electricity generated from renewables (specifically, solar and wind) and from coal by each country over a number of years.
This data has been sourced from Our World In Data, but has been cleaned to remove empty data entries and other exceptional cases. See the attached file `OWID_SolarWind_vs_Coal.csv`.


Have a look at the structure of this data to make sure you understand it. Each row in the file is a record for a specific country and a specific year. Each element in the row is separated by a comma, giving 5 columns:

Country: The name of the country

Code: The unique three-letter ISO country code for the country

Year: The year in which the electricity was produced

SolarWindTWh: The total number of terawatt hours of electricity from solar and wind power produced by that country in that year

CoalTWh: The total number of terawatt hours of electricity from coal produced by that country in that year


You are required to implement a Bash script, which must be called renewables_stats, and must take exactly 4 arguments:

1. The name of a CSV data set formatted like the above OWID data set
2. One of the following:
    2.1 The three-letter ISO country code for a country, or
    2.2 A year
3. The type of energy to be queried: Either solar_wind or coal
4. The operation to perform: Either min or max

In short, calls of the renewables_stats script will have the form:
renewables_stats <csv file path> <country_code | year> <'solar_wind' | 'coal'> <'min' | 'max'>`
where `<a | b>` means to enter a choice of either a or b.
Your program is expected to detect when it is given invalid arguments and report a meaningful error message explaining what went wrong.
When a country code is specified, the program should report the minimum or maximum amount of electricity produced from the specified source by the specified country in any year, and the (or a) year with that amount.
When a year is specified, the program should report the minimum or maximum amount of electricity produced from the specified source in the specified year by any country, and the (or a) country with that amount.

Examples


The following are some sample queries showing how your program is expected to respond with the provided OWID data set:

% ./renewables_stats OWID_SolarWind_vs_Coal.csv 2013 solar_wind max

The maximum amount of electrical energy produced from solar and wind in 2013 was 176.87 TWh by United States (USA).

% ./renewables_stats OWID_SolarWind_vs_Coal.csv 2013 coal max

The maximum amount of electrical energy produced from coal in 2013 was 4077.37 TWh by China (CHN).

% ./renewables_stats OWID_SolarWind_vs_Coal.csv AUS coal min

The minimum amount of electrical energy produced from coal for Australia (AUS) was 123.36 TWh in 1990.

% ./renewables_stats OWID_SolarWind_vs_Coal.csv AUS coal avg

Error: Unknown operations avg. Expected 'min' or 'max'.

% ./renewables_stats nope.csv AUS coal max

Error: The specified input file nope.csv does not exist or is empty.
