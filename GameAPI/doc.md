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
    "playerIp":"223.27.48.212",
    "transactionId":"672f27df1dcc401fa4ed6cdc14fb78f8",
    "type":"BonusPick",
    "amount":200,
    "betAmount":200,
    "winAmount": 15,
    "jpc":0,
    "selections":5,
    "betPerSelection":2,
    "freeGames":false, 
    "round":0,
    "roundsRemaining":0
    }]

 
  * **Content:**

    | Field                 | Required | Type     | Description                                                      |
    |:----------------------|:---------|:----------------------------------------------------------------------------|
    | timestamp             | Yes      | Long     |                                                                  |
    | sessionId             | Yes      | String (32 chars)     |                                                     |
   
   

* **Success Response:**

  * **Content:**

    | Field                 | Type     | Description                                                                 |
    |:----------------------|:---------|:----------------------------------------------------------------------------|
    | status                | boolean  | TRUE/FALSE                                                                  |
    | msg                   | string   | error message                                                               |
    | info                  | JSON     | JSON Encoded                                                                |
    | - app_name                | string  | TRUE/FALSE                                                               |
    | - designer                | string   |                                                                         |
    | - app_icon                | string   | url                                                                     |
    | - purpose_of_design       | string   |                                                                         |
    | - still_missing           | string   |                                                                         |
    | - for_what_is_not_missing | string   |                                                                         |
   

* **Sample Call:**

  ```
  /start?hash=663187fac4edbcdff62ea239deacc34719305749201267929e
  
  ```
 
