# Code Togather: Let's make iPhone app in an hour

  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/mapApp-en/blob/master/Resourses/smaple.gif" /></div>
  
  Thank you for visiting our account. We are going to make a simple map app in an hour. If would you like to study yourself before hands-on, or review what you have learned in the session, please use the following material.
  
## We are providing free hands-on on a monthly basis
  Meetup  
  https://www.meetup.com/iOS-Development-Meetup-for-Beginner/
  
## We also hold face-to-face or group lesson for indivisual interested in making iOS app themselves
  http://ios-class-for-beginner.esy.es/

## Development Environment
  XCode 8.1 / Swift 3

## Full procedure

#### 0, Import nessesary frameworks
> 0-1. Add "MappKit" Framework
  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/mapApp-en/blob/master/Resourses/1.gif" /></div>

#### 1, Design app
> 1-1. Drap & Drop "MapView" from UI components
  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/mapApp-en/blob/master/Resourses/2.gif" /></div>

> 1-2. Resize MapView
  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/mapApp-en/blob/master/Resourses/3.gif" /></div>

> 1-3. Set "Autoresizing" for adjusting frame depending on devices
  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/mapApp-en/blob/master/Resourses/4.gif" /></div>

> 1-4. Connect UI components on Storyboard to ViewController.swift
  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/mapApp-en/blob/master/Resourses/5.gif" /></div>

#### 3, Add code blocks in ViewController.swift
  
```Swift  
import UIKit
import MapKit

class ViewController: UIViewController {

    @IBOutlet var myMap: MKMapView!
    
    override func viewDidLoad()
    {
        super.viewDidLoad()
        
        // Setup latitude and longitude
        let location = CLLocationCoordinate2DMake(49.28061, -123.122463)
        myMap.setCenter(location,animated: true)
        
        // Setup a reduced scale
        var region = myMap.region
        region.center = location
        region.span.latitudeDelta = 0.02
        region.span.longitudeDelta = 0.02
        myMap.setRegion(region,animated:true)
        
        // Specify the type of map to display
        myMap.mapType = MKMapType.standard
//        myMap.mapType = MKMapType.satellite
//        myMap.mapType = MKMapType.hybrid
//        myMap.mapType = MKMapType.satelliteFlyover
//        myMap.mapType = MKMapType.hybridFlyover
        
        // You can set an annotation object if you like to say something about the location
        let pin = MKPointAnnotation()
        pin.coordinate = CLLocationCoordinate2DMake(49.28061, -123.122463)
        pin.title = "iOS Development Meetup for Beginner"
        pin.subtitle = " We will make an simple map app @ Waves Cofee!"
        myMap.addAnnotation(pin)
    }

    override func didReceiveMemoryWarning()
    {
        super.didReceiveMemoryWarning()
    }
}
```
