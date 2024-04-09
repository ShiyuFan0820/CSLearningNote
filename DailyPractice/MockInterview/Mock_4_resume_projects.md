# Resume Projects

## FitU Gym Coach MatchMaker
```py
import pandas

# # Collect Students Data and Coaches Data
# # ----------Students Information Collection----------
# name_s = input("What's your name?\n").capitalize()
# gender_s = input("What's your gender? (Female or Male)\n").lower()
# age_s = input("what's your age?\n")
# goal_s = input("What's your fitness goal?\n")
# budget_s = int(input("How much is your budget?\n"))
# date_s = int(input("Which day do you prefer to exercise? (Insert 1-7 for Monday to Sunday)\n"))
# time_s = int(input("Which time slot do you prefer for exercising?\n--Insert 2 for 9:00 - 10:00--\n--Insert 3 for 10:00 - 11:00--\n--Insert 4 for 11:00 - 12:00--\n--Insert 5 for 12:00 - 13:00--\n--Insert 6 for 13:00 - 14:00--\n--Insert 7 for 14:00 - 15:00--\n--Insert 8 for 15:00 - 16:00--\n--Insert 9 for 16:00 - 17:00--\n--Insert 10 for 17:00 - 18:00--\n--Insert 11 for 18:00 - 19:00--\n--Insert 12 for 19:00 - 20:00--\n--Insert 13 for 20:00 - 21:00--\n--Insert 14 for 21:00 - 22:00--\n"))
#
# # ----------Coaches Information Collection----------
# name_c = input("What's your name?\n").capitalize()
# gender_c = input("What's your gender? (Female or Male)\n").lower()
# age_c = input("what's your age?\n")
# certi_c = input("What certification do you have?\n")
# cost_c = int(input("How much do you plan to charge per lesson?\n"))
# date_c = int(input("On which days are you available? (Insert 1-7 for Monday to Sunday')\n"))
# time_c = int(input("During which time slots are you available?\n--Insert 2 for 9:00 - 10:00--\n--Insert 3 for 10:00 - 11:00--\n--Insert 4 for 11:00 - 12:00--\n--Insert 5 for 12:00 - 13:00--\n--Insert 6 for 13:00 - 14:00--\n--Insert 7 for 14:00 - 15:00--\n--Insert 8 for 15:00 - 16:00--\n--Insert 9 for 16:00 - 17:00--\n--Insert 10 for 17:00 - 18:00--\n--Insert 11 for 18:00 - 19:00--\n--Insert 12 for 19:00 - 20:00--\n--Insert 13 for 20:00 - 21:00--\n--Insert 14 for 21:00 - 22:00--\n"))

# Load Students Data and Coaches Data to Match
# Read data file using pandas
coaches_data = pandas.read_csv("FitU - Coaches.csv", index_col=False)
coaches_dict = {row["Name"]: {"Gender": row["Gender"], "Age": row["Age"], "Cost": row["Cost"], "Date": [int(date) for date in row["Date"].split(",")], "Time": [int(time) for time in row["Time"].split(",")]} for index, row in coaches_data.iterrows()}
print(f"=======The coaches information dictionary=======\n{coaches_dict}\n")
students_data = pandas.read_csv("FitU - Students.csv", index_col=False)
direct_dict = students_data.to_dict()
print(f"=======Students Data Direct to Dict=======\n{direct_dict}")
students_dict = {row["Name"]: {"Gender": row["Gender"], "Age": row["Age"], "Goal": row["Fitness Goal"], "Budget": row["Budget"], "Date": [int(date) for date in row["Date"].split(",")], "Time": [int(time) for time in row["Time"].split(",")]} for index, row in students_data.iterrows()}
print(f"=======The students information dictionary=======\n{students_dict}\n")

# Match students with coaches
matched = {}

for stu in students_dict:
    for coach in coaches_dict:
        if students_dict[stu]["Budget"] >= coaches_dict[coach]["Cost"]:
            for date in students_dict[stu]["Date"]:
                if date in coaches_dict[coach]["Date"]:
                    for time in students_dict[stu]["Time"]:
                        if time in coaches_dict[coach]["Time"]:
                            if stu in matched:
                                if coach in matched[stu]:
                                    matched[stu][coach]["Matched Date and Time"].append((date, time))
                                else:
                                    matched[stu][coach] = {"Cost": coaches_dict[coach]["Cost"], "Matched Date and Time": [(date, time)]}
                            else:
                                matched[stu] = {coach: {"Cost": coaches_dict[coach]["Cost"], "Matched Date and Time": [(date, time)]}}
print(f"The matched students with coaches is:\n{matched}")
flat_data = {
    'Name': {},
    'Coach': {},
    'Cost': {},
    'Time': {}
}
for i, (stu, coaches) in enumerate(matched.items()):
    flat_data['Name'][i] = stu
    flat_data['Coach'][i] = list(coaches.keys())
    flat_data['Cost'][i] = [coach_info['Cost'] for coach_info in coaches.values()]
    flat_data['Time'][i] = [coach_info['Matched Date and Time'] for coach_info in coaches.values()]
print("=========Convert Matched Results to csv=========")
print(flat_data)
# Convert to DataFrame
df = pandas.DataFrame(flat_data)

# Write to CSV file
df.to_csv('matched_students_and_coaches.csv', index=False)

```
