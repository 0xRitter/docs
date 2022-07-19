## 获取所有工厂合约铸造的地址:
```
query Factories(
    $where: factoryWhereInput!
){
  factories(where: $where) {
    id
    height
    tx_hash
    tx_time
    creator
    owner
    address
    master_address
    contract_type
    created_time
    updated_time
  }
}

Query Variables: {"where":{}}
```

## 获取所有LazyMint上架记录(lazy mint列表)
```
query PreMints(
    $where: pre_mintWhereInput!
){
  preMints(where: $where) {
    id
    owner
    contract
    name
    symbol
    base_uri
    royalty_receiver
    royalty_rate
    begin_time
    end_time
    tier
    price
    start_id
    end_id
    current_id
    payment_token
    created_time
    updated_time
  }
}

Query Variables: {"where":{}}
```

## 获取LazyMint购买记录(购买列表)
```
query PreMintRecords(
    $where: pre_mint_recordWhereInput!
){
  preMintRecords(where: $where) {
    id
    height
    tx_hash
    tx_time
    from
    to
    recipient
    contract
    tier
    token_id
    price
    payment_token
    created_time
    updated_time
  }
}

Query Variables: {"where":{}}
```

## 获取所有铸造出来的Erc721合约地址(erc721合约列表)
```
query Record721s(
    $where: record_721WhereInput!
){
  record721s(where: $where) {
    id
    height
    tx_hash
    tx_time
    token
    name
    symbol
    owner
    base_uri
    created_time
    updated_time
  }
}

Query Variables: {"where":{}}
```

## 获取我的NFT列表(只有工厂合约铸造出来的合约地址, 地址要全小写)
```
query Assets721s(
    $where: assets_721WhereInput!
){
  assets721s(where: $where) {
    id
    height
    tx_hash
    tx_time
    token
    token_id
    owner
    uri
    created_time
    updated_time
  }
}

Query Variables: {"where":{"owner": {"equals": "0x9a70b15c2936d440c82eb988a20f11ef2cd79395"}}}
```
