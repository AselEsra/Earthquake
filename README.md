Eartquake-Data
==================================================================

> Author Info

- Name and Surname: Asel Esra Ozyilmaz
- Email: esra.ozyilmaz@iaau.edu.kg
- Study: Computer Science Department of Alatoo International University.
- Final Project.

A GUI created by using Processing and Unfolding Maps library functions in Eclipse IDE to display and print out the earthquakes which have occured all over the world.

This is a project that I have created with the help of the Object Oriented Programming in Java course offered by 
UC San Diego through Coursera. The project was half created and the other half was asked to implement throughout the course. However, in the course the project has further features but to not make it more complex I haven't added all of them.

# DESCRIPTION

ss of the map

The project has an interactive map which displays where the earthquakes have occured with the help of markers. Optionally you can work online or offline with it. If you work online GoogleMapProvider will display a map otherwise an offline map is displayed.The data of earthquakes are taken from this live RSS feed https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_week.atom and parsed by the course in order to read the data inside it. In addition, there are two more files: cityFile and countryFile. countryFile includes features of the countries such as: name, location, type. If an earthquake occurs in a particular country it is added as a marker to the map. cityFile on the other hand, includes cities and their properties just like countryFile.

ss of the UMLs

**As shown above, the project contains 5 classes: EarthquakeCityMap, CityMarker, EarthqukeMarker, LandQuakeMarker and OceanQuakeMarker.**

- **EarthquakeCityMarker;**
It is the main class which extends PApplet in order to create a GUI. This class includes some methods and helper methods such as isInCountry to test whether a given earthquake is in a given country. This will also add the country property to the properties of the earthquake feature if it's in one of the countries. 


MANUAL INSTALLATION

If the import does not work follow the steps below.

- Create new Java project
- Copy+Paste all files into project
- Add all lib/*.jars to build path
- Set native library location for jogl.jar. Choose appropriate folder for your OS.
- Add data/ as src


TROUBLE SHOOTING

Switch Java Compiler to 1.6 if you get VM problems. (Processing should work with Java 1.6, and 1.7)




