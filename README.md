# Project 2

For the ETL mini project, you will work with a partner to practice building an ETL pipeline using Python, Pandas, and either Python dictionary methods or regular expressions to extract and transform the data. After you transform the data, you'll create four CSV files and use the CSV file data to create an ERD and a table schema. Finally, you’ll upload the CSV file data into a Postgres database.

Since this is a one-week project, make sure that you have done at least half of your project before the third day of class to stay on track.

Although you and your partner will divide the work, it’s essential to collaborate and communicate while working on different parts of the project. Be sure to check in with your partner regularly and offer support.

## Files

Download the starter code and files to help you get started:

[Project 2 ETL files](https://static.bc-edx.com/data/dl-1-2/m13/lms/starter/Starter_Files.zip)📁

## Before You begin

1. Have one member of your group create a new repository, named **Crowdfunding_ET**L, for this project. Add your partner as a collaborator. **Do not add this project to an existing repository.**
2. Clone the new repository to your computer.
3. Have one person rename the **ETL_Mini_Project_starter_code.ipynb** file with the first name initial and last name of each member of the group, for example, **ETL_Mini_Project_NRomanoff_JSmith.ipynb**. Then, add this Jupyter notebook file and the Resources folder containing the crowdfunding.xlsx and the **contacts.xlsx** files to your repository.
4. Push the changes to GitHub.
5. Have your partner pull the changes, so both of you have the same notebook available on your computer.
6. As you work through the project deliverables, you may find it helpful to break up the work across other notebooks that you each work on individually. However, once complete, please combine all the subsections back into the final ETL_Mini_Project notebook.

## Instructions

The instructions for this mini project are divided into the following subsections:

* Create the Category and Subcategory DataFrames
* Create the Campaign DataFrame
* Create the Contacts DataFrame
* Create the Crowdfunding Database

## Create the Category and Subcategory DataFrames

1. Extract and transform the **crowdfunding.xlsx** Excel data to create a category DataFrame that has the following columns:
   
    * A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories
    * A "category" column that contains only the category titles
    * The following image shows this category DataFrame:

<img width="190" alt="category_DataFrame" src="https://github.com/wsylliac/Crowdfunding_ETL/assets/140991773/957d9dd6-4bf4-4cd5-8852-fed44ccd43ef">

2. Export the category DataFrame as **category.csv** and save it to your GitHub repository.
3. Extract and transform the **crowdfunding.xlsx** Excel data to create a subcategory DataFrame that has the following columns:

     * A "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories
     * A "subcategory" column that contains only the subcategory titles
     * The following image shows this subcategory DataFrame:

![Screenshot 2023-12-11 at 10 16 42 PM](https://github.com/wsylliac/Crowdfunding_ETL/assets/140991773/c2b5aa0f-a0c9-4341-b13d-7b53811c2fce)

4. Export the subcategory DataFrame as **subcategory.csv** and save it to your GitHub repository.

## Create the Campaign DataFrame

1. Extract and transform the **crowdfunding.xlsx** Excel data to create a campaign DataFrame has the following columns:

  * The "cf_id" column
  * The "contact_id" column
  * The "company_name" column
  * The "blurb" column, renamed to "description"
  * The "goal" column, converted to the **float** data type
  * The "pledged" column, converted to the **float** data type
  * The "outcome" column
  * The "backers_count" column
  * The "country" column
  * The "currency" column
  * The "launched_at" column, renamed to "launch_date" and with the UTC times converted to the **datetime** format
  * The "deadline" column, renamed to "end_date" and with the UTC times converted to the **datetime** format
  * The "category_id" column, with unique identification numbers matching those in the "category_id" column of the category DataFrame
  * The "subcategory_id" column, with the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame
  * The following image shows this campaign DataFrame:

<img width="1074" alt="campaign_DataFrame" src="https://github.com/wsylliac/Crowdfunding_ETL/assets/140991773/3e98a3c4-9dd8-4916-8b53-b2c5b55dc924">


2. Export the campaign DataFrame as **campaign.csv** and save it to your GitHub repository.

## Create the Contacts DataFrame

1. Choose one of the following two options for extracting and transforming the data from the contacts.xlsx Excel data:

*   **Option 1**: Use Python dictionary methods.
*   **Option 2**: Use regular expressions.

2. If you chose Option 1, complete the following steps:

* Import the contacts.xlsx file into a DataFrame.
* Iterate through the DataFrame, converting each row to a dictionary.
* Iterate through each dictionary, doing the following:
  * Extract the dictionary values from the keys by using a Python list comprehension.
  * Add the values for each row to a new list.

* Create a new DataFrame that contains the extracted data.
* Split each "name" column value into a first and last name, and place each in a new column.
* Clean and export the DataFrame as contacts.csv and save it to your GitHub repository.

3. If you chose Option 2, complete the following steps:
    * Import the contacts.xlsx file into a DataFrame.
    * Extract the "contact_id", "name", and "email" columns by using regular expressions.
    * Create a new DataFrame with the extracted data.
    * Convert the "contact_id" column to the integer type.
    * Split each "name" column value into a first and a last name, and place each in a new column.
    * Clean and then export the DataFrame as contacts.csv and save it to your GitHub repository.

4. Check that your final DataFrame resembles the one in the following image:

<img width="415" alt="contact_DataFrame_final" src="https://github.com/wsylliac/Crowdfunding_ETL/assets/140991773/8fdfad4f-ac11-4bce-90e6-ae94b42a5236">

## Create the Crowdfunding Database

1. Inspect the four CSV files, and then sketch an ERD of the tables by using QuickDBD Links to an external site..
2. Use the information from the ERD to create a table schema for each CSV file.

   **Note**: Remember to specify the data types, primary keys, foreign keys, and other constraints.
   
4. Save the database schema as a Postgres file named **crowdfunding_db_schema.sql**, and save it to your GitHub repository.
5. Create a new Postgres database, named **crowdfunding_db**.
6. Using the database schema, create the tables in the correct order to handle the foreign keys.
7. Verify the table creation by running a **SELECT** statement for each table.
8. Import each CSV file into its corresponding SQL table.
9. Verify that each table has the correct data by running a **SELECT** statement for each.


### Hints

* To split each "category & sub-category" column value into "category" and "subcategory" column values, use **df[["new_column1","new_column2"]] = df["column"].str.split()**. Make sure to pass the correct parameters to the split() function.
* To get the unique category and subcategory values from the "category" and "subcategory" columns, create a NumPy array where the array length equals the number of unique categories and unique subcategories from each column. For information about how to do so, see [numpy.arange](https://numpy.org/doc/stable/reference/generated/numpy.arange.html)📁. in the NumPy documentation.
* To create the category and subcategory identification numbers, use a list comprehension to add the "cat" string or the "subcat" string to each number in the category or the subcategory array, respectively.
* For more information about creating a new Pandas DataFrame, see the [pandas.DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html)📁 in the Pandas documentation.
* To convert the "goal" and "pledged" columns to the **float** data type, use the **astype()** method.
* To convert the "launch_date" and "end_date" UTC times to the **datetime** format, see the **Transform_Grocery_Orders_Solved.ipynb** activity solution.
* For more information about how to add the "category_id" and "subcategory_id" unique identification numbers to the campaign DataFrame, see the [pandas.DataFrame.merge](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html)📁. in the Pandas documentation.
