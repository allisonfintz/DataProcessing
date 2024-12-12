# DataProcessing

# Description
This project mimics transactions to allow “all or nothing” updates to databases to prevent dirty writes. 
For example: For building a money transfer application a transaction woul look like this:
  When A initiates a transfer of X dollars to B, two things need to happen:
    X dollars should be deducted from A’s account
    X dollars should be added to B’s account

# Features

Key-Value: Keys should be string and values should be integers and creates a new key with the provided value.

Transaction: Provides methods to begin, commit, and rollback transactions.

Error Handling: Ensures invalid operations throw meaningful exceptions.

Isolation: Transactions should not be “visible” to get(), until the transaction is committed.

# Setup
1. Clone the repository:

   git clone (giturl provided)
   cd your-folder

# Running the Code

  You can use an online Python interpreter or an IDE with web support to test your code without having Python installed locally. Here are a few easy-to-use options:

  Option 1 (Online IDE) 
    Replit
      Visit: https://replit.com/
      Create a new Python project.
      Copy and paste your code into the editor with test code.
      Run the code directly in the browser.

  Option 2:
    1. Install Visual Studio Code
      Download and install VS Code from https://code.visualstudio.com/.
    2. Open code in Visual Studio Code
    3. Install python extension in extensions tab
    4. Open DataProcess repository from folder
    5. Run DataProcess.py 
    6. Adjust main with different inputs as needed

  This will run the code and allow you to test it.

  Example Test:

    # Create database
    db = KeyValueDatabase()
    
    # put transaction or throw exception
    try:
        db.put("transaction1", 10) 
    except Exception as e:print(e)
    
    print(db.get("a"))  # Should print None
    
    # Begin a transaction
    db.begin_transaction()
    db.put("transaction1", 15)
    print(db.get("transaction1"))  # print 15
    
    db.put("transaction2", 10)
    print(db.get("transaction2"))  #print 10
    
    # Rollback transaction
    db.rollback()
    print(db.get("transaction1"))  # Should print None
    print(db.get("transaction2"))  # Should print None
    
    # Begin another transaction
    db.begin_transaction()
    db.put("transaction1", 30)
    db.commit()
    print(db.get("transaction1"))  # Should print 30

# Modifications for Future
    - Include more detailed instruction for testing and how the testing should be written for the TAs
    - Maybe have a wordcount for readME to know around how detailed it should be
    - Include a rubric for code and ReadME
