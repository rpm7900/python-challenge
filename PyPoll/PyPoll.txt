# Import modules
import csv
import os

# Questions to be answered from file
def poll(csv):
    votes = 0
    vote_count = 0
    candidate_data = 0
    name = []
    percent_votes = 0
    count_votes = 0
    changes =[]      

## List of Candidates
    for row in csv:
        if row[2] not in name:
            name.append(row[2])

## Number of votes cast
        votes = row[2]
        vote_count += 1

## % of votes received by candidate
## total number of votes each candidate received
## Winner of election

# Return results
    return[name, votes]

# Open the source file and Read
with open("election_data.csv") as file:
    csvreader = csv.reader(file, delimiter = ',')
    header = next(csvreader)
    analysis = poll(csvreader)

# Print results
print(f"""
Election Results
--------------------------------------------
Total Votes: {analysis[1]}
--------------------------------------------
{analysis[0]}

--------------------------------------------
Winner:
--------------------------------------------
""")

