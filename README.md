# personal-project-
import pwinput
from tkinter import *
from datetime import date
import matplotlib.pyplot as plt import matplotlib.image as mpimg import random
import smtplib
import sys
from tabulate import tabulate import pandas as pd
import requests,json
import pandas as pa
import subprocess
import webbrowser
from PIL import Image
import mysql.connector as mc mycon=mc.connect(host="localhost",user="root",passwd="root@12 3",database="project")
if mycon.is_connected():
print("Connected") mycursor=mycon.cursor()
greetings=['hi','hello','bonjour','hi there','namaste' ,'hey','wassup']
responsegree=['hiiiii','helooo','hii,Nice to meet you' ,'heyy']
responsebot=['I am a computer program that simulates human conversation through voice commands or text chats or both'
,'I am not a robot nor a human, but I can be considered the mind of a robot xD']
m=input("Bot-->Did you create an account before y/n?") if m=="n":
print("Bot-->Enter your username of your choice:") u=input()
print("Bot-->Enter password of your choice") p=int(input())
aa="insert into projusers(login_username,password) values('%s',%s)"%(u,p)
mycursor.execute(aa) mycon.commit() m="y"
b="select * from projusers" mycursor.execute(b) o=mycursor.fetchall() d=dict(o)
print(d)
if m=="y" or m=="Y":
print("BOT-->Enter login_username:") a=input()
print("BOT-->Enter your passwd")
c=int(input()) if a not in d:
print("Unknown username check and try again later") elif d[a]==c:
print("BOT-->Succesful Login Welcome",a) print("BOT-->Please Choose an option to continue") print("OPTIONS")
print("1.Talk with the bot")
print("2.Lunch Menu") print("3.Timetable")
print("4.Date")
print("5.School Timings") print("6.Latest News")
print("7.Basic Admission info") print("8.Weather of city of ur choice") print("9.Opening important websites") print('10.Calculator')
print('11.Timings of school')
print('12.Cut off marks for science and commerce stream') print('13.Admission fees')
print("14.System Calculator")
print("15.Holidays")
print("16.Teacher names based on subject") print("17.Competition dates")
print("18.Emails")
print("19.EXIT")
while True:
print("BOT-->Enter choice") e=int(input())
if e==1:
while True: a=input("User-->") if a in greetings:
print("BOT-->",random.choice(responsegree)) if "human" in a or "robot" in a:
print("Bot-->",random.choice(responsebot)) if "name" in a:
print("Bot-->My name is bvs chatbot :)") if "age" in a:
print("Bot-->I can live forever haha") if "date" in a:
today=date.today()
print("Bot-->Today's date is:",today) if "save data" in a:
print("Bot-->No!!!,your data other than your username,password is saved,the convos will be deleted :)")
if "leave talk" in a: break
if e==2:
print("Bot-->The Lunch Menu is:") img=mpimg.imread('lunch.png') imgplot=plt.imshow(img) plt.show()
if e==3:
print("Bot-->Which grade's timetable are you looking for") t=input()
if t=="12A" or t=="12a" or t=="12B" or t=="12b":
img=mpimg.imread('timetable.png') imgplot=plt.imshow(img)
plt.show()
if e==4:
print("Bot-->Today's date is") today=date.today() print(today)
if e==5:
print("Bot-->The School office timings are from 8:00AM
TO 4:30PM")
print("BOT-->The School office timings are from 8:30AM
to 3:50PM")
if e==6:
webbrowser.open("https://news.google.com/topstories?",new=1)
if e==7:
print("Confirm Interest - Walk into the school on the third
Monday of February (Falling on 14th February 2022 next year*) to reconfirm your registration.")
print("Fill online - After you confirm interest in person on this day, an application form link will be sent to the registered email id provided by you along with instructions to apply.")
reg=input("Register - Would you like to register now- y/n?")
if reg=="y" or reg=="Y": webbrowser.open("https://www.babajividhyashram.org/registration/" ,new=1)
if e==8:
ak="9859cb456223eaa7fccd42c2923a52fc" url="http://api.openweathermap.org/data/2.5/weather?" city_name=input("Enter city name : ") full_url=url+"appid="+ak+"&q="+city_name response=requests.get(full_url)
x=response.json()
if x["cod"]=="404":
print("City Not Found") else:
y=x["main"]
current_temperature=y["temp"] current_pressure=y["pressure"] current_humidity=y["humidity"] weather_description=x["weather"][0]["description"] wind_speed=x["wind"]["speed"] print("----------------------------------------")
print(" Temperature (in kelvin
unit)="+str(current_temperature)+"\n atmospheric pressure(in hPa unit)="+str(current_pressure)
+"\n humidity (in percentage)="+str(current_humidity)+"\n
description="+str(weather_description)
+"\n wind speed="+str(wind_speed))
print("----------------------------------------") if e==9:
print("List of webpages you can open:") print("1.Google classroom") print("2.Gmail")
print("3.Google drive") print("4.Youtube")
print("5.Google docs")
print("6.Google maps")
print("7.Google calender")
print("8.Google forms")
print("9.Google slides") print("10.Myaccount page") op=int(input("Enter the option you want:")) if op==1:
webbrowser.open("https://classroom.google.com/h",new=1) elif op==2:
webbrowser.open("https://mail.google.com/mail/u/0/",new=1) elif op==3:
webbrowser.open("https://drive.google.com/drive/",new=1) elif op==4:
webbrowser.open("https://www.youtube.com/",new=1) elif op==5:
webbrowser.open("https://docs.google.com/document/u/0/",new=1) elif op==6:
webbrowser.open("https://www.google.co.in/maps/",new=1) elif op==7:
webbrowser.open("https://calendar.google.com/calendar/u/0/",new= 1)
elif op==8: webbrowser.open("https://docs.google.com/presentation/u/0/",new= 1)
elif op==9: webbrowser.open("https://docs.google.com/forms/u/0/",new=1)
elif op==10: webbrowser.open("https://myaccount.google.com/
",new=1)
else:
print("Invalid option") if e==10:
ex = ""
def press(num):
global ex ex=ex+ str(num) equation.set(ex)
def equalpress():
try:
global ex
total = str(eval(ex)) equation.set(total) ex = ""
except:
equation.set(" error ") ex= ""
def clear(): global ex
ex= ""
equation.set("")
if __name__ == "__main__":
gui=Tk()
gui.configure(background="black") gui.title("Calculator")
gui.geometry("280x170")
equation = StringVar()
expression_field = Entry(gui, textvariable=equation) expression_field.grid(columnspan=4, ipadx=70)
b_1 = Button(gui, text=' 1 ', bg='white',command=lambda: press(1), b_1.grid(row=2, column=0) b_2 = Button(gui, text=' 2 ', bg='white',command=lambda: press(2), b_2.grid(row=2, column=1) b_3 = Button(gui, text=' 3 ', bg='white',command=lambda: press(3), b_3.grid(row=2, column=2) b_4 = Button(gui, text=' 4 ', bg='white',command=lambda: press(4), b_4.grid(row=3, column=0) b_5 = Button(gui, text=' 5 ', bg='white',command=lambda: press(5), b_5.grid(row=3, column=1) b_6 = Button(gui, text=' 6 ', bg='white',command=lambda: press(6), b_6.grid(row=3, column=2)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
b_7 = Button(gui, text=' 7 ', bg='white',command=lambda: press(7), b_7.grid(row=4, column=0) b_8 = Button(gui, text=' 8 ', bg='white',command=lambda: press(8), b_8.grid(row=4, column=1) b_9 = Button(gui, text=' 9 ', bg='white',command=lambda: press(9), b_9.grid(row=4, column=2) b_0 = Button(gui, text=' 0 ', bg='white',command=lambda: press(0), b_0.grid(row=5, column=0)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
fg='black', height=1, width=7)
plus = Button(gui, text=' + ', fg='black', bg='white',command=lambda: press("+"), height=1, width=7)
plus.grid(row=2, column=3)
minus = Button(gui, text=' - ', fg='black', bg='white',command=lambda: press("-"), height=1, width=7)
minus.grid(row=3, column=3)
mul = Button(gui, text=' * ', fg='black', bg='white',command=lambda: press("*"), height=1, width=7)
mul.grid(row=4, column=3)
divide = Button(gui, text=' / ', fg='black', bg='white',command=lambda: press("/"), height=1, width=7)
divide.grid(row=5, column=3)
equal = Button(gui, text=' = ', fg='black', bg='white', command=equalpress, height=1, width=7)
equal.grid(row=5, column=2)
clear = Button(gui, text='Clear', fg='black', bg='white',command=clear, height=1, width=7)
clear.grid(row=5, column='1')
dec= Button(gui, text='.', fg='black', bg='white',command=lambda: press('.'), height=1, width=7)
dec.grid(row=6, column=0)
gui.mainloop() if e==11:
char=input('For which day do you want to know the timing?')
if char in 'monday' or 'tuesday' or 'wednesday' or 'thursday' or 'friday':
print('8 a.m. - 4.30 p.m.') elif char in 'saturday':
print('8 a.m. - 1 p.m.') elif char in 'sunday':
print('Closed') else:
print("Enter valid option") if e==12:
cut=input('Enter the course: ') if cut in 'science':
print('The cut off marks for science group is 80
percent.')
elif cut in 'commerce':
print('The cut off marks for commerce group is 70
percent.')
else:
print("Enter valid course") if e==13:
ad=int(input('Enter the grade: '))
if ad==1 or ad==2 or ad==3 or ad==4 or ad==5:
print('The admission fees is Rs.80000') elif ad==6 or ad==7 or ad==8:
print('The admission fees is Rs.100000') elif ad==9 or ad==10 or ad==11 or ad==12:
print('The admission fees is Rs.120000') else:
print("Enter valid option") if e==14:
subprocess.Popen('C:\\Windows\\System32\\calc.exe') if e==15:
holiday={'Festivals':['Rama Navami','Ambedkar Jayanti','Tamil new year',
'Good Friday','Labour Day','Independence Day','Gandhi Jayanti','Dussehra','Diwali',
'Christmas'], 'Dates':['10 Apr 2022','14 Apr 2022','14 Apr 2022','15 Apr 2022','1 May 2022',
'15 Aug 2022','2 Oct 2022','5 Oct 2022','24 Oct 2022','25 Dec 2022']}
di=pd.DataFrame(holiday)
print(tabulate(di, headers = 'keys', tablefmt = 'psql')) if e==16:
sub=input('Which subject?') if 'math' in sub:
print('Arulselvi Kamaraj') elif 'physics' in sub:
print('David Jayakumar') elif 'chemistry' in sub:
print('Brinda Devadoss') elif 'computer science' in sub:
print('Lydia Catherine Felix') elif 'english' in sub:
print('Rajeshwari') elif 'bs' in sub:
print('Usha Ramakrishnan') elif 'psychology' in sub:
print('Srividhya') else:
print("Enter valid option") if e==17:
comp=input('Which competition?') if comp in 'sof':
print('The sof dates are tentatively scheduled from march to april.')
elif comp in 'trinity':
print('The trinity competitions has already been
conducted during january.') elif comp in 'stage':
print('The stage competitions are scheduled during september.')
else:
print("No such competition will take place according to
updated schedule") if e==18:
x=input("Enter your gmail:")
print("Your query is related to:")
print("1:admin")
print("2:applying a leave")
print("3:not regarding any of the above queries:")
d=input("Enter the number associated with the query:") if d=='1':
sender_email=x rec_email="kavin.bharathi@babajividhyashram.org" password=input(str("please enter the password:")) message=input("Enter the query:") server=smtplib.SMTP('smtp.gmail.com',587) server.starttls() server.login(sender_email,password)
print("login successful") server.sendmail(sender_email,rec_email,message) print("query submitted successfully")
if d=='2':
f=input("Enter your class and section:") if f=="12a" or f== "12A":
rec_email="aditya.karthikeyan@babajividhyashram.org" if f=="12b" or f== "12B":
rec_email="pavithra.manogaran@babajividhyashram.org" sender_email=x
gmail:"))
password=input(str("please enter the password for your
message=input("enter the reason for leave:") server=smtplib.SMTP('smtp.gmail.com',587) server.starttls() server.login(sender_email,password) server.sendmail(sender_email,rec_email,message) print("leave application successfully applied")
if d=='3':
k=("Enter the teacher name who you want to discuss
about it:")
sender_email=x rec_email="aditya.karthikeyan@babajividhyashram.org"
gmail:")
password=input("please enter the password for your
message=input("enter your query:") server=smtplib.SMTP('smtp.gmail.com',587) server.starttls() server.login(sender_email,password)
if e==19:
break else:
print("Bot-->Wrong password please check and try again")
