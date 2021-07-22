# pwa-memo
something about PWA Web APP
預計寫一篇PWA相關的文，先memo一下相關文章，等做好，測試好了，就來完整他

## ref link
- [PWA計算機，說明寫得不錯](https://zhung.com.tw/project/pwa-calculator/)
- [itheme about PWA APP](https://ithelp.ithome.com.tw/articles/10188514)

- [最後是看這一篇文章，2021-07-06](https://blog.techbridge.cc/2018/10/13/pwa-in-action/)

## 實作紀錄

- `manifest.json` 這是必須要的檔案，要放在你要做為PWA的網頁根目錄下
- 比如結構長這樣:
```
/
|- static
|   |- pwa_dir
|      |- index.html
|      |- manifest.json
|      |- img
|   |- app1_dir
|   |- app2_dir
|
|- app.py
```
- 我們的manifest.json如下:
  - 其中，name會是你要顯示的App名稱，但如果有"short_name"在，就會改用sort_name
  - start_url 則是你這一個PWA APP的位置，但是注意早期iOS(11以前)不會管這一欄，他會用你`加入主畫面`時的url位置
  - icon: 是程式載入時要顯示的圖
  - !! `name`、`background_color`、`icon`組成`Splash screens` --> 重要! 這是android的做法
  - 但是iOS就要改成在 index.html中的描述標籤決定了 --> 這可以讓你自己放一張圖片，客製化的更好
  ```
        <link
          rel='apple-touch-startup-image'
          href='img/eg_300.png'
          media='(device-width: 375px) and (orientation: portrait)'
        />  
  ```
  - 另外就是產生在桌面的icon圖示，iOS也跟人家不同，他也是看index.html中的:
  ```
  <link rel='apple-touch-icon' sizes='300x300' href='img/eg_300.png'/> <!--桌面icon-->
  ```
```
{
    "name": "我的監控",
    "short_name": "我的監控APP",
    "start_url": "https://myapp.herokuapp.com/mobile/index.html?source=pwa",
    "display": "standalone",
    "background_color": "#EEEEEE",
    "orientation": "portrait-primary",
    "icons": [
        {
            "src": "img/eg_300.png",
            "type": "image/png",
            "sizes": "300x300"
        },
        {
            "src": "img/eg_16.png",
            "type": "image/png",
            "sizes": "16x16"
        }
    ]
}
```
