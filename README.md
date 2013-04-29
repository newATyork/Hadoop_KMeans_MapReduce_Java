Hadoop_KMeans_MapReduce_Java
============================
####Mapper####
OUTPUT: `<centroid,point>`     
key is the center point of the cluster which the point from value belongs to     

####Combiner####
INPUT: Mapper Output    
OUTPUT:`<centroid, string((sum of point)+(point count))`    
the value will be used to calculate new centroid in reducer   

####Reducer####
INPUT: Combiner Output   
OUTPUT: `<new_centroid,count_of_current_unchanged_centroid_point>`      


You can know something more about what I encounterd when I did it:    
http://sbzhouhao.blogspot.com/2013/04/weird-combiner-in-hadoop.html

## Sorry, I haven't given enough comments to these code files.

You can also contact me directly for more detail: hzhou@wpi.edu 

##Description
K‐Means clustering is a popular algorithm for clustering similar objects into K groups (clusters). It starts with an initial seed of K points (randomly chosen) as centers, and then the algorithm iteratively tries to enhance  these  centers.  The  algorithm  terminates  either  when  two  consecutive  iterations  generate  the same K centers, i.e., the centers did not change, or a maximum number of iterations is reached.  
 
Hint: You may reference these links to get some ideas (in addition to the course slides): 
>[http://en.wikipedia.org/wiki/K-­‐means_clustering#Standard_algorith](http://en.wikipedia.org/wiki/K-­‐means_clustering#Standard_algorithm )     
>[https://cwiki.apache.org/confluence/display/MAHOUT/K-­‐Means+Clustering](https://cwiki.apache.org/confluence/display/MAHOUT/K-­‐Means+Clustering)
 
 
###Step 1 (Creation of Dataset):  
•	Create a dataset that consists of 2-­‐dimenional points, i.e., each point has (x, y) values. X and Y values each range from 0 to 10,000. Each point is in a separate line.    
•	Scale the dataset such that its size is around 100MB.    
•	Create another file that will contain K initial seed points. Make the “K” value as a parameter to your program, so in the demo session, I will give you certain K, your program will generate these K seeds, and then you upload the generated file to the cluster.    
 
 
###Step 2 (Clustering the Data):  
Write map-­‐reduce job(s) that implement the K-­‐Means clustering algorithm as given in the course slides. The algorithm should terminates if either of these two conditions become true:    
>>a)	The K centers did not change over two consecutive iterations    
>>b)	The maximum number of iterations (make it six (6) iterations) has reached.   

•	Apply the tricks given in class and in the 2nd link above such as:   
>o	Use of a combiner    
>o	Use a single reducer    
>o	The reducer should indicate in its output file whether centers have changed or not.    
 
*Hint*: Since the algorithm is iterative, then you need your program that generates the map-­‐reduce jobs to control whether it should start another iteration or not. 
