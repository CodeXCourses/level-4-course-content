**Assignment Title: Create and Configure a DynamoDB Instance on AWS**

**Summary:**  
In this 1-hour assignment, you will learn how to create an Amazon DynamoDB table, add data to it, and query the data using the AWS Management Console. This table will serve as a foundational step in working with NoSQL databases in AWS.

**Learning Objectives:**

- Create a DynamoDB table on AWS.
- Configure table settings such as primary keys and provisioned capacity.
- Add items to the table and query them using the AWS Console.

**Instructions:**

### Step 1: Set Up a DynamoDB Table

1. **Sign in to AWS Console:** Go to [AWS Management Console](https://aws.amazon.com/console/).
2. **Navigate to DynamoDB Service:** In the search bar, type **DynamoDB** and select **Amazon DynamoDB** from the list of services.
3. **Create a New Table:**
   - Click **Create table**.
   - **Table Name:** Enter a unique name for your table (e.g., `my-products-table`).
   - **Partition Key:** Enter `ProductID` as the key name and select `String` as the data type.
   - Leave the **Sort Key** field blank for this assignment.
   - **Table Settings:** Select **On-demand capacity mode** to avoid setting a fixed read/write capacity.
   - Click **Create table**.

### Step 2: Add Items to the Table

1. **Open the Table:** Once your table is created, click on its name to open the table details.
2. **Add Items:**
   - Go to the **Items** tab.
   - Click **Create item**.
   - Use the JSON editor to enter the following data for the first item:

     ```json
     {
       "ProductID": "101",
       "Name": "Laptop",
       "Price": 1200,
       "Stock": 15
     }
     ```

   - Click **Save**.
   - Repeat the process to add at least two more items with different `ProductID` values and properties.

### Step 3: Query Data from the Table

1. **Run a Query:**
   - In the **Items** tab, click **Search**.
   - Under **Partition key**, enter a `ProductID` value you added (e.g., `101`) and click **Run**.
   - Verify that the correct item is returned.

2. **Scan All Items:**
   - Click **Scan** to view all items in the table.
   - Ensure all the items you added are visible.

### Step 4: Explore Additional Features (Optional)

1. **Add an Index:**
   - Navigate to the **Indexes** tab and create a new Global Secondary Index (GSI) with:
     - **Index Name:** `PriceIndex`
     - **Partition Key:** `Price` (Number)
   - Use the GSI to query items by price.

2. **Monitor Table Activity:**
   - Go to the **Metrics** tab to explore DynamoDB performance metrics.

### Step 5: Delete Resources

1. **Delete Items:**
   - Go to the **Items** tab in your DynamoDB table.
   - Select all items and click **Actions > Delete** to remove them from the table.

2. **Delete the Table:**
   - Navigate to the **Tables** tab in DynamoDB.
   - Select your table and click **Delete table**.
   - Confirm the deletion in the prompt that appears.

3. **Clean Up Additional Resources:**
   - Ensure that any Global Secondary Indexes or other resources linked to the table are also deleted to avoid unnecessary charges.

**Deliverable:**

1. Submit the following:
   - A screenshot of your DynamoDB table’s **Items** tab showing the added data.
   - A screenshot of a successful query result in the **Search** tab.
2. Create a repository called `aws-dynamodb` with a `README.md` file.
3. Create a file called `HOW-TO-USE-DYNAMODB.md`.
4. Add your screenshots to this file along with notes on what you did to complete the assignment. These notes will help you to remember how to accomplish this task.
5. Add notes about the concepts you learned, such as Partition Key, On-demand Capacity, and Global Secondary Index.

**Tips:**

- Ensure the `ProductID` values are unique to avoid conflicts.
- If you encounter issues querying data, double-check the table’s partition key settings.

**Rubric:**

| Criteria                  | Limited (0 pts)                                   | Partial (3 pts)                              | Complete (5 pts)                                  |
|---------------------------|---------------------------------------------------|----------------------------------------------|---------------------------------------------------|
| DynamoDB Table Setup      | Significant issues in table creation or settings  | Minor issues in table creation               | Table is correctly created with appropriate settings |
| Data Entry                | Items not added or missing required fields        | Some items added with minor issues           | All items added with correct data and structure    |
| Querying Data             | Unable to query data or incorrect results         | Some issues with queries                     | Data successfully queried with correct results     |
| GitHub Repository Setup   | Repository not created or incorrect structure     | Repository created with minor issues         | Repository correctly set up with appropriate structure |
| Documentation Quality     | Documentation missing or unclear                  | Documentation provided with minor details missing | Detailed documentation provided in `HOW-TO-USE-DYNAMODB.md` with all required notes  |

