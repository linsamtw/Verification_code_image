# 驗證碼影像處理 ( Verification_code_image )

## 主要是將圖片，灰度化、去雜點、切割，再搭配DL，將有助於提高準確率

首先，下圖是台鐵的驗證碼<br><br>
 ![train](https://github.com/f496328mm/Verification_code_image/blob/master/t3.jpg)

## 讀取圖片 input image <br>
```sh
im = cv2.imread('t3.jpg', cv2.IMREAD_COLOR)
plt.imshow(im)
```

## 灰度化( transform gray scale )<br>
```sh
retval, im2 = cv2.threshold(im, 115, 255, cv2.THRESH_BINARY_INV)
plt.imshow(im2)
```
## 刪除雜點( del miscellaneous points ) <br>
```sh
im3 = del_mis_pt_by_threshold(im2)  )
plt.imshow(im3)
```
## 雜點去除後，我們必須對剩下的影像做強化<br>
```sh
im4 = cv2.dilate(im3, (2, 2), iterations=1)
plt.imshow(im4)
# save figure
plt.savefig('del_mix_pt.png')
```
 以下是處理完後的 image<br>
![del_mix_pt](https://github.com/f496328mm/Verification_code_image/blob/master/del_mix_pt.png)

## 接下來將分割數字，分割有助於 DL 預測 <br>
```sh
x_split_start,x_split_end = catch_axis_start_and_end(im4,axis='x')
```
## 分割完後的圖片<br>
```sh
img1 = my_plt_fun(x_split_start,x_split_end,0)
plt.imshow(img1)
```
![split_image_0](https://github.com/f496328mm/Verification_code_image/blob/master/split_image_0.png)
![split_image_1](https://github.com/f496328mm/Verification_code_image/blob/master/split_image_1.png)
![split_image_2](https://github.com/f496328mm/Verification_code_image/blob/master/split_image_2.png)
![split_image_3](https://github.com/f496328mm/Verification_code_image/blob/master/split_image_3.png)
![split_image_4](https://github.com/f496328mm/Verification_code_image/blob/master/split_image_4.png)
## 儲存<br>
```sh
for i in range(len(x_split_start)):
    my_plt_fun(x_split_start,x_split_end,i)
```


