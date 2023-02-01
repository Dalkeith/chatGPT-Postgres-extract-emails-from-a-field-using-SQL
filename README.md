# chatGPT-Postgres-extract-emails-from-a-field-using-SQL

You can extract emails from a string in PostgreSQL using the following SQL statement:

vbnet
Copy code
WITH cte AS (
  SELECT 
    string_to_array(string_field, ' ') AS words
  FROM 
    table_name
)
SELECT 
  unnest(words) AS word
FROM 
  cte
WHERE 
  word ~ E'\\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Z|a-z]{2,}\\b'
  
Replace string_field with the actual name of your string field, and table_name with the actual name of your table. The above statement uses the string_to_array function to split the string into an array of words, which are then unnested using the unnest function. The WHERE clause filters the words based on the regular expression that matches the pattern of an email address.
