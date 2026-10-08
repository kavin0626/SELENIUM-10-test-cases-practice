# Selenium Automation – 10 Test Cases

## Description

This repository contains **10 Selenium automation test cases using Python**.

The project demonstrates basic and commonly used Selenium concepts such as:

* WebDriver
* Alerts
* Prompt Alerts
* Mouse Hover
* Double Click
* Drag and Drop
* Explicit Wait
* Clickable Wait
* Alert Wait

## Technologies Used

* Python
* Selenium
* Google Chrome
* ChromeDriver
* VS Code

## Installation

Install Selenium using:

```bash
pip install selenium
```

Make sure Python and Google Chrome are installed on your computer.

---

# Test Cases

## TC-1: Open Online Shopping Website

### Test Case

Customer opens an online shopping website and logs in.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

driver.get("https://www.saucedemo.com/inventory.html")

driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")

driver.find_element(By.ID, "login-button").click()

time.sleep(10)

driver.quit()
```

### Selenium Concept

**WebDriver and element identification using ID.**

---

## TC-2: Alert Accept

### Test Case

Customer clicks a button and an alert popup appears. The customer accepts the alert.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")

driver.find_element(By.XPATH, "//button[@onclick='myDesk()']").click()

alert = driver.switch_to.alert

time.sleep(5)

alert.accept()

time.sleep(10)

driver.quit()
```

### Selenium Concept

**Accepting JavaScript alerts using `alert.accept()`.**

---

## TC-3: Alert Dismiss

### Test Case

Customer clicks a button and an alert popup appears. The customer chooses Cancel/Dismiss.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")

driver.find_element(By.XPATH, "//button[@onclick='myDesk()']").click()

alert = driver.switch_to.alert

time.sleep(5)

alert.dismiss()

time.sleep(10)

driver.quit()
```

### Selenium Concept

**Dismissing an alert using `alert.dismiss()`.**

---

## TC-4: Prompt Alert

### Test Case

Customer enters a name in a prompt popup.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")

driver.find_element(By.XPATH, "//button[@onclick='myPromp()']").click()

time.sleep(1)

alert = driver.switch_to.alert

alert.send_keys("kavin")

time.sleep(10)

alert.accept()

time.sleep(2)

driver.quit()
```

### Selenium Concept

**Entering text into a prompt alert using `send_keys()`.**

---

## TC-5: Mouse Hover

### Test Case

Customer moves the mouse over the Products/Category menu.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains

driver = webdriver.Chrome()

driver.get("https://demoqa.com/menu/")

time.sleep(5)

menu = driver.find_element(By.XPATH, "//a[text()='Main Item 2']")

actions = ActionChains(driver)

time.sleep(2)

actions.move_to_element(menu).perform()

time.sleep(3)

driver.quit()
```

### Selenium Concept

**Mouse hover using `ActionChains`.**

---

## TC-6: Double Click

### Test Case

Customer double-clicks a button.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains

driver = webdriver.Chrome()

driver.get("https://demoqa.com/buttons")

time.sleep(10)

button = driver.find_element(By.ID, "doubleClickBtn")

ActionChains(driver).double_click(button).perform()

time.sleep(10)

driver.quit()
```

### Selenium Concept

**Double-click action using `ActionChains`.**

---

## TC-7: Drag and Drop

### Test Case

Customer drags an item from one location and drops it into another location.

### Code

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains

driver = webdriver.Chrome()

driver.get("https://demoqa.com/droppable")

driver.maximize_window()

time.sleep(2)

source = driver.find_element(By.ID, "draggable")
target = driver.find_element(By.ID, "droppable")

time.sleep(3)

actions = ActionChains(driver)

actions.click_and_hold(source)
actions.move_to_element(target)
actions.release()
actions.perform()

time.sleep(3)

driver.quit()
```

### Selenium Concept

**Drag and drop using `ActionChains`.**

---

## TC-8: Explicit Wait

### Test Case

Customer logs in and waits until the product becomes visible before clicking it.

### Code

```python
import time

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()

driver.get("https://www.saucedemo.com/")

driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")

driver.find_element(By.ID, "login-button").click()

wait = WebDriverWait(driver, 10)

product = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//div[text()='Sauce Labs Backpack']")
    )
)

product.click()

time.sleep(10)

driver.quit()
```

### Selenium Concept

**Explicit wait using `WebDriverWait` and `visibility_of_element_located`.**

---

## TC-9: Clickable Wait

### Test Case

Customer adds a product to the cart, goes to checkout, and waits until the Finish button becomes clickable.

### Code

```python
import time

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()

driver.get("https://www.saucedemo.com/")

driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")

driver.find_element(By.ID, "login-button").click()

driver.find_element(
    By.ID, "add-to-cart-sauce-labs-backpack"
).click()

driver.find_element(
    By.CLASS_NAME, "shopping_cart_link"
).click()

driver.find_element(By.ID, "checkout").click()

time.sleep(5)

driver.find_element(By.ID, "first-name").send_keys("kavin")
driver.find_element(By.ID, "last-name").send_keys("Test")
driver.find_element(By.ID, "postal-code").send_keys("600001")

driver.find_element(By.ID, "continue").click()

wait = WebDriverWait(driver, 10)

finish_button = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "finish")
    )
)

finish_button.click()

time.sleep(2)

driver.quit()
```

### Selenium Concept

**Waiting until an element becomes clickable using `element_to_be_clickable`.**

---

## TC-10: Alert Wait

### Test Case

Customer clicks a button and waits until the alert popup appears.

### Code

```python
import time

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()

driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")

driver.find_element(
    By.XPATH,
    "//button[@onclick='myMessage()']"
).click()

wait = WebDriverWait(driver, 10)

alert = wait.until(
    EC.alert_is_present()
)

time.sleep(5)

alert.accept()

time.sleep(5)

driver.quit()
```

### Selenium Concept

**Waiting for an alert using `alert_is_present()`.**

---

# Selenium Concepts Summary

| Test Case | Concept Used   |
| --------- | -------------- |
| TC-1      | WebDriver      |
| TC-2      | Alert Accept   |
| TC-3      | Alert Dismiss  |
| TC-4      | Prompt Alert   |
| TC-5      | Mouse Hover    |
| TC-6      | Double Click   |
| TC-7      | Drag and Drop  |
| TC-8      | Explicit Wait  |
| TC-9      | Clickable Wait |
| TC-10     | Alert Wait     |

# How to Run

Clone the repository:

```bash
git clone https://github.com/kavin026/SELENIUM-10-test-cases-practice.git
```

Open the project in VS Code:

```bash
cd SELENIUM-10-test-cases-practice
```

Install Selenium:

```bash
pip install selenium
```

Run any test case:

```bash
python test_case_1.py
```

# Project Structure

```text
SELENIUM-10-test-cases-practice/
│
├── test_case_1.py
├── test_case_2.py
├── test_case_3.py
├── test_case_4.py
├── test_case_5.py
├── test_case_6.py
├── test_case_7.py
├── test_case_8.py
├── test_case_9.py
├── test_case_10.py
│
└── README.md
```

