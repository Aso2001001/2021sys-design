```startuml
@startuml
entity "購入テーブル" <d_parchase> {
  + order_id [PK]
  --
  customer_code
  purchase_date
  total_price
}

entity "購入テーブル詳細" <d_purchase_detail> {
  +detail_id[PK]
  --
  order_id
  item_code
  price
  num
}



@enduml
```
