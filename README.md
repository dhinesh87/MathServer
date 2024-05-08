# Ex.05 Design a Website for Server Side Processing
## Date:23.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
''''
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
<style>
.formelt{
    color: rgb(245, 242, 236);
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: rgb(244, 235, 241);
    text-align: center;
    padding-top: 20px;
}
body{
    background-color:rgb(206, 22, 38);
}
.edge
{
    border:2px solid rgb(27, 26, 25);
    margin-top:10%;
}
</style>
</head>
<body>
    <h1>Area of a Rectangle</h1>
<div class="edge">
    <div class="box">
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Length: <input type="text" name="length" value="{{l}}"></input>(in m)<br/>
            </div>
            <div class="formelt">
                Breadth <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"></input><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>
```
```
views.py

from django.shortcuts import render

# Create your views here.from django.shortcuts import render
def rectarea(request):
    context={}
    context ['area'] = "0"
    context['1'] = "0"
    context ['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l=request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')
        print('request=', request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l)*int(b)
        context['area'] = area
        context['l']= l
        context['b'] = b
        print('Area', area)
    return render(request, 'mathapp/math.html', context) 
```
```
urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
''''

## SERVER SIDE PROCESSING:

![Screenshot 2024-05-06 215406](https://github.com/dhinesh87/MathServer/assets/146917182/681d662f-3051-4b6f-9ab1-79f9e545d0da)

## HOMEPAGE:

![Screenshot 2024-05-06 220449](https://github.com/dhinesh87/MathServer/assets/146917182/3ce0a56d-6622-4266-88a9-7bfce245dcfc)

## RESULT:
The program for performing server side processing is completed successfully.
