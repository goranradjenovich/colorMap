Get a colored map of the United States by providing a CSV containing a list of states with a numeric value for each state. Writes out an SVG with the colored map.

#Options

##Input and output
Specify your input file - the filename must have a .csv extension. If none is specified, program will prompt for one.

Specify your output file - the filename must have a .svg extension. If non is specified, program will output to `newMap.svg`.

e.g. `colorMap input.csv output.svg`

##Colors
Set your own colors - provide 2 or 3 hex color values in your arguments. If fewer than 2 are provided, we will use the default colors. If more than three are provided, only the first three colors will be used. Default colors: yellow (#F4EB37), orange (#FFA500), red (#8B0000)

e.g. `colorMap "#4286f4" "#42f448 "ee42f4"`

##Gradient options
###Default 
Retrieves one color for every unique value.
Each neighboring value has the same color distance between it, regardless of the value difference. e.g. given the set [1, 3, 6, 7], 1 and 3 will have the same difference as 6 and 7.

Unique values: `1, 3, 4, 7`

Retrieves a 4-color (`a, b, c, d`) gradient and assigns them to the 4 values

Color match: `1: a, 3: b, 4: c, 7: d`

###Increment
`-increment`
Gets one color for every value between the minimum and maximum in our set.
The color difference between each value is proporitional to the value difference. e.g. 1 and 5 will have a greater color difference than 6 and 7.

Unique values: `1, 3, 4, 7`

Retrieves a 7 color gradient (`a-g`) and assigns them proportionally among the 4 values

Color match: `1: a, 3: c, 4: d, 7: g`

###Truncate
`-truncate`
Gets one color for every value between the minimum and maximum in the value set, but assigns the values incrementally to each _unique_ value. Every value has an equal separation (same as with default), but the color range will be shorter.

Unique values: `1, 3, 4, 7`

Retrieves a 7-color (`a-g`) gradient, but only assigns the first 4 values (`a-d`)

Color match: `1:a, 3: b, 4: c, 7: d`