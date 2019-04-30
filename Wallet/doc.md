# Wallet Restful API Documentation
## NOTICES

## URL

  * API : http://wallet.gramgoldlab.com/api/v1/
  * All records of transaction on TRON blockchain : https://shasta.tronscan.org/#/contract/TLciAxFyz54pt7haMDpnDSD8vFjk5hzePR

SSL will be accomplished soon.

## Table of Contents

1. [Play](#play)
1. [Balance](#balance)

### Play

告知每一筆下注及派彩結果給錢包

* **URL**

  * /play

* **Method:**

  `POST`
  
* **Request:**

  * **JSON Body (Player wins: winAmount > 0):** 
 
  {"timestamp":1556270669,"betAmount":100, "winAmount":200, "round":1556271724,"unlockToken":"GKps4KAYe5MRGEL35zh4NyuAdpHFVowmSXESAYmU12s6","walletAddress":"TAVQVeCSVX43pzu2BTHrgsLLTaLkvQxxcD" }
  
  * **HASH:** 
 
 ```
$message = '{"timestamp":1556270669,"betAmount":100, "winAmount":200, "round":1556271724,"unlockToken":"GKps4KAYe5MRGEL35zh4NyuAdpHFVowmSXESAYmU12s6","walletAddress":"TAVQVeCSVX43pzu2BTHrgsLLTaLkvQxxcD" }';

$secret_key = '<AS MENTIONED BEFORE>';

hash_hmac('SHA256',  $message, $secret_key)
  
  ```
 
 
  * **JSON Content:**

    | Field           | Required | Type     | Description                                                      |
    |:----------------|:---------|:---------|:-----------------------------------------------------------------|
    | timestamp       | Yes      | Long     | 發出請求的時間戳，以毫秒為單位的 Epoch time(UTC milliseconds since 1/1/1970) |
    | unlockToken     | Yes      | String   |                                                                  |
    | walletAddress   | Yes      | String   |                                                                  |
    | betAmount  | Yes      | Long   | 玩家下注金額 |
    | winAmount  | Yes      | Long   | 玩家贏得派彩。沒有贏得派彩也必須帶0 |
    | round      | Yes      | Int    | 局辨識碼，是唯一值 |

* **Success Response:**

  * **Content:**

    | Field           | Type     | Description                                                      |
    |:----------------|:---------|:---------|
    | status          | String   | 信息回應狀態說明，如果成功請回傳 "success";如果有其他錯誤，請回傳特定的錯誤信息。該錯誤信息不會顯示在玩家的遊戲畫面，而是用以協助遊戲平台追蹤或 解決相關問題 |
    | statusCode      | Int      |                                                                  |
    | userMessage     | String   |              |
    | balance         | Long     | 玩家錢包最新的餘額 | 
    | nextUnlockToken | String   |              |
    | walletAddress   | String   |              |


* **Sample Call:**

  ```
  /play?hash=c9570f6c74f38e45714e67c746562f292744558c24b07433ebfd0efcb1f0c29e
  
  ```
 
### Balance

查詢餘額

* **URL**

  * /balance

* **Method:**

  `POST`
  
* **Request:**

  * **JSON Body** 
 
    {"timestamp":1556270669,"walletAddress":"TAVQVeCSVX43pzu2BTHrgsLLTaLkvQxxcD","unlockToken":"GKps4KAYe5MRGEL35zh4NyuAdpHFVowmSXESAYmU12s6" }
 
  * **JSON Content:**

   | Field           | Required | Type     | Description                                                      |
    |:----------------|:---------|:---------|:-----------------------------------------------------------------|
    | timestamp       | Yes      | Long     | 發出請求的時間戳，以毫秒為單位的 Epoch time(UTC milliseconds since 1/1/1970) |
    | unlockToken     | Yes      | String   |                                                                  |
    | walletAddress   | Yes      | String   |                                                                  |

* **Success Response:**

  * **Content:**

    | Field           | Required | Type     | Description                                                      |
    |:----------------|:---------|:---------|:-----------------------------------------------------------------|
    | status          | Yes      | String   | 信息回應狀態說明，如果成功請回傳 "success";如果有其他錯誤，請回傳特定的錯誤信息。該錯誤信息不會顯示在玩家的遊戲畫面，而是用以協助遊戲平台追蹤或 解決相關問題 |
    | statusCode      | Int      |                                                                  |
    | userMessage     | String   |              |
    | balance         | Long     | 玩家錢包最新的餘額 | 
    | walletAddress   | String   |              |
    
* **Sample Call:**

  ```
  /balance?hash=663187fac4edbcdff62ea239deacc34719305749201267929e
  
  ```
