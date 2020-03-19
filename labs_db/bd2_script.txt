

CREATE DATABASE store;

CREATE TABLE store.product_type (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    typ TINYINT NOT NULL,
    PRIMARY KEY(id)
    );


CREATE TABLE store.goods (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    good_name VARCHAR(45),
    product_type_id SMALLINT UNSIGNED NOT NULL,
    PRIMARY KEY(id),
	CONSTRAINT goods_type FOREIGN KEY (product_type_id)
    REFERENCES store.product_type (id) ON DELETE NO ACTION ON UPDATE NO ACTION 
	
	);
    
CREATE TABLE store.prop_mobile (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    screen VARCHAR(45),
    cpu VARCHAR(45),
    battery VARCHAR(45),
    goods_id SMALLINT UNSIGNED NOT NULL,
    PRIMARY KEY(id),
	CONSTRAINT prop_mobile_id FOREIGN KEY (goods_id)
    REFERENCES store.goods (id) ON DELETE NO ACTION ON UPDATE NO ACTION 
	
	);

CREATE TABLE store.prop_laptop (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    screen VARCHAR(45),
    cpu VARCHAR(45),
    ram VARCHAR(45),
    video_card VARCHAR(45),
    goods_id SMALLINT UNSIGNED NOT NULL,
    PRIMARY KEY(id),
	CONSTRAINT prop_laptop_id FOREIGN KEY (goods_id)
    REFERENCES store.goods (id) ON DELETE NO ACTION ON UPDATE NO ACTION 
	
	);

CREATE TABLE store.counterparties (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    name VARCHAR(60) NOT NULL,
    PRIMARY KEY (id)
    );

CREATE TABLE store.prices (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    price_buy VARCHAR(45) NOT NULL,
    price_sell VARCHAR(45) NOT NULL,
    criteria TINYINT NOT NULL ,
    goods_id SMALLINT UNSIGNED NOT NULL,
    counterparties_id SMALLINT UNSIGNED NOT NULL,
    Primary KEY (id),
    CONSTRAINT prices_goods FOREIGN KEY(goods_id)
    REFERENCES store.goods (id) ON DELETE NO ACTION ON UPDATE NO ACTION,
    CONSTRAINT prices_counterparties FOREIGN KEY(counterparties_id)
    REFERENCES store.counterparties (id) ON DELETE NO ACTION ON UPDATE NO ACTION
    
    
    );

CREATE TABLE store.users (
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
	name VARCHAR(45) NOT NULL,
    sirname VARCHAR(45) NOT NULL,
    email VARCHAR(45),
    PRIMARY KEY (id)
    );

CREATE TABLE store.comments(
	id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
	message VARCHAR(45) NOT NULL,
    goods_id  SMALLINT UNSIGNED NOT NULL ,
	user_id  SMALLINT UNSIGNED NOT NULL ,
    Primary KEY(id),
    
    CONSTRAINT comment_goods FOREIGN KEY (goods_id)
    REFERENCES store.goods (id) ON DELETE NO ACTION ON UPDATE NO ACTION,
    
    CONSTRAINT comment_user FOREIGN KEY (user_id)
    REFERENCES store.users (id) ON DELETE NO ACTION ON UPDATE NO ACTION
);    
