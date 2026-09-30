# Software Design: Budget_Trackor
The budget tracker tracks income and expenses (duh)

**Course** ITP 100 Software design and Logic.
**Author** Abdullah Lone
**Deliverable** Algorithm Design (IPO, Flowchart, Pseudocode)

## 1. Problem Description & Scope
** Command line interface to track budget spending, such as income gained and where it was spent. **  
**Scope**
* Features a main loop with 2 hierarchical submenus (Income and spent)    
* Validates menu bounds (Rejects values outside menu options) and duration input (no negative numbers)  
*  Aggerates total minutes in memory during execution and outputs a progress summary  
*  terminates cleanly when the user selects the exit option.  

## 2. IPO Chart (Input - Process - Output)
| Input | Process | Output |
| :--- | | :--- | | :--- | 
| `main_choice` (Integer 1-4) <br>
| `sub_choice` (Integer 1-3) <br>
`total` (Real / Integer: $\ge 0$) |
1. Initionalize `total_income = 0`, ` total_expense = 0`. <br>2. Loop main menu display until user enter `4`. <br> 3. Validate that `main_choice` is between 1-4.<br> 4. if `1` (Log Income) or `2` (Log Expense):<br>&emsp;a.Display the respective submenu.<br>&emsp;b. Validate `sub_choice` between 1-3<br>&emsp;c. Prompt for duration; Loop until `total >= 0`.<br>&emsp;d. Map choice to activity name.<br>&emsp;e. Add `Total` to running total.<br>5. If `3` (Summary):<br>&emsp;a. Calculate `total_money = total_income - total_expense`.<br>&emsp;b. Determine goal achivement status ($)<br>&emsp;c. Display formatted summary report.<br>6. If `4` (Exit): Display the exit farewell and terminate. | Invalid input warning messages.<br> Success confirmation of logged income and expense and where it came from<br> Formatted Budget Summary<br>&emsp;- Total Income<br>&emsp;- Total Expense<br>&emsp;- total budget<br>&emsp;- Congrats on being profitable message <br>&emsp;- exit Farewell Message |


---

## 3. Pseduocode

...

```

MODULE main()
    DECLARE Integer total_income = 0
    DECLARE Integer total_expense = 0
    DECLARE integer total_budget = 0
    DECLARE string main_choice = ""
    DECLARE String sub_choice = ""
    DECLARE Real total = 0.0
    DECLARE String finacial_summary = ""

    print("==========================================")
    print("        PERSONAL BUDGET TRACKER            ")
    print("==========================================")

    WHILE true
        // Step 1: Main menu & Input Validation
        DISPLAY "---MAIN MENU---"
        DISPLAY "1. Log Income"
        DISPLAY "2. Log Expense"
        DISPLAY "3. Financial Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4):"
        INPUT main_choice

        WHILE main_choice != 1 AND main_choice != 2 AND main_choice != 3 AND main_choice != 4
          DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
          INPUT main_choice
        END WHILE

        // Step 2: Route Submenu and Actions
        IF main_choice = 1
        DISPLAY "--- INCOME MENU ---"
        DISPLAY "1. Design"
        DISPLAY "2. Coding"
        DISPLAY "3. User Documentation"
        DISPLAY "Enter income catagory (1-3):"
        INPUT sub_choice

        WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice != 3
          DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
          INPUT sub_choice
        END WHILE

        IF sub_choice == 1 THEN
          total = "Design"
        ELSE sub_choice == 2 THEN
          total = "Coding"
        ELSE
          total = "User Documentation"
        END IF

        DISPLAY "Enter total for the catagory."
        INPUT total
        WHILE total < 0
            DISPLAY "Invalid. Please enter a value >= 0:"
            INPUT total
        END WHILE

        total_income = total_income + total
        DISPLAY "Successfully added ", total, " for the total income of the budget tracker."

        ELSE IF main_choice == 2 THEN
            DISPLAY "---Total expense---"
            DISPLAY "1. Software"
            DISPLAY "2. Equipment"
            DISPLAY "3. Workspace"
            DISPLAY "4. Exit"
            DISPLAY "Enter your choice (1-4):"

        WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice != 3
          DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
          INPUT sub_choice
        END WHILE

        IF sub_choice == 1 THEN
          activity_name = "Software"
        ELSE sub_choice == 2 THEN
          activity_name = "Equipment"
        ELSE
          activity_name = "Workspace"
        END IF

        DISPLAY "Enter total of the expenses."
        INPUT total
        WHILE total < 0
            DISPLAY "Invalid. Please enter a value >= 0:"
            INPUT total
        END WHILE

        total_expense = total_expense + total
        DISPLAY "Successfully added ", total, " Expenses to the budget tracker."

       ELSE IF main_choice == 3 THEN
            finacial_summary = total_income - total_expense
            DISPLAY "=========================================="
            DISPLAY "FINANCIAL SUMMARY"             
            DISPLAY "=========================================="
            DISPLAY "Total Income:", total_income
            DISPLAY "Total Expenses:", total_expense
            DISPLAY "Total Summary:", finacial_summary
            IF total_active >= 0 THEN
                DISPLAY "Status: Net Positive! Congratulations."
            ELSE IF total_active > 0 THEN
                DISPLAY "Status: You spent more than you gained... Keep an eye on it next time!"
            ELSE
                DISPLAY "Status: literally nothing logged what did you expect?"
            END IF
            DISPLAY "=========================================="
        ELSE IF main_choice == 4
            DISPLAY "Thank you for using the budget tracker, Keep an eye out on it!"
            BREAK
        END IF
    END WHILE
END MODULE


    ```
