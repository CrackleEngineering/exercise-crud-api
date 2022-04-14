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

#### Clone/Mirror/Commit Instructions
The [repository](https://github.com/CrackleEngineering/exercise-crud-api) for the assignment is public and Github does not allow the creation of private forks for public repositories.

The correct way of creating a private fork by duplicating the repo is documented [here](https://help.github.com/articles/duplicating-a-repository/).

For this assignment the commands are:

 1. Create a bare clone of the repository.
    (This is temporary and will be removed so just do it wherever.)
    ```bash
    git clone --bare git@github.com:CrackleEngineering/exercise-crud-api.git
    ```

 2. [Create a new private repository on Github](https://help.github.com/articles/creating-a-new-repository/) and name it `exercise-crud-api`.
    > If you are unable to create a private repo, you can request unlimited private repos as a student by getting
    > the [student pack](https://education.github.com/pack) from Github.

 3. Mirror-push your bare clone to your new `exercise-crud-api` repository.
    > Replace `<your_username>` with your actual Github username in the url below.
    
    ```bash
    cd exercise-crud-api.git
    git push --mirror git@github.com:<your_username>/exercise-crud-api.git
    ```

 4. Remove the temporary local repository you created in step 1.
    ```bash
    cd ..
    rm -rf exercise-crud-api.git
    ```
    
 5. You can now clone your `exercise-crud-api` repository on your machine (in my case in the `code` folder).
    ```bash
    cd ~/code
    git clone git@github.com:<your_username>/exercise-crud-api.git
    ```
   
 6. If you want, add the original repo as remote to fetch (potential) future changes.
    Make sure you also disable push on the remote (as you are not allowed to push to it anyway).
    ```bash
    git remote add upstream git@github.com:CrackleEngineering/exercise-crud-api.git
    git remote set-url --push upstream DISABLE
    ```
    You can list all your remotes with `git remote -v`. You should see:
    ```
    origin	git@github.com:<your_username>/exercise-crud-api.git (fetch)
    origin	git@github.com:<your_username>/exercise-crud-api.git (push)
    upstream	git@github.com:CrackleEngineering/exercise-crud-api.git (fetch)
    upstream	DISABLE (push)
    ```
    > When you push, do so on `origin` with `git push origin`.
   
    > When you want to pull changes from `upstream` you can just fetch the remote and rebase on top of your work.
    ```bash
      git fetch upstream
      git rebase upstream/main
      ```
      And solve the conflicts if any
