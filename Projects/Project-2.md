![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/c44cbb64-fa00-4c18-bbe2-5b3db2e728ff)

<sub>Picture from https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.cnet.com%2Fhealth%2Fsleep%2Ftop-8-signs-of-sleep-apnea-and-what-to-do-about-it%2F&psig=AOvVaw01pxsWo-K3jwdEhUMPkGfy&ust=1702626680430000&source=images&cd=vfe&ved=0CAUQjB1qFwoTCLDltuW4joMDFQAAAAAdAAAAABAE </sub>

# Unit 2: A Distributed Weather Station for ISAK

## Criteria A: Planning

## Problem definition

A student at an international boarding school notices that he is quite sensitive to the temperature of his room while he sleeps. If it's too hot, he can not sleep, but if it's too cold, he falls ill. Although the student believes that opening the window affects the temperature strongly (due to his school being at a high altitude), his roommates do not believe him, so he wants the data to prove them wrong. He has asked for the humidity data as well, just in case there might be a correlation. He is also worried about losing his data as his computer is prone to crashing, therefore he wants a backup. He has left it up to the discretion of the developer to choose a solution for his backup problem.

## Proposed Solution
Considering the client requirements an adequate solution includes a low cost sensing device for humidity and temperature and a custom data script that process and anaysis the samples acquired. For a low cost sensing device an adequate alternative is the DHT11 sensor[^1] which is offered online for less than 5 USD and provides adequare precision and range for the client requirements (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as the DHT22, AHT20 or the AM2301B [^2] have higher specifications, however the DHT11 uses a simple serial communication (SPI) rather than more eleborated protocols such as the I2C used by the alternatives. For the range, precision and accuracy required in this applicaiton the DHT11 provides the best compromise. Connecting the DHT11 sensor to a computer requires a device that provides a Serial Port communication. A cheap and often used alternative for prototyping is the Arduino UNO microcontroller [^3]. "Arduino is an open-source electronics platform based on easy-to-use hardware and software"[^4]. In additon to the low cost of the Arduino (< 6USD), this devide is programable and expandable[^1]. Other alternatives include diffeerent versions of the original Arduino but their size and price make them a less adequate solution.

Considering the budgetary constrains of the client and the hardware requirements, the software tool that I proposed for this solution is Python. Python's open-source nature and platform independence contribute to the long-term viability of the system. The use of Python simplifies potential future enhancements or modifications, allowing for seamless scalability without the need for extensive redevelopment [^5][^6]. In comparison to the alternative C or C++, which share similar features, Python is a High level programming language (HLL) with high abstraction [^7]. For example, memory management is automatic in Python whereas it is responsability of the C/C++ developer to allocate and free up memory [^7], this could result in faster applications but also memory problems. In addition a HLL language will allow me and future developers extend the solution or solve issues proptly.  

**Design statement**

I will design a program capable of generating different graphs based off of information collected through Arduino DH11s sensors and API requesting. This will be about measuring humidity and temperature, and the code will developed in the virtual environment PyCharm using Python version 3.10.11, and the Arduino IDE. It will take 3 weeks to develop

## Success Criteria

[^1]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS, https://www.adafruit.com/product/386. 
[^2]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^3]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^4]:Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.  
[^5]:Tino. “Tino/PyFirmata: Python Interface for the Firmata (Http://Firmata.org/) Protocol. It Is Compliant with Firmata 2.1. Any Help with Updating to 2.2 Is Welcome. the Capability Query Is Implemented, but the Pin State Query Feature Not Yet.” GitHub, https://github.com/tino/pyFirmata. 
[^6]:Python Geeks. “Advantages of Python: Disadvantages of Python.” Python Geeks, 26 June 2021, https://pythongeeks.org/advantages-disadvantages-of-python/. 
[^7]: Real Python. “Python vs C++: Selecting the Right Tool for the Job.” Real Python, Real Python, 19 June 2021, https://realpython.com/python-vs-cpp/#memory-management. 

1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours. 
1. ```[HL]``` The local variables will be measure using a set of 3 sensors around the dormitory.
2. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)```
3. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
4. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server as a backup.
5. The solution provides a prediction for the subsequent 12 hours for both temperature and humidity.
6. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.

_TOK Connection: To what extent does ```the use of data science``` in climate research influence our understanding of environmental issues, and what knowledge questions arise regarding the ```reliability, interpretation, and ethical implications``` of data-driven approaches in addressing climate change_

1. How does our use of technology shape our understanding of the environment
2. What responsibilities do we have as technologists when it comes to handling personal data related to our living spaces?
3. What cultural and contextual factors might impact our interpretation of the results, especially when comparing our local readings with those from the campus? 

# Criteria B: Design

## System Diagram **HL**

![HL](https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/4891d5e9-b8ab-46ed-bd75-b606e25e3383)

<sub>**Fig. 1** shows the system diagram for the proposed solution (**HL**). The indoor variables will be measured using an Arduino and three DHT11 sensors located inside a room. Three sensors are used to determine more precisely the physical values and include measurement uncertainty. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.153/readings```. The local values are stored in a CSV database locally and a backup copy will be store in the remote server using the **Weather API**.</sub>


