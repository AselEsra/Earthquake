Eartquake-Data
==================================================================

- Name and Surname: Asel Esra Ozyilmaz
- Email: esra.ozyilmaz@iaau.edu.kg
- Study: Computer Science Department of Alatoo International University.
- Project for CS-102 Java class.

A GUI created by using Processing and Unfolding Maps library functions in Eclipse IDE to display and print out the earthquakes which have occured all over the world.

This is a project that I have created with the help of the Object Oriented Programming in Java course offered by 
UC San Diego through Coursera. The project was half created and the other half was asked to implement throughout the course. However, in the course the project has further features but to not make it more complex I haven't added all of them.

## Description Of The Project

ss of the map

The project has an interactive map which displays where the earthquakes have occured with the help of markers. Optionally you can work online or offline with it. If you work online GoogleMapProvider will display a map otherwise an offline map is displayed.The data of earthquakes are taken from this live RSS feed https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_week.atom and parsed by the course in order to read the data inside it. In addition, there are two more files: cityFile and countryFile. countryFile includes features of the countries such as: name, location, type. If an earthquake occurs in a particular country it is added as a marker to the map. cityFile on the other hand, includes cities and their properties just like countryFile. The project also includes several classes which are described below.

![cityMarker](https://user-images.githubusercontent.com/64264345/81471618-325a4780-9214-11ea-8e99-df2282f58376.png) ![UML class diagram](https://user-images.githubusercontent.com/64264345/81473170-8c600a80-921e-11ea-9533-7f2078ac851e.png)

> As shown above, the project contains 5 classes: EarthquakeCityMap, CityMarker, EarthqukeMarker, LandQuakeMarker and OceanQuakeMarker. Let's further investigate them;

**EarthquakeCityMarker Class;**

- It is the main class which extends PApplet in order to create a GUI. This class includes some methods and helper methods such as isInCountry to test whether a given earthquake is in a given country. This will also add the country property to the properties of the earthquake feature if it's in one of the countries. Moreover, printQuakes method will prints out countries with number of earthquakes.

**CityMarker Class;**
 
- This class extends SimplePointMarker to mark the cities on the map.

**EarthquakeMarker Class;**

- An abstract class which iplements a visual marker for earthquakes on an earthquake map. It has two subclasses: LandQuakeMarker and OceanQuakeMarker. EarthquakeMarker class allows these two classes to implement abstract method **drawEarthquake** differently. Moreover, class includes method **colorDetermine** which allows the derived classes to determine color of marker from depth of the earthquake.

**LandQuakeMarker and OceanQuakeMarker Classes;**

- The main difference between these two child classes is that they both implement markers on different places. LandQuakeMarker implements quakes markers  on the land; however, OceanQuakeMarker implements the it on the ocean.

```java	

private void printQuakes() {
		int totalWaterQuakes = quakeMarkers.size();
		for (Marker country : countryMarkers) {
			String countryName = country.getStringProperty("name");
			int numQuakes = 0;
			for (Marker marker : quakeMarkers)
			{
				EarthquakeMarker eqMarker = (EarthquakeMarker)marker;
				if (eqMarker.isOnLand()) {
					if (countryName.equals(eqMarker.getStringProperty("country"))) {
						numQuakes++;
					}
				}
			}
			if (numQuakes > 0) {
				totalWaterQuakes -= numQuakes;
				System.out.println(countryName + ": " + numQuakes);
			}
		}
		System.out.println("OCEAN QUAKES: " + totalWaterQuakes);
	} 
	```
