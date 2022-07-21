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


## Metadata存储
```
mutation CustomCreateNFTMeta(
  $Artists: [String!]
  $AudioTrack: String!
  $CoverArtwork: String!
  $TrackInfo: String
	$TrackDescription: String
	$Title: String
	$RecordLabel: [String]
	$Tiers: [MetadataTierJson!]!
  $VibeProperties: [MetadataAttribute!]
){
  customCreateNFTMeta(
    Artists: $Artists
    AudioTrack: $AudioTrack
    CoverArtwork: $CoverArtwork
    TrackInfo: $TrackInfo
    TrackDescription: $TrackDescription
    Title: $Title
    RecordLabel: $RecordLabel
    Tiers: $Tiers
    VibeProperties: $VibeProperties
  ) {
    baseUri
    success
  }
}

Query Variables:
{
  "Artists": ["Artist1"],
  "AudioTrack": "https://audioTrack.com",
  "CoverArtwork": "https://coverArtwork",
  "TrackInfo": "trackInfo",
  "TrackDescription": "trackDescription",
  "Title": "title",
  "RecordLabel": ["recordLabel"],
  "Tiers": [{
    "TierID": 1,
    "TierName": "tierName1",
    "StartID": 0,
    "EndID": 9,
    "Attributes": [{
      "TraitType": "autograph",
      "Value": "https://autograph.com"
    }]
  }]
}
```


## 分页步骤
```
1. 先取回所需数据的总数
query Record721sCount(
  $where: record_721WhereInput!
){
  record721sCount(where: $where) 
}
Query Variables: {"where": {}}


2. 分页获取, 偏移skip: 0, 条数take: 2
query Record721s(
  $where: record_721WhereInput!
  $take: Int
  $skip: Int!
){
  record721s(where: $where, take: $take, skip: $skip) {
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
Query Variables: {"where":{},"take": 2, "skip": 0}

注意，需要两个请求的where条件相同
```

## 获取所有拍卖池子
```
query AuctionPools(
    $where: auction_poolWhereInput!
){
  auctionPools(where: $where) {
    id
    height
    tx_hash
    tx_time
    creator
    pool_id
    name
    token0
    token1
    token_id
    token_amount0
    swapped_amount0
    amount_total1
    amount_max1
    amount_min1
    amount_min_incr1
    price
    duration
    open_at
    close_at
    nft_type
    auction_type
    creator_claimed
    bidder_claimed
    state
    royalty_receiver
    royalty_ratio
    created_time
    updated_time
  }
}

Query Variables: {"where": {}}
```