## Record of Tasks
| **Task No** |            **Planned Action**            |                                                                                                                                                                 **Planned Outcome**                                                                                                                                                                 | **Time Estimate** | **Target Completion Date** | **Criterion** |
|:-----------:|:----------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|-------------------|----------------------------|---------------|
|      1      | Write the problem defintion              | The problem definition concerning what the client is looking for, and why they need temperature and humidity measurements, and why they need them uploaded to the cloud.                                                                                                                                                                            | 10 min            | November 29                | A             |
|      2      | Write the design statement               | This design statement will show the plan of the developer when it comes to their goals and how they intend on achieving them                                                                                                                                                                                                                        | 10 min            | November 29                | A             |
|      3      | Set up DH11s and Arduino system in room  | Gain a range of different measurements in the environment of the room. One DH11 will be placed on desk, one will be placed above bed, and one will be placed near the window. Ribbon wires will be used to connect over long distances, while jumper cables, a breadboard, and an Arduino connected to a laptop will be used to control the system. | 3 hours           | November 30                | C             |
|      4      | Write code for DH11 control              | Edited code in Arduino control panel, as well as python code that saves values collected over time in a list as y values. These will be used to make graphs later on in the project.                                                                                                                                                                | 3 hours           | November 30                | C             |
|      5      | Collect data and upload to csv and cloud | The arduino will collect data every 5 minutes, save it to a csv file in the local database and upload it to the cloud. In case the computer crashes, there will be two backups: the csv file and the cloud in a worst case scenario.                                                                                                                | 7 hours           | December 10                | C             |
|      6      | Data pre-processing                      | Take the mean of every 5 values on the y-axis and find their mean, making graphs more readable, create a quadratic best fit to show average                                                                                                                                                                                                         | 30 min            | December 12                | C             |
|      7      | Create predictive model                  | Use numpy polyfit to create a 4th degree polynomial that returns five values (a, b, c, d, e) that can be used to create a nice looking function to accompany graphs                                                                                                                                                                                 | 30 min            | December 13                | C             |
|      8      | Use predictive model                     | Use created function to predict potential temperature changes 12 hours into the future and add it to a graph with existing data                                                                                                                                                                                                                     | 30 min            | December 13                | C             |
|      9      | Fetch data from API                      | Use requests functions to retrieve data from outdoor sensors                                                                                                                                                                                                                                                                                        | 1 hour            | December 13                | C             |
|      10     | Sort through broken sensors              | Create graphs for every sensor to make sure none are broken. This revealed sensors 3 and 6 are broken.                                                                                                                                                                                                                                              | 2 hours           | December 13                | B             |
|      11     | Create flowcharts                        | One complex for api and csv upload, one medium for getting data from outoor sensors through api, and one for developping 4th degree polynomial graphing values                                                                                                                                                                                      | 2 hour            | December 13                | B             |
|      12     | Alpha Testing                            | Functionality testing to make sure graphs correspond to value lists, that mean data is not taking in broken sensors, and that all data possible is represented without leaving out vital information                                                                                                                                                | 1 hour            | December 14                | C             |
|      13     | Code Humidity composite graphs           | Includes smaller dimension sensors to represent broken and functioning sensors, and a bigger box to represent average humidity excluding broken sensor                                                                                                                                                                                              | 1 hour            | December 14                | C             |
|      14     | Code Temperature composite graphs        | Includes smaller dimension sensors to represent broken and functioning sensors, and a bigger one to show average temperature excluding the broken sensor 3                                                                                                                                                                                          | 30 min            | December 14                | C             |
|      15     | Research for poster and healthy levels   | Look at reliable sources such as the world health organization to suggest to client what levels of humidity and temperature are optimal for their room to be at while they sleep                                                                                                                                                                    | 30 min            | December 14                | D             |
|      16     | Beta testing                             | Ask people with no matplotlib expereince what they can make of the graphs to check legibility                                                                                                                                                                                                                                                       | 30 min            | December 14                | B             |
|      17     | Beta polishing                           | Using collected feedback from tester, make data more legible. This involves increasing space between graphs and adding legends and titles                                                                                                                                                                                                           | 2 hours           | December 14                | C             |
|      18     | Design Poster                            | Create *scientifc* poster which maximizes information over design, making sure to include all different kinds of citations and conclusions                                                                                                                                                                                                          | 2 hours           | December 14                | D             |
|      19     | Record Video                             | Record a video going over poster and explaining different parts of it, as well as different parts of code that are important                                                                                                                                                                                                                        | 7 min             | December 14                | D             |
|      20     | Compile GitHub Documentation             | Arrange GitHub documentation from criterion A to D, to make sure all is orderly for submission. Upload pictures, videos, and poster through google drive document.                                                                                                                                                                                  | 30 min            | December 14                | D             |
## Flow Diagrams

