```startuml
@startuml

package "ECサイト" as target_system {
  entity "購入テーブル" <d_parchase>{
    + order_id [PK]
    --
    customer_code
    purchase_date
    total_price
  }

  entity "購入テーブル詳細" <d_purchase_detail> {
    +detail_id[PK]
    +order_id [PK]
    --
    item_code
    price
    num
  }

  entity "ユーザー（顧客）テーブル" <m_customers> {
    +customer_code[PK]
    +pass [PK]
    --
    name
    address
    tel
    mail 
    del_flag
    reg_date
  }
  
  entity "カテゴリーテーブル" <m_category> {
    +category_id [PK]
    --
    name
    reg_date
  }

  entity "商品テーブル" <m_items> {
    +item_code [PK]
    --
    item_name
    price
    category_id
    image
    detail
    del_flag
    reg_date
    }

"ユーザー（顧客）テーブル" |o-ri-o{ "購入テーブル"
"購入テーブル詳細" }--|| "商品テーブル"


}

 
@enduml
```
