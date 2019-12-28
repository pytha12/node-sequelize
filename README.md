# node-sequelize
Node sequelize ORM. Models, Migrations, Seeding, Config, DB connection to Postgres Db

# Steps
1. npm install sequelize sequelize-cli pg pg-hstore
2. touch .sequelizerc (update .sequelizerc)
3. sequelize init
4. Update config
5. Create db Url :
        createdb dev_db -U <db_user>
        createdb test_db -U <db_user>
        
        connection string from above...
        
        postgres://<db_user>:<db_password>@127.0.0.1:5432/dev_db
        postgres://<db_user>:<db_password>@127.0.0.1:5432/test_db
        
        .env:
        DATABASE_URL=
        DEV_DATABASE_URL=postgres://<db_user>:<db_password>@127.0.0.1:5432/dev_db
        TEST_DATABASE_URL=postgres://<db_user>:<db_password>@127.0.0.1:5432/test_db
        
6. Create Models and Migrations:

        sequelize model:generate --name User --attributes name:string,email:string
        sequelize model:generate --name Post --attributes title:string,content:text,userId:integer
        sequelize model:generate --name Comment --attributes postId:integer,comment:text,userId:integer  
        
7. Remember to add notNull constraints to foreign keys
8. Define the model relationships. 1:many or hasMany and belongsTo in models' associate section
9. sequelize db:migrate

10. Seeding data to database:
        sequelize seed:generate --name User
        sequelize seed:generate --name Post
        sequelize seed:generate --name Comment  
        
11. sequelize db:seed:all
  
# reference
https://www.oriechinedu.com/posts/getting-started-with-sequelize-and-postgres
