**Lecture Notes: Create and Configure a DynamoDB Instance on AWS**

**1. Introduction to DynamoDB**
   - **DynamoDB** is a fully managed NoSQL database service provided by AWS.
   - It is designed for scalability, low-latency performance, and ease of use.
   - DynamoDB stores data in tables, consisting of items (rows) and attributes (columns).

**2. Key Concepts**
   - **Table:** A collection of data organized in items.
   - **Item:** A single data record, similar to a row in a relational database.
   - **Attributes:** Data fields within an item (e.g., `ProductID`, `Name`).
   - **Primary Key:** Uniquely identifies each item in a table. Can be:
     - **Partition Key:** A single attribute used for partitioning data.
     - **Composite Key:** Combines a partition key and a sort key.
   - **Global Secondary Index (GSI):** Enables querying data based on attributes other than the primary key.
   - **Capacity Modes:**
     - **Provisioned:** Fixed read/write capacity limits.
     - **On-Demand:** Scales automatically based on traffic.

**3. Steps to Create and Configure a DynamoDB Table**
   - Navigate to the **DynamoDB** service in the AWS Management Console.
   - Select **Create Table** and configure the following:
     - **Table Name:** Choose a unique name.
     - **Partition Key:** Define the attribute (e.g., `ProductID`).
     - **Sort Key (optional):** Leave blank for this assignment.
     - **Capacity Mode:** Choose **On-Demand** to simplify setup.
   - Click **Create Table** to finalize.

**4. Adding and Querying Data**
   - **Add Items:**
     - Navigate to the **Items** tab and select **Create Item**.
     - Use the JSON editor to add data (e.g., `{ "ProductID": "101", "Name": "Laptop", "Price": 1200, "Stock": 15 }`).
     - Repeat for additional items.
   - **Query Items:**
     - Use the **Search** tab to query by partition key (e.g., `ProductID: 101`).
     - Use **Scan** to retrieve all table data.

**5. Optional Features**
   - **Indexes:** Create a GSI to query data by non-primary key attributes (e.g., `Price`).
   - **Metrics:** Monitor table performance using the **Metrics** tab.

**6. Cleanup and Best Practices**
   - Delete items and the table when finished to avoid charges.
   - Regularly monitor usage and performance metrics to optimize costs.

**7. Key Takeaways**
   - DynamoDB offers a scalable solution for managing NoSQL data.
   - Properly configuring keys and indexes ensures efficient querying.
   - Understanding capacity modes helps balance cost and performance.

**Assignment Deliverables**
   - Screenshots of the **Items** tab and successful query results.
   - Documentation in a GitHub repository with notes on table setup, data entry, and learned concepts.

