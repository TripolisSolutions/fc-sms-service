# fc-sms-service

## description
Golang service to send sms messages.

Sample use cases are sms notification for vitim's members and sms registration confirm number.

The service will run workers. Example worker's payload:

```json
{
  correlation_id,
  tenant_id,
  user_id,
  provider,
  message,
  ...
}
```

`provider` can be (`viettel`, `mobiphone`)

### Events
The service should publish the appropriate message to the message bus when these events happen: `event.sms.sent`

```json
{
  correlation_id
  tenant_id
  doc {
    user_id
    provider
    message
  }
}
```

## references
* <https://tinhte.vn/threads/viettel-dang-thu-nghiem-kinh-doanh-api-ap-dung-voi-cac-nha-phat-trien-game-ung-dung.2491797/>

* <http://www.shoponeviettel.com.vn/tin-nhan-thuong-hieu-sms-brand-name-viettel-gia-re-245d.html>
