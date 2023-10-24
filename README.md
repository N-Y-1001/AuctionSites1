# AuctionSites1
訓練学校卒業作品としてグループで作成した作品です

#--商品マスタ
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

-- ジャンルマスタ
CREATE TABLE genre (
    genre_id SERIAL PRIMARY KEY,
    genre_name VARCHAR(100)
);

-- 入札情報
CREATE TABLE bitinfo (
    goods_id INT,
    account_id INT,
    bid_time TIMESTAMP,
    current_price INT,
    PRIMARY KEY (goods_id, account_id, bid_time)
);

-- 会員マスタ
CREATE TABLE account (
    account_id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    address VARCHAR(255),
    tel VARCHAR(20),
    mail VARCHAR(100),
    password VARCHAR(100),
    money INT DEFAULT 0
);

-- コメントテーブル(チャット機能で使用)
CREATE TABLE comment (
    goods_id INT,
    account_id INT,
    comment_number SERIAL,
    goodsaccount_id INT,
    comment_content TEXT,
    comment_time TIMESTAMP,
    is_approved BOOLEAN DEFAULT false,
    PRIMARY KEY (goods_id, account_id, comment_number)
);

-- 落札商品マスタ
CREATE TABLE dropgoods (
    dropgoods_id SERIAL PRIMARY KEY,
    goods_id INT,
    name VARCHAR(255),
    genre_id INT ,
    initial_price INT,
    drop_time TIMESTAMP,
    image_number VARCHAR(255),
    comment TEXT,
    account_id INT
);

初期のジャンルをインサート
INSERT INTO genre (genre_id, genre_name)
VALUES
    (1, '家電'),
    (2, 'ファッション'),
    (3, 'スポーツ用品'),
    (4, 'コレクション'),
    (5, '美容・健康'),
    (6, '本・雑誌'),
    (7, '趣味・アウトドア'),
    (8, '車・バイク'),
    (9, '食品・お酒'),
    (10, 'その他');
