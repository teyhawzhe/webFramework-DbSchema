<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=2 orderedList=false} -->

<!-- code_chunk_output -->

- [1. 資料庫](#1-資料庫)
  - [1.1. 用戶帳密(USERS)](#11-用戶帳密users)
  - [1.2. 用戶角色(ROLES)](#12-用戶角色roles)
  - [1.3. 用戶資料(USER_PROFILE)](#13-用戶資料user_profile)
  - [1.4. 登入歷史(LOGIN_HISTORY)](#14-登入歷史login_history)
  - [1.5. 嘗試登入計算(LOGIN_ATTEMPT)](#15-嘗試登入計算login_attempt)
  - [1.6. 紀錄登入TOKEN(TOKEN_RECORD)](#16-紀錄登入tokentoken_record)
  - [1.7. 角色設置(ROLE_SETTING)](#17-角色設置role_setting)
  - [1.8. 路徑設定(PATH_SETTING)](#18-路徑設定path_setting)
  - [1.9. 前端畫面權限設置(VIEW_PERMISSION)](#19-前端畫面權限設置view_permission)
  - [1.10. 路徑與前端畫面權限關聯(PATH_VIEW_PERMISSION_REL)](#110-路徑與前端畫面權限關聯path_view_permission_rel)
  - [1.11. 路徑與前端畫面權限與角色關聯(PATH_VIEW_PERMISSION_ROLE_REL)](#111-路徑與前端畫面權限與角色關聯path_view_permission_role_rel)
  - [1.12. API權限管理(API_PERMISSION_SETTING)](#112-api權限管理api_permission_setting)

<!-- /code_chunk_output -->


# 1. 資料庫

## 1.1. 用戶帳密(USERS)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||USERNAME|VARCHAR(200)|Y|||帳號ID
 |||PASSWORD|VARCHAR(200)|Y|||帳號密碼
 |||ENABLE|BOOLEAN|Y|||帳號狀態，true為開啟，false為鎖定

## 1.2. 用戶角色(ROLES)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||USERNAME|VARCHAR(200)|Y|||帳號ID
Y||ROLE|VARCHAR(200)|Y|||帳號角色

## 1.3. 用戶資料(USER_PROFILE)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||USERNAME|VARCHAR(200)|Y|||帳號ID
|||NAME|VARCHAR(100)|Y|||用戶姓名
|||IMAGE|CLOB|Y|||大頭照
|||EMAIL|VARCHAR(100)|Y|||用戶EMAIL
|||SEX|VARCHAR(1)|Y|||性別
|||DEPARTMENT|VARCHAR(100)|Y|||部門
|||CREATE_DATE|VARCHAR(13)|Y|||創建時間，YYYYMMDD HHMM
|||CREATER|VARCHAR(13)|Y|||創建者

## 1.4. 登入歷史(LOGIN_HISTORY)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||USERNAME|VARCHAR(100)|Y|||帳號ID
Y||LOGIN_TIME|VARCHAR(15)|Y|||登入時間，YYYYMMDD HHMMSS
|||SUCCESS|BOOLEAN|Y|||登入成功或失敗,TRUE為成功，FALSE為失敗
|||REASON|VARCHAR(100)||||當欄位SUCCESS為FALSE時，會記錄登入失敗的原因

## 1.5. 嘗試登入計算(LOGIN_ATTEMPT)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||USERNAME|VARCHAR(100)|Y|||帳號ID
|||ATTEMPT|INTEGER(10)|Y|||嘗試登入的次數
|||ALLOW_DATE|VARCAHR(13)||||允許再次嘗試登入的時間，YYYYMMDD HHMM

## 1.6. 紀錄登入TOKEN(TOKEN_RECORD)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||TOKEN|VARCHAR(2000)|Y|||用戶登入後的TOKEN
||Y|USERNAME|VARCHAR(100)|Y|||帳號ID
|||EXPRIED_DATE|VARCHAR(13)|Y|||TOKEN過期時間，YYYYMMDD HHMM
|||CREATE_DATE|VARCHAR(13)|Y|||TOKEN創建時間，YYYYMMDD HHMM

## 1.7. 角色設置(ROLE_SETTING)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||ROLE|VARCHAR(100)|Y|||角色ID
|||ENABLED|BOOLEAN|Y|||角色狀態，TRUE為開啟,FALSE為關閉
|||NAME|VARCHAR(100)|Y|||角色名稱
|||DEF|VARCHAR(100)||||角色敘述

## 1.8. 路徑設定(PATH_SETTING)

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

## 1.9. 前端畫面權限設置(VIEW_PERMISSION)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||VIEW_PERMISSION|VARCHAR(100)|Y|||前端畫面權限ID
|||NAME|VARCHAR(100)|Y|||前端畫面權限名稱
|||DEF|VARCHAR(100)||||前端畫面權限敘述

## 1.10. 路徑與前端畫面權限關聯(PATH_VIEW_PERMISSION_REL)

PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||PATH|VARCHAR(100)|Y|||路徑
Y||VIEW_PERMISSION|VARCHAR(100)|Y|||前端畫面權限

## 1.11. 路徑與前端畫面權限與角色關聯(PATH_VIEW_PERMISSION_ROLE_REL)
PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||PATH|VARCHAR(100)|Y|||路徑
Y||VIEW_PERMISSION|VARCHAR(100)|Y|||前端畫面權限
Y||ROLE|VARCHAR(100)|Y|||角色

## 1.12. API權限管理(API_PERMISSION_SETTING)
PK|UNI|欄位|型態|NOT NULL|AUTO|預設|定義
:-:|:-:|-|-|:-:|:-:|-|-
Y||PATH|VARCHAR(100)|Y|||路徑
Y||ROLE|VARCHAR(100)|Y|||API權限管理
