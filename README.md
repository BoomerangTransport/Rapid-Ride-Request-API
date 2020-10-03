## Getting Started
* All requests are POST requests to this API
* There is one query parameter which is your API key
* There is only one endpoint which is the base url
* The processing time for these requests is up to 180s
* Average response time is around 60s

# API

## BASE URL
```
https://script.google.com/macros/s/AKfycbziBycki1g5jYZ_78IKxhSZ7KbOmwGibEMEAI-XDOA2aV3nV6Q/exec
```

## POST
### Query params:
```
@parameter-required key=XXXXXXXX_YOUR_KEY_HERE_XXXXXXXX
```
### Body params:
#### `rideDate` | required | *timestamp*
* Expressed as seconds (not milliseconds) since the Unix epoch.
* The date that the pickup will occur. Only the date itself will be considered, not the time of day.
#### `pickupTime` | required | *timestamp*
* Expressed as seconds (not milliseconds) since the Unix epoch.
* The timestamp for when the pickup will occur
#### `apptTime` | required | *timestamp*
* Expressed as seconds (not milliseconds) since the Unix epoch.
* The timestamp for when the appointment will occur
#### `originAdd` | required | *string*
* The origin aka pickup address for the trip 
#### `dest1Add` | required | *string*
* The destination 1 address for the trip, often the appointment address
#### `dest2Add` | optional | *string*
* The destination 2 address for the trip, same as the origin address for a round trip
#### `dest3Add` | optional | *string*
* The destination 3 address for the trip
#### `dest4Add` | optional | *string*
* The destination 4 address for the trip
#### `dest5Add` | optional | *string*
* The destination 5 address for the trip


## Example request 
### URL
`POST https://script.google.com/macros/s/AKfycbziBycki1g5jYZ_78IKxhSZ7KbOmwGibEMEAI-XDOA2aV3nV6Q/exec?key=XXXXXXXX_YOUR_KEY_HERE_XXXXXXXX`
### Body
```
  {
    rideDate: '1602553082',
    pickupTime: '1602507600',
    apptTime: '1602511200',
    originAdd: '4710 Eisenhower Blvd., Tampa, FL 33634',
    dest1Add: '3210 Lake Emma Rd, Lake Mary, FL 32746',
    dest2Add: '4710 Eisenhower Blvd., Tampa, FL 33634',
  }
```

## Example Response:
```
{
   "processed":true,
   "data":{
      "rideDate":1602553962,
      "pickupTime":1602507600,
      "apptTime":1602511200,
      "originAdd":"4710 Eisenhower Blvd., Tampa, FL 33634",
      "dest1Add":"3210 Lake Emma Rd, Lake Mary, FL 32746",
      "dest2Add":"4710 Eisenhower Blvd., Tampa, FL 33634",
      "dest3Add":"",
      "dest4Add":"",
      "dest5Add":"",
      "cr":6,
      "fr":4,
      "available":true
   }
}
```
### Response Object (only new items detailed):
#### `processed` | *boolean*
* Boolean which shows true is a complete request was received and processed
#### `cr` | *number*
* An integer showing the number of drivers potentially available for this trip in contract rates
#### `fr` | *number*
* An integer showing the number of drivers potentially available for this trip with a flat rate needed
#### `available` | *boolean*
* Boolean which indicates if we have at least one driver potentially available for this trip


## Author

* **JP Carlin**  - [Locatejp](https://github.com/locatejp)

## License

This project is licensed under the Do What The F___ You Want To Public License (WTFPL) - see the [LICENSE]([http://www.wtfpl.net/](http://www.wtfpl.net/)) for details.
