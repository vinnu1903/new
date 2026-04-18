from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.edge.service import Service
import time
service = Service("C:/webdriver/msedgedriver.exe")   # change path
driver = webdriver.Edge(service=service)
driver.get("https://www.google.com")
time.sleep(2)
search_box = driver.find_element(By.NAME, "q")
print("Search box element found:", search_box)
driver.quit()

2ndone

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


docker-------------------------------------------------------------

# Check Docker
docker --version
docker info

# -----------------------------
# 1. UBUNTU CONTAINER
# -----------------------------
docker pull ubuntu
docker run -it ubuntu bash -c "apt update && apt install nano -y"

# -----------------------------
# 2. ALPINE + NANO (Dockerfile)
# -----------------------------
echo 'FROM alpine:latest
RUN apk add --no-cache nano
CMD ["/bin/sh"]' > Dockerfile

docker build -t alpine-nano .
docker run -it alpine-nano

# -----------------------------
# 3. NGINX WEBSITE
# -----------------------------
echo '<h1>Hello Docker</h1>' > index.html

echo 'FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80' > Dockerfile

docker build -t mynginx .
docker run -d -p 8080:80 mynginx

# -----------------------------
# 4. CONTAINER MANAGEMENT
# -----------------------------
docker ps
docker ps -a

# Stop all running containers
docker stop $(docker ps -q)

# Start first container (example)
docker start $(docker ps -aq | head -n 1)

# Remove all containers
docker rm $(docker ps -aq)

# -----------------------------
# 5. CLEANUP
# -----------------------------
docker container prune -f
docker image prune -f

# -----------------------------
# 6. EXTRA
# -----------------------------
# Logs (replace <id>)
docker logs <container_id>

# Execute inside container
docker exec -it <container_id> /bin/sh
