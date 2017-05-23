---
layout: post
title: "Build API with Sequelize"
quote : a promise-based ORM for Node.js.
date: "2017-04-09 23:27:57 +0700"
---

Sequelize is a promise-based ORM for Node.js v4 and up. It supports the dialects PostgreSQL, MySQL, SQLite and MSSQL and features solid transaction support, relations, read replication and more.

# Install

{% highlight ruby %}npm install --save sequelize mysql{% endhighlight %}

# Init

{% highlight ruby %}sequelize init{% endhighlight %}

# Create model

{% highlight ruby %}sequelize model:create --name User --attributes idAgent:string,password:string,name:string,area:string,email:string,noHp:string,role:string{% endhighlight %}

# Running Migrations

{% highlight ruby %}sequelize db:migrate{% endhighlight %}

# Create Controller

{% highlight ruby %}
const User = require('../models').User;

module.exports = {
    // gel list of All Users
    getAll(req, res){
        User.findAll()
            .then(function(data){
                res.status(200).json(data)
            })
            .catch(function(err){
                res.status(500).json(err)
            })
    },
    getId(req, res){
        User.findById(req.params.id)
            .then(function(data){
                res.status(200).json(data)
            })
            .catch(function(err){
                res.status(500).json(err)
            })
    },
    create(req, res){
        User.create(req.body)
            .then(function(data){
                res.status(200).json(data)
            })
            .catch(function(err){
                res.status(500).json(err)
            })
    },
    update(req, res){
        User.update(req.body, {
            where : {
                id : req.params.id
            }
        })
            .then(function(data){
                res.status(200).json(data)
            })
            .catch(function(err){
                res.status(500).json(err)
            })
    },
    delete(req, res){
        User.destroy({
            where : {
                id : req.params.id
            }
        })
            .then(function(data){
                res.status(200).json(data)
            })
            .catch(function(err){
                res.status(500).json(err)
            })
    },        
}

{% endhighlight %}

# Adding API Endpoints

{% highlight ruby %}
const UserCtrl = require('../controller/users');

router.get('/', UserCtrl.getAll);
router.get('/:id', UserCtrl.getId);
router.post('/register', UserCtrl.create);
router.put('/edit/:id', UserCtrl.update);
router.delete('/delete/:id', UserCtrl.delete);
{% endhighlight %}