### Prediction Model (Simple)
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/1445264d-7fd5-4794-8259-2f10d443a267)
<sub>**Fig. 1** shows the flowchart for the prediction model</sub>
### Get data from API (Medium)
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/98abe180-5f48-472b-9508-21397c4bc342)
<sub>**Fig. 2** shows the flowchart for the API retrieval code</sub>
### API upload (Complex)
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/4484d981-bc54-4360-9bdf-2f9134e81e6e)
<sub>**Fig. 3** shows the flowachart for the API upload system</sub>

## Test Plan
| **Test No** |                                **Type Of Test**                               | **Date** |                                                                **Procedure**                                                                |                                                **Expected Outcome**                                                |
|:-----------:|:-----------------------------------------------------------------------------:|:--------:|:-------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------:|
|      1      | Functional Test: Data collected by DH11s is similar to thermometer hygrometer | Dec 11   | Hold the thermometer/hygrometer near the DH11s for 5 minutes                                                                                | Comparing data should confirm whether the data collected is accurate                                               |
|      2      | Functional Test: Polyfit Graphs are represented properly by matplotlib        | Dec 11   | Copy the values extracted by numpy into desmos graphing calculator and compare similarities between that and what was graphed by Matplotlib | This will show whether the graphing within the expected list of values is correct                                  |
|      3      | Functional Test: Check if backup uploaded to API works                        | Dec 12   | Call on API to retrieve data and compare it with the CSV values                                                                             | Check if any data is being lost in the process of uploading and if all the uploads are succeful                    |
|      4      | Non-functional Test: Test Legibility                                          | Dec 13   | Show graphs to non-computer science students and receive their feedback on the legibility of the graph                                      | Add legends and titles corresponding to their feedback                                                             |
|      5      | Non-functional Test: Test Legibility 2                                        | Dec 13   | See if comparison between the values of outdoor and indoor temperature is legible                                                           | Change color of plots and extend gridspec figure setting accordingly                                               |
|      6      | Non-functional Test: Poster Design                                            | Dec 13   | Ask user to write small bullet point list of all the information they can conclude from the poster                                          | Maximize information added through changing fonts and replacing useless pictures with more graphs and explanations |
# Criteria C: Development

## List of techniques used

### Existing Tools
- If Statements
- For Loops
- While Loops
- Arduino DH11 Libraries
- CSV Files
- Pycharm
- Weather API
- Arduino UNO
- Numpy library

### Techinques Used
- Matplotlib plotting
- Gridspec subplotting
- Serial Arduino UNO data collection
- CSV Reading and Appending
- API requests, login, and uploading
- Splitting dictionaries to unpack API station measurements
- Smoothing graphs
- Using numpy polyfit to create predictive models
  
