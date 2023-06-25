# Decision Table Testing

This repository contains the solution for the problem statement related to decision table testing for the **COMMISION** software component. The component is responsible for automatically computing the commission for salespersons in the XYZ-store. The purpose of this project is to design test cases using decision table-based testing to thoroughly test the **COMMISION** program.

## Problem Statement

The **COMMISION** component accepts five inputs:

1. Salesman name
2. Salesman type
3. Item type
4. Customer type
5. Item price

The commission calculation rules for different scenarios are as follows:

- For non-salaried salespersons:
  - If a non-salaried salesperson sells an item that is neither standard nor bonus to someone other than a regular customer, he/she receives a 7% commission, unless the item costs more than $5,000, in which case the commission is 3%.
  - If a standard item is sold, or if any item is sold to a regular customer, no commission is given.
  
- For salaried salespersons:
  - If a salaried salesperson sells a bonus item, he/she receives a 3% commission, unless the item sells for more than $500, in which case he/she receives a flat $30 commission.
  
- For non-salaried salespersons selling bonus items:
  - If a non-salaried salesman sells a bonus item to someone other than a regular customer, he/she receives a 7% commission, unless the item sells for more than $500, in which case he/she receives a flat commission of $65.
  
- For all other cases, a salesman receives a 2% commission.

Assumptions:
- The maximum size of the Salesman name is 20 characters.
- Salesman type values: Salaried (S), Non-salaried (NS)
- Item type values: Standard (ST), Bonus (B), General (G)
- Customer type values: Regular (R), Walk-in (W)
- Item price is an integer.

## Decision Table

Based on the problem statement, the following decision table is derived:

| Salesman Type | Item Type | Customer Type | Item Price | Commission |
|---------------|-----------|---------------|------------|------------|
| Salaried      | Standard  | Regular       | Any        | No         |
| Salaried      | Bonus     | Regular       | Any        | No         |
| Salaried      | Standard  | Walk-in       | Any        | No         |
| Salaried      | Bonus     | Walk-in       | <= 500     | 3%         |
| Salaried      | Bonus     | Walk-in       | > 500      | $30        |
| Non-salaried  | Standard  | Regular       | Any        | No         |
| Non-salaried  | Bonus     | Regular       | Any        | No         |
| Non-salaried  | Standard  | Walk-in       | <= 5000    | 2%         |
| Non-salaried  | Standard  | Walk-in       | > 5000     | 3%         |
| Non-salaried  | Bonus     | Walk-in       | <= 500     | 7%         |
| Non-salaried  | Bonus     | Walk-in       | > 500      | $65        |

## Sample Test Cases

Based on the decision table, the following sample test cases can be derived:

1. Test Case 1:
   - Salesman name: Smith
   - Salesman type: Non-salaried (NS)
   - Item type: Standard (ST)
   - Customer type: Walk-in
   - Item price: 1400
