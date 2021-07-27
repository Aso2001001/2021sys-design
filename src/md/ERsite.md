```startuml
@startuml

!define MASTER_MARK_COLOR Orange 
!define TRANSACTION_MARK_COLOR DeepSkyBlue
skinparam class {
    BackgroundColor Snow
    BorderColor Black
    ArrowColor Black
}


package "ECサイト" as target_system {
  entity "購入テーブル" as purchase <d_parchase> <<T,TRANSACTION_MARK_COLOR>> {
    + order_id [PK]
    --
    customer_code
    purchase_date
    total_price
  }

  entity "購入テーブル詳細" as purchase_detail <d_purchase_detail> <<T,TRANSACTION_MARK_COLOR>> {
    +detail_id[PK]
    +order_id [PK]
    --
    item_code
    price
    num
  }

  entity "ユーザー（顧客）テーブル" as customer <m_customers> <<M,MASTER_MARK_COLOR>> {
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
  
  entity "カテゴリーテーブル" as category <m_category> <<M,MASTER_MARK_COLOR>>  {
    +category_id [PK]
    --
    name
    reg_date
  }

  entity "商品テーブル" as items <m_items> <<M,MASTER_MARK_COLOR>> {
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
    
    entitiy "お気に入り商品テーブル" as f_items <f_items> <<T,TRANSACTION_MARK_COLOR>> {
    +item_code[PK]
    }

customer |o-ri-o{ purchase
purchase_detail }--|| items
purchase ||-ri-|{ purchase_detail
items }o-le-|| category
items ||--|| f_items


}

 
@enduml
```
