# Linux Command Line Lab – Working with Commands

This repository documents a hands-on lab focused on essential Linux command-line utilities used for text processing and command chaining. The lab demonstrates how to manipulate files, process structured data, and redirect output using common shell commands.

# Objectives

The goal of this lab is to practice and understand the following Linux commands:

tee – write output to both the terminal and a file

sort – organize and reorder file contents

cut – extract specific fields from text files

sed – modify text using stream editing

| (pipe operator) – pass the output of one command to another

# Environment

Linux Terminal

Amazon EC2 instance

Working directory:

/home/ec2-user

# Task 1 – Using the tee Command

The tee command reads from standard input and writes the output to both the terminal and a file.

Verify current directory
pwd


Expected output:

/home/ec2-user

Execute the tee command
hostname | tee file1.txt


Example output:

[ec2-user@ ~]$ hostname | tee file1.txt
ip-10-0-10-81.us-west-2.compute.internal


The command performs the following actions:

Executes hostname

Displays the output in the terminal

Writes the output into file1.txt

Verify file creation
ls


Example output:

companyA  file1.txt

Task 2 – Sorting Data with the sort Command
Create a CSV file
cat > test.csv


Insert the following data:

Factory, 1, Paris
Store, 2, Dubai
Factory, 3, Brasilia
Store, 4, Algiers
Factory, 5, Tokyo


Press CTRL + D to save the file.

Verify the file exists
ls

Sort the file contents
sort test.csv


Output:

Factory, 1, Paris
Factory, 3, Brasilia
Factory, 5, Tokyo
Store, 2, Dubai
Store, 4, Algiers


The sort command organizes lines alphabetically by default.

Task 3 – Using the Pipe Operator

The pipe operator (|) sends the output of one command directly to another command.

Search for entries containing Paris:

cat test.csv | grep Paris


Output:

Factory, 1, Paris


This command:

Reads the contents of test.csv

Pipes the output to grep

Filters the results for the pattern Paris

Task 4 – Extracting Fields with the cut Command
Create another CSV file
cat > cities.csv


Insert:

Dallas, Texas
Seattle, Washington
Los Angeles, California
Atlanta, Georgia
New York, New York


Save using CTRL + D.

Extract the first column
cut -d ',' -f 1 cities.csv


Output:

Dallas
Seattle
Los Angeles
Atlanta
New York


Explanation:

Option	Meaning
-d ','	Specifies comma as the delimiter
-f 1	Extracts the first field
Additional Challenge – Editing Text with sed

The sed command is a stream editor used to search and replace text within files.

Syntax
sed 's/old-text/new-text/' filename

Replace the first comma with a period
sed 's/,/./' cities.csv


Output:

Dallas. Texas
Seattle. Washington
Los Angeles. California
Atlanta. Georgia
New York. New York

Apply the same change to multiple files
sed 's/,/./' cities.csv test.csv


Expected output:

Dallas. Texas
Seattle. Washington
Los Angeles. California
Atlanta. Georgia
New York. New York
Factory. 1, Paris
Store. 2, Dubai
Factory. 3, Brasilia
Store. 4, Algiers
Factory. 5, Tokyo

Project Structure
linux-working-with-commands-lab
│
├── README.md
├── test.csv
├── cities.csv
└── images
    ├── tee.jpg
    ├── ls.jpg
    ├── sort.jpg
    ├── pipe.jpg
    └── cut.jpg

Key Learning Outcomes

After completing this lab, the following skills were demonstrated:

Redirecting command output using tee

Sorting structured data using sort

Filtering results with grep

Extracting fields with cut

Editing text streams with sed

Combining commands using the pipe operator
