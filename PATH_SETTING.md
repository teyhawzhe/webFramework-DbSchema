# 路徑設定(PATH_SETTING)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||ID|VARCHAR(200)|Y|||路徑ID
|||PATH|VARCHAR(100)|Y|||路徑
|||TITLE|VARCHAR(100)|Y|||路徑標題
|||COMPONENT|VARCHAR(100)|Y|||前端畫面元件
|||HIDDEN|BOOLEAN|Y|||前端畫面目錄是否顯示此路徑
|||TIER|INTEGER(10)|Y|||路徑階層
|||ICON|VARCHAR(100)|Y|||前端畫面目錄圖示
|||SORT|INTEGER(10)|Y|Y||路徑排序
|||PARENT|VARCHAR(100)||||路徑父層
|||NAME|VARCHAR(200)|Y|||路徑名稱，保留此欄位，資料與ID相同
|||REDIRECT|VARCHAR(100)||||點擊前端畫面目錄下的子目錄所顯示的預設畫面