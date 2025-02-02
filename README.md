from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
import random
import time

# Inisialisasi WebDriver
driver = webdriver.Chrome(executable_path='/path/to/chromedriver')  # Ganti dengan path ke chromedriver

# Buka halaman TikTok
driver.get('https://www.tiktok.com/login')

# Tunggu beberapa detik agar halaman sepenuhnya dimuat
time.sleep(5)

# Login ke akun TikTok (gunakan akun dan password yang sudah dibuat)
username_field = driver.find_element(By.NAME, 'username')
password_field = driver.find_element(By.NAME, 'password')

# Username dan password yang sudah ditentukan
username = 'duniacerita424'  # Nama TikTok kamu
password = '#Alif108084354442'  # Password akun TikTok kamu

# Tempelkan username dan password ke field login
username_field.send_keys(username)
password_field.send_keys(password)
password_field.send_keys(Keys.RETURN)

# Tunggu beberapa detik untuk login selesai
time.sleep(10)  # Perpanjang waktu tunggu jika diperlukan

# Cek apakah login berhasil dengan memeriksa elemen yang hanya ada setelah login
try:
    driver.find_element(By.XPATH, '//*[@data-e2e="user-info"]')  # Ganti dengan elemen yang menunjukkan login sukses
    print("Login berhasil!")
except:
    print("Login gagal. Pastikan username dan password sudah benar.")
    driver.quit()
    exit()

# Acak nama pengguna (contoh nama acak)
name = ''.join(random.choices('abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', k=10))

# Mencari video dan memberi like
video_url = 'https://vt.tiktok.com/ZS6TxeMPp/'  # URL video TikTok yang diberikan
driver.get(video_url)

# Tunggu beberapa detik agar video dimuat
time.sleep(5)

# Klik tombol like (asumsi tombol like dapat ditemukan dengan XPath yang sesuai)
# Sesuaikan XPath tombol like yang sesuai dengan yang terdeteksi pada halaman
try:
    like_button = driver.find_element(By.XPATH, '//span[@data-e2e="like-icon"]')  # XPath tombol like TikTok
    like_button.click()
    print("Video berhasil di-like!")
except:
    print("Tidak dapat menemukan tombol like.")
    
# Tunggu beberapa detik sebelum menutup
time.sleep(2)

# Menutup browser
driver.quit()
