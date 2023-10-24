# AuctionSites1
これは訓練学校の卒業作品としてグループで作成したオークションサイトのデータベース設計です。

## テーブル定義

### 商品マスタ
```sql
CREATE TABLE goods (
    goods_id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    genre_id INT,
    initial_price INT,
    start_time TIMESTAMP,
    end_time TIMESTAMP,
    image_number VARCHAR(255),
    comment TEXT,
    account_id INT
);

