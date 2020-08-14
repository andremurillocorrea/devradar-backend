## Description

DevRadar backend application. Node.js Rest API along with socket.io for real time communication.

Search for especialized developpers around you!

## Setup

To setup the database, we used a MongoDB from Mongo Atlas provider (free tier cluster). You will need to subscribe, create the cluster and save the connection string to an environment variable.

In CMD, run:
```
  set DB_CONNECTION_STRING="YOUR DB CONNECTION STRING"
```

Or you can use a .env config file.

To start the server run:

```
  yarn install
  yarn dev
```

## Routes

### List Devs

List all developpers registered in the platform.

```
URL: /devs
Method: GET
Params: {}
Body: {}

Status: 200
Response: [
            {
              "techs": [
                "ReactJS",
                "Javascript",
                "Node.js",
                "React Native"
              ],
              "_id": "5e25d052218c0616e0b291c6",
              "github_username": "andremurillocorrea",
              "name": "André Corrêa",
              "avatar_url": "https://avatars3.githubusercontent.com/u/27099418?v=4",
              "bio": "Mechatronic engineer",
              "location": {
                "coordinates": [
                  -48.6861764,
                  -21.6050182
                ],
                "_id": "5e25d052218c0616e0b291c7",
                "type": "Point"
              },
              "__v": 0
            }
          ]
```

### Create Devs

Register new developper using github profile and location.

```
URL: /devs
Method: POST
Params: {}
Body: {
  {
    "github_username": "andremurillocorrea",
    "latitude": -41.6496186,
    "longitude": -25.5481843,
    "techs": [
      "ReactJS",
      "Javascript"
    ]
  }
}

Status: 200
Response: {
            "techs": [
              "ReactJS",
              "Javascript"
            ],
            "_id": "5e25d052218c0616e0b291c6",
            "github_username": "andremurillocorrea",
            "name": "André Corrêa",
            "avatar_url": "https://avatars3.githubusercontent.com/u/27099418?v=4",
            "bio": "Mechatronic engineer",
            "location": {
              "coordinates": [
                -41.6496186,
                -25.5481843
              ],
              "_id": "5e25d052218c0616e0b291c7",
              "type": "Point"
            },
            "__v": 0
          }
```

### Search Devs

Search for developpers in area filtering technologies and location.

```
URL: /search
Method: GET
Params: {
  latitude: -23.548,
  longitude: -46.649,
  techs: "ReactJS, Javascript"
}
Body: {}

Status: 200
Response: {
            "techs": [
              "ReactJS",
              "Javascript"
            ],
            "_id": "5e25d052218c0616e0b291c6",
            "github_username": "andremurillocorrea",
            "name": "André Corrêa",
            "avatar_url": "https://avatars3.githubusercontent.com/u/27099418?v=4",
            "bio": "Mechatronic engineer",
            "location": {
              "coordinates": [
                -41.6496186,
                -25.5481843
              ],
              "_id": "5e25d052218c0616e0b291c7",
              "type": "Point"
            },
            "__v": 0
          }
```