## Functions
### CSV and API Upload
```.py
'''
Saves data in csv and uploads to api
:returns: Full data in both api and csv in 48 hours
'''
sensor_ids = [65, 62, 66, 63, 67, 64] # top hum65, top temp 62, mid hum66, mid temp63, bot hum67, bot temp64,
stopwatch = 0 # in minutes
while stopwatch < 2880: # minute cap
    time.sleep(0.1)
    value = read()
    msg = value.decode('utf-8') # remove the extra characters created by arduino
    stripped_msg = msg.strip()
    save = f"{stripped_msg}" #datetime, hum top, temp top, hum mid, temp mid, hum bot, temp bot
    if stripped_msg == 'Hello Amine! Arduino has started':
        pass
    else: # Upload to CSV
        with open("data.csv", mode='a') as f:
            f.writelines(f"{datetime.isoformat(datetime.now())},{save}\n")
        # Upload to API
        api_save = save.split(',') # creating list to make it easier to work with
        print(api_save)
        print(datetime.isoformat(datetime.now()))
        for i in range(6): # 3 sensors, each take in 1 humidity value and 1 temperature value
            new_record = { # lists arranged in order so that certain humidity aligns with correct sensor
                'datetime': datetime.isoformat(datetime.now()),
                'value': float(api_save[i]),
                'sensor_id': int(sensor_ids[i]),
            }
            r=requests.post(f'http://{ip}/reading/new', json=new_record, headers=header) # where to save, what to save, header grants access
            print(r.json()) # check
        time.sleep(299.8) # in seconds
    stopwatch += 5 # adding minutes
```
This code includes four different functionalities. First is splitting and stripping data to turn it into manageable bits that correspond to the format required. Second is the stopwatch which has time added to it every loop so that the while loop stops once it reaches 48 hours. Third is the CSV upload, where the file is opened in append mode and the data is sent to it. The last is the API upload, where the API is accessed, and inorder to efficiently upload to all sensors at once, a for loop is used to align every sensor id with the correct value type.

### Creating Sensors
```.py
'''
Creates ids in API server
:results: 6 sensors, 3 humidity and 3 temperature
'''
ip = "192.168.6.153"
username = 'amine_project2_tryagain'
password = input('please enter your password') # for extra security
request = requests.post(f'http://{ip}/register',json={'username':username, 'password':password})
answer = request.json() # logging into the server
# login into the server
request = requests.post(f'http://{ip}/login', json={'username':username, 'password':password})
token = request.json()["access_token"]
header = {"Authorization":f"Bearer {token}"} # the access token will validate all future uploads, it is important
# create sensor
locations = ['bed','desk','windowsill'] # locations where DH11s are posted
for i in range(1,4): # for loop for efficiency, then creating values
    new_temp = {"type":f"Temperature_{locations[i-1]}","location":f"{locations[i - 1]}","name":f"amine_measures_{locations[i-1]}","unit":"C"}
    new_hum = {"type": f"Humidity_{locations[i - 1]}","location": f"{locations[i - 1]}","name": f"amine_measures_hum_{locations[i-1]}","unit": "%"}
    temp_req = requests.post(f'http://{ip}/sensor/new', json=new_temp, headers=header) # where to upload, what to upload, header for login
    hum_req = requests.post(f'http://{ip}/sensor/new', json=new_hum, headers=header)
````
This function logs into the API server, sets a password for secuirty, then saves an access token that is used in every following API upload request. It then uses a for loop along with list indexing to create 6 sensors as efficiently as possible. First it makes three for temperature, then three for humidity. Computational thinking is shown through the efficiency of the system and good variable names.

### Polynomial Prediction and Subplot Graphing
```.py
'''
This function creates polyfit models that predict the temperature and humidity of the outdoors
:returns: a graph with actual data and additional 25 points of prediction
'''
a_temp, b_temp, c_temp, d_temp, e_temp = np.polyfit(range(len(mean_temp_out)), mean_temp_out, 4)
a_hum, b_hum, c_hum, d_hum, e_hum = np.polyfit(range(len(mean_hum_out)), mean_hum_out, 4)
# 4th degree polynomial (quartic) created for mean humidity and temperature
temp_pred = []
hum_pred = []
for i in range(len(x)+25): # additional 25 points are those predicted
    temp_pred.append((a_temp*(i**4))+ (b_temp*(i**3)) + (c_temp*(i**2)) + (d_temp*i) + e_temp)
    hum_pred.append((a_hum*(i**4)) + (b_hum*(i**3)) + (c_hum*(i**2)) + (d_hum*i) + e_hum)
fig = plt.figure(figsize= (10, 8))
grid = GridSpec(3, 6, fig) # 3 rows, 6 columns
plt.subplots_adjust(wspace=2.5, hspace=1)

