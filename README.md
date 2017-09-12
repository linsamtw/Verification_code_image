# 驗證碼影像處理 ( Verification_code_image )

主要是將圖片，灰度化、去雜點、切割，再搭配DL，將有助於提高準確率

首先，下圖是台鐵的驗證碼<br><br>
 ![train](https://github.com/f496328mm/Verification_code_image/blob/master/t3.jpg)

## 讀取圖片 input image <br>
```sh
im = cv2.imread('t3.jpg', cv2.IMREAD_COLOR)
plt.imshow(im)
```
