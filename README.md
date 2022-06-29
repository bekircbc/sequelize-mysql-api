# import vs. require

      add "type":"module" in package.json
      import express from "express"

      const express = require('express')

- if you use sequelize, choose require instead of import.

# config.json in sequelize

      "development": {
      "dialect": "sqlite",
      "storage": "data/main.sqlite"
      },

# create Flaschcard model and migration

      sequelize model:generate --name Flashcard --attributes category:string,front:string,back:string

# add async-await and sequelize model to server.js

      const { sequelize } = require("./models");

      app.listen(port, async () => {
      console.log(`Listening on http://localhost:${port}`);
      await sequelize.sync();
      });

# create API routes in sever.js

      const { sequelize, Flashcard } = require('./models');

      app.use(express.json());

      app.post('/flashcards', async (req, res) => {
      const { category, front, back } = req.body;
      try {
        const flashcard = await Flashcard.create({ category, front, back });
        return res.json(flashcard);
      } catch (err) {
        console.log(err);
        return res.status(500);
      }
      });

      ## test in Postman

      POST -- http://localhost:PORT/flashcards

        {
          "category":"vim",
          "front":"duploicate line",
          "back":"yyp"
        }

# getting flashcards

      app.get('/flashcards', async (req, res) => {
      try {
        const flashcards = await Flashcard.findAll();
        return res.json(flashcards);
        } catch (err) {
        console.log(err);
        return res.status(500);
        }
        });
