Has the shift from a 4-team playoff format to a 12-team playoff format affected the gap in success between Power 4 schools and non-Power 4 schools in college football from 2015-2025?
September 10, 2026

Problem Definition
    College Football used a 4-team playoff format from 2014 to 2023 for the College Football Playoffs. A 13-member selection committee met to determine the 4 teams that would compete in the College Football Playoffs. They used factors like strength of schedule, game results, and conference championships to select the 4 teams. But in 2024, they decided to move to a 12-team format. This format included an automatic bid for the conference champions in the ACC, Big Ten, Big 12, and SEC, plus the 2 highest ranked teams from other conferences. Historically, few teams outside a Power 4 (ACC, SEC, Big Ten, and Big 12) conference have been selected for the 4-team format. This looks into the gap between Power 4 schools and non-Power 4 schools when it comes to the playoffs as well as the week 16 rankings. I am exploring whether the shift from a 4-team College Football Playoff format to a 12-team format has affected the gap in success between schools in Power 4 conferences and those not in a Power 4 conference. 

Data Description
    This project uses 2 datasets: one showing college football rankings and one showing college football playoff participants. The first dataset looks at the rankings of teams throughout the season from the years 2015-2025. The season variable tells us which year the rankings are from. The season type indicates whether the ranking is from the regular season or the postseason. Week tells us which week of the college football season the ranking is from, as it can change from week to week. Lastly, the poll column indicates which poll the ranking comes from, such as the Coaches Poll or AP Poll. The second dataset covers participants in the College Football Playoffs from 2015-2025. The dataset tells us the team and season year. Committee Rank is the ranking the committee gave each team based on who they think the best teams are, along with their seed, which determines whether they get a home game or a first-round bye. Qualification reason and conference champion indicate whether a team was an automatic qualifier or an at-large bid. The dataset also includes each team's outcome and elimination round. One observation from this dataset is that most teams that appeared were in the SEC and Big Ten conferences, both of which are Power 4 conferences. 

Data Cleaning and Preparation
For data cleaning, I first selected the years I wanted to analyze and created a CSV file. 
url = "https://api.collegefootballdata.com/rankings"
headers = {
    "Authorization": f"Bearer {API_KEY}" #Bearer token for authentication
}
years_to_pull = [2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024, 2025] #Years wanted to pull
all_playoff_data = []

for year in years_to_pull:
    query_params = {"year": year}
    response = requests.get(url, headers=headers, params=query_params)
    if response.status_code == 200:
        data = response.json()
        for team in data:
            team["season_year"] = year
            all_playoff_data.extend(data)
df2 = pd.DataFrame(all_playoff_data)
df2.to_csv("cfp_playoff_rankings.csv", index=False) #Saving data to a csv file

Then I checked for any missing values and checked the type of each variable. 
#Data cleaning and checking for missing values
df2.isnull()
df2.isnull().sum()
season         0
seasonType     0
week           0
polls          0
season_year    0
dtype: int64
#Looking at the data types (str,float,int,bool)
df2.dtypes
season          int64
seasonType        str
week            int64
polls          object
season_year     int64
dtype: object

To define the conferences, I identified the Power 4 and which schools belonged to each conference. 
#Define Conferences
power_4 = ['ACC', 'SEC', 'Big-10', 'Big-12']

school_to_conference = {
    'Miami': 'ACC', 'SMU':'ACC', 'Virgina': 'ACC', 'Duke': 'ACC', 'North Carolina': 'ACC', 'Pittsburgh': 'ACC', 'Syracuse': 'ACC', 
    'Virginia Tech': 'ACC', 'Wake Forest': 'ACC', 'Boston College': 'ACC', 'California': 'ACC', 'Clemson': 'ACC', 'Georgia Tech': 'ACC',
    'Louisville': 'ACC', 'Flordia State': 'ACC', 'Standford': 'ACC', 'NC State': 'ACC', 'Norte Dame': 'ACC', 'Illinois': 'Big-10',
    'Indiana': 'Big-10', 'Iowa': 'Big-10', 'Maryland': 'Big-10', 'Michigan': 'Big-10', 'Michigan State': 'Big-10', 'Minnesota': 'Big-10',
    'Nebraska': 'Big-10', 'Northwestern': 'Big-10','Ohio State': 'Big-10', 'Oregon': 'Big-10', 'Penn State': 'Big-10', 'Purdue': 'Big-10',
    'Rutgers': 'Big-10', 'UCLA': 'Big-10', 'USC': 'Big-10', 'Washington': 'Big-10', 'Wisconsin': 'Big-10', 'Arizona': 'Big-12', 
    'Arizona State': 'Big-12', 'BYU': 'Big-12', 'Cincinnati': 'Big-12', 'Colorado': 'Big-12', 'Houston': 'Big-12', 'Iowa State': 'Big-12', 
    'Kansas': 'Big-12', 'Kansas State': 'Big-12','Texas Tech': 'Big-12', 'UCF': 'Big-12', 'Utah': 'Big-12', 'West Virginia': 'Big-12', 
    'Baylor': 'Big-12', 'Oklahoma State': 'Big-12', 'TCU': 'Big-12', 'Alabama': 'SEC', 'Arkansas': 'SEC', 'Auburn': 'SEC', 'Florida': 'SEC', 
    'Georgia': 'SEC', 'Kentucky': 'SEC', 'LSU': 'SEC', 'Mississippi State': 'SEC', 'Missouri': 'SEC', 'Oklahoma': 'SEC', 'Ole Miss': 'SEC', 
    'South Carolina': 'SEC', 'Tennessee': 'SEC', 'Texas': 'SEC', 'Texas A&M': 'SEC', 'Vanderbilt':'SEC'
}


Visualizations and Insights
    The first thing I looked at was the AP Top 25 rankings by Conference Group for Week 16 leading up to the playoffs. I made a line graph to be able to easily identify any differences between Power 4 schools and Other schools from the years 2015- 2025. 

<img width="1184" height="584" alt="image" src="https://github.com/user-attachments/assets/a5a2d6b4-e0b5-48a2-a4db-97ba51662db9" />


This graph shows that the gap between Power 4 schools and Other schools has always been there. 2019 and 2022 were the closest, with Power 4 schools having 15 teams ranked in the top 25 and non-Power 4 schools having 10. Since the switch from the 4-team to 12-team playoff format, the gap has widened. In 2024 and 2025, Power 4 conferences had 20 schools ranked, while non-Power 4 schools had only 5. 

<img width="1485" height="784" alt="image" src="https://github.com/user-attachments/assets/6f0073bb-0827-4777-8790-92500381c129" />


The next graph breaks down College Football Playoff appearances by Power 4 vs. Other.  The graph shows the clear switch from a 4-team to 12-team format. Before 2024, only 4 non-Power 4 teams total from 2015-2023 made the College Football Playoff. 

<img width="1184" height="584" alt="image" src="https://github.com/user-attachments/assets/c797d6c0-9ca1-4e56-9341-4e2da34aa969" />

The College Football Playoff Team Appearances by Conference shows the breakdown of appearances by specific conference. The SEC and Big Ten have led the way since 2015 in most playoff appearances followed by the ACC and Big 12. The American Athletic, FBS Independents, and Pac-12 have 2 appearances each, and the Mountain-West and Sun Belt have 1. 
<img width="1481" height="684" alt="image" src="https://github.com/user-attachments/assets/6f5fe258-cb3d-482b-a453-a17ef19b1ff0" />

Storytelling and Narrative
