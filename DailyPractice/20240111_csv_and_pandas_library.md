# CSV Data and Pandas Library (Updating)

**Exercise: Map Game**

1. Create a screen, set the background photo to the map of China.
2. Let users enter the name of the province.
3. Once the users enter the name and hit the "ok" button, if it's actually exists, add the name to the map.
4. Show the numbers of the correct names that the users entered.

**What will be made in the end:**



**Collapse the exercise into small blocks:**

1. Download an empty map from the internet.
2. Create a Turtle screen and set the map picture as the background.
3. Get the x and y cordinations of provinces on the screen.
4. Let users enter the name, one name at one time.
5. Check if the name in the name data file, if it is, show the corresponding position on the map and add one score to the total score.

**The code is:**
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

_**Issues Recorded:**_

_1. The hardest part is how to get the coridnations of all provinces on the turtle screen._  

_Using the build-in function `onscreenclick` in turtle to print the cordinations and collect the data as a CSV file._


   
