We are required to implement a Bash script, which must be called renewables_stats, and must take exactly 4 arguments:
1. The name of a CSV data set formatted like the above OWID data set
2. One of the following:
   2.1 The three-letter ISO country code for a country, or
   2.2 A year
3. The type of energy to be queried: Either solar_wind or coal
4. The operation to perform: Either min or max
   
In short, calls of the renewables_stats script will have the form:

renewables_stats <csv file path> <country_code | year> <'solar_wind' | 'coal'> <'min' | 'max'>`

where `<a | b>` means to enter a choice of either a or b.

Program is expected to detect when it is given invalid arguments and report a meaningful error message explaining what went wrong.

1. When a country code is specified, the program should report the minimum or maximum amount of electricity produced from the specified source by the specified country in any year, and the (or a) year with that amount.
2. When a year is specified, the program should report the minimum or maximum amount of electricity produced from the specified source in the specified year by any country, and the (or a) country with that amount.

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
