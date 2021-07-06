```startuml
@startuml
entity "購入テーブル" <d_parchase> {
  + order_id [PK]
  --
  customer_code
  purchase_date
  total_price
}
@enduml
```
