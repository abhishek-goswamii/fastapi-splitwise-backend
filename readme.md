# Expense Splitter

- skipping token authentication for endpoints

- i am using nosql database(mongodb), so data validation is done by models 

## Getting Started

To begin using this project, follow these simple steps:

1. **Clone the Repository:**
   Clone the project to your local system:

    ```
    git clone https://github.com/abhishek-goswamii/fastapi-expense-tracker.git
    ```

2. **Python Version:**
   need Python version 3.12.1 

3. **Cd Project Directory:**
   Open your terminal and change directory to the project folder:

    ```
    cd to project folder
    ```

4. **Run Docker Compose file and Activate Virtual Environment:**
    
    ```
    docker-compose up -d
    ```

    ```
    source venv/bin/activate
    ```

5. **Navigate to the App Directory:**
   Move to the 'app' directory :

    ```
    cd app
    ```

6. **Run the Server:**
   Launch the API server by executing the following command:

    ```
    uvicorn main:app --reload
    ```

   This command will start the API server, and you can access it at [http://127.0.0.1:8000](http://127.0.0.1:8000).

7. **Test APIs Using Postman:**
   You can test the APIs using Postman. i've included a Postman collection in the project directory. Simply import the collection into Postman to use APIs





8. **Expenses Collection Structure:**
    {
        "_id": "65b6538dc626f3f4bca526f3",
        "name": "Electricity Bill",
        "amount": 1000.0,
        "expense_type": "EQUAL",
        "participants": [
            {
                "user_id": "65b64f6cc1ec164304dcf440",
                "share": 1
            },
            {
                "user_id": "65b64f65c1ec164304dcf43f",
                "share": 1
            },
            {
                "user_id": "65b64f59c1ec164304dcf43e",
                "share": 1
            },
            {
                "user_id": "65b64f46c1ec164304dcf43d",
                "share": 1
            }
        ],
        "paid_by": "65b64f46c1ec164304dcf43d",
        "timestamp": "2024-01-28T18:45:57.663000",
        "is_active": true
    }


9. **Balance collection structure**
{
    "user_id": "A",
    "balances": {
        "B": -30.0,  # User A owes 30 to User B
        "C": 20.0    # User A is owed 20 by User C
    }
}


ENDPOINTS


/user (POST METHOD create new user)
request body -> {
    "name":"u4",
    "email":"u7",
    "mobile":"13433423434"
}

/expense (POST METHOD create new expense)

request body {
    "name": "Electricity Bill",
    "amount": 1000.00,
    "expense_type": "EQUAL",
    "participants": [
        {"user_id": "65b64f6cc1ec164304dcf440", "share": 1},
        {"user_id": "65b64f65c1ec164304dcf43f", "share": 1},
        {"user_id": "65b64f59c1ec164304dcf43e", "share": 1},
        {"user_id": "65b64f46c1ec164304dcf43d", "share": 1}
    ],
    "paid_by": "65b64f6cc1ec164304dcf440"
}

/balance/65b64f46c1ec164304dcf43d (GET METHOD summery of my account, who owes me how much)

response - > {
    "user_id": "65b64f46c1ec164304dcf43d",
    "balances": {
        "65b64f6cc1ec164304dcf440": 500.0,
        "65b64f65c1ec164304dcf43f": 750.0,
        "65b64f59c1ec164304dcf43e": 750.0
    },
    "my_net_balance": 2000.0
}