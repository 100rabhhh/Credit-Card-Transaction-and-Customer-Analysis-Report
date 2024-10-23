
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <h1>🏦 Credit Card Transaction and Customer Analysis Report 📊</h1>
    <h2>📌 Project Overview</h2>
    <p>
        This project presents <strong>two Power BI dashboards</strong>:
    </p>
    <ol>
        <li><strong>Credit Card Transaction Report</strong>: Focused on analyzing revenue, transaction types, and quarterly performance.</li>
        <li><strong>Credit Card Customer Report</strong>: Highlights customer demographics, job roles, income levels, and their impact on revenue.</li>
    </ol>
    <p>
        The data was connected from <strong>PostgreSQL</strong>, and we used a <strong>Python script</strong> to automate data loading, saving significant time and effort compared to manual processes.
    </p>
    <h2>🚀 Dashboard Highlights</h2>
    <h3>1️⃣ Credit Card Transaction Report 💳</h3>
    <p>
        This dashboard gives an in-depth analysis of how different transaction types, card categories, and time periods contribute to overall revenue.
    </p>
    <h4>Key Insights:</h4>
    <ul>
        <li><strong>Revenue by Transaction Type</strong>: Swipe transactions lead with $35M, while Chip and Online methods contribute $17M and $3M respectively.</li>
        <li><strong>Quarterly Performance</strong>: The highest revenue was achieved in Q3, reaching $14.2M, with a total of 166.6K transactions.</li>
        <li><strong>Card Category Breakdown</strong>: Blue Card dominates, generating $46M in revenue, while Gold, Platinum, and Silver contribute smaller portions.</li>
    </ul>
    <h3>2️⃣ Credit Card Customer Report 👥</h3>
    <p>
        This report focuses on customer demographics and how they influence credit card usage and spending behavior.
    </p>
    <h4>Key Insights:</h4>
    <ul>
        <li><strong>Revenue by Income Group</strong>: Customers in the Low Income group contribute $10M in revenue, while Medium and High Income groups add $8M and $7M, respectively.</li>
        <li><strong>Job Type Analysis</strong>: Businessmen lead in revenue generation, contributing $17M, followed by White-collar workers with $10M.</li>
        <li><strong>Age-wise Segmentation</strong>: Customers aged 40-50 generate the most revenue ($14M), followed by those aged 30-40 ($11M).</li>
    </ul>
    <h2>🧑‍💻 Automation with Python 🐍</h2>
    <p>
        We automated the data-loading process using a <strong>Python script</strong>, which significantly reduced the time it takes to upload tables to PostgreSQL. Without automation, manual data insertion would have taken considerably longer.
    </p>
    <p>Here’s the <strong>Python code</strong> used for the automation:</p>
    <pre><code>
import pandas as pd
from sqlalchemy import create_engine
import os

# Connection string for PostgreSQL with URL-encoded password
conn_string = 'postgresql://postgres:yug%402019@localhost/ccdb'
db = create_engine(conn_string)

# List of CSV files to process
csv_files = [
    'credit_card.csv',
    'customer.csv'
]

# Base path for the CSV files
base_path = 'D:/SQL, BI, XL PROJECT/Power bi + Tablue PROJECT/creadit card/'

for file_name in csv_files:
    csv_path = os.path.join(base_path, file_name)    
    if os.path.exists(csv_path):
        # Load the CSV file into a DataFrame
        df = pd.read_csv(csv_path)
        # Try connecting to the database and writing the DataFrame
        try:
            with db.connect() as conn:  # Automatically closes the connection
                # Use the file name (without .csv) as the table name
                table_name = os.path.splitext(file_name)[0]
                df.to_sql(table_name, con=conn, if_exists='replace', index=False)
                print(f"{table_name} table updated successfully.")
        except Exception as e:
            print(f"Error updating {file_name}: {e}")
    else:
        print(f"{file_name} does not exist.")
    </code></pre>
    <h2>🔗 How the Data Pipeline Works</h2>
    <ol>
        <li><strong>PostgreSQL Setup</strong>: We created two tables in PostgreSQL: transactions and customers. The <strong>Python script</strong> was run to upload the data into these tables automatically, saving hours of manual work.</li>
        <li><strong>Connecting Power BI</strong>: In Power BI Desktop, we connected to the PostgreSQL database and imported the transactions and customers tables. Visualizations were built using these datasets to generate meaningful insights on transactions and customer behavior.</li>
        <li><strong>Excel Integration</strong>: Excel was used during the data preprocessing phase to ensure the data's structure was optimized before loading it into Power BI. This included handling missing values, adjusting formats, and validating column data.</li>
    </ol>
    <h2>✨ Tools Used</h2>
    <ul>
        <li><strong>Power BI</strong>: For creating interactive dashboards and visualizations.</li>
        <li><strong>PostgreSQL</strong>: As the backend database to store transaction and customer data.</li>
        <li><strong>Python</strong>: To automate the data loading process and save time.</li>
        <li><strong>Excel</strong>: For preprocessing and cleaning data before importing it into PostgreSQL and Power BI.</li>
    </ul>
    <h2>📜 Conclusion</h2>
    <p>
        This project delivers deep insights into customer behavior and transaction patterns, leading to <strong>key conclusions</strong> that can help shape business strategies:
    </p>
    <ul>
        <li><strong>Transaction Methods</strong>: The dominance of Swipe transactions ($35M) over other methods indicates that physical card usage is still the most preferred. Focusing on enhancing this experience or promoting Chip and Online methods could lead to growth in these areas.</li>
        <li><strong>Customer Segmentation</strong>: By identifying high-value customer groups like Businessmen and White-collar professionals, targeted marketing campaigns can be developed to drive more revenue from these segments.</li>
        <li><strong>Product Performance</strong>: The Blue Card’s overwhelming revenue share ($46M) suggests that this category is popular among customers. This can guide businesses to prioritize offerings tied to this card, while refining the strategies for Gold, Platinum, and Silver cards.</li>
        <li><strong>Income-based Strategy</strong>: The insights into revenue contribution by Low Income customers ($10M) provide an opportunity to tailor products for lower-income groups, potentially increasing revenue in underserved segments.</li>
    </ul>
    <p>
        Through the use of <strong>automation</strong> with Python, the entire data import process was completed in seconds, drastically reducing manual effort. These dashboards now provide a comprehensive view of the <strong>credit card ecosystem</strong>, equipping decision-makers with the right data to make informed business choices.
    </p>
    <h2>👥 Credits</h2>
    <p>Built by <a href="https://github.com/100rabhhh">Sourabh Jha</a></p>
    <h2>📄 License</h2>
    <p>This project is licensed under the MIT License.</p>

<p align="center">
  <strong>Thanks for exploring this project! Feel free to contribute and suggest improvements. 💼📈</strong>
</p>

</body>
</html>
