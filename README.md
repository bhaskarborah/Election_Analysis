# VBA Challenge

## Overview of Project

Tom, an employee of the Colorado Board of Election, has been tasked to do an election audit of the tabulated results of US Congressional Precinct of Colorado. These election results consist of votes from Mail In Ballot, Punch Cards and Direct Recording Electronic (DRE). This audit and certification task is generally done using excel, but Tom's Manager wants to automate the process using Python. If the process is successfully automated using Python, then it can be used to automate the audit and certification of senatorial district and local elections as well.


### Purpose

The purpose of the project is to automate the audit and certification process of the US Congressional Precinct of Colorado election for Tom, an employee of Colorado Board of Election.
The automated report should contain the below results:

1. Total number of votes cast
2. The voter turnout for each county
3. The percentage of votes from each county out of the total count
4. The county with the highest turnout
5. Total number of votes for each candidate
6. Total number of votes for each candidate
7. Percentage of votes for each candidate
8. Winner of the election based on popular vote

## Analysis and Challenges

The results for this project has been generated using Python.

A comma separated sheet (CSV) file with the total election results has been created.
This sheet contains the below fields:
Ballot ID,County,Candidate

There are three counties whose election results is present in the CSV file namely Jefferson, Denver, Arapahoe.

The below code snippet is used to find the total votes per county, the percentage of votes per county and writing the county name, votes and votes percentage to the output report

for county_name in county_votes:

        # 6b: Retrieve the county vote count.
        votes = county_votes.get(county_name)

        # 6c: Calculate the percentage of votes for the county.
        vote_percentage = float(votes) / float(total_votes) * 100

        # 6d: Print the county results to the terminal.
        county_results = (f"{county_name}: {vote_percentage:.1f}% ({votes:,})\n")
        print(county_results)

        # 6e: Save the county votes to a text file.
        txt_file.write(county_results)

The below code is used to determine the winning county and write the result to the output report:

        # 6f: Write an if statement to determine the winning county and get its vote count.
        if (votes > winning_county_count) and (vote_percentage > winning_county_percentage):
            winning_county_count = votes
            winning_county = county_name
            winning_county_percentage = vote_percentage

    # 7: Print the county with the largest turnout to the terminal.
    winning_county_summary = (
        f"\n-------------------------\n"
        f"Largest County Turnout: {winning_county}\n"
        f"-------------------------\n")
    print(winning_county_summary)

There are multiple candidates running in this election. 

Below is the code snippet used to find the total votes per candidate, the percentage of votes per candidate and writing the candidate name, votes and votes percentage to the output report for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)


The below code is used to determine the winning candidate and write the result to the output report:

       # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)

       # Save the winning candidate's name to the text file
       txt_file.write(winning_candidate_summary)

The challenges while generating the report are as below:

1. Writing multiple loops to generate the county and candidate data
2. Indentation of the code. If the indentation is improper, we either get syntax errors or the output is not generated correctly

# Election-Audit Results

(1) How many votes were cast in this congressional election?

   
   The total number of votes cast is: 369,711

   Below screen shot shows it:


   ![Screen Shot 2021-05-21 at 12.03.58 PM](https://i.imgur.com/LLVEVaJ.png)


(2) Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.

  Below is the breakdown of the number of votes and the percentage of total votes for each county in the precinct:

  County Name: Jefferson
  Number of votes: 38,855 
  Percentage of votes: 10.5% 

  County Name: Denver
  Number of votes: 306,055
  Percentage of votes: 82.8%

  County Name: Arapahoe
  Number of votes: 24,801
  Percentage of votes: 6.7%

  Below screen shot provides the consolidated report:

![Screen Shot 2021-05-21 at 12.09.13 PM](https://i.imgur.com/PoFaDvN.png)

(3)  Which county had the largest number of votes?

Below county has the largest number of votes:
County Name: Denver
Number of votes: 306,055

Below screenshot provides the same in the report:


![Screen Shot 2021-05-21 at 12.10.45 PM](https://i.imgur.com/i428jsD.png)


(4) Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.

Below is the breakdown of the number of votes and the percentage of the total votes each candidate received:

Candidate Name: Charles Casper Stockham
Number of votes: 85,213
Percentage of votes: 23.0%

Candidate Name: Charles Diana DeGette
Number of votes: 272,892
Percentage of votes: 73.8%

Candidate Name: Raymon Anthony Doane
Number of votes: 11,606
Percentage of votes: 3.1%

Below screenshot shows the consolidated data as written to the report:


![Screen Shot 2021-05-21 at 12.16.17 PM](https://i.imgur.com/c1Oizpz.png)


(5) Which candidate won the election, what was their vote count, and what was their percentage of the total votes?

Below are the winning candidate's vote detail's:
Winning Candidate's Name: Diana DeGette
Winning Candidate's Vote Count: 272,892
Winning Candidate's Vote Percentage: 73.8%

Below screenshot shows the winning candidate's vote details as written to the report:

# Election-Audit Summary

The Python script used to generate the output election report can be used to generate reports for any election with some modifications.

Instead of finding the total number of votes, percentage of votes and winner per county, this script can be used to find the same for states as well. The updates to the code that would be required is to change all the county variables to state variables making it easier to understand and maintain.

For example the below county variables can be updated to store and calculate state details:

county_options = [], 
county_votes = {}, 
winning_county= "", 
winning_county_count = 0, 
winning_county_percentage = 0

to

state_options = [], 
state_votes = {}, 
winning_state = "", 
winning_state_count = 0, 
winning_state_percentage = 0

Similarly the candidate details can be updated to use senatorial candidate details as well.

Also, the Python script can be updated to calculate the state vote and state candidate details along with the county votes and county candidate details. The script needs to be updated with the code to do so. This can be done by replicating the exact process for county and candidates, and then introducing new variables for state and state candidates.







