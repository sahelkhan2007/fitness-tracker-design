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
