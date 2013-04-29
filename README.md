Hadoop_KMeans_MapReduce_Java
============================
####Mapper####
OUTPUT: <centroid,point>     
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
