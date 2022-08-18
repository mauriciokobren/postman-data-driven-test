# postman-data-driven-test
API testing using Postman with data-driven approach
## Overview
This collection uses Trello REST API to demonstrate how to run data-driven tests with Postman.  
Trello REST API is presented with more details in https://developer.atlassian.com/cloud/trello/rest/  
The main ideia here is to read a data file in which each row represents a Trello Card.  
For each row/card the following actions are done using Trello REST API:  
- Creates a new card
- Reads card data
- Updates the card
- Delete the card
  
The board used in the tests is available here: https://trello.com/b/yrrwS93X/kanban-board  
## Data file
The data file is expected to have the following columns:  
- title: card title
- description: card description
- column: column of the board in which the card is created
- status: expected status received after the creation request
- new_title: the new title used in card update
- new_description: the new description used in card update
- new_column: the new column of the board used in card update
- new_status: the new status received after the update
- new_due_date: the new due date used in card update
  
trello_api_data_driven_tests.csv in this repository is an example of the data file.  

## Environment Variables
An environment was created with 2 variables:  
- trello_apikey: this variable stores the API key for your Trello account
- trello_apitoken: similarly, this variable stores the API token

To know how to find you API key and token please visit the following page: https://developer.atlassian.com/cloud/trello/guides/rest-api/api-introduction/  
## Collection Variables
The collection has the following variables:  
- base_url: this variable stores the base address of Trello API
- cards_endpoint: stores the endpoint itself. Concatenated with base url should allow a request
- todo_list_id: the id of the "To Do" column of the board
- doing_list_id: the id of the "Doing" column
- column_id: this variable is used in the Creates Card request and its value is set based on the column name in data file. The value is set in the Pre-request Script.
- new_column_id: this variable is used in the Update Card request and its value is set based on the column name in data file. The value is set in the Pre-request Script.
  
## Run the Collection using a data file  
The following article has more details about running the collection using a data file: https://learning.postman.com/docs/running-collections/working-with-data-files/  

The biggest advantage of using data files is that you can add more combinations of values and run the requests many times. For example, if dev team is still changing the code, data file can help you with regression tests and avoid that a change breakes a piece of your application.  

The course Exploring Service APIs through Test Automation, by Amber Race, is an inspiration for this project: https://testautomationu.applitools.com/exploring-service-apis-through-test-automation/