box2 = fig.add_subplot(grid[0:3, 0:3]) # design choices
plt.plot(x, mean_temp_out, color='red')
plt.plot(x_predict, temp_pred, color='purple', label= 'Predictive Model')
plt.title("Mean Outside Temp + Prediction", fontsize=15)
plt.xticks([61, 349],['Dec 12','Dec 13'], fontsize=15)
plt.yticks(fontsize=15)
plt.xlabel("Time (days)", fontsize= 15)
plt.ylabel("Temperature (C)", fontsize=15)
plt.legend()
plt.show()
```
This function uses the numpy library to take existing data values retrieved from the API sensors and create a 4th degree polynomial function based off of their behavior. This allows the prediction of future values, which involves runnig values through the polyfit equation and then graphing using matplotlib with title, ticks, and labels font adjusted. It also creates a legend to increase legibility.

### Arduino IDE
```.cpp
//Sets up data collection :returns: ready arduino//
#define DHTPIN_T 12 # create dht pins based on their arduino board plugin
#define DHTPIN_M 13
#define DHTPIN_B 11
#define DHTTYPE DHT11
# Show their type
DHT dhttop(DHTPIN_T, DHTTYPE);
DHT dhtmid(DHTPIN_M, DHTTYPE);
DHT dhtbot(DHTPIN_B, DHTTYPE);
void setup() {
  pinMode(5, OUTPUT); # Postive pin set to high to create closed circuit
  digitalWrite(5, HIGH);
  Serial.begin(9600); # wait a second for boot up
  Serial.println(F("Hello Amine! Arduino has started")); # in case code doesn't work, this will not appear
  dhttop.begin(); # begin collecting data
  dhtmid.begin();
  dhtbot.begin();
```
This code shows the transferibility of computational thinking in higher level coding. Although a different language from python altogether, it is still comprehensible because it functions in a similar way. Begin with defining pins so that the computer knows where to look, then show their type. Do not begin instantly to avoid shortcircuiting risk, and add a string introduction as a check for code working.

## Graphs and Data Analysis

### Comparison Data
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/fafef9e3-e894-48f1-a799-148e7663a059)
<sub>**Fig. 4** shows the graph comparing outdoor and indoor mean temperatures, blue is outdoor and yellow is indoor</sub>
From this graph we can conclude a couple things:
- The maximum and minimum points of the outdoor temperature are much higher and lower respectively than those of the indoor temperature
- Fluxes in each graph do not correspond to the other, showing they do not correlate and thefore have not affected each other
- This indicates that the inhabitants of the room did not open the window at any point over the 48 horus of measuring data

### Predictions
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/c75c0d91-a189-454d-ab34-2598debed180)
<sub>**Fig. 5** shows teh existing data from the API sensors and the predicitve model labeled in purple</sub>

The purple preditive model, a quartic equation, shows that the trend of the temperature is to keep going down to 13C till December 14th and the humidity to keep rising till approx. 65% on Decmeber 14th. This is in line with the movemnt of the data up to till that point, but it does not show any evidence of going back up or down at any point. This could show a weakness in the method of prediction, as it does not account for the natural day cycle

### Composite Graph: Outdoor Temperature
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/c47eb590-4fb7-4e37-8360-36945df5ea86)
<sub>**Fig. 6** shows composite graph including average of outdoor temperatures and smaller representations of individula sensors</sub>

This composite graph shows important factoids:
- It shows the mean temperature of the outdoors, with minimums at 15 degrees and maximums at approx. 38 degrees. This gives the reader and good idea of what's going on outside throughout the day.
- It shows why sensor 3 wasn't included: it is clearly broken
- Shows other sensors for additional infomration

### Smoothed & Fitted Mean Indoor Temperature & Humidity
![image](https://github.com/Amine-Itani/Unit-2/assets/123438294/0ff3de3d-8a4d-46e4-ae46-6c52a7bf45e2)
<sub>**Fig. 7** shows smoothed indoor temperature averages and a fitted quadratic equation to make it a little more legible</sub>

This graph shows the average indoor temperatures and humidity levels, but it is made smooth to make it more legibile. This is done through taking every 5 points and finding their mean, and using that as the y values. A quadratic model is also added for additional legibility. This data can help give the reader a better idea of what the humidity level is usually like in this room, if they want to be able to pinpoint it to one value. That would be 19.5 degrees for temperature and 44% for humidity.
# Criteria D: Functionality
https://drive.google.com/drive/folders/1aM5ZuzC7h_fGhEh3PfTZVkJHlK-noTXV?usp=sharing 

A 7 min video demonstrating the proposed solution with narration
A poster with all infomration compiled and presented neatly

