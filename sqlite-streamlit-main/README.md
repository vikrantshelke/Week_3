# Build SQL Editor web app using streamlit and sqlite!

![](https://github.com/vikrantshelke/Week_3/blob/main/sqlite-streamlit-main/data/sqlite_streamlit.gif)

We're going to develop a web app using Streamlit, a Python framework, along with the SQLite3 library. This app will enable users to create and query database tables, making data management both accessible and user-friendly.

To begin, we'll install Streamlit, SQLite, and any other necessary dependencies. This can be done using the pip package manager by running the following command in the terminal:

```python 
pip install streamlit pysqlite streamlit-ace pandas pathlib
```

Next, we'll import the required libraries and set up a basic Streamlit application. The code below creates a simple Streamlit app that displays a title and a message on the screen:

```python 
import streamlit as st
import sqlite3
import pandas as pdpyth
from streamlit_ace import st_ace, KEYBINDINGS, LANGUAGES, THEMES
import  streamlit_toggle as tog
from pathlib import Path
```


With our basic Streamlit app ready, we can now add functionality to create a new database file using the sqlite3 library. The code below takes user input to create a new database file and stores it in the current working directory:

```python 
def create_connection(db_file):
        """ create a database connection to the SQLite database
        specified by the db_file
    :param db_file: database file
    :return: Connection object or None
    """
        conn = None
        try:
            conn = sqlite3.connect(db_file)
        except Exception as e:
            st.write(e)

        return conn
```

```python 
def create_database():
        st.markdown("# Create Database")

        st.info("""A database in SQLite is just a file on same server. 
        By convention their names always must end in .db""")


        db_filename = st.text_input("Database Name")
        create_db = st.button('Create Database')
        
        conn = create_connection('default.db')
        mycur = conn.cursor() 
        mycur.execute("PRAGMA database_list;")
        available_table=(mycur.fetchall())
        with st.expander("Available Databases"): st.write(pd.DataFrame(available_table))
        
        if create_db:
            
            
            if db_filename.endswith('.db'):
                conn = create_connection(db_filename)

                st.success("New Database has been Created! Please move on to next tab for loading data into Table.")
            else: 
                st.error('Database name must end with .db as we are using sqlite in the background to create files.')
```

st.success, st.error, st.info are different types of text alerting formats offered by streamlit.
![](https://github.com/user-attachments/assets/8626513e-be18-4999-96f3-c7055508e0b1)

Blue represents an information message, while red shows an error message.

We want users to be able to create tables in their chosen database. To achieve this, let's create a function that allows users to load data from CSV files into the database as tables.

```python
def upload_data():
        st.markdown("# Upload Data")
        sqlite_dbs = [file for file in os.listdir('.') if file.endswith('.db')]
        db_filename = st.selectbox('Database', sqlite_dbs)
        table_name = st.text_input('Table Name to Insert')
        conn = create_connection(db_filename)
        uploaded_file = st.file_uploader('Choose a file')
        upload = st.button("Create Table")
        if upload:
            #read csv
            try:
                df = pd.read_csv(uploaded_file)
                df.to_sql(name=table_name, con=conn)
                st.write('Data uploaded successfully. These are the first 5 rows.')
                st.dataframe(df.head(5))

            except Exception as e:
                st.write(e)
```

With the main functions in place, let's add a tabbed view using Streamlit. This will allow users to easily switch between the SQL cheat sheet and other features of the app.

```python
intro, db, tbl, qry = st.tabs(["1 Intro to SQL","2 Create Database", "3 Upload Data", "4 Query Data"])
```

Finally, we can use these tabs to display or invoke the appropriate functions, as well as to run SQL queries on the tables within the database. This will provide a user-friendly interface for interacting with the database and utilizing the app's features.

We're using streamlit-ace as the code editor in our app, and streamlit-toggle-switch to add a toggle switch for enabling dark mode in the editor.
![](https://github.com/user-attachments/assets/0fe9acdf-6561-46dd-9275-641f146f20b7)

In this example, we'll retrieve all the data from the "customers" table. Users will also have the option to download their query results as a CSV file.
![](https://github.com/user-attachments/assets/bfaa87bd-1b9c-46e8-ad9c-ea01c60ca8f5)

In short, we've created a simple web application using Streamlit, integrating it with the SQLite library to manage the database. The app allows users to create or upload data tables and run queries directly through an editor.
