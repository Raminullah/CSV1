# CSV1

Simple console application which converts a csv data file into oracle insert script
# (This code is on Python)

import csv

# Define the CSV file and Oracle table name
csv_file = 'data.csv'
# Define the Oracle table name
table_name = 'your_table_name'

# Read the CSV file and generate Oracle insert statements
with open(csv_file, 'r') as file:
    csv_reader = csv.reader(file)
    header = next(csv_reader)  # Assuming the first row contains column names

    for row in csv_reader:
        columns = ', '.join(header)
        values = ', '.join(f"'{value}'" for value in row)
        insert_statement = f"INSERT INTO {table_name} ({columns}) VALUES ({values});"
        print(insert_statement)
