# Database

Why use System Programming language for Database Development?

Rust is known for its safety and performance, which makes it great for database applications.

1. **Drivers and ORMs**: Rust has solid drivers for major databases like PostgreSQL, MySQL, and SQLite. You've got ORMs (Object-Relational Mappers) like `Diesel` which makes database interactions more Rust-like and safe.
2. **Async/Await**: Rust's async programming model works well with databases, especially for web apps. Libraries like `tokio-postgres` offer async database access.
3. **Safety and Concurrency**: Rust's focus on safety and its powerful concurrency model can help prevent common database-related bugs, like race conditions.
4. **Custom Database Systems**: Some folks even build custom database systems in Rust, thanks to its low-level control and efficiency.
5. **Web Frameworks Integration**: With Web frameworks like Actix and Rocket, integrating databases into web applications is straightforward in Rust.

**Free** Cloud-based Databases (MySQL, PostgreSQL, CouchDB, RabbitMQ)

[https://www.alwaysdata.com/en/register/?d](https://www.alwaysdata.com/en/register/?d) \
\
\------

## Read Environment Variables

```
// SET Environment Variables

// Linux or MAC

// export MY_POSTGRESQL_USERID=value

// Windows

// Goto Environment Variables and Add

fn main() {
    println!("{}",std::env::var("MY_POSTGRESQL_USERID").unwrap());
}

```

cargo.toml

```
postgres="0.19.7"
```

**Create Table**

```
use postgres::{Client, Error, NoTls};

fn main() -> Result<(), Error> {

    // clearscreen::clear().expect("failed to clear screen");

    let postgresql_userid = std::env::var("MY_POSTGRESQL_USERID").unwrap();
    let postgresql_pwd = std::env::var("MY_POSTGRESQL_PWD").unwrap();

    let conn_str = format!("postgresql://{postgresql_userid}:{postgresql_pwd}@postgresql-dbworldgc.alwaysdata.net:5432/dbworldgc_pg");

    let mut client = Client::connect(&conn_str, NoTls)?;

    client.batch_execute(
        "
    CREATE TABLE if not exists sitcoms (
        id      SERIAL PRIMARY KEY,
        name    TEXT NOT NULL,
        genre    TEXT NULL
    )
",
    )?;

    Ok(())
}

```

NoTls is a type provided by the postgres crate in Rust, which specifies that the connection to the PostgreSQL database should not use TLS (Transport Layer Security) encryption. Essentially, it indicates that the connection should be made without any encryption.

**Unencrypted Connection**: Non prod or Used in Trusted environment.
**Performance**: Faster due to absence of encryption overhead.


```
use postgres::{Client, Error, NoTls};

fn main() -> Result<(), Error> {

    clearscreen::clear().expect("failed to clear screen");

    let postgresql_userid = std::env::var("MY_POSTGRESQL_USERID").unwrap();
    let postgresql_pwd = std::env::var("MY_POSTGRESQL_PWD").unwrap();

    let conn_str = format!("postgresql://{postgresql_userid}:{postgresql_pwd}@postgresql-dbworldgc.alwaysdata.net:5432/dbworldgc_pg");

    let mut client = Client::connect(&conn_str, NoTls)?;
        
    //INSERT

    let name = "Friends";
    let genre = "RomCom";

    client.execute(
        "INSERT INTO sitcoms (name, genre) VALUES ($1, $2)", &[&name, &genre],
    )?;

    //UPDATE

    let genre = "Comedy";
    let id = 2;

    client.execute(
         "UPDATE sitcoms SET genre = $2 WHERE id = $1", &[&id, &genre],
    )?;

    //DELETE

    let id = 1;
    client.execute(
        "DELETE FROM sitcoms WHERE id = $1", &[&id],
    )?;


    // Multiple Rows Insert

    let tup_arr = [("Seinfeld","Standup"),("Charmed","Drama")];

    for row in tup_arr{
        client.execute(
            "INSERT INTO sitcoms (name, genre) VALUES ($1, $2)", &[&row.0, &row.1],
        )?;
        println!("Inserting --- {},{}",row.0,row.1);
    }

    // Read the Value

    for row in client.query("SELECT id, name, genre FROM sitcoms", &[])? {
        let id: i32 = row.get(0);
        let name: &str = row.get(1);
        let genre: &str = row.get(2);
        println!("---------------------------------");
        println!("{} | {} | {:?}", id, name, genre);
    }


    #[derive(Debug)]
    struct Sitcom {
        id: i32,
        name: String,
        genre: Option<String>, // Use Option for nullable fields
    }


    // Read the Value and store in a vector
    let mut sitcoms: Vec<Sitcom> = vec![];
    
    for row in client.query("SELECT id, name, genre FROM sitcoms", &[])? {
         let sitcom = Sitcom {
             id: row.get(0),
             name: row.get(1),
             genre: row.get(2),
         };
         sitcoms.push(sitcom);
     }

    // // Print the sitcoms vector
     for sitcom in sitcoms {
         println!("{:?}", sitcom);
     }

    Ok(())
}

```

### Transactions

```
use postgres::{Client, Error, NoTls, Transaction};

fn main() -> Result<(), Error> {
    let postgresql_userid = std::env::var("MY_POSTGRESQL_USERID").unwrap();
    let postgresql_pwd = std::env::var("MY_POSTGRESQL_PWD").unwrap();
    let conn_str = format!("postgresql://{postgresql_userid}:{postgresql_pwd}@postgresql-dbworldgc.alwaysdata.net:5432/dbworldgc_pg");

    let mut client = Client::connect(&conn_str, NoTls)?;

    // Create table
    client.batch_execute(
        "
        CREATE TABLE IF NOT EXISTS public.sitcoms_tran (
            id      SERIAL PRIMARY KEY,
            name    TEXT UNIQUE NOT NULL,
            genre   TEXT NULL
        )
        ",
    )?;

    // Start a transaction
    let mut transaction = client.transaction()?;

    // Insert rows within the transaction
    match insert_sitcoms(&mut transaction) {
        Ok(_) => {
            // If no error, commit the transaction
            transaction.commit()?;
            println!("Transaction committed.");
        },
        Err(e) => {
            // If there is an error, rollback the transaction
            transaction.rollback()?;
            eprintln!("Transaction rolled back due to error: {}", e);
        }
    }

    Ok(())
}

fn insert_sitcoms(transaction: &mut Transaction) -> Result<(), Error> {
    transaction.execute("INSERT INTO sitcoms_tran (name, genre) VALUES ($1, $2)", &[&"Seinfeld", &"RomCom"])?;

    Ok(())
}

```


### Error Handling

```
use postgres::{Client, Error, NoTls};

fn main() -> Result<(), Error> {
    let postgresql_userid = std::env::var("MY_POSTGRESQL_USERID").unwrap();
    let postgresql_pwd = std::env::var("MY_POSTGRESQL_PWD").unwrap();
    let conn_str = format!("postgresql://{postgresql_userid}:{postgresql_pwd}@postgresql-dbworldgc.alwaysdata.net:5432/dbworldgc_pg");

    let mut client = Client::connect(&conn_str, NoTls)?;

    client.batch_execute(
        "
        CREATE TABLE IF NOT EXISTS public.sitcoms (
            id      SERIAL PRIMARY KEY,
            name    TEXT NOT NULL,
            genre   TEXT NULL
        )
        ",
    )?;

    let result = client.execute("INSERT INTO sitcoms (name, genre) VALUES ($1, $2)", &[&"Friends", &"RomCom"]);

    match result {
        Ok(rows) => println!("Inserted {} row(s)", rows),
        Err(err) => eprintln!("Error inserting row: {}", err),
    }

    Ok(())
}
```