## County Density/Distance/Population Map

#### Author: Jeff Erickson `<jeff@erick.so>`
#### Date: 2014-06-22

### Motivation

I am from Missoula County, Montana, which had a population of 109,299 in the 2010 United States Census. Now that I live in Brooklyn, NY, I often get the question: "Did you grow up on a farm?" I usually say, "No, Missoula is a college town with about 70,000 people." To this, the inevitable comparison to other towns --- often suburbs --- comes up. "Oh, that's not that bad. That's bigger than White Plains!"

The difference between Missoula, Montana and White Plains, New York may be obvious, yet this type of reply is common. So what is the difference? I usually say, "Well, yes, but White Plains is just outside of one of the largest cities in the world, while Missoula is a 7-hour drive to its closest city." But what is the best way to measure this difference? This is the primary motivation of this project.

In addition, I've wanted to try a mapping project in R for sometime, so this also felt like a great opportunity to learn about mapping with census boundary files and ggplot2.

### Approach

#### Version 1

For the initial version, I decided to use a ratio of county density and distance to closest primary statistical area with population over 2 million within the United States. While the map produced results similar to what I expected, it was too heavily weighted by the county densities creating a skewed distribution of the ratio and a few outlier counties that would normally not be thought of as "urban."

![Version 1 of Map](https://raw.githubusercontent.com/jefferickson/county-dendist-map/master/map_output/map.v1.png)

#### Version 2

In doing some research for Version 2, I came across a paper by Brigitte S. Waldorf defining the Index of Relative Rurality (link below). With that as background, I decided to modify my measure to be a simple average of the normalized distance to the closest primary staistical area (though mirrored so that higher meant more urban) and the normalized logarithm of the density. This produced a much "smoother" map than Version 1 and eliminated the outliers mentioned before.

![Version 2 of Map](https://raw.githubusercontent.com/jefferickson/county-dendist-map/master/map_output/map.v2.png)

#### Version 3

While Version 2 was better than Version 1, I still felt that there wasn't enough differentiation among rural counties that are relatively populated when compared to the rest of the otherwise rural state. For example, looking at Montana, the population centers (which are not large compared with the rest of the country) were almost identical to the counties in Montana that are rural even by Montana standards.

To improve upon this, I used Waldorf's method of including the normalized logarithm of county population in addition to the other two measures from Version 2. This lead to an improved measure which continues to be "smooth," doesn't have as many outliers, and still can differentiate in places like Montana. 

![Version 3 of Map](https://raw.githubusercontent.com/jefferickson/county-dendist-map/master/map_output/map.v3.png)  
[Large PDF](https://raw.githubusercontent.com/jefferickson/county-dendist-map/master/map_output/map.v3.pdf)

### References

A Continuous Multi-dimensional Measure of Rurality: Moving Beyond Threshold Measures. Waldorf, Brigitte S. 2006. [(link)]( http://purl.umn.edu/21383)
