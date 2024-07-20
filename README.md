# learnGrpahQL

#GraphQL

- GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data.
- It provides a complete and understandable description of the data in your API
- This allows clients to request exactly the data they need, and nothing more, making your API faster, more efficient, and easier to use
- GraphQL was developed by Facebook to optimize RESTful API calls

\*\* Disadvantages of REST API

- Over fetching :- Getting back more data than we need
- Under fetching:- Getting back less data than we need


#Some Querys

1. query GamesQuery {
  reviews {
   id,
   content,
   rating
 }
}

2. query GamesQuery {
 authors {
   name,
   verified
 }
}

3.query GamesQuery {
  games{
    title,
    platform
  }
}

#Query Variable for getting a single valued query

1.query GamesQuery($id:ID!) {
   review(id:$id) {
     rating,
     content
   }
 }


#Related Data

1. query GamesQuery($id:ID!) {
  game(id:$id) {
   title,
   reviews {
     rating,
     content,
     
   }
  }
}

2 . query ReviewQuery($id: ID!) {
  review(id: $id) {
    rating
    game {
      title
      platform
      reviews {
        rating
      }
    }
  }
}

#Mutations(Adding and Deleting Data)

1. mutation DeleteMutation($id: ID!) {
  deleteGame(id: $id) {
    id
    title
    platform
  }
}

2. mutation AddMutation($game: AddGameInput!) {
  addGame(game: $game) {
    id
    title
    platform
  }
}
JSON Given for adding new Game :-
{
  "game": {
    "title": "GTA V",
    "platform":["PS5"]
  }
}
