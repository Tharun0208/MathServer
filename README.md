# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
  math.html
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Area of a Rectangle</title>
    <style>
      h1 {
        font-size: 20px;
        background-color: blue;
        color: orange;
        text-align: center;
        padding: 7px;
        margin-bottom: 6px;
      }
  
      .formelt {
        color: rgb(255, 0, 179);
        text-align: center;
        padding-top: 20px;
      }
    </style>
  </head>
  <body>
    <div class="edge">
      <div class="box">
        <h1>Area of a Rectangle</h1>
        <form method="POST">
          {% csrf_token %}
          <div class="formelt">
            Length: <input type="text" name="length" value="{{ l }}" required></input> (in m)<br />
          </div>
          <div class="formelt">
            Breadth: <input type="text" name="breadth" value="{{ b }}" required></input> (in m)<br />
          </div>
          <div class="formelt">
            <input type="submit" value="Calculate"></input><br />
          </div>
          <div class="formelt">
            Area: <input type="text" name="area" value="{{ area }}" readonly></input> m<sup>2</sup><br />
          </div>
        </form>
      </div>
    </div>
  </body>
  </html>
  
  
  views.py
  from django.shortcuts import render
  
  def rectarea(request):
      context = {}
      context['area'] = "0"
      context['l'] = "0"
      context['b'] = "0"
      
      if request.method == 'POST':
          print("POST method is used")
          l = request.POST.get('length', '0')
          b = request.POST.get('breadth', '0')
          print('request=', request)
          print('Length=', l)
          print('Breadth=', b)
          area = int(l) * int(b)
          context['area'] = area
          context['l'] = l
          context['b'] = b
          print('Area=', area)
  
      return render(request, 'mathapp/math.html', context)
  
  
  urls.py
  from django.contrib import admin
  from django.urls import path
  from mathapp import views
  
  urlpatterns = [
      path('admin/', admin.site.urls),
      path('areaofrectangle/', views.rectarea, name="areaofrectangle"),
      path('', views.rectarea, name="areaofrectangleroot")
  ]



## SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/c2842c46-f802-4de7-9d9c-b7990b5c30d0)
![image](https://github.com/user-attachments/assets/3e4dae7c-ec72-4046-bfbd-334cca764812)


## HOMEPAGE:
![Screenshot 2024-12-12 225613](https://github.com/user-attachments/assets/d1b150a7-bbfa-45c7-88e0-49d66b2df6b8)


## RESULT:
The program for performing server side processing is completed successfully.
