# demo1
Demo I


SELECT * FROM [INSERT TABLE] 
WHERE customers_table IS NOT NULL AND user_id IN 
  (SELECT user_id FROM customers);
