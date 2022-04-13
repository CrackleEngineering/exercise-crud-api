# Video Crud Operation using serverless

As a API user, I'd like to be able to create, retrieve, update and delete Video objects using REST API, and preserve the data in the DynamoDB.

- [Video Crud Operation using serverless](#video-crud-operation-using-serverless)
  - [Requirements](#requirements)
  - [Appendix](#appendix)
    - [CRUD Endpoints](#crud-endpoints)
    - [Object Schema definition](#object-schema-definition)
      - [Video Example Object](#video-example-object)
      - [Video Object field definitions](#video-object-field-definitions)

## Requirements

- Implement Restful VIDEO CRUD operation using latest [serverless framework](https://www.serverless.com/framework/docs)
- Make application to be available in `us-east-1` region
- Make API accessible through `API Gateway` (endpoints are defined in the appendix)
- Store the data in the Dynamo DB in the `catalog` table
- Implement using Javascript or Typescript
- Validate an incoming requests and sanitize data if needed (attributes defined in the appendix)
- Write Unit test using your desire framework to test those methods
- submit a PR to the repo

## Appendix

### CRUD Endpoints

- Create: `${host}/video`
- Retrieve: `${host}/video/:id`
- Update: `${host}/video/:id`
- Remove: `${host}/video/:id`

### Object Schema definition

#### Video Example Object

```json

{
    "id": "ac93a6f3-364a-4a48-9442-1e06a4aee557",
    "type": "movie",
    "genre": [
        "crime",
        "drama",
        "thriller"
    ],
    "metadata": {
        "title": "10th & Wolf",
        "description": "A former street tough returns to his Philadelphia home after a stint in the military. Back on his home turf, he once again finds himself tangling with the mob boss who was instrumental in his going off to be a soldier."
    },
    "rating": 5,
    "url": "http://example.com"
}

```

#### Video Object field definitions

| Name                 	| Description                      	| Attribute type and requirements       	|
|----------------------	|----------------------------------	|---------------------------------------	|
| id                   	| id of the video                  	| Guid or UUID                          	|
| type                 	| type of the video                	| allowed values: `movie` or `trailer`      	|
| genre                	| genre of the video               	| array of strings                      	|
| metadata             	| editorial metadata of the video  	| object that has title and description 	|
| metadata.video       	| title of the video               	| string, max length `100` characters     	|
| metadata.description 	| description of the video         	| string, max length `255` characters     	|
| rating               	| movie rating                     	| number , range `0-5`                    	|
| url                  	| url of the location of the video 	| string, valid url                     	|
