### DevRant.io Unofficial API documentation

API base endpoint: [https://www.devrant.io/api](https://www.devrant.io/api)

```/get-user-id```
Method: GET
Parameters: app, user
Brief: Get user ID from username. 
Example: [https://www.devrant.io/api/get-user-id?app=3&username=abhn](https://www.devrant.io/api/get-user-id?app=3&username=abhn)
Response:
```
{
  "success": true,
  "user_id": 101178
}
```

```/devrant/rants/```
Method: GET
Parameters: app
Optional parameters: 
* sort[algo, top, recent]
* limit: number of rants to fetch 
* skip: Skip the first N rants and fetch from there
Brief: Fetches a list of rants
Example: [https://www.devrant.io/api/devrant/rants?app=3](https://www.devrant.io/api/devrant/rants?app=3)
Response: An array of rants with various parameters
```
{
  "success": true,
  "rants": [
    {
      "id": 327111,
      "text": "My girlfriend got me this mug. She's the one.",
      "num_upvotes": 59,
      "num_downvotes": 1,
      "score": 59,
      "created_time": 1481230115,
      "attached_image": {
        "url": "https://img.devrant.io/devrant/rant/r_327111_pMWmu.jpg",
        "width": 562,
        "height": 1000
      },
      "num_comments": 6,
      "tags": [
        "linus",
        "torvalds",
        "mug"
      ],
      "vote_state": 0,
      "edited": false,
      "user_id": 118128,
      "user_username": "blackmarket",
      "user_score": 3086,
      "user_avatar": {
        "b": "d55161",
        "i": "v-11_c-3_b-5_g-m_9-1_1-1_16-2_3-6_8-4_7-4_5-1_12-1_6-3_10-1_2-41_15-19_18-4_4-1_19-3.jpg"
      }
    }
  ]
}
```

```devrant/rants/${rant_id}?app=3	```
Method: GET
Parameters: app
Brief: Fetches a single rant with comments
Example: [https://www.devrant.io/api/devrant/rants/327111?app=3](https://www.devrant.io/api/devrant/rants/327111?app=3)
Response:
```
{
  "rant": {
    "id": 32710,
    "text": "When manager wants daily merges to a source control system that updates every 3 days.",
    "num_upvotes": 6,
    "num_downvotes": 0,
    "score": 6,
    "created_time": 1463743428,
    "attached_image": "",
    "num_comments": 0,
    "tags": [
      "conflictsgalore fml merge source control"
    ],
    "vote_state": 0,
    "edited": false,
    "user_id": 14984,
    "user_username": "rantmaster",
    "user_score": 112,
    "user_avatar": {
      "b": "d55161",
      "i": "v-11_c-3_b-5_g-m_9-1_1-2_16-1_3-1_8-1_7-1_5-1_12-2_6-15_10-1_2-18_15-19_4-1.jpg"
    }
  },
  "comments": [],
  "success": true
}
```

```/devrant/search```
Method: GET
Parameters: app, term
Brief: Fetches rants matching the search term
Example: [https://www.devrant.io/api/devrant/search?app=3&term=git](https://www.devrant.io/api/devrant/search?app=3&term=git)
Response:
```
{
  "success": true,
  "results": [
    {
      "id": 83521,
      "text": "What do you call a party with developers?\n\nA git together\n\nI'm so sorry.",
      "num_upvotes": 532,
      "num_downvotes": 3,
      "score": 532,
      "created_time": 1466749353,
      "attached_image": "",
      "num_comments": 12,
      "tags": [
        "github",
        "git"
      ],
      "vote_state": 0,
      "edited": false,
      "user_id": 80968,
      "user_username": "idontcare",
      "user_score": 543,
      "user_avatar": {
        "b": "2a8b9d"
      }
    }
  ]
}

```/users/${user_id}```
Method: GET
Parameters: app
Brief: Fetches detailed information about a user (profile, rants, favorites, upvoted)
Example: [https://www.devrant.io/api/users/101178?app=3](https://www.devrant.io/api/users/101178?app=3)
Response: A large JSON blog with the following important keys
```
Object.keys(temp1.profile)
["username", "score", "about", "location", "created_time", "skills", "github", "website", "content", "avatar"]
Object.keys(temp1.profile.content.content)
["rants", "upvoted", "comments", "favorites"]
```
