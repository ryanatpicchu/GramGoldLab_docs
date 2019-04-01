# Game Restful API Documentation

## URL

  * http://game.gramgoldlab.com/api/v1/

SSL will be accomplished soon.

## Table of Contents

1. [Start](#start)
1. [Play](#play)
1. [Balance](#balance)
1. [Credit](#credit)
1. [End](#end)
1. [Revoke](#revoke)


### Start

開始新遊戲會話

* **URL**

  * /start

* **Method:**

  `POST`
  
* **Request:**

  * **Json Body:** 
 
    [{ 
    "timestamp":1503383341514,
    "sessionId":"375e3e418a45494c92bf1e6ec2f7460e", 
    "partnerPlayerId":"demouserf",
    "currency":"ISO 4217",
    "gameId":"Vampire",
    "action":"play",
    "playerIp":"223.27.48.212"
    }]

 
  * **Content:**

    | Field           | Required | Type     | Description                                                      |
    |:----------------|:---------|:---------|:-----------------------------------------------------------------|
    | timestamp       | Yes      | Long     | 發出請求的時間戳，以毫秒為單位的 Epoch time(UTC milliseconds since 1/1/1970) |
    | sessionId       | Yes      | String (32 chars)     | 遊戲會話識別碼，這個數值由KA 遊戲平台 在新遊戲開啟時創建，並且在整個遊戲過程 中維持不變 |
    | partnerPlayerId | Yes      | String   | 遊戲啟動鏈結中指定的合作夥伴玩家識別碼，這個數值由合作夥伴錢包系統創建，必須具有唯一性，能永久識別個別玩家 |
    | currency        | Yes      | String   | 遊戲啟動鏈結中指定的貨幣代碼 (ISO 4217) |
    | gameId          | Yes      | String   | 遊戲啟動鏈結中指定的遊戲識別碼 |
    | token           | No       | String   | 遊戲啟動鏈結中指定的權杖，該權杖由合作夥伴的錢包系統創建 |
    | operatorName    | No       | String   | 遊戲啟動鏈結中指定的合作夥伴子品牌或代理商 |
    | action          | Yes      | String   | 信息類型，包含:start, balance, play, credit, end, revoke |
    | playerIp        | Yes      | String   | 玩家 IP 位址 (IPv4 或 IPv6) |
   
   

* **Success Response:**

  * **Content:**

    | Field           | Required | Type     | Description                                                      |
    |:----------------|:---------|:---------|:-----------------------------------------------------------------|
    | status          | Yes      | String   | 信息回應狀態說明，如果成功請回傳 "success";如果有其他錯誤，請回傳特定的錯誤信息。該錯誤信息不會顯示在玩家的遊戲畫面，而是用以協助遊戲平台追蹤或 解決相關問題 |
    | statusCode      | Yes      | Int      |                                                                  |
    | userMessage     | No       | String   | 如果有指定該欄位，則在遊戲中以對話框方式向玩家顯示該信息。這可以用來即時通知玩家各種信息，例如:帳戶狀態、錯誤發生或是獲得的獎勵活動獎金 |

* **Sample Call:**

  ```
  /start?hash=663187fac4edbcdff62ea239deacc34719305749201267929e
  
  ```
 
