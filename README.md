
<!--
**Canalytics24/Canalytics24** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

1. Code high_risk_default.sql is solving the below question:

**QUESTION:**
Identify customers who are at high risk of default based on the following conditions:
- Outstanding balance > 50% of the original loan amount.
- More than 2 missed repayments.
- Loan tenure exceeds 12 months.


**DATESET - TABLE**
-- Drop tables if they already exist
DROP TABLE IF EXISTS Repayments;
DROP TABLE IF EXISTS Loans;
DROP TABLE IF EXISTS Customers;

-- Create Customers table
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(255)
);

-- Create Loans table
CREATE TABLE Loans (
    loan_id INT PRIMARY KEY,
    customer_id INT,
    loan_amount DECIMAL(15,2),
    loan_term_months INT,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

-- Create Repayments table
CREATE TABLE Repayments (
    repayment_id INT PRIMARY KEY,
    loan_id INT,
    repayment_date DATE,
    amount_paid DECIMAL(15,2),
    payment_status VARCHAR(20) CHECK (payment_status IN ('On Time', 'Missed')),
    FOREIGN KEY (loan_id) REFERENCES Loans(loan_id)
);

INSERT INTO Customers (customer_id, customer_name) VALUES
(1, 'Alice'),
(2, 'Bob'),
(3, 'Charlie');

INSERT INTO Loans (loan_id, customer_id, loan_amount, loan_term_months) VALUES
(101, 1, 10000.00, 24),
(102, 2, 15000.00, 36),
(103, 3, 20000.00, 12);

INSERT INTO Repayments (repayment_id, loan_id, repayment_date, amount_paid, payment_status) VALUES
(1, 101, '2024-01-10', 2000.00, 'On Time'),
(2, 101, '2024-02-15', 2000.00, 'Missed'),
(3, 101, '2024-03-20', 0.00, 'Missed'),
(4, 101, '2024-04-10', 0.00, 'Missed'),
(5, 102, '2024-05-15', 5000.00, 'On Time'),
(6, 103, '2024-06-10', 10000.00, 'On Time'),
(7, 103, '2024-07-15', 10000.00, 'On Time');
-->
