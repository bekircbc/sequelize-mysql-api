# config.json

            "development": {
            "username": "root",
            "password": "rootroot",
             "database": "flashcard",
             "host": "127.0.0.1",
             "dialect": "mysql"
            },

# mysql

            sudo mysql -p
            create database flaschcard
            use flashcard
            select * from Flashcards

# postman

            POST -- http://localhost:3070/flashcards

                    {
          "category":"vim",
          "front":"duploicate line",
          "back":"yyp"
        }

                {
          "category":"git",
          "front":"hold the line",
          "back":"git log -1"
        }
