from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.edge.service import Service
import time

# Set path to msedgedriver
service = Service("C:/webdriver/msedgedriver.exe")   # change path

# Start Edge browser
driver = webdriver.Edge(service=service)

# Open Google
driver.get("https://www.google.com")
time.sleep(2)

# Find search box
search_box = driver.find_element(By.NAME, "q")
print("Search box element found:", search_box)

# Close browser
driver.quit()


from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.edge.options import Options
import time

options = Options()
options.add_argument("--disable-blink-features=AutomationControlled")
options.add_argument("user-agent=Mozilla/5.0")

driver = webdriver.Edge(options=options)

driver.get("https://www.google.com")
driver.maximize_window()

time.sleep(3)

search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Selenium Web Testing")

time.sleep(2)
search_box.send_keys(Keys.RETURN)

time.sleep(5)

print("Page loaded successfully")

driver.quit()

