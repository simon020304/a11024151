#南華大學 11024151
使用Google Colaboratory進行辨識圖片中的人臉

程式碼:

import cv2
from google.colab import files
from google.colab.patches import cv2_imshow

#上傳圖片
uploaded = files.upload()

#讀取圖片
for filename in uploaded.keys():
    img = cv2.imread(filename)

#將圖片轉為灰度
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

#加載Haar Cascade分類器
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')

#檢測人臉
faces = face_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=5)

#在圖片中標記人臉
for (x, y, w, h) in faces:
    cv2.rectangle(img, (x, y), (x+w, y+h), (0, 255, 0), 2)

#顯示結果圖片
cv2_imshow(img)
cv2.waitKey()
cv2.destroyAllWindows()]
