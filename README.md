## tw.bitasset.com REST API

API endpoint for tw.bitasset.com

This documentation contains API end points for the following services

reference: third party payment documentation version:1.4
https://cwww.spgateway.com/website/Page/content/download_api


1.  [Third party Payment Receiption API](#head1)
2.  [User data one-way synchronization REST API](#head2)
2-1.  User
2-2.  UserBank
2-3.  asset_cny_bank_bill_detail
3.  Bank Transfer Payment Receiption API (Not yet implemented)
4.  Bank Transfer Payment Receiption WriteOff(对账) API (Not yet implemented)
5.  Future works to be announced.


Live URL:
https://api.tw.bitasset.com/


Test URL:
http://test.tw.bitasset.com/



## <a name="head1"></a>1. Third-party Payment Receipt API

### PUT `/core/TWDThirdPartyBill/[TransactionID]`

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
| 7   | String     | tradeInfo          | 檢查碼                |
| 8   | String     | tradeSha           | 檢查碼                |
| 9   | String     | itemDesc           | 商品資訊              |
| 10  | BigDecimal | transferFromAmount | 金額                  |
| 11  | String     | email              | Email                 |
| 12  | String     | orderComment       | 商店備註              |
| 13  | Boolean    | credit             | 信用卡 一次付清啟用   |
| 14  | Boolean    | instFlag           | 信用卡 分期付款啟用   |
| 15  | Boolean    | unionPay           | 銀聯卡啟用            |
| 16  | Boolean    | webatm             | WEBATM 啟用           |
| 17  | Boolean    | vacc               | ATM 轉帳啟用          |
| 18  | Boolean    | creditRed          | 信用卡紅利支付方式 啟用 |
| 19  | Boolean    | p2g                | Pay2go 電子錢包支付  |
| 20  | Boolean    | barcode            | Barcode 條碼繳費啟用  |


`transferStatus` 's initial status is `Pending`
`transferStatus` has `Pending`, `Success`, `Cancelled`, `Failed`

The status can be changed with the next API `/core/thirdparty/notify/[user Id]/Bank ID]/[TransactionID]`

 \
> note:
> In a perfect situation, user ID is actually not required but in order to make sure synchronization of User data is done prior to making a transaction, so we need the user ID to double check everything is correct.

> Important
> I assume `User` to `UserBank` is a one-to many relationship and bank to transaction is a one-to-many relationship. But when third party payment is used, it is assumed to be the role of the `UserBank`. If this assumption is incorrect, please inform me asap.

 \

### POST `/core/TWDThirdPartyBill/`

Update Transaction in case there are changes

#### Request:
The parameter used is the same as PUT operation

\

### POST `/core/TWDThirdPartyBill/notify/[TransactionID]`

#### Request:
| sno | Field type | field name      |  memo               |
|-----|------------|-----------------|---------------------|
| 1   | String     | transferStatus  | 交易狀態            |
| 2   | String     | notifypaymentType  | 支付方式 请参考 note1           |
| 3   | String     | notifyErrorCode | 请参考 八，错误代码 |
| 4   | String     | notifyMessage  | 回傳訊息            |
| 5   | JSON       | notifyResult   | 回傳資料            |

note1: 支付方式 = CREDIT、ANDROIDPAY、SAMSUNGPAY、InstFlag、CreditRed、 UNIONPAY、WEBATM、VACC、CVS、BARCODE、P2G、CVSCOM
\

## <a name="head2"></a>2. User data one-way synchronization REST API


to be continued...


```sss
```
