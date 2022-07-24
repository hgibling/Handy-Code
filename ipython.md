Get history of session 1 before current
```
%hist ~1/
```

Set up virtual environment
```
module load python/2.7.11
virtualenv name
source name/bin/activate
pip install modulename
deactivate
#setup in bash, source to run python scripts
```

sort a dictionary based on values (python 3.7)
```
sorted(dict.items(), key=lambda x: x[1])
# key is for the sorted function, not the dictionary keys
# lambda function considers element x and returns the second item in x, which in this case is the value from dict.items() (key, value)
```