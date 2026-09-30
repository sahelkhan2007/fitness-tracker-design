# fitness-tracker-design
fitness tracker psuedocode and flo chart and IPO chart

**Course:** ITP 100 Software Design and Logic  
**Author:** Sahel Khan  
**Deliverable:** Algorithm Design (IPO, Flowhart, Psuedocode)  

## 1. Problem Description & Scope   
**Problem** Students need a command-line interface to track daily cardovasculiar and strength excersise durations, Validate that inputs are realistic, and review their progress weekly tragert of 120 minutes  
**Scope** 
  * Featuers a continouis main loop with 2 hireahical submenus (Cardio and Strength).
  *  Validates menu bounds (reject 0 value outside menu options) and duration inputs (rejects negitive inputs).
  *  Agressive total minutes in memory during execution and outputs a progress summary on demand.
  *  Terminates cleanly when user selects the Exit option.

## 2. IPO Chart (Input - Process - Output) 
| Input | Processing | Output |
|:---|:---|:---|
| `main_choice` (Integer: 1-4)<br>`sub_choice` (Integer: 1-3)<br>`duration` (Real / Integer: >= 0) | 1. Initialize `total_cardio = 0`, `total_strength = 0`.<br>2. Loop main menu until user enters `4`.<br>3. Validate that `main_choice` is between 1 and 4.<br>4. If `1` (Cardio):<br>&emsp;a. Display cardio submenu.<br>&emsp;b. Validate `sub_choice` between 1 and 3.<br>&emsp;c. Prompt for duration; loop until `duration >= 0`.<br>&emsp;d. Match choice to cardio activity.<br>&emsp;e. Add `duration` to `total_cardio`.<br>5. If `2` (Strength):<br>&emsp;a. Display strength submenu.<br>&emsp;b. Validate `sub_choice` between 1 and 3.<br>&emsp;c. Prompt for duration; loop until `duration >= 0`.<br>&emsp;d. Match choice to strength activity.<br>&emsp;e. Add `duration` to `total_strength`.<br>6. If `3` (Summary):<br>&emsp;a. Calculate `total_active = total_cardio + total_strength`.<br>&emsp;b. Compare `total_active` to 120 minutes.<br>7. If `4`, exit the program. | Main menu<br>Cardio menu<br>Strength menu<br>Invalid choice messages<br>Invalid duration messages<br>Workout confirmation message<br>Total cardio minutes<br>Total strength minutes<br>Total active minutes<br>Goal status message<br>Exit message |  

- - -

 ## 3. Pseudocode

Module Main()

    Module Main()

    DECLARE Real total_income = 0
    DECLARE Real total_expenses = 0
    DECLARE Real net_balance = 0
    DECLARE Integer main_choice = 0
    DECLARE Integer sub_choice = 0
    DECLARE Real amount = 0
    DECLARE String category_name = ""

    DISPLAY "=========================================="
    DISPLAY "         PERSONAL BUDGET TRACKER"
    DISPLAY "=========================================="

    WHILE main_choice != 4

        DISPLAY "--- MAIN MENU ---"
        DISPLAY "1. Log Income"
        DISPLAY "2. Log Expense"
        DISPLAY "3. View Financial Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4):"
        INPUT main_choice

        WHILE main_choice < 1 OR main_choice > 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT main_choice
        END WHILE


        IF main_choice == 1 THEN

            DISPLAY "--- INCOME MENU ---"
            DISPLAY "1. Design"
            DISPLAY "2. Coding"
            DISPLAY "3. User Documentation"
            DISPLAY "Enter income category:"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                SET category_name = "Design"
            ELSE IF sub_choice == 2 THEN
                SET category_name = "Coding"
            ELSE
                SET category_name = "User Documentation"
            END IF

            DISPLAY "Enter income amount ($):"
            INPUT amount

            WHILE amount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT amount
            END WHILE

            SET total_income = total_income + amount

            DISPLAY "Successfully added $ ", amount, " for ", category_name, "."


        ELSE IF main_choice == 2 THEN

            DISPLAY "--- EXPENSE MENU ---"
            DISPLAY "1. Software"
            DISPLAY "2. Equipment"
            DISPLAY "3. Workspace"
            DISPLAY "Enter expense category:"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                SET category_name = "Software"
            ELSE IF sub_choice == 2 THEN
                SET category_name = "Equipment"
            ELSE
                SET category_name = "Workspace"
            END IF

            DISPLAY "Enter expense amount ($):"
            INPUT amount

            WHILE amount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT amount
            END WHILE

            SET total_expenses = total_expenses + amount

            DISPLAY "Successfully added $ ", amount, " for ", category_name, "."


        ELSE IF main_choice == 3 THEN

            SET net_balance = total_income - total_expenses

            DISPLAY "=========================================="
            DISPLAY "          FINANCIAL SUMMARY"
            DISPLAY "=========================================="
            DISPLAY "Total Income:   $", total_income
            DISPLAY "Total Expenses: $", total_expenses
            DISPLAY "Net Balance:    $", net_balance

            IF net_balance > 0 THEN
                DISPLAY "Status: You are profitable this month!"
            ELSE IF net_balance < 0 THEN
                DISPLAY "Status: You had a loss this month!"
            ELSE
                DISPLAY "Status: You broke even this month!"
            END IF

            DISPLAY "=========================================="


        ELSE IF main_choice == 4 THEN

            DISPLAY "Thank you for using Personal Budget Tracker. Goodbye!"
            BREAK

        END IF

    END WHILE

End Module

End Module
