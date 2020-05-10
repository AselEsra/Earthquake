Eartquake-Data
==================================================================

- Name and Surname: Asel Esra Ozyilmaz
- Email: esra.ozyilmaz@iaau.edu.kg
- Computer Science Department of Alatoo International University.
- Individual final project for CS-102 Java class.

A GUI created by using Processing and Unfolding Maps library functions in Eclipse IDE to display and print out the earthquakes which have occured all over the world.

This is a project that I have created with the help of the Object Oriented Programming in Java course offered by 
UC San Diego through Coursera. The project was half created and the other half was asked to implement throughout the course. However, in the course the project has further features but to not make it more complex I haven't added all of them.

### Processing and Unfolding map libraries;

**Processing library:** an open-source graphical library and integrated development environment (IDE) built for the electronic arts, new media art, and visual design communities with the purpose of teaching non-programmers the fundamentals of computer programming in a visual context.
Processing uses the Java language, with additional simplifications such as additional classes and aliased mathematical functions and operations. It also provides a graphical user interface for simplifying the compilation and execution stage. 

**Unfolding maps library:** Enables you to quickly create interactive maps. Simply create geo-positioned markers to display data on a map. The library supports loading and displaying user-defined shapes, such as points, lines, or polygons.

## Description Of The Project

<img src="https://user-images.githubusercontent.com/64264345/81493697-6b51f500-92c4-11ea-9770-faf08fc44470.png" width="100">
![zoomed](https://user-images.githubusercontent.com/64264345/81493699-73119980-92c4-11ea-9f8e-3081fd3982f2.png =250x250)
![console](https://user-images.githubusercontent.com/64264345/81493700-760c8a00-92c4-11ea-8d53-df1326af7941.png)

The project has an interactive map which displays where the earthquakes have occured with the help of markers. Optionally you can work online or offline with it. If you work online **GoogleMapProvider()** will display a map otherwise, an offline map is displayed. 

The data of earthquakes are taken from this live RSS feed https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_week.atom and parsed by the course in order to read the data inside it. In addition, there are two more files: cityFile and countryFile. countryFile includes features of the countries such as: name, location, type. Also, if an earthquake occurs in a particular country it is added as a marker to the map. cityFile on the other hand, includes cities and their properties. 

A RuntimeException is checked While reading and adding the cityFile to the map as shown below;

### Code of exception handling;

``` Java	
//read in city data and check if an runtime exception occurs
try {
   List<Feature> cities = GeoJSONReader.loadData(this, cityFile);
   cityMarkers = new ArrayList<Marker>();
   for(Feature city : cities) {
	cityMarkers.add(new CityMarker(city));
}}
catch (RuntimeException e) {
    System.out.println("Exception occured in Runtime");
}
```
### UML Class/Data Diagrams 

![cityMarker](https://user-images.githubusercontent.com/64264345/81471618-325a4780-9214-11ea-8e99-df2282f58376.png) ![UML class diagram](https://user-images.githubusercontent.com/64264345/81473170-8c600a80-921e-11ea-9533-7f2078ac851e.png)

> As shown above, the project contains 5 classes: EarthquakeCityMap, CityMarker, EarthqukeMarker, LandQuakeMarker and OceanQuakeMarker. Let's further investigate them;

### Five Classes

**EarthquakeCityMarker Class;**

- It is the main class which extends PApplet in order to create a GUI. This class includes some methods and helper methods. **addKey()** is a helper method which draws key in GUI and **isInCountry()** is another helper method which is used to test whether a given earthquake is in a given country or not. It also adds the country property to the properties of the earthquake feature if it's in one of the countries. Moreover, there is a method called **printQuakes()** which prints out countries with number of earthquakes. 

**CityMarker Class;**
 
- This class extends SimplePointMarker to mark the cities on the map. SimplePointMarker is a class of UnfoldingMaps library which   represents marker on a single location. 

**EarthquakeMarker Class;**

- An abstract class which implements a visual marker for earthquakes on an earthquake map. It has two subclasses: LandQuakeMarker and OceanQuakeMarker. EarthquakeMarker class allows these two classes to implement abstract method **drawEarthquake()** differently. Moreover, class includes method **colorDetermine()** which allows the derived classes to determine color of marker from depth of the earthquake.

**LandQuakeMarker and OceanQuakeMarker Classes;**

- The main difference between these two child classes is that they both implement markers on different places. LandQuakeMarker implements quakes markers on the land; however, OceanQuakeMarker implements them on the ocean.

