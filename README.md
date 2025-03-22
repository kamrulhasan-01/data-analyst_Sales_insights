# data-analyst_Sales_insights

Data Analysis Using SQL
1. Show all customer records

        SELECT * FROM customers;

2. Show the total number of customers

        SELECT count(*) FROM customers;

3. Show transactions for the Chennai market (the market code for Chennai is Mark001

        SELECT * FROM transactions where market_code='Mark001';

4. Show distinct product codes that were sold in Chennai

        SELECT distinct product_code FROM transactions where market_code='Mark001';

5. Show transactions where the currency is US dollars

        SELECT * from transactions where currency="USD"

6. Show transactions in 2020 join by date table

        SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

7. Show total revenue in the year 2020,

        SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

8. Show total revenue in the year 2020, January Month,

        SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date
        where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or 
        transactions.currency="USD\r");

10. Show total revenue in the year 2020 in Chennai

        SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date
        where date.year=2020 and transactions.market_code="Mark001";

Data Analysis Using Power BI
Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any) 
