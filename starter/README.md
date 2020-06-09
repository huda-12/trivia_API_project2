 # Full Stack API Final Project

## Full Stack Trivia

Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a  webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out. 

That's where you come in! Help them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application must:

1) Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer. 
2) Delete questions.
3) Add questions and require that they include question and answer text.
4) Search for questions based on a text query string.
5) Play the quiz game, randomizing either all questions or within a specific category. 

Completing this trivia app will give you the ability to structure plan, implement, and test an API - skills essential for enabling your future applications to communicate with others. 

## Tasks general

There are `TODO` comments throughout project. Start by reading the READMEs in:

1. [`./frontend/`](./frontend/README.md)
2. [`./backend/`](./backend/README.md)

We recommend following the instructions in those files in order. This order will look familiar from our prior work in the course.

## Starting and Submitting the Project

[Fork](https://help.github.com/en/articles/fork-a-repo) the [project repository]() and [Clone](https://help.github.com/en/articles/cloning-a-repository) your forked repository to your machine. Work on the project locally and make sure to push all your changes to the remote repository before submitting the link to your repository in the Classroom. 

## About the Stack

We started the full stack application for you. It is desiged with some key functional areas:

### Backend

The `./backend` directory contains a partially completed Flask and SQLAlchemy server. You will work primarily in app.py to define your endpoints and can reference models.py for DB and SQLAlchemy setup. 

### Frontend

The `./frontend` directory contains a complete React frontend to consume the data from the Flask server. You will need to update the endpoints after you define them in the backend. Those areas are marked with TODO and can be searched for expediency. 

Pay special attention to what data the frontend is expecting from each API response to help guide how you format your API. 
## Testing

In order to run tests navigate to the backend folder and run the following commands:

To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
API Reference
##Getting Started

Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, http://127.0.0.1:5000/, which is set as a proxy in the frontend configuration.


##Tasks

One note before you delve into your tasks: for each endpoint you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior. 

1. Use Flask-CORS to enable cross-domain requests and set response headers. 
2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories. 
3. Create an endpoint to handle GET requests for all available categories. 
4. Create an endpoint to DELETE question using a question ID. 
5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score. 
6. Create a POST endpoint to get questions based on category. 
7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question. 
8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions. 
9. Create error handlers for all expected errors including 400, 404, 422 and 500. 

## Error Handling

Errors are returned as JSON objects in the following format:
```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return three error types when requests fail:

    400: Bad Request
    404: Resource Not Found
    422: Not Processable
    405: Method not allowed

##Endpoints

GET '/categories'
GET ... '/questions' or '/questions?page=1'
DELETE ...'/questions/<int:question_id>'
POST ...'/questions'
POST ...'/questions/search'
GET ...'/categories/<int:category_id>/questions'
POST ...'/quizzes'


GET '/categories'
1)General: 
    - Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
    - Request Arguments: None
    - Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs. 
2) Sample request : curl http://127.0.0.1:5000/categories
3)Detailed response:

```
{'1' : "Science",
'2' : "Art",
'3' : "Geography",
'4' : "History",
'5' : "Entertainment",
'6' : "Sports"}
```

GET '/questions?page=<page_number>' 

 1)General:
    -Fetches a paginated dictionary groups of 10 questions of all categories .
    -Request Arguments (OPTIONAL): page:int
    -Returns a list of questions objects, success value, and total number of questions categories,current category 
 2)Smaple request : curl http://127.0.0.1:5000/questions?page=1
 3)Detailed response:
 ```

{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "current_category": null,
  "questions": [
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    },
    {
      "answer": "Escher",
      "category": 2,
      "difficulty": 1,
      "id": 16,
      "question": "Which Dutch graphic artist–initials M C was a creator of optical illusions?"
    }
  ],
  "success": true,
  "total_questions": 19
}
```
DELETE /questions/<question_id> 

 1)General:
   -Deletes the book of the given ID if it exists. 
   -Request arguments:(REQUIRED) question_id:int
   -Returns the id of the deleted book, success value.
 2)sample Request curl -X DELETE http://127.0.0.1:5000/questions/16
 3)Detailed response:
```

{
  "deleted": "16", 
  "success": true
}
```
POST /questions 

 1) General:
   -Creates a new questions using the questions,answer,category,difficulty
   -Request Arguments: None
   -Returns the id of the created question, success value, total questions, and questions list based on current page number to update                      the frontend.
2)sample Request:
curl -i -H "Content-Type: application/json" -X POST -d "{\"question\":\"what is the capital city of saudi arabia? \", \"answer\":\"Riyadh\", \"category\":\"3\", \"difficulty\":\"3\"}" 127.0.0.1:5000/questions
3)Detailed response:
```
{
  "questions": [
    {
      "question": "what is the capital city of saudi arabia?",
      "id": 29,
      "answer":"Riyadh",
      "category": 3,
      "difficulty":3
    }
  ],
  "created": 29,
  "success": true,
  "total_questions": 20
}
```
POST /questions/search 

  1)General:
      -Fetches all questions based on a search term. (not case-sensitive)
      -Request Arguments: None
      -Returns dictionary  of quetions success value, total questions for whom the search term .
  2)sample Request: curl -i -H "Content-Type: application/json" -X POST -d "{\"searchTerm\":\"Organ\"}" 127.0.0.1:5000/questions/search
  3)Detailed response:
  ```
{
  "questions": [
    {
      "answer": "The Liver",
      "category": 1,
      "difficulty": 4,
      "id": 20,
      "question": "What is the heaviest organ in the human body?"
    }
  ],
  "success": true,
  "total_questions": 1
```


GET /categories/<int:category_id>/questions 

 1)General:
    -Fetches a all questions for the specified category. 
    -Request Arguments(REQUIRED):  category_id:int 
    -Returns  current_category ,dictionary of quetions ,success value, total questions for for the specified category.
 2)sample Request:curl http://127.0.0.1:5000/categories/3/questions
 3)Detailed response:
 ```
{
  "current_category": "Geography",
  "questions": [
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    }
  ],
  "success": true,
  "total_questions": 3
}

```

POST /quizzes 

1)General:
   -Fetches one random question within a given category to play the quiz, and the previously asked questions are not asked again.Request body: {previous_questions: arr, quiz_category: {id:int, type:string}}
    -Request Arguments(REQUIRED):  category_id:int 
    -Returns  current_category ,dictionary of quetions ,success value, total questions for for the specified category.

2)Sample Request:
curl -i -H "Content-Type: application/json" -X POST -d "{\"previous_questions\":[1,3],\"quiz_category\":{\"id\":\"3\",\"type\":\"Geography\"}}" 

3)Detailed response:
```
{
  "question": {
    "answer": "Lake Victoria",
    "category": 3,
    "difficulty": 2,
    "id": 13,
    "question": "What is the largest lake in Africa?"
  },
  "success": true
}
```





[View the README.md within ./frontend for more details.](./frontend/README.md)
