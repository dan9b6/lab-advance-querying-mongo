![Ironhack Logo](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Answers

### 1. All the companies whose name match 'Babelgum'. Retrieve only their `name` field.

//Query:
{"name" : "Babelgum"}
//Options:
{"name" : 1}

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

//Query:
{number_of_employees : {\$gt : 5000}}
//Options:
{limit : 20}
Sort:
{number_of_employees : -1 }

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fields. //INCOMPLETE

//Query:
{ $and: [ { "founded_year" : {$gte : 2000}}, { "founded_year" : {\$lte : 2005}} ] }
//Project:
{name : 1, founded_year : 1}

### 4. All the companies that had a Valuation Amount of more than 100.000.000, and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

//Query
{ $and: [ { "founded_year" : {$gte : 2000}}, { "founded_year" : {\$lte : 2005}} ] }
//Project
{name : 1, ipo : 1}

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

//Query
{ $and: [ { number_of_employees : {$lte : 1000}}, { founded_year : {\$lt : 2005}} ] }
//Sort
{number_of_employees : 1}
//Limit
10

### 6. All the companies that don't include the `partners` field.

//Query
{'partners': {"\$exists": false}}

### 7. All the companies that have a null value on the `category_code` field.

//Query
{category_code : null }

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

//Query
{ $and: [ { number_of_employees : {$gte : 100}}, { number_of_employees : {\$lte : 1000}} ] }
//Project
{name : 1, number_of_employees : 1}

### 9. All the companies ordered by their IPO price in a descending manner.

//Sort
{"ipo.valuation_amount" : -1}

### 10. The 10 companies with the highest amount of employees, order by the `number of employees`.

//Sort
{number_of_employees : -1}
//Limit
10

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.

//Query
{ $and: [ { founded_month : {$gt : 6}}, { founded_month : {\$lte : 12 }} ] }
//Limit
1000

### 12. All the companies founded before 2000 that have an acquisition amount of more than 10.000.000.

//Query
{ $and: [ { founded_year : {$lt : 2000}}, { "acquisition.price_amount" : {\$gt : 1000000}} ] }

### 13. All the companies that have been acquired after 2010, ordered by the acquisition amount, retrieving only their `name` and `acquisition` fields.

//Query
{ "acquisition.acquired_year" : {\$gt : 2010}}
//Project
{acquisition : 1, name : 1}
//Sort
{acquisition_price_amount : -1}

### 14. All companies ordered by their `founded year`, retrieving only their `name` and `founded year`.

//Project
{name : 1, founded_year: 1}

//Sort
{founded_year : 1}

### 15. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `acquisition price` in a descending order. Limit the search to 10 documents.

//Query
{founded_day : {\$lte : 7}}
//Sort
{"acquisition.price_amount" : -1}
//Limit
10

### 16. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascending order.

//Query
{ $and: [ { category_code : "web" }, { number_of_employees : {$gt : 4000}} ] }
//Sort
{number_of_employees : 1}

### 17. All the companies whose acquisition amount was more than 10.000.000, and in which the acquisition currency is 'EUR'.

//Query
{ $and: [ { "acquisition.price_amount" : {$gt : 10000000} }, { "acquisition.price_currency_code" : {\$eq :"EUR"} } ] }

### 18. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

//Query
{ $and: [ { "acquisition.acquired_month": {$lt : 4} }, { "acquisition.acquired_month": {\$gt : 1} } ] }
//Project
{name: 1, acquisition : 1}

### 19. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

//Query
{ $and: [ { founded_year : {$lte : 2010} }, {founded_year : {\$gte : 2000} } ] }
