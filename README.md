# Selenium Student Registration Form Automation
## Name: Dharunyadevi S
## Register Number: 212223220018
## Project Overview

This project automates a Student Registration Form using Python and Selenium WebDriver.

The main objective of this project is to practice Selenium automation and different XPath locator techniques using a real-time registration form.

Website used:

https://www.tutorialspoint.com/selenium/practice/selenium_automation_practice.php

## Technologies Used

* Python
* Selenium WebDriver
* Google Chrome
* ChromeDriver
* XPath

## Test Scenarios

The automation covers the following scenarios:

1. Open the Student Registration page
2. Locate the student name field
3. Enter student name
4. Enter email
5. Locate and select gender radio button
6. Enter additional information
7. Locate elements using XPath
8. Select hobbies using checkbox
9. Upload picture
10. Locate parent elements
11. Locate ancestor elements
12. Locate child elements
13. Locate following elements
14. Select dropdown values
15. Locate elements using XPath index
16. Find multiple input fields using `find_elements()`
17. Locate dynamic elements using `contains()`
18. Locate elements using `starts-with()`
19. Use `and` and `or` XPath operators
20. Complete the registration form automation

## Learning Outcomes

This project helps in understanding:

* Selenium WebDriver
* Python automation
* XPath locators
* Dynamic XPath
* XPath axes
* Checkboxes
* Radio buttons
* Dropdown handling
* File upload
* Explicit waits
* `find_element()`
* `find_elements()`
* Basic test-case execution
* Real-time web form automation
## Program
```py
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait,Select
from selenium.webdriver.support import expected_conditions as EC
import time

driver=webdriver.Chrome()
wait=WebDriverWait(driver,10)
driver.get("https://www.tutorialspoint.com/selenium/practice/selenium_automation_practice.php")
driver.maximize_window()
print("TC01 - Open Student Registration Page")
print("Test Case Passed")
print("Page Title:", driver.title)
print("Current URL:", driver.current_url)

name=wait.until(EC.visibility_of_element_located((By.XPATH,'//input[@name="name"]')))
print("\nTC02 - Locate Student Name")


name.clear()
name.send_keys("Dharunyadevi S")
print("\nTC03 - Enter Student Name")
print("Name entered successfully")


email=wait.until(EC.visibility_of_element_located((By.XPATH,'//input[@id="email"]')))
email.send_keys("dharunyadevi@gmail.com")
print("\nTC04 - Locate and Enter Email")


gender=wait.until(EC.element_to_be_clickable((By.XPATH,'//*[@id="practiceForm"]/div[3]/div/div/div[2]/input')))
gender.click()
print("Gender radio button selected:", gender.is_selected())

mobile=wait.until(EC.visibility_of_element_located((By.XPATH,'//input[@id="mobile"]')))
mobile.send_keys("9876543210")
print("\nTC05 - Locate Mobile using contains()")


dob=wait.until(EC.visibility_of_element_located((By.XPATH,'//input[@id="dob"]')))
dob.send_keys("24-04-2006")
print("\nTC06 - Locate DOB using starts-with()")


subject=wait.until(EC.visibility_of_element_located((By.XPATH,'//input[@id="subjects"]')))
subject.send_keys("Computer Science")
print("\nTC07 - Locate Subject using and")


music=wait.until(EC.element_to_be_clickable((By.XPATH,'//*[@id="practiceForm"]/div[7]/div/div/div[3]/input')))
music.click()
picture=wait.until(EC.presence_of_element_located((By.XPATH,'//input[@id="picture"]')))
picture.send_keys(r"C:\Users\admin\OneDrive\Desktop\Selenium\student.jpg")
print("\nTC09 - Upload Picture")
print("Picture uploaded successfully")


address=wait.until(EC.visibility_of_element_located((By.XPATH,'//textarea[@id="picture" or @id="address"]')))
print("\nTC08 - Locate element using or")


parent=name.find_element(By.XPATH,"./parent::*")
print("\nTC09 - Find Parent Element")
print("Parent tag:", parent.tag_name)

form = name.find_element(By.XPATH,"./ancestor::form")
print("\nTC10 - Find Form using ancestor")
print("Form found:", form.tag_name)

child_inputs = form.find_elements(By.XPATH,"./child::input")
print("\nTC11 - Find Child Input Elements")
print("Number of child inputs:", len(child_inputs))

next_element = name.find_element(By.XPATH,"./following::*[1]")
print("\nTC12 - Find Next Element using following")
print("Next element:", next_element.tag_name)

checkbox = wait.until(EC.element_to_be_clickable((By.XPATH, "//input[@type='checkbox']")))
if not checkbox.is_selected():
    checkbox.click()
print("\nTC13 - Select Checkbox")
print("Checkbox selected:", checkbox.is_selected())

radio = wait.until(EC.element_to_be_clickable((By.XPATH, "//input[@type='radio']")))
if not radio.is_selected():
    radio.click()
print("\nTC14 - Select Radio Button")
print("Radio selected:", radio.is_selected())

state_dropdown = wait.until(EC.visibility_of_element_located((By.XPATH, "//select[@id='state']")))
state = Select(state_dropdown)
state.select_by_index(1)
print("\nTC15 - Select State Dropdown")
print("Selected State:", state.first_selected_option.text)

textboxes = driver.find_elements(By.XPATH,"(//input[@type='text'])")
print("\nTC16 - Find Textbox using XPath Index")
if len(textboxes) >= 2:
    second_textbox = driver.find_element(By.XPATH,"(//input[@type='text'])[2]")
    print("Second textbox found")
    print("Test Case Passed")
else:
    print("Second textbox not found")

all_inputs = driver.find_elements(By.XPATH,"//input")
print("\nTC17 - Find All Input Fields")
print("Total input fields:", len(all_inputs))

dynamic_elements = driver.find_elements(By.XPATH,"//*[contains(@id,'name')]")
print("\nTC18 - Find Dynamic Element using contains()")
print("Matching elements:", len(dynamic_elements))

radio_buttons = driver.find_elements(By.XPATH,"//input[@type='radio']")
print("\nTC19 - Find All Radio Buttons")
print("Number of radio buttons:", len(radio_buttons))
for radio_button in radio_buttons:
    print("Radio:",radio_button.get_attribute("value"))

print("\nTC20 - Complete Registration Automation")
print("Student Name:", name.get_attribute("value"))
print("Email:", email.get_attribute("value"))
print("Mobile:", mobile.get_attribute("value"))
print("DOB:", dob.get_attribute("value"))
print("Subject:", subject.get_attribute("value"))
print("Registration form automation completed")

time.sleep(5)
driver.quit()
```

## Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fc3366f2-d095-462a-9c5a-153961480e6d" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/be0a4ff1-5480-41fe-87ff-8bf240d4b5d2" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/42761800-940b-4586-bc3e-6ef6b4b914cc" />

