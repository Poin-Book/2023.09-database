# 과제 풀이

> 작성자: 이재혁

### Database System Concept 7th Problem Solving
Chapter 2

## 목차
- Figure 2.17, 2.18
- 2.1
- 2.6
- 2.7
- 2.12
- 2.14
- 2.15

---
### Figure 2.17
$$employee\,(person\_name,\,street,\,city)\\
works\,(person\_name, \,company\_name, \,salary)\\
company\,(company\_name, \,city)$$
<br><br>
### Figure 2.18
$$branch\,(branch\_name,\,branch\_city,\,assets)\\
customer\,(ID,\,customer\_name,\,customer\_street,\,customer\_city)\\
loan\,(loan\_number,\,branch\_name,\,amount)\\
borrower\,(ID,\,loan\_number)\\
account\,(account\_number,\,branch\_name,\,balance)\\
depositor\,(ID,\,account\_number)
$$

---

## 문제 풀이
### <span style= "color: blue">Problem 2.1</span>
Consider the employee database of Figure 2.17. What are the appropriate **primary keys**?

#### <span style= "color: red">Answer</span>
***Employee (<u>person_name</u>, street, city)***<br>
***works (<u>person_name</u>, <u>company_name</u>, <u>salary</u>)***<br>
***company (<u>company_name</u>, city)***

### <span style= "color: blue">Problem 2.6</span>
Consider the employee database of Figure 2.17. Give an expression in the relational algebra to express each of the following queries: <br>
> a. Find the name of each employee who lives in city "Miami". <br>
> b.	Find the name of each employee whose salary is greater than $100000. <br>
> c.	Find the name of each employee who lives in "Miami" and whose salary is greater than $100000.

#### <span style= "color: red">Answer</span>
a. 
$$ \Pi_{person\_name}\,(\sigma_{city= "Miami"}(employee)) $$
b.
$$ \Pi_{person\_name}\,(\sigma_{salary>100000}(works)) $$
c.
$$ \Pi_{person\_name}\,(\sigma_{city= "Miami"\wedge \,salary>100000}(employee\bowtie works)) $$

### <span style= "color: blue">Problem 2.7</span>
Consider the bank database of Figure 2.18. Give an expression in the relational algebra for each of the following queries: <br>
> a. Find the name of each branch located in "Chicago". <br>
> b. Find the ID of each borrower who has a loan in branch "Downtown". <br>

#### <span style= "color: red">Answer</span>
a. 
$$ \Pi_{branch\_name}\,(\sigma_{branch\_city="Chicago"}(branch)) $$
b.
$$ \Pi_{ID}\,(\sigma_{branch\_name="Downtown"}(borrower\bowtie loan)) $$


### <span style= "color: blue">Problem 2.12</span>
Consider the bank database of Figure 2.18. Assume that branch names and customer names uniquely identify branches and customers, but loans and accounts can be associated with more than one customer. <br>
> a.	What are the appropriate primary keys? <br>
> b.	Given your choice of primary keys, identify appropriate foreign keys. <br>

#### <span style= "color: red">Answer</span>
a. <br>
***branch (<u>branch_name</u>, branch_city, assets)***<br>
***customer (<u>ID</u>, customer_name, customer_street, customer_city)***<br>
***loan (<u>loan_number</u>, branch_name, amount)***<br>
***borrower (<u>ID</u>, <u>loan_number</u> )*** <br>
***account (<u>account_number</u>, branch_name, balance)*** <br>
***depositor (<u>ID</u>, <u>account_number</u>)***

b. <br>
- ***loan*** : branch_name referencing branch
- ***borrower*** : ID referencing customer, loan_number referencing loan
- ***account*** : branch_name referencing branch
- ***depositor*** : ID referencing customer, account_number referencing account

### <span style= "color: blue">Problem 2.14</span>
Consider the employee database of Figure 2.17. Give an expression in the relational algebra to express each of the following queries: <br>
> a.	Find the ID and name of each employee who works for “BigBank”. <br>
> b.	Find the ID, name, and city of residence of each employee who works for “BigBank”. <br>
> c.	Find the ID, name, street address, and city of residence of each employee who works for “BigBank” and earns more than $10000.
> d.	Find the ID and name of each employee in this database who lives in the same city as the company for which she or he works.

#### <span style= "color: red">Answer</span>
a. 
$$ \Pi_{ID,\,person\_name}\,(\sigma_{company\_name="BigBank"}(works)) $$
b.
$$ \Pi_{ID,\,person\_name,\,city}\,(employee\bowtie (\sigma_{company\_name="BigBank"}(works))) $$
c.
$$ \Pi_{ID,\,person\_name,\,street,\,city}\,(\sigma_{company\_name="BigBank"\wedge \,salary>10000}(works\bowtie employee)) $$
d.
$$ \Pi_{ID,\,person\_name}\,(\sigma_{employee.city=company.city}(employee\bowtie works \bowtie company)) $$

### <span style= "color: blue">Problem 2.15</span>
Consider the bank database of Figure 2.18. Give an expression in the relational algebra for each of the following queries: <br>
> a.	Find each loan number with a loan amount greater than $10000.	<br>
> b.	Find the ID of each depositor who has an account with a balance greater than $6000. <br>
> c.	Find the ID of each depositor who has an account with a balance greater than $6000 at the "Uptown" branch.

#### <span style= "color: red">Answer</span>
a. 
$$ \Pi_{loan\_number}\,(\sigma_{amount>10000}(loan)) $$
b.
$$ \Pi_{ID}\,(\sigma_{balance>6000}(depositor\bowtie account)) $$
c.
$$ \Pi_{ID}\,(\sigma_{balance>6000\wedge \,branch\_name="Uptown"}(depositor\bowtie account)) $$