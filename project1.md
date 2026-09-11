
# Has the shift from a 4-team playoff format to a 12-team playoff format affected the gap in success between Power 4 schools and non-Power 4 schools in college football from 2015-2025?
### September 10, 2026

## Problem Definition

 College Football used a 4-team playoff format from 2014 to 2023 for the College Football Playoffs. The original bowl system was seen as controversial so in 2014 the started the 4-team format (Olsen, 2014). A 13-member selection committee met to determine the 4 teams that would compete in the College Football Playoffs. They used factors like strength of schedule, game results, and conference championships to select the 4 teams. But in 2024, they decided to move to a 12-team format. This format included an automatic bid for the conference champions in the ACC, Big Ten, Big 12, and SEC, plus the 2 highest ranked teams from other conferences. Historically, few teams outside a Power 4 (ACC, SEC, Big Ten, and Big 12) conference have been selected for the 4-team format. This looks into the gap between Power 4 schools and non-Power 4 schools when it comes to the playoffs as well as the week 16 rankings. I am exploring whether the shift from a 4-team College Football Playoff format to a 12-team format has affected the gap in success between schools in Power 4 conferences and those not in a Power 4 conference. 

## Data Description

This project uses 2 datasets: one showing college football rankings and one showing college football playoff participants. The first dataset looks at the rankings of teams throughout the season from the years 2015-2025. People have been rating and ranking teams since 1924 (Carlin, 1999). The season variable tells us which year the rankings are from. The season type indicates whether the ranking is from the regular season or the postseason. Week tells us which week of the college football season the ranking is from, as it can change from week to week. Lastly, the poll column indicates which poll the ranking comes from, such as the Coaches Poll or AP Poll. The second dataset covers participants in the College Football Playoffs from 2015-2025. The dataset tells us the team and season year. Committee Rank is the ranking the committee gave each team based on who they think the best teams are, along with their seed, which determines whether they get a home game or a first-round bye. Qualification reason and conference champion indicate whether a team was an automatic qualifier or an at-large bid. The dataset also includes each team's outcome and elimination round. One observation from this dataset is that most teams that appeared were in the SEC and Big Ten conferences, both of which are Power 4 conferences. 

## Data Cleaning and Preparation

For data cleaning, I first selected the years I wanted to analyze and created a CSV file. 
<img width="1214" height="332" alt="Screenshot 2026-09-11 at 5 04 40 PM" src="https://github.com/user-attachments/assets/2453a89d-7dfb-4ccc-9f51-756be460aefa" />


Then I checked for any missing values and checked the type of each variable. 
<img width="415" height="354" alt="Screenshot 2026-09-11 at 5 05 37 PM" src="https://github.com/user-attachments/assets/d07a543f-278e-4368-b1c4-1296cbbce2f1" />

To define the conferences, I identified the Power 4 and which schools belonged to each conference. 
<img width="1214" height="416" alt="Screenshot 2026-09-11 at 5 06 12 PM" src="https://github.com/user-attachments/assets/92f5d003-1ae8-489e-ba92-60dbc20b60d3" />

## Visualizations and Insights

 The first thing I looked at was the AP Top 25 rankings by Conference Group for Week 16 leading up to the playoffs. I made a line graph to be able to easily identify any differences between Power 4 schools and Other schools from the years 2015- 2025. 

<img width="1184" height="584" alt="image" src="https://github.com/user-attachments/assets/a5a2d6b4-e0b5-48a2-a4db-97ba51662db9" />


This graph shows that the gap between Power 4 schools and Other schools has always been there. 2019 and 2022 were the closest, with Power 4 schools having 15 teams ranked in the top 25 and non-Power 4 schools having 10. Since the switch from the 4-team to 12-team playoff format, the gap has widened. In 2024 and 2025, Power 4 conferences had 20 schools ranked, while non-Power 4 schools had only 5. 

<img width="1485" height="784" alt="image" src="https://github.com/user-attachments/assets/6f0073bb-0827-4777-8790-92500381c129" />


The next graph breaks down College Football Playoff appearances by Power 4 vs. Other.  The graph shows the clear switch from a 4-team to 12-team format. Before 2024, only 4 non-Power 4 teams total from 2015-2023 made the College Football Playoff. 

<img width="1184" height="584" alt="image" src="https://github.com/user-attachments/assets/c797d6c0-9ca1-4e56-9341-4e2da34aa969" />

The College Football Playoff Team Appearances by Conference shows the breakdown of appearances by specific conference. The SEC and Big Ten have led the way since 2015 in most playoff appearances followed by the ACC and Big 12. The American Athletic, FBS Independents, and Pac-12 have 2 appearances each, and the Mountain-West and Sun Belt have 1. 
<img width="1481" height="684" alt="image" src="https://github.com/user-attachments/assets/6f5fe258-cb3d-482b-a453-a17ef19b1ff0" />

## Storytelling and Narrative

The visual analysis shows that within the last 10 years, the change from a 4-team playoff format to a 12-team playoff format has slightly affected the gap between Power 4 conferences and Other conferences. We can see that the rankings of the Top 25 teams not in a Power 4 conference have declined since the format change. It would be incorrect to say that there is a big affect since we only have 2 years worth of data for the 12-team format. 

## Limitations, Ethics, and Reflection

When starting this project, I knew there would be limitations and possible bias. The new conference realignment after 2023 is not accounted for, and the data does not show the realignments. Another detail the dataset does not account for is Notre Dame. Notre Dame is an independent football team, meaning they do not belong to a conference. There is always going to be bias when it comes to the selection committee. Because the data relies on selection committees to determine who gets a spot in the College Football Playoffs, it is biased with many voters favoring teams located in their home state (Coleman, 2010).  With the 12-team playoff format being only 2 years old, it really limits our ability to see patterns over time. Next time, I would explore committee rankings and try to go back even further. I would want to see whether there has always been a gap between the number of Power 4 schools that received a playoff spot and the number of non-Power 4 schools. 

## Code and Transparency

## References:

https://api.collegefootballdata.com/playoffs/cfp/participants

https://api.collegefootballdata.com/rankings

https://theacc.com/

https://bigten.org/

https://big12sports.com/

https://www.secsports.com/

Jupyter Notebook: [Studio2project1final.html](https://github.com/user-attachments/files/32131134/Studio2project1final.html)

AI DISCLAIMER: For this project, I used Copilot to assist in creating the visuals. 

## Sources:

Carlin, B. P., & Stern, H. S. (1999). Designing a college football playoff system. Chance, 12(3), 21-26.

Coleman, B. J., Gallo, A., Mason, P. M., & Steagall, J. W. (2010). Voter bias in the associated press college football         poll. Journal of Sports Economics, 11(4), 397-417.

Olson, J., & Stone, D. F. (2014). Suspense-optimal college football play-offs. Journal of Sports Economics, 15(5), 519-540.
