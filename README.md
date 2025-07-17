# alter-table-null-values
learn about alter table/null values in sql



-- Learn to alter table and null values

drop table flipkart_orders;

create table flipkart_orders
(
order_Id int,
order_date date, -- "yyyy-mm-dd" is standard format
product_name varchar(50),
total decimal(10,2),
payment_method varchar(30)
);

-- i want to make change in datatype.

alter table flipkart_orders alter column order_date datetime -- this is DDL (data definitio language)

select * from flipkart_orders;

insert into flipkart_orders values (1,'2022-04-05 12:05:57','Froak',4000,'card'),
 (2,'2022-04-05 14:08:57','Bed Sheet',3000,'UPI'),
 (3,'2022-04-05 17:03:57','Pillow',1700,'Card'),
 (4,'2022-04-10 14:08:57','Bed Sheet',3000,'Card');

 insert into flipkart_orders values (5, 2022-04-05,'Froak',4000,'card'); -- if time is not mention, it will take automatically 00:00:00
 
 -- now i want to add new column

 alter table flipkart_orders add user_name varchar (20); -- this will add colum user_name at the end of the table

 insert into flipkart_orders values  (6,'2022-04-05 17:03:57','Pillow',1700,'Card', 'Bhanu'),
  (7,'2022-04-05 17:03:57',null,1700,'Card','Sachin'), -- this is real null, means data is missing under column product_name 
  (8,'2022-04-05 17:03:57','null',1700,'Card','Ravi'); -- this null is a string, not a missing data

  -- let's add one more column 
  alter table flipkart_orders add category varchar (15); 

  select * from flipkart_orders; 

  -- now i feel like , i dont need column = 'category' anymore

  alter table flipkart_orders drop column category; 

  -- now we will change data type
  alter table flipkart_orders alter column order_date varchar (30); -- this work because under datatype (varchar)  - we can add any kind of data under varchar, does not mean you add varchar as datatype for all type of column.  
  alter table flipkart_orders alter column total date; -- error (decimal couldn't be added inside date , datatype)
  alter table flipkart_orders alter column product_name varchar (5); -- error, beacuse value (5) is less for data inside product_name, we can miss some data, so it could not execute
  
  alter table flipkart_orders alter column order_date datetime; -- we run this to get back into origional data


  
