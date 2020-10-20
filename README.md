# M3 - `README.md` Example

<br>

# Quick Compo

<br>

## Description

This is an app to manage unofficial tournaments within communities. The app helps to organize, manage and track competitions.


# Server / Backend


## Models

User model

```javascript
{
  username: {type: String, required: true, unique: true},
  email: {type: String, required: true, unique: true},
  password: {type: String, required: true},
  favorites: [Tournament]
}
```



Tournament model

```javascript
 {
   name: {type: String, required: true},
   img: {type: String},
   players: [{type: Schema.Types.ObjectId,ref:'Participant'}],
   games: [{type: Schema.Types.ObjectId,ref:'Game'}]
 }
```



Player model

```javascript
{
  name: {type: String, required: true},
  img: {type: String},
  score: []
}
```



Game model

```javascript
{
  player1: [{type: Schema.Types.ObjectId,ref:'Participant'}],
  player2: [{type: Schema.Types.ObjectId,ref:'Player'}],
  player2: [{type: Schema.Types.ObjectId,ref:'Player'}],
  winner: {type: String},
  img: {type: String}
}
```


<br>


## API Endpoints (backend routes)

| HTTP Method | URL                         | Request Body                 | Success status | Error Status | Description                                                  |
| ----------- | --------------------------- | ---------------------------- | -------------- | ------------ | ------------------------------------------------------------ |
| GET         | `/auth/profile    `           | Saved session                | 200            | 404          | Check if user is logged in and return profile page           |
| POST        | `/auth/signup`                | {name, email, password}      | 201            | 404          | Checks if fields not empty (422) and user not exists (409), then create user with encrypted password, and store user in session |
| POST        | `/auth/login`                 | {username, password}         | 200            | 401          | Checks if fields not empty (422), if user exists (404), and if password matches (404), then stores user in session |
| POST        | `/auth/logout`                | (empty)                      | 204            | 400          | Logs out the user                                            |
| GET         | `/tournaments`                |                              |                | 400          | Show all tournaments                                         |
| GET         | `/tournaments/:id`            | {id}                         |                |              | Show specific tournament                                     |
| POST        | `/tournaments/add-tournament` | {}                           | 201            | 400          | Create and save a new tournament                             |
| PUT         | `/tournaments/edit/:id`       | {name,img,players}           | 200            | 400          | edit tournament                                              |
| DELETE      | `/tournaments/delete/:id`     | {id}                         | 201            | 400          | delete tournament                                            |
| GET         | `/players`                    |                              |                | 400          | show players                                                 |
| GET         | `/players/:id`                | {id}                         |                |              | show specific player                                         |
| POST        | `/players/add-player`         | {name,img,tournamentId}      | 200            | 404          | add player                                                   |
| PUT         | `/players/edit/:id`           | {name,img}                   | 201            | 400          | edit player                                                  |
| DELETE      | `/players/delete/:id`         | {id}                         | 200            | 400          | delete player                                                |
| GET         | `/games`                      | {}                           | 201            | 400          | show games                                                   |
| GET         | `/games/:id`                  | {id,tournamentId}            |                |              | show specific game                                           |
| POST        | `/games/add-game`             | {player1,player2,winner,img} |                |              | add game                                                     |
| POST        | `/games/add-all-games`        |                              |                |              | add all games from a tournament. Gets a list of players and populates them via algorithm. |
| PUT         | `/games/edit/:id`             | {winner,score}               |                |              | edit game                                                    |


<br>


## Links

### Trello/Kanban

[Link to your trello board](https://trello.com/b/PBqtkUFX/curasan) 
or picture of your physical board

### Git

The url to your repository and to your deployed project

[Client repository Link](https://github.com/screeeen/project-client)

[Server repository Link](https://github.com/screeeen/project-server)

[Deployed App Link](http://heroku.com)

### Slides

The url to your presentation slides

[Slides Link](http://slides.com)







