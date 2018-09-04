## tw.bitasset.com REST API

API endpoint for tw.bitasset.com

This documentation contains API end points for the following services

1.  [Third party Payment Receiption API](#head1)
2.  [Third party payment WriteOff(对账) API](#head2)
3.  [User data one-way synchronization REST API](#head3)
3-1.  User
3-2.  UserBank
3-3.  asset_cny_bank_bill_detail
4.  Bank Transfer Payment Receiption API (Not yet implemented)
5.  Bank Transfer Payment Receiption WriteOff(对账) API (Not yet implemented)
6.  Future works to be announced.

Live URL:
https://api.tw.bitasset.com/

Test URL:
http://test.tw.bitasset.com/

## <a name="head1"></a>1. Third-party Payment Receipt API

### PUT `/core/thirdparty/[user Id]/[Bank ID]/[TransactionID]`

Newly create thirdparty payment transaction with user Id, bank Id and Transaction ID.

#### Request:

| sno | Field type | field name         | Memo                  |
|-----|------------|--------------------|-----------------------|
| 1   | Integer    | id                 | 交易流水序號          |
| 2   | Integer    | fbid               | 銀行機構 ID 序號      |
| 3   | String     | transferFrom       | 帳號='spgateway'      |
| 4   | Date       | transferTime       | 交易日期              |
| 5   | String     | transferStatus     | 交易狀態              |
| 6   | String     | metchantId         | 商家代碼              |
| 7   | String     | checkValue         | 檢查碼                |
| 8   | String     | itemDesc           | 商品資訊              |
| 9   | BigDecimal | transferFromAmount | 金額                  |
| 10  | String     | email              | Email                 |
| 11  | String     | orderComment       | 商店備註              |
| 12  | Boolean    | credit             | 信用卡 一次付清啟用   |
| 13  | Boolean    | instFlag           | 信用卡 分期付款啟用   |
| 14  | Boolean    | unionPay           | 銀聯卡啟用            |
| 15  | Boolean    | webatm             | WEBATM 啟用           |
| 16  | Boolean    | vacc               | ATM 轉帳啟用          |
| 17  | Boolean    | cvs                | CVS 超商代碼繳費 啟用 |
| 18  | Boolean    | barcode            | Barcode 條碼繳費啟用  |

`transferStatus` 's initial status is `Pending`
`transferStatus` has `Pending`, `Success`, `Cancelled`, `Failed`

The status will be changed with the next API `/core/thirdparty/notify/[user Id]/Bank ID]/[TransactionID]`


> note:
> In a perfect situation, user ID is actually not required but in order to make sure synchronization of User data is done prior to making a transaction, so we need the user ID to double check everything is correct.


\
\
### POST `/core/thirdparty/[user Id]/[Bank ID]/[TransactionID]`

Update Transaction in case there are changes

#### Request:
The parameter used is the same as PUT operation


### POST `/core/thirdparty/notify/[user Id]/[Bank ID]/[TransactionID]`

#### Request:
| sno | Field type | field name      |  memo               |
|-----|------------|-----------------|---------------------|
| 1   | String     | transferStatus  | 交易狀態            |
| 2   | String     | notifyErrorCode | 请参考 八，错误代码 |
| 3   | String     | notify_message  | 回傳訊息            |
| 4   | JSON       | notify_result   | 回傳資料            |




NotifyURL



```sss
```
