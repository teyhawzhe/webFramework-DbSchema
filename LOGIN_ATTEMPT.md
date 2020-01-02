# 嘗試登入計算(LOGIN_ATTEMPT)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||USERNAME|VARCHAR(100)|Y|||帳號ID
|||ATTEMPT|INTEGER(10)|Y|||嘗試登入的次數
|||ALLOW_DATE|VARCAHR(13)||||允許再次嘗試登入的時間，YYYYMMDD HHMM
