# CSV Data and Pandas Library (Updated on 1/2/2024)

**Exercise: Map Game**

1. Create a screen, set the background photo to the map of China.
2. Let users enter the name of the province.
3. Once the users enter the name and hit the "ok" button, if it's actually exists, add the name to the map.
4. Show the numbers of the correct names that the users entered.
5. Set a secret word "Exit" to end the game.
6. When the game is end, collect the provinces that are not answered right and print them.

**What will be made in the end:**

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/4bcce553-ecde-474a-8200-df6a0fcb26d9">
</div>

[Python Daily Practice -- Map Game (Click to watch the video)](https://youtu.be/pAmmX2WsfeE)

_Note: I tried serval ways to move the input window to the upper left corner, but it still in the middle of the Turtle screen, I will leave this issue for now :(._

**Collapse the exercise into small blocks:**

1. Download an empty map from the internet.
2. Create a Turtle screen and set the map picture as the background.
3. Get the x and y cordinations of provinces on the screen.
4. Let users enter the name, one name at one time.
5. Check if the name in the name data file, if it is, show the corresponding position on the map by creating a turtle to draw the name, and add one score to the total score.
6. When the game is end, check which provinces are answered right, using for loop add the provinces which are not answered in a missing list.

**The code is:**

1. Get the cordinations of all provinces:
```py
# Get the cordinations of all provinces:
from turtle import Turtle, Screen
## Create a screen and set the bg to an empty map
screen = Screen()
screen.setup(width=900, height=800)
screen.title("Map Game")
screen.bgpic("blank_map.png")


## Get the cordinations of the provinces by click the position on the map
def get_cor_on_click(x, y):
    print(x, y)


screen.onscreenclick(get_cor_on_click)
screen.mainloop()

## Convert the positions of provinces into CSV file.
import pandas

data_dict = {
    "Province": ["Xinjiang",
                 "Xizang",
                 "Qinghai",
                 "Gansu",
                 "Sichuan",
                 "Yunnan",
                 "Inner Mongolia",
                 "Ningxia",
                 "Shanxi",
                 "Chongqing",
                 "Guizhou",
                 "Guangxi",
                 "Hainan",
                 "Guangdong",
                 "Hongkong",
                 "Macao",
                 "Hunan",
                 "Hubei",
                 "Henan",
                 "Shanxi",
                 "Hebei",
                 "Beijing",
                 "Tianjin",
                 "Shandong",
                 "Jiangsu",
                 "Shanghai",
                 "Anhui",
                 "Zhejiang",
                 "Jiangxi",
                 "Fujian",
                 "Taiwan",
                 "Liaoning",
                 "Jilin",
                 "Heilongjiang"
                 ],
    "Position": [
        (-196, 121),
        (-190, -52),
        (-92, 14),
        (-84, 82),
        (-15, -73),
        (-41, -180),
        (68, 93),
        (26, 28),
        (64, -12),
        (42, -97),
        (30, -148),
        (48, -191),
        (74, -265),
        (124, -196),
        (134, -218),
        (114, -226),
        (98, -131),
        (105, -79),
        (117, -30),
        (96, 31),
        (135, 45),
        (142, 97),
        (151, 73),
        (165, 19),
        (190, -26),
        (217, -66),
        (163, -57),
        (204, -97),
        (152, -127),
        (183, -151),
        (227, -181),
        (211, 113),
        (243, 152),
        (261, 213)
    ]
}

province_data = pandas.DataFrame(data_dict)
province_data.to_csv("province_data.csv")
```

2. The main code:
 ```py
import turtle
from turtle import Screen, Turtle
import pandas


# Read the province data file
provinces_data = pandas.read_csv("province_data.csv")
all_provinces = provinces_data.province.to_list()
# Create the screen of the game
map_screen = Screen()
map_screen.setup(width=900, height=800)
map_screen.title("Map Game")
map_screen.bgpic("blank_map.png")


right_answer = []
while len(right_answer) < 34:
    # Create an input board
    answer_input = map_screen.textinput(title=f"{len(right_answer)}/34 Guess the Provinces", prompt="What's the name of the provinces?").title()
    if answer_input == "Exit":
        # When the game is end, collect the provinces that are not answered right
        missing_provinces = []
        for province in all_provinces:
            if province not in right_answer:
                missing_provinces.append(province)
        print(f"You got {len(right_answer)} name of the provinces right, but still get {len(missing_provinces)} provinces to learn.")
        print(missing_provinces)
        break
    # Check if the answer is in the data file
    if answer_input in all_provinces:
        right_answer.append(answer_input)
        t = Turtle()
        t.hideturtle()
        t.penup()
        draw_province = provinces_data[provinces_data.province == answer_input]
        t.goto(int(draw_province.x), int(draw_province.y))
        t.write(answer_input)

 ```

_**Issues Recorded:**_

_1. The hardest part is how to get the coridnations of all provinces on the turtle screen._  

_Using the build-in function `onscreenclick` in turtle to print the cordinations and collect the data as a CSV file._


   
