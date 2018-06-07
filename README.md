# geodesy
all geography related useful links for data and formulas

# Data Source  
* USA zip code to latitude longitude  
[NBER](http://www.nber.org/data/zip-code-distance-database.html)


# Vectorized calculations
* Haversine formula for getting distance between two points 
```
earth_radius_miles = 3959.0 #changed this value  
def get_distance(needle, haystack):
    """needle is a single (lat,long) tuple.
        haystack is a numpy array to find the point in
        that has the shortest distance to needle
        source: https://stackoverflow.com/questions/6656475/python-speeding-up-geographic-comparison
        similar code: https://engineering.upside.com/a-beginners-guide-to-optimizing-pandas-code-for-speed-c09ef2c6a4d6
    """
    dlat = np.radians(haystack[:,0]) - radians(needle[0])
    dlon = np.radians(haystack[:,1]) - radians(needle[1])
    a = np.square(np.sin(dlat/2.0)) + cos(radians(needle[0])) * np.cos(np.radians(haystack[:,0])) * np.square(np.sin(dlon/2.0))
    great_circle_distance = 2 * np.arcsin(np.minimum(np.sqrt(a), np.repeat(1, len(a))))
    d = earth_radius_miles * great_circle_distance
    return d
  ```
