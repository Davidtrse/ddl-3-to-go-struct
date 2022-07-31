<h3 align="center">
  DDL (sql) to Go Struct
</h3>

This is a simple tool to convert the DDL instructions to a struct in Goland using the SQL package.

The steps is simple.

First select the ddl create table instructions, example:
```sql
CREATE TABLE IF NOT EXISTS apps
(
    id uuid NOT NULL DEFAULT uuid_generate_v4 (),
    app_nome varchar(255) NOT NULL UNIQUE,
    app_icone varchar(255),
    app_ativa boolean NOT NULL DEFAULT true,
    created_at timestamp with time zone NOT NULL DEFAULT now(),
    updated_at timestamp with time zone NOT NULL DEFAULT now(),
    deleted_at timestamp with time zone,    
    CONSTRAINT apps_pkey PRIMARY KEY (id)
);
```

Then type `CTRL+SHIFT+p`

And run the `DDLTOGS: Convert the DDL (SQL) instructions to Go Struct` to convert the sql text selected to go struct

Or just select it and press `CTRL+SHIFT+i`

Will result in:

```go
// apps --
	ID	uuid.UUID	`db:"id"`
	APPNome	string	`db:"app_nome"`
	APPIcone	*string	`db:"app_icone"`
	APPAtiva	bool	`db:"app_ativa"`
	CreatedAT	*time.Time	`db:"created_at"`
	UpdatedAT	*time.Time	`db:"updated_at"`
	DeletedAT	time.Time	`db:"deleted_at"`
```

## Edition of Code

```
npm install -g vsce

cd /extension
vsce package

- The file will be generated: ddl-to-go-struct-0.0.3.vsix

- Right click on the file and install the vsix extension
```

## Publish

```
vsce publish -p <token>

or access link direct and click in + New extension

https://marketplace.visualstudio.com/manage/publishers/farnetani
```

## Creating a new extension

```
npm install -g yo generator-code

yo code
```

## Version
`V0.0.7`

## License

This project is a copy of the extension: [https://github.com/farnetani/ddl-to-go-struct](https://github.com/farnetani/ddl-to-go-struct) with customizations made by me to accept varchar and uuid fields for the my private use. I'm not responsible for any bugs/problems.

Customized and Refactored with :heart: by [David Tran](https://github.com/Davidtrse)
