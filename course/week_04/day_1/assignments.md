# Week 4 - Day 1

**NOTE:** Follow the instructions carefully and follow coding discipline

**SUBMISSION:**

- Folder `~/cohort_2/submissions/<your_folder>/week_4/day_1/assignments`
- Create a file `firstname_lastname.html` with your first name and last name
- Once you complete the assignment push that file to the online repo


## FSD.W4.1.A

- Complete the file `firstname_lastname.html` so that it looks similar to the link <https://raw.githubusercontent.com/masai-school/full-stack-dev-1908/master/course/week_4/day_1/templates/score_card_games.jpg>
- Functionality
  - By clicking on any number it shows up in the score box joined to any previous numbers already present (Eg: To enter a score of `423` you have to press `4` `2` `3`)
  - Once the button `ENTER` is pressed the score gets compared with the `MIN` and `MAX` boxes, if the current score is less than the `MIN` score it gets updated with the current score, if the current score is greater than the `MAX` score it gets updated with the current score. The `TOTAL` score will gets updated with the sum of all scores
  - The score should also be added to the board on the right side along with the appropriate game number the number starts with `1` (Eg: Game 1)
  - The `SCORE` box will be reset with empty value
  - By clicking the `REMOVE ALL` button all the scores should be removed from the score card and `MIN` `MAX` and `TOTALS` updated accordingly
  - By clicking the `REMOVE ODD` button all the scores with the odd game numbers `Game 1`  `Game 3` and so on should be removed from the score card, the `MIN` `MAX` and `TOTALS` updated accordingly and the new game numbers should be assigned again like `Game 2` will now become `Game 1`
  - By clicking the `REMOVE EVEN` button all the scores with the even game numbers `Game 2`  `Game 4` and so on should be removed from the score card, the `MIN` `MAX` and `TOTALS` updated accordingly and the new game numbers should be assigned again like `Game 3` will now become `Game 2`
  - By clicking the `REMOVE LAST` button the last game score should be removed from the score card, the `MIN` `MAX` and `TOTALS` updated accordingly