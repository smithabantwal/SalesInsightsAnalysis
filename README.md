## Sales Insights Data Analysis Project

 Problem Statement
AtliQ Hardware is a company which supplies computer hardware and peripherals to many of clients such as Excel stores, Surge stories across India. AtliQ Hardware head office is situated in Delhi, India and they have many regional office throughout the India.

Challenges- Market is growing dynamically and Sales Director is facing issue in terms of tracking the Sales in this dynamically growth market and he is having issues with growth of his business, as overall sales was declining. He has regional managers for North India, South and Central India. Whenever he wants to get insight of these region he would call these people and on the phone regional manager give some insights to him.

Now Problem was that all these thing happening is verbal and there was no proof with facts that how his business is affected and which made him frustrated as he can see that overall sales is declining but when he ask regional manager, he is not getting complete picture of his business. And when he ask to give detail, they give lot of excel file and this AtliQ hardware is big business so to see insight clearly , he needs a dashboard to look at real data . And he will get proper insight and can take data driven decision to increase sales of his company.



AIMS Grid -is a project management tool and it has four component-

Purpose- to unlock sales insights that are not visible before for the sales team for decision support and automate them to reduced manual time spent in data gathering.

Stakeholders- are people who will involve in this project like sales director, marketing team, customer service team, data analytics team and IT.

End Result- An automated dashboard providing quick and latest sales insights in order to support data driven decision making.


1. SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`


