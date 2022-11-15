# Regular Expressions

## HTTP Requests (`req.py`)

Create a file called `req.py`. Make the file executable `chmod +x` and include the proper hashbang at the top of the file `#!/usr/bin/env python3`.

In this file we will demonstrate how we can very simply use the Python 3 built-in module called `urllib.request` to retrieve data using the HTTP protocol. 
See the `urllib.request` [module documentation here](https://docs.python.org/3/library/urllib.request.html#module-urllib.request).

Add the following code to the file and save it.
```
#!/usr/bin/env python3

import urllib.request


with urllib.request.urlopen("https://cs.indstate.edu/~lmay1/assets/rig.txt") as req:
  req_data = req.read().decode("utf-8")
  
print(req_data)
```
When you run this program you should see some results similiar to that of the `rig` command. The difference here is that this rig file has been specifically generated to ensure it has certain properties and characteristics in the data. In each of the following programs we will use a similiar setup to get this data blob from the URL https://cs.indstate.edu/~lmay1/assets/rig.txt

### Grading (4pts)

1. **(1pts)** File `req.py` exists and imports `urllib.request` module.
2. **(1pts)** File `req.py` contains the URL `https://cs.indstate.edu/~lmay1/assets/rig.txt` as a sting in the source code.
3. **(2pts)** File `req.py` outputs to the terminal the exact text from the request using utf-8 character encoding. 

## JSON Data (`me.py`, `me.json`)

Create a file named `me.py`. Make the file executable `chmod +x` and include the proper hashbang at the top of the file `#!/usr/bin/env python3`.\

Create a dictionary with the following data keys. Below I am entering my information but you should enter your info:
```
me = {
  "first": "Lea",
  "last": "T",
  "account": "cs40100",
  "birthMonth": 1, 
  "birthDay": 1,
}
```
Make sure you name the key names of your dictionary exactly as I have here. Now import the built-in `json` module, convert this dictionary to a string, then save that string to a file using **4 spaces of indentation**. Name the file `me.json`. here is the [documentation for the `json` module.](https://docs.python.org/3/library/json.html)

### Grading (6pts)

1. **(1pts)** File `me.py` exists and uses the `json` module.
2. **(1pts)** File `me.py` uses the `indent=4` keyword argument appropriately to format the string data in a readable way.
3. **(1pts)** File `me.py` creates a file `me.json`.
4. **(1pts)** File `me.json` is formatted as a json.
5. **(1pts)** File `me.json` has 4 space indentation.
6. **(1pts)** File `me.json` contains all of the keys specified in the instructions.

## 3) Regular Expressions in Python (`01.py`, ..., `13.py`)

For each of the following questions us the provided `rig.txt` data from the URL https://cs.indstate.edu/~lmay1/assets/rig.txt. **Do not use any external pip packages to do this** because if you do that makes grading difficult and you will lose points. 

For each of the below questions, there should be a python script with a programmatic solution, printing the **specified solution only** with no other output. The hashbang `#!/usr/bin/env python3` should be used in each, and with the proper permissions to make it executable (`+x`). The name of the file should be the two-digit number of the file. So the answer to Question Number 1 would be in a file `01.py`:
```
#!/usr/bin/env python3

import re
import urllib.request

# ...
# Use urllib.request to get the data in a variable called 'req_data'
# ...

# Compile a regular expression here (this would work for `01.py`)
# Use raw strings so yo udo not have to escape backslashes: 
#    `r"raw\string"`
r = re.compile(r"^[0-9]")

# ...
# Use the `re` module utilities to determine which lines match the regular expression
# and then print the lines that the problem specifies.
# ...

# ...
# If the problem requires you print the number of matches then do it here.
# ...
```
Use similiar setup for all of the problems below. For problem `01` cretae a file `01.py`, for `02` create a file `02.py` etc.:

1. Print ONLY the "Street Address" lines. After these have been printed, print the out the number of matches (the number of lines you printed).

**Example of Last Lines of Output**
```
...
25 Pleasant View Dr
449 Main St
108 Second St
172 Tomkins Blvd
676
```
2. Print ONLY the "City State Zip" lines. Then print the out the number of matches. 

**Example of the Last Lines of Output**
```
...
Roanoke, VA 24022
Hamilton, OH 45012
Utica, NY 13504
Phoenix, AZ 85026
676
```
3. Print ONLY the "Phone Number" lines. Then print the out the number of matches.

**Example of Last Lines of Output**
```
(703) xxx-xxxx
(513) xxx-xxxx
(315) xxx-xxxx
(602) xxx-xxxx
676
```
4. Print ONLY the "Name" lines. Then print the out the number of matches. 

**Example of Last Lines of Output**
```
...
Augustus Zoe
Lorna Xandro 
Roxie Jan
Eileen Santiago
676
```
5. Print the entire rig entry (all 4 rig lines) with a blank linke between each rig entry for all identities from either New York, California, or Indiana. Then print the out the number of matches (all 4 rig lines count as 1 match).

**Example of Last Lines of Output**
```
...

Anibal Isabella
8 Cooper St
Gary, IN 46401
(219) xxx-xxxx

Roxie Jan
108 Second St
Utica, NY 13504
(315) xxx-xxxx
122
```
6. Print the entire rig entry (all 4 rig lines) with a blank line between each rig entry for all identities from either New York, California, or Indiana, that are in cities that contain the characters "ny", "ca", or "in", regardless of case. Examples of such cities would include "Indianapolis", "Albany", and "Utica", etc. Then print the out the number of matches (all 4 rig lines count as 1 match).

**Example of Last Lines of Output**
```
...

Nona Angelita
380 Hamlet St
Binghamton, NY 13902
(607) xxx-xxxx

Roxie Jan
108 Second St
Uticak, NY 13504
(315) xxx-xxxx
53
```
7. Print the entire rig entry (all 4 rig lines) with a blank line between each rig entry for all identities that live on a Street or an Avenue. Then print the out the number of matche (all 4 rig lines count as 1 match). Then print the out the number of matches (all 4 rig lines count as 1 match).

**Example of Last Lines of Output**
```
...

Lorna Xandro
449 Main St
Hamilton, OH 45012
(513) xxx-xxxx

Roxie Jan 
108 Second St
Utica, NY 13504
(315) xxx-xxxx
203
```
8. Print the entire rig entry (all 4 rig lines) with a blank line between each rig entry for all identities that live on a Boulevard, Lane, Terrace, or Avenue, and have a single digit house number. Then print the out the number of matches (all 4 rig lines count as 1 match).

**Example of Last Lines of Output** 
```
...

Antoine Frankie
5 Spring County Blvd
Irving, TX  75061
(903) xxx-xxxx

Ute Zeke
3 Stonehedge Blvd
Milwaukee, WI  53201
(414) xxx-xxxx
5
```
9. Print the entire rig entry (all 4 rig lines) with a blank line between each rig entry for all identities that live on a Lane, Street, Road, or Avenue, and have a street name containing either the characters "ln", "st", "rd", "ave" regardless of letter casing. Then print the out the number of matches (all 4 rig lines count as 1 match).

**Example of Last Lines of Output** 
```
...

Louise Shawn
414 Third St
Austin, TX  78710
(512) xxx-xxxx

Zahir Quincey
931 Third St
Berkeley, CA  94704
(510) xxx-xxxx
66
```
10. Print ONLY the "Name" line and "Phone Number" line (2 lines) with a blank line between each set for all identities that have a cardinal direction in the street name. Then print the out the number of matches (the 2 rig lines count as 1 match).

**Example of Last Lines of Output** 
```
...

Uhtred Ragnarson
(317) xxx-xxxx

Inez Felipe
(513) xxx-xxxx

Hazel Yoneko
(708) xxx-xxxx
46
```
11. Print the entire rig entry (all 4 rig lines) with a blank line between each rig entry for all identities whose first names start with the letter of your first name and whose last names start with the first letter of your last name. Then print the out the number of matches (all 4 rig lines count as 1 match).

**Example of Last Lines of Output (Using My JSON Data)** 
```
Lidia Marvin
776 Fairfield Rd
Hampton, VA  23670
(804) xxx-xxxx
1
```
12. Print ONLY the "Name" line and "City State Zip" line (2 lines) with a blank line between each set for all identities whose first names start with the letter of your first name and whose last names start with the first letter of your last name. Then print the out the number of matches (the 2 rig lines count as 1 match).

**Example of Last Lines of Output (Using My JSON Data)** 
```
Lidia Marvin
Hampton, VA  23670
1
```
13. Print ONLY the "Name" line and "Street Address" line (2 lines) with a blank line between each set for all identities whose street address number is either the exact match of your birth month, birth day of month, or last 2 digits of your CS account (if your last 2 digits are 05, use just 5, if your last two digits are 21, use 21). Then print the out the number of matches (the 2 rig lines count as 1 match).

**Example of Last Lines of Output (Using My JSON Data)** 
```
Abraham Phyllis
15 Ashland St

Allan Jarvis
9 Plinfate St

Wendi Quent
15 Freeland Ave
3
```

### Grading (52 pts)

**(4pts each * 13)** Each python program exists with the solution to each question (`01.py`, `02.py`, etc.)

1. **(1pts)** You found >= 50% of the matches.
2. **(1pts)** You had no false matches (printing a line that you should not have). 
3. **(1pts)** The count is correct and agrees with the number of printed matches.
4. **(1pts)** The output is exactly correct. 
