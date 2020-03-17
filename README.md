# springboot-maven-thymeleaf-mybatis-postgresql

[1] Document Details:
In this document , we will learn how to set the local java environment path, database
configuration, and other dependencies too further also explained about how to
develop the Spring Boot web application using M aven , My B atis , T hyme l eaf, and
PostgreSQL.
S tep by Step procedure to develop the web app lication and export the data sets
from database using library like DataT ables, PDFMake and Export to Excel along with
Search and Sorting options.

[2] DB Initialization:
-- Table: pgroonga.catalog_data

-- DROP TABLE pgroonga.catalog_data;

CREATE TABLE pgroonga.catalog_data
(
    ktrg_no character(20) COLLATE pg_catalog."default" NOT NULL,
    prdct_nm_jp character varying(120) COLLATE pg_catalog."default" NOT NULL,
    prdct_nm_en character varying(120) COLLATE pg_catalog."default",
    prdct_ktsk character varying(80) COLLATE pg_catalog."default",
    iri_su character varying(20) COLLATE pg_catalog."default",
    lst_price money,
    curr_cd character varying(10) COLLATE pg_catalog."default",
    mkt_price_kbn character(1) COLLATE pg_catalog."default",
    grn_skbt_kbn character(1) COLLATE pg_catalog."default",
    sell_price money,
    keyword text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT catalog_data_pkey PRIMARY KEY (ktrg_no)
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE pgroonga.catalog_data
    OWNER to postgres;

-- Index: catalog_search

-- DROP INDEX pgroonga.catalog_search;

CREATE INDEX catalog_search
    ON pgroonga.catalog_data USING pgroonga
    (keyword COLLATE pg_catalog."default")
    TABLESPACE pg_default;
