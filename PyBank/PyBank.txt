# Import modules
import csv
import os

# Write a function that does:
def bank(csv):
    months = 0
    Total_Dollars = 0
    Average_Change = 0
    Greatest_Profit = 0
    Greatest_Loss = 0
    maxmonth = ""
    minmonth = ""
    lastmonth =  None
    changes = []
    for row in csv:
        Current_Month = row[0] 
        current_pnl = int(row[1])
        Total_Dollars += current_pnl
        months += 1

        if lastmonth is not None:
            changes.append(current_pnl-lastmonth)
            current_change = current_pnl-lastmonth
              
            if current_change > Greatest_Profit:
                Greatest_Profit = current_change 
                maxmonth = Current_Month
        
            if current_change < Greatest_Loss:
                Greatest_Loss = current_change
                minmonth = Current_Month
        
      
        lastmonth = current_pnl
    Average_Change = sum(changes)/len(changes)


    return[Current_Month, Total_Dollars, Average_Change, Greatest_Profit, Greatest_Loss, maxmonth,minmonth]


# Open the source file
# Read the source file
with open("budget_data.csv") as file:
    csvreader = csv.reader(file, delimiter = ',')
    header = next(csvreader)
    analysis = bank(csvreader)
print(f"""
Financial Analysis
------------------
Total Months: {analysis[0]}
Total: ${round(analysis[1],2)}
Average Change: ${round(analysis[2],2)}
Greatest Increase: {analysis[5]} (${analysis[3]})
Greatest Decrease: {analysis[6]} (${analysis[4]})
""")
# Set output file path


# Print the answer
# Save to text file

