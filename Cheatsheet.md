# Selenium CheatSheet with Python

## 1️⃣ Cài đặt Anaconda và Selenium trên Local

### Bước 1: Tải và Cài đặt Anaconda
- Truy cập: [🔗 Anaconda Download](https://www.anaconda.com/download/success)  
- Chọn phiên bản phù hợp với hệ điều hành (Windows/macOS/Linux).  
- Cài đặt theo hướng dẫn mặc định.  

### Bước 2: Kiểm tra cài đặt Anaconda
Mở **Anaconda Prompt** (Windows) hoặc **Terminal** (macOS/Linux) và kiểm tra:
```bash
conda --version  # Kiểm tra phiên bản Conda
python --version  # Kiểm tra phiên bản Python trong Anaconda
```
Nếu hiển thị phiên bản hợp lệ, nghĩa là cài đặt thành công.

### Bước 3: Tạo môi trường ảo trong Anaconda
```bash
conda create --name selenium_env python=3.9
conda activate selenium_env
```

### Bước 4: Cài đặt Selenium
```bash
pip install selenium
```

### Bước 5: Cài đặt WebDriver
- **Chrome**: [ChromeDriver](https://developer.chrome.com/docs/chromedriver/downloads)  
- **Firefox**: [GeckoDriver](https://github.com/mozilla/geckodriver/releases)  
- **Edge**: [EdgeDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)  

### Bước 6: Thêm WebDriver vào PATH
Di chuyển file WebDriver vào thư mục **Anaconda environment**:
```bash
mv chromedriver ~/anaconda3/envs/selenium_env/bin/
```
Hoặc thêm vào **PATH** bằng lệnh:
```bash
export PATH=$PATH:/path/to/webdriver
```

---

## 2️⃣ Khởi tạo WebDriver
```python
from selenium import webdriver

# Chạy với Chrome
driver = webdriver.Chrome()

# Mở trang web
driver.get("https://example.com")
```

---

## 3️⃣ Tìm kiếm phần tử trên trang
```python
from selenium.webdriver.common.by import By

# Tìm bằng ID
element = driver.find_element(By.ID, "element-id")

# Tìm bằng class
element = driver.find_element(By.CLASS_NAME, "class-name")

# Tìm bằng name
element = driver.find_element(By.NAME, "name-attribute")

# Tìm bằng XPath
element = driver.find_element(By.XPATH, "//tag[@attribute='value']")

# Tìm bằng CSS Selector
element = driver.find_element(By.CSS_SELECTOR, "tag[attribute='value']")
```

---

## 4️⃣ Tương tác với phần tử
```python
# Click vào phần tử
element.click()

# Nhập văn bản vào ô input
element.send_keys("Hello, Selenium!")

# Xóa dữ liệu trong ô input
element.clear()

# Lấy văn bản của phần tử
text = element.text

# Lấy giá trị thuộc tính
value = element.get_attribute('href')
```

---

## 5️⃣ Điều hướng trình duyệt
```python
driver.back()      # Quay lại trang trước
driver.forward()   # Tiến tới trang sau
driver.refresh()   # Refresh trang
```

---

## 6️⃣ Xử lý cửa sổ bật lên (Alerts)
```python
alert = driver.switch_to.alert
alert.accept()  # Nhấn OK
alert.dismiss()  # Nhấn Cancel
```

---

## 7️⃣ Chờ đợi phần tử xuất hiện (Waits)
```python
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Chờ tối đa 10 giây để phần tử xuất hiện
element = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.ID, "element-id"))
)
```

---

## 8️⃣ Cuộn trang (Scrolling)
```python
# Cuộn xuống cuối trang
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

# Cuộn tới một phần tử cụ thể
element = driver.find_element(By.ID, "element-id")
driver.execute_script("arguments[0].scrollIntoView();", element)
```

---

## 9️⃣ Xử lý Iframe
```python
# Chuyển vào iframe
driver.switch_to.frame("iframe_id")

# Chuyển ra ngoài iframe
driver.switch_to.default_content()
```

---

## 🔟 Xử lý nhiều tab
```python
# Mở tab mới
driver.execute_script("window.open('https://example.com');")

# Chuyển sang tab mới
driver.switch_to.window(driver.window_handles[1])

# Đóng tab hiện tại
driver.close()
```

---

## 🔹 Thoát trình duyệt
```python
driver.quit()  # Đóng toàn bộ trình duyệt
```

---

## 📖 Tài liệu tham khảo
- [Selenium với Python](https://selenium-python.readthedocs.io/)
