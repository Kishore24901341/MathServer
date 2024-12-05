# Ex.05 Design a Website for Server Side Processing
## Date:01:12:24

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
'''
mathapp:
<html>
<head>
    <title>Math</title>
    <style>
        body {
            background: url('background-image.jpg') no-repeat center center fixed;
            background-size: cover;
            font-family: Arial, sans-serif;
            color: white;
        }

        h1 {
            border: 2px solid black;
            padding: 20px;
            margin: 10px;
            border-radius: 5px;
            position: fixed;
            top: 200px;
            right: 500px;
            font-size: 2.5em;
            font-weight: bold;
            font-variant: small-caps;
            background: linear-gradient(to bottom, rgba(13, 237, 229, 0.9), rgba(208, 189, 21, 0.9));
            font-family: Georgia, 'Times New Roman', Times, serif;
            font-style: italic;
            color: #ff5733;
            text-align: center;
        }

        form {
            border: 2px solid rgba(20, 202, 234, 0.9);
            background-color: rgba(0, 0, 0, 0.7);
            padding: 30px;
            margin: 10px;
            border-radius: 10px;
            width: 450px;
            position: fixed;
            top: 300px;
            left: 527px;
            font-style: oblique;
            color: #ffff66;
            font-size: 1.2em;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        input[type="text"] {
            width: 100%;
            padding: 8px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }

        input[type="submit"] {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1em;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <h1>Power Calculator</h1>
    <form align="center" method="POST">
        {% csrf_token %}
        <div class="power">
            <label for="INTENSITY"><b>INTENSITY (I):</b></label>
            <input type="text" name="intensity" id="INTENSITY" placeholder="Enter the Value" value="{{i}}">
        </div>
        <div class="power">
            <label for="RESISTANCE"><b>RESISTANCE (Ohms):</b></label>
            <input type="text" name="resistance" id="RESISTANCE" placeholder="Enter the Value" value="{{r}}">
        </div>
        <input type="submit" value="CALCULATE">
        <div class="power">
            <label for="POWER"><b>POWER (in Watts):</b></label>
            <input type="text" name="POWER" id="POWER" placeholder="Answer" value="{{power}}">
        </div>
    </form>
</body>
</html>

views.py:

from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)

urls.py:
from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]
'''


## SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/49e7e91f-3afc-46f6-b7ed-94031ed061f9)

## HOMEPAGE:
![image](https://github.com/user-attachments/assets/4928ab08-3853-4316-b91f-f9403e42ab09)

## RESULT:
The program for performing server side processing is completed successfully.
