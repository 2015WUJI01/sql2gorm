# sql2gorm

sql2gorm is a command line tool to generate Go code with [Gorm](https://gorm.io/) Tag and Json Tag from SQL.

Web tool: https://sql2gorm.mccode.info/

## Download

```
go build -o /usr/local/bin/sql2gorm
```

## Usage (Command Line)

generate struct from arguments

```bash
sql2gorm -sql="CREATE TABLE person_info (
  age INT(11) unsigned NULL,
  id BIGINT(11) PRIMARY KEY AUTO_INCREMENT NOT NULL COMMENT '这是id',
  name VARCHAR(30) NOT NULL DEFAULT 'default_name' COMMENT '这是名字',
  created_at datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  sex VARCHAR(2) NULL,
  num INT(11) DEFAULT 3 NULL,
  comment TEXT
  ) COMMENT='person info';"
```

```shell
sql="{query}"

no_backticks=$(echo "$sql" | sed 's/`//g')

sql2gorm -json -with-tablename -with-type -sql $no_backticks
```