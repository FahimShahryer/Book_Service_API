Follow these steps:

Clone the Repository:

Use the git clone command in your terminal or Git Bash to copy the repository to your local machine.

git clone https://github.com/FahimShahryer/Book_Service_API.git

This command will create a directory named Book_Service_API in your current location and download the repository files into it.

Run on terminal
pip install -r requirements.txt

Creating a PostgreSQL Database using pgAdmin 4:

Step 1: Open pgAdmin 4
Log in using your credentials.

Step 2: Connect to a PostgreSQL Server
In the left sidebar, expand the "Servers" section.
Right-click on "Servers" and choose "Create" > "Server..."
Enter the required server information:
Name: Give your server a descriptive name.
Hostname/address:localhost (Enter the address of your PostgreSQL server.)
Port: Default is 5432.
Maintenance database: (PostgreSQL's default maintenance database is postgres.)
Username: Your PostgreSQL username.
Password: Your PostgreSQL password.
Click "Save" to connect to the server.

Step 3: Create a New Database
Once connected to the server, expand the server in the left sidebar.
Right-click on "Databases" and select "Create" > "Database..."
Name: Provide a name for your database.
Click "Save" to create the new database.

#Keep the server running

Edit the code for your database connection

Edit the database url in app/database/session.py script

DATABASE_URL =
"postgresql://<user>:<password>@localhost/<Database_Name>"

Edit the sqlalchemy url in alembic.ini file

sqlalchemy.url = postgresql://<user>:<password>@localhost/<Database_Name>


Run the project
Run on terminal
alembic init migrations

It will create a ‘migrations’ folder in the directory . There should be a ‘env.py’ file in the migrations folder. Look for ‘target_metadata = None’ line in the env.py script, and replace this line with - 

‘target_metadata = models.Base.metadata’

Run on terminal
alembic revision --autogenerate -m "initial_migration"
alembic upgrade head

Run app/main.py

Test the API using POSTMAN

Open POSTMAN
Import the BookServiceApi_postman_collection.json file in postman
There will be several command in BookServiceApi 


Send All the commands sequentially for testing the operations.
