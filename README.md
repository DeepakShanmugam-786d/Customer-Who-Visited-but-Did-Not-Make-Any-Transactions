# 🛍️ Customers Who Visited but Did Not Make Any Transactions

## 🎯 Problem Description

We have two tables:

### 1️⃣ **Visits** table — Who visited the mall?
| visit_id | customer_id |
|----------|-------------|
| 1        | 23          |
| 2        | 9           |
| 4        | 30          |
| 5        | 54          |
| 6        | 96          |
| 7        | 54          |
| 8        | 54          |

- **visit_id** is a unique number for each visit.
- **customer_id** tells us which customer visited.

---

### 2️⃣ **Transactions** table — Who actually bought something?
| transaction_id | visit_id | amount |
|----------------|----------|--------|
| 2              | 5        | 310    |
| 3              | 5        | 300    |
| 9              | 5        | 200    |
| 12             | 1        | 910    |
| 13             | 2        | 970    |

- **transaction_id** is a unique number for each purchase.
- **visit_id** connects the purchase to a visit.
- **amount** is how much money they spent.

---

## ❗ Goal: Find Customers Who Didn't Buy Anything
We want to find **customers who visited the mall but didn't buy anything** — and count **how many times** they visited without buying.

For example, if a customer visited 3 times but never bought anything, they should show up with a count of **3**.

### ✅ Output Table
We need this format:
| customer_id | count_no_trans |
|-------------|----------------|
| 54          | 2              |
| 30          | 1              |
| 96          | 1              |

- **customer_id**: The customers who didn’t buy anything.
- **count_no_trans**: How many times they visited without buying.

---

## 🧠 Example Breakdown

Let's walk through it! 🎉

**From the Visits table:**
- Customer **54** visited **3 times** (visits 5, 7, 8).

**From the Transactions table:**
- Customer **54** only bought things during **visit 5**, so visits **7** and **8** are no-transaction visits.
  - Count of no-transaction visits for **54** = **2** ✅

**Customer 30:**
- Visited **once** (visit 4) — but didn’t buy anything.
  - Count = **1** ✅

**Customer 96:**
- Visited **once** (visit 6) — no purchase.
  - Count = **1** ✅

---

## 🔥 How to Solve
Here’s the basic idea:
1️⃣ Find customers who visited (from the **Visits** table).  
2️⃣ Check if their **visit_id** is **missing** from the **Transactions** table.  
3️⃣ Count how many times this happened for each customer.  
4️⃣ Return the list of those customers and their **count_no_trans**.

🚀 Now you’re ready to write the query and find those window shoppers!

