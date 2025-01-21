The policy is week based. I have to maintain 75% of a metric called Qattend.
Qattend is calculated as a ratio. The numerator is the number of days I have attended onsite to a Qualcomm office. 
The denominator is the number of working days minus public holidays. 
Also as a added bonus for every week one day is removed from the denominator. 
So for example, 
In the following week if there is one public holiday on Wednesday and I attend office on Monday Tuesday and Thursday. 
My Qattend for this week is 3/3 or 100%. 
Because denominator is calculated as 5*number of weeks - public holidays - number of weeks. 

In the program give me a array where I can provide the public holidays for the entire year ahead of time. 
For everyweek do not display the current weeks Qattend it is irrelevant. 
Store the data for days attended in a proper format but keep in encrypted such that even I am not able to open and see, because I don't want to always be distracted by it. 
Also when I run the program i should be given an option just to see Qattend without entering data for this week. 
I may not be able to fill for a particular week because I was busy during the weekend, the program should detect that data for previous week is empty and ask me to fill that first. 

Also my company is very secretive about if they are counting leave that I take in the Qattend calculation. Just to be sure I want to be able to see both. Therefore Now I when entering data I should have 3 options, Worked from Home, Attended Onsite and Applied Leave. 
Accordingly there should be two Qattend ratios that you need to calculate and display, the first one (without leave) is the same are previous, but a new one (with leaves) should be calculated that does the similar calculation but does not count the day I took leave in the numerator and denominator

I also want another set of data that stores the value for each individual day. This file should only be updated and saved, you can still use the above csv structure to make calculations. You can decide the type of file you want to use to store this new data


Issue: What happens if a public holiday is added after some weekly data has already been entered?
The main menu should have an option to enter new public holidays and also have option to display all public holidays. When entering weekly data, public holidays should be shown but the value for that day should be make uneditable. If a new public holiday is added later the calculations have to be modified and retroactively changed. 
Issue: What if a user:
Enters more than 5 working days in a week (e.g., 6 days onsite)? Enters overlapping statuses for the same day (e.g., “Onsite” and “Leave” for one day)?
The program should show the data, day and give a drop down to select among the three options, unless it is a public holiday (In which case it should display that as well). So overlapping and over reporting should not occur. 
Issue: What if you don’t fill data for a week (or some days in a week)?
Should the program prevent you from skipping weeks? Should it assume default values (e.g., “Work from Home” for all missing days)?
If there is missing data (verify through JSON file) then that has to be filled first before proceeding to any next week. This can be done by first maintaining a value in the JSON “last checked date” and then checking the JSON file for every date from that date. 
Issue: What should happen if Qattend is viewed while there is incomplete weekly or daily data? 
I accept your proposal here, but there is a caveat, if Qattend is viewed in between a week, the current week should be ignored. Qattend can be calculated until the previous weekend. But if there is missing info for the previous week as well then an error should be displayed. 
Issue: If data for a day or week is already entered, should the program allow you to overwrite it?
Generally the program should only allow user to enter the previous weeks data. In the main menu under a Extras (rename it appropriately) section there should be an option to edit the status of a particular date (unless a publis holiday) individually, but not a whole week.
Issue: If the start date is Monday, 30th December 2024:
How do we handle weeks that span across two years (e.g., the week containing both December 2024 and January 2025)?
I accept your proposal here. 
Should the program calculate Qattend separately for each calendar year if tracking continues across years?
No end of year summary is not required, Qattend should be calculated whenever I give the command. 
Issue: What if the CSV or JSON file gets corrupted or manually altered?
I accept your proposal here. 
Issue: If the program is used across time zones, how do we ensure date consistency for daily data?
I am not sure why timezones matter, we are only recording data for days, however you can ignore this possibility. I will be in only one time zone. 
Issue: Should the program allow you to reset all data (weekly and daily)?
No do not give this option. 

The main menu should have edit public holidays option instead of add new public holidays, because I might want to delete a previously added holiday as well 

First lets discuss the interface 
There should be main menu and a sub menu to deal with the public holiday section. Also ensure that the output file that store the data are added into a separate folder so that I can use gitignore for the whole folder. 
Make the user interface a little engaging, one example is if the Qattend without leaves is less that 75% you can make the background red and green if it is. 

Should the user explicitly specify the week (e.g., via a dropdown for week numbers)?

No by default show the latest week, the main menu should contain an option to only edit the status of individual days of any previous week. 

Should we pre-fill days with default statuses like “Work from Home,” or leave them blank?

Leave it blank

Should holidays be displayed in a calendar view, a simple list, or both?

Both a calender which shows current month and left and right to change the month, and a button on top right to change to list view which shows a list. 

For deleting holidays, should we allow multi-selection, or limit it to one holiday at a time?

One at a time

Should Qattend percentages (with and without leaves) be displayed in the main window itself or in a separate popup?

Separate pop up 

Would you like additional data visualization, such as progress bars or pie charts for the Qattend ratio?

Yes a little vizualisation can be done, lets postpone this to future work

Should the program prevent saving if the input data is incomplete or invalid, or allow saving with warnings?

Show warnings but allow force save

What specific error messages or prompts would you like to see for common errors (e.g., missing dates, exceeding the maximum number of days in a week)?

show appropriate messages in pop ups, nothing specific

Do you prefer a minimalistic design, or should I incorporate additional visual elements like icons and color schemes?

Include simple visual elements and colours schemes but it should not be too bright or show offy. Keep it simple, use stuff when required. 

Would you like a “Back” button in all submenus? 

yes

Should we include tooltips or hover text on buttons to explain their functionality?

Do not need of hover functionality, a icon on bottom right like a blue question mark which explain the page when clicked in a pop up 

Should the program allow clearing all data for a specific week (in case of errors), or just individual day edits?

When adding data for a particular week (Enter weekly data option) there should be a clear all data button which makes everything go to blank value (except public holidays which are uneditable). But when editing for a particular day this option is not required. 

Should the program display historical trends of Qattend over multiple weeks/months?

Historical data visualization is not so important, we can add this feature later. 

Is the data/ folder location suitable, or would you like the option to choose a custom folder?

This is fine 

Are you planning to expand this program in the future (e.g., adding additional features like exporting reports)? If yes, I can structure the code to simplify future enhancements.

Yes please keep make it so its easy for modifications

Should the program handle future weeks proactively, or restrict data entry strictly to the current and past weeks?

No it should not be proactive, also i should not be able to enter data for the current week as well if I start the program on a weekday, the program should expect that I only enter data on a saturday for the current week or anyday in the future weeks. 

Should the cleared data be left entirely blank (no placeholders), or should we add something like “Select” as a placeholder for dropdowns?

select as palceholder 

Should the holidays in the list view be displayed with additional details like their corresponding weekday (e.g., “2025-01-01 - Wednesday”), or is just the date sufficient? 

Please mention the day as well 

Provide general tips for the page (e.g., “Here’s how to enter weekly data”).

Yes this is enough 

Offer a link to a more comprehensive documentation file if needed later?

No I will be the one using the program so this is not required 

Should deleting public holidays or editing individual days always show a confirmation popup, or should it just save immediately?

Show confirmation with previous info and changed info in a pop up 

Should the program allow renaming the files (e.g., weekly_data.csv to something custom), or are the default names (weekly_data.csv, daily_data.json, etc.) sufficient?

default names are correct and should not be changed