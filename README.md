# fc-sms-service

# Attention

* Not to use <https://github.com/zenazn/goji>. Checkout the later version <https://goji.io/>. Or look for something else widely used by the community.
* Use <https://github.com/Sirupsen/logrus> for logging for structure logging. The motivation is to easily take advantage of logrus hooks to centralize logs data into one searchable place. With the `correlation_id` on every payload, it should be possible to trace the whole data flow through all micro services.
* Do not share models or business logic code across services.

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
