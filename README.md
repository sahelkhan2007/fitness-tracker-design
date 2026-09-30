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

    DECLARE Integer total_cardio = 0
    DECLARE Integer total_strength = 0
    DECLARE Integer total_active = 0
    DECLARE Integer main_choice = 0
    DECLARE Integer sub_choice = 0
    DECLARE Integer duration = 0
    DECLARE String activity_name = ""

    DISPLAY "=========================================="
    DISPLAY "         PERSONAL FITNESS TRACKER"
    DISPLAY "=========================================="

    WHILE main_choice != 4

        DISPLAY "--- MAIN MENU ---"
        DISPLAY "1. Log Cardio"
        DISPLAY "2. Log Strength"
        DISPLAY "3. View Activity Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4):"
        INPUT main_choice

        WHILE main_choice < 1 OR main_choice > 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT main_choice
        END WHILE


        IF main_choice == 1 THEN

            DISPLAY "--- CARDIO MENU ---"
            DISPLAY "1. Running"
            DISPLAY "2. Walking"
            DISPLAY "3. Cycling"
            DISPLAY "Enter cardio activity:"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                SET activity_name = "Running"
            ELSE IF sub_choice == 2 THEN
                SET activity_name = "Walking"
            ELSE
                SET activity_name = "Cycling"
            END IF

            DISPLAY "Enter workout duration in minutes:"
            INPUT duration

            WHILE duration < 0
                DISPLAY "Invalid. Please enter duration >= 0:"
                INPUT duration
            END WHILE

            SET total_cardio = total_cardio + duration

            DISPLAY "Successfully added ", duration, " minutes for ", activity_name, "."


        ELSE IF main_choice == 2 THEN

            DISPLAY "--- STRENGTH MENU ---"
            DISPLAY "1. Upper Body"
            DISPLAY "2. Lower Body"
            DISPLAY "3. Full Body"
            DISPLAY "Enter strength activity:"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                SET activity_name = "Upper Body"
            ELSE IF sub_choice == 2 THEN
                SET activity_name = "Lower Body"
            ELSE
                SET activity_name = "Full Body"
            END IF

            DISPLAY "Enter workout duration in minutes:"
            INPUT duration

            WHILE duration < 0
                DISPLAY "Invalid. Please enter duration >= 0:"
                INPUT duration
            END WHILE

            SET total_strength = total_strength + duration

            DISPLAY "Successfully added ", duration, " minutes for ", activity_name, "."


        ELSE IF main_choice == 3 THEN

            SET total_active = total_cardio + total_strength

            DISPLAY "=========================================="
            DISPLAY "          ACTIVITY SUMMARY"
            DISPLAY "=========================================="
            DISPLAY "Total Cardio Minutes:   ", total_cardio
            DISPLAY "Total Strength Minutes: ", total_strength
            DISPLAY "Total Active Minutes:   ", total_active

            IF total_active >= 120 THEN
                DISPLAY "Status: You reached your weekly goal!"
            ELSE
                DISPLAY "Status: You need ", 120 - total_active, " more minutes to reach your weekly goal."
            END IF

            DISPLAY "=========================================="


        ELSE IF main_choice == 4 THEN

            DISPLAY "Thank you for using Campus Fitness Tracker. Stay Active!"
            BREAK

        END IF

    END WHILE

End Module
