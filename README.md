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


#### Example request 
`POST https://script.google.com/macros/s/AKfycbziBycki1g5jYZ_78IKxhSZ7KbOmwGibEMEAI-XDOA2aV3nV6Q/exec?key=XXXXXXXX_YOUR_KEY_HERE_XXXXXXXX`
```
  const payload = {
    rideDate: '1602553082',
    pickupTime: '1602507600',
    apptTime: '1602511200',
    originAdd: '4710 Eisenhower Blvd., Tampa, FL 33634',
    dest1Add: '3210 Lake Emma Rd, Lake Mary, FL 32746',
    dest2Add: '4710 Eisenhower Blvd., Tampa, FL 33634',
  };
```


# JP to pick back up here



Response:
```
{"success":true,"data":[{"id":1,"name":"Carls","email":"carls@employee.com","account":000000000,"row":2},{"id":2,"name":"Alf","email":"alf@employee.com","account":000000000,"row":3},{"id":3,"name":"Rich","email":"rich@employee.com","account":000000000,"row":4},{"id":4,"name":"Salem!","email":"salem@cats.org","account":000000000,"row":5}]}
```
### Insert

Query params:
```
@parameter-required action=insert
@parameter-required table=<SHEET_NAME>
@parameter-required data=JSON
```

#### Example request :
`GET https://<yourappscripturl>?action=insert&table=employees&data={"id":5,"name":"John Doe","email":"john@mail.org","account":1111}`

Response:
```
{"success":true,"data":{"id":5,"name":"John Doe","email":"john@mail.org","account":1111}
```
### Update
Query params:
```
@parameter-required action=update
@parameter-required table=<SHEET_NAME>
@parameter-required id=ID
@parameter-required data=JSON
```
To update you only need to provide with the key-value JSON of what's going to change.
#### Example:
Request 
`GET https://<yourappscripturl>?action=update&table=employees&id=5&data={"name":"Johnnathan"}`

Response:
```
{"success":true,"data":{"id":5,"name":"Johnnathan","email":"john@mail.org","account":1111}
```

### Delete
Query params:
```
@parameter-required action=delete
@parameter-required table=<SHEET_NAME>
@parameter-required id=ID
```
#### Example:
Request 
`GET https://<yourappscripturl>?action=delete&table=employees&id=5`

Response:
```
{"success":true,"data":{"id":5,"name":"Johnnathan","email":"john@mail.org","account":1111}
```

## Author

* **Richard Blondet**  - [RichardBlondet](https://github.com/richardblondet)

## License

This project is licensed under the MIT License - see the [LICENSE]([https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)) file for details.
