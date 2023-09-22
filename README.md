# Mario-Game

2hrs to code Mario with Auth + save scores | JavaScript, CSS, HTML

https://www.youtube.com/watch?v=1CVSI3MZNNg 

https://raw.githubusercontent.com/RodrigoMvs123/Mario-Game/main/README.md

https://github.com/RodrigoMvs123/Mario-Game/blame/main/README.md

https://www.npmjs.com/package/jsdelivr 
https://kaboomjs.com/

AppWrite
https://appwrite.io/ 

AppWrite / Personal Projects / Mario

Visual Studio Code
EXPLORER
OPEN EDITORS 
index.html

index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mario Game</title>
</head>
<body>
    
</body>
</html>

Visual Studio Code
EXPLORER
OPEN EDITORS 
index.html
styles.css
game.js 

index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mario Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    
    <div id="modal" class="modal">
        <div class="button-container">
            <button id="register-button">Register</button>
            <button id="login-button" class="not-active">Login</button>
        </div>

        <form onsubmit="register(event)" id="register-form">
            <label for="register-email"></label>
            <input type="email" id="register-email" value="demo@example.com" required>
            <label for="register-password">Password</label>
            <input type="password" id="register-password" value="password" required pattern=".{6,}">
            <label for="register-username">Username</label>
            <input id="register-username" value="User" required>
            <br/>
            <input type="submit" value="Sign Up">
        </form>

        <form onsubmit="" id="login-form" class="hidden">
            <label for="login-email"></label>
            <input type="email" id="login-email" placeholder="demo@example.com" required>
            <label for="login-password">Password</label>
            <input type="password" id="login-password" placeholder="password" required pattern=".{6,}">         
            <br/>
            <input type="submit" value="Sign In">
        </form>
    </div>

    <div class="info-container">
        <button id="logout-button" class="hidden">Log out</button>
        <h3 id="username"></h3>
        <h3 id="highscore-tag" class="hidden">HighScore: <span id="highscore"></span></h3>
    </div>

<script src="https://kaboomjs.com/lib/0.5.0/kaboom.js"></script>
<script src="https://cdn.jsdelivr.net/npm/appwrite@11.0.0"></script>
<script src="game.js"></script>
</body>
</html>

Visual Studio Code
EXPLORER
OPEN EDITORS 
index.html
styles.css
game.js 

styles.css
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;600;700;800&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,200&family=VT323&display=swap');

* {
    font-family: 'VT323', monospace;
    font-size: xx-large;
}

body {
    margin: 0;
    overflow: hidden;
    background-color: #000;
    color: #fff;
}

.modal {
    width: 600px;
    margin: auto;
    margin-top: 100px;
}

form {
    display: flex;
    flex-direction: column;
    background-color: #0aad02;
    padding: 10px;
}

.button-container button {
    border: none;
    background-color: transparent;
    color: #fff;
    padding: 5px;
    background-color: #0aad02;
}

form input[type=submit] {
    background-color: #bb3333;
}

.button-container button.not-active {
    background-color: #808080;
}

.hidden {
    display: none;
}

.info-container {
    position: absolute;
    top: 10px;
    right: 10px;
    text-align: right;
}

h3 {
    color: #fff;
}

https://fonts.google.com/specimen/VT323?query=vt323 

Visual Studio Code
EXPLORER
OPEN EDITORS 
index.html
styles.css
game.js 

game.js
const { Client, Account, Databases, ID, Query } = Appwrite
const projectId = '65087cc07844ae9e15b2'
const databaseId = '' 
const collectionId = ''

const client = new Client()
    .setEndpoint('https://cloud.appwrite.io/v1')
    .setProject(projectId)

const account = new Account(client)

function register(event) {
    account.create (
        ID.unique(),
        event.target.elements['register-email'].value,
        event.target.elements['register-password'].value,
        event.target.elements['register-username'].value
    ).then(response => {
        console.log(response)
        // Create a document in a databse

        account.createEmailSession(
            event.target.elements['register-email'].value,
            event.target.elements['register-password'].value
        )
    }).catch(error => console.error(error))
    event.preventDefault()
}

Appwrite
https://appwrite.io/  

AppWrite / Personal Projects / Mario / Auth 
Users
Name     IDENTIFIERS            STATUS     ID           JOINED
Ania       ania@example.com   unverified   User ID   Sep 19, 2023, 15:03
Dina       ania@example.com   unverified   User ID   Sep 19, 2023, 15:10

Visual Studio Code
Terminal 
npm init

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package.json 
index.js

package.json
{
  "name": "mario-game",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}

Visual Studio Code
Terminal 
npm i express

https://www.npmjs.com/package/express 


Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

index.js 
const express = require('express')
const app = express()

app.use(express.static('public'))

const server = app.listen(8000, () => {
    const port = server.address().port
    console.log(`Appstarted at http://localhost:${port}`)
})

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

package.json
{
  "name": "mario-game",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "node index.js", 
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  }
}

Visual Studio Code
Terminal
npm run start

> mario-game@1.0.0 start
> node index.js

Appstarted at http://localhost:8000

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

game.js
const { Client, Account, Databases, ID, Query } = Appwrite
const projectId = '65087cc07844ae9e15b2'
const databaseId = '650b2fe269955675ae09' 
const collectionId = '650b30519a8feccf250f'

const client = new Client()
    .setEndpoint('https://cloud.appwrite.io/v1')
    .setProject(projectId)

const account = new Account(client)
const database = new Databases(client)

function register(event) {
    account.create (
        ID.unique(),
        event.target.elements['register-email'].value,
        event.target.elements['register-password'].value,
        event.target.elements['register-username'].value
    ).then(response => {
        console.log(response)
        databse.createDocument(
            databaseId,
            collectionId
        )

        account.createEmailSession(
            event.target.elements['register-email'].value,
            event.target.elements['register-password'].value
        )
    }).catch(error => console.error(error))
    event.preventDefault()
}

Appwrite 
https://appwrite.io/ 

AppWrite / Personal Projects / Mario / Databases
Create database
Name
game
create
Database Id - 650b2fe269955675ae09 

Create collection 
Name
highscores
            Collection Id - 650b30519a8feccf250f

AppWrite / Personal Projects / Mario / Databases / game / highscores 

AppWrite / Personal Projects / Mario / Databases / game / highscores / Attributes
Create Attribute
Attribute Key
userid
Attribute type
string
Size
300
Create
Attributes 
KEY          TYPE
userid        string

Create Attribute
Attribute Key
highscore
Attribute type
Integer
Create
Attributes 
KEY             TYPE
highscore     Integer

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

game.js
const { Client, Account, Databases, ID, Query } = Appwrite
const projectId = '65087cc07844ae9e15b2'
const databaseId = '650b2fe269955675ae09' 
const collectionId = '650b30519a8feccf250f'

const client = new Client()
    .setEndpoint('https://cloud.appwrite.io/v1')
    .setProject(projectId)

const account = new Account(client)
const database = new Databases(client)

function register(event) {
    account.create (
        ID.unique(),
        event.target.elements['register-email'].value,
        event.target.elements['register-password'].value,
        event.target.elements['register-username'].value
    ).then(response => {
        console.log(response)
        databse.createDocument(
            databaseId,
            collectionId,
            response.$id,
            {
                "userId:": response.$id,
                "highscore": 0
            }
        )

        account.createEmailSession(
            event.target.elements['register-email'].value,
            event.target.elements['register-password'].value
        )
    }).catch(error => console.error(error))
    event.preventDefault()
}

http://localhost:8000/

Appwrite 
https://appwrite.io/ 

AppWrite / Personal Projects / Mario / Databases / game / highscores / Settings / Update Permissions
Any
ROLE / CREATE / READ / UPDATE / DELETE
Update

AppWrite / Personal Projects / Mario / Databases / game / highscores / Indexes
Create index 
Index Key
userId
Attribute
userId
Create

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

game.js
const { Client, Account, Databases, ID, Query } = Appwrite
const projectId = '65087cc07844ae9e15b2'
const databaseId = '650b2fe269955675ae09' 
const collectionId = '650b30519a8feccf250f'

const client = new Client()
    .setEndpoint('https://cloud.appwrite.io/v1')
    .setProject(projectId)

const account = new Account(client)
const database = new Databases(client)

async function isLoggedIn() {
    return account.get().then(response => {
        if(response) {
            return true
        }
        return false
    }).catch(error => console.error(error))
}

function register(event) {
    account.create (
        ID.unique(),
        event.target.elements['register-email'].value,
        event.target.elements['register-password'].value,
        event.target.elements['register-username'].value
    ).then(response => {
        console.log(response)
        database.createDocument(
            databaseId,
            collectionId,
            response.$id,
            {
                "userId:": response.$id,
                "highscore": 0
            }
        )

        account.createEmailSession(
            event.target.elements['register-email'].value,
            event.target.elements['register-password'].value
        ).then(() => {
                showDisplay()
        })
    }).catch(error => console.error(error))
    event.preventDefault()
}

function login() {
    
}

function logout() {
    account.deleteSessions().then(() => {
        alert('Logged out')
        console.log('Current session deleted')
        showDisplay()
        const highScoreElement = document.getElementById('highscore')
        highScoreElement.textContent = ""
    }).catch(error => console.error(error))
}

function showDisplay {
    const modalElement = document.getElementById('modal')
    modalElement.classList.add('hidden')
    isLoggedIn().then(isLogin => {
        if (isLogin) {
            const modalElement = document.getElementById('modal')
            modalElement.classList.add('hidden')
            const logoutButton = document.getElementById('logout-button')
            logoutButton.classList.remove('hidden')
            const highScoreTag = document.getElementById('highscore-tag')
            highScoreTag.classList.remove('hidden')
            startGame()
        } else {
            const modalElement = document.getElementById('modal')
            modalElement.classList.remove('hidden')
            const logoutButton = document.getElementById('logout-button')
            logoutButton.classList.add('hidden')
            const highScoreTag = document.getElementById('highscore-tag')
            highScoreTag.classList.add('hidden')
            startGame()
            const usernameElement = document.getElementById('username')
            usernameElement.textContent = ""
            const canvas = document.querySelector('canvas')
            if (canvas) canvas.remove()
        }
    }).catch(error => console.error(error))
}

showDisplay()

// Kaboom Game
function startGame() {
    kaboom({
        global: true,
        fullscreen: true,
        scale: 2
        clearColor: [0, 0, 0, 1]
    })    

    // Speed identifiers 
    const moveSpeed = 120
    const jumpForce = 360
    const bigJumpForce = 550
    let currentJumpForce = jumpForce
    const fallDeath = 400
    const enemySpeed = 20

    // Game logic 
    let isJumping = true

    loadRoot('https://i.imgur.com/')
    loadSprite('coin', 'wbKxhcd.png')
    loadSprite('evil-shroom', 'KPO3fR9.png')
    loadSprite('brick', 'pogC9x5.png')
    loadSprite('block', 'M6rwarW.png')
    loadSprite('mario', 'Wb1qfhK.png')
    loadSprite('mushroom', '0wMd92p.png')
    loadSprite('surprise', 'gesQ1KP.png')
    loadSprite('unboxed', 'bdrLpi6.png')
    loadSprite('pipe-top-left', 'ReTPiWY.png')
    loadSprite('pipe-top-right', 'hj2GK4n.png')
    loadSprite('pipe-bottom-left', 'c1cYSbt.png')
    loadSprite('pip-bottom-right', 'nqQ79eI.png')
    loadSprite('blue-block', 'fVscIbn.png')
    loadSprite('blue-brick', '3e5YRQd.png')
    loadSprite('blue-steel', 'gqVoI2b.png')
    loadSprite('blue-evil-mushroom', 'SvV4ueD.png')
    loadSprite('blue-surprise', 'RMqCc1G.png')

    scene("game", ({ level, score }) => {
        layers(["bg", "obj", "ui"], "obj")

        const maps = [
            [
                '                                      ',
                '                                      ',
                '                                      ',
                '                                      ',
                '                                      ',
                '      %    =*=%=                      ',
                '                                      ',
                '                             -+       ',
                '                 ^     ^    ()        ',
                '======================================'
            ],
            [
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£      @@@@@@                x x          £',
                '£                          x x x          £',
                '£                        x x x x   x    -+£',
                '£              z    z  x x x x x   x    ()£',
                '!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!'
            ]
        ]

        const levelCfg = {
            width : 20,
            height : 20,
            '=' : [sprite('block'), solid()],
            '$' : [sprite('coin'), 'coin'],
            '%' : [sprite('surprise'), solid(), 'coin-surprise'],
            '*' : [sprite('surprise'), solid(), 'mushroom-surprise'],
            '}' : [sprite('unboxed'), solid()],
            '(' : [sprite('pipe-bottom-left'), solid(), scale(0.5)],
            ')' : [sprite('pipe-bottom-right'), solid(), scale(0.5)],
            '-' : [sprite('pipe-top-left'), solid(), scale(0.5), 'pipe'],
            '+' : [sprite('pipe-top-right'), solid(), scale(0.5), 'pipe'],
            '^' : [sprite('evil-shroom'), solid(), 'dangerous'],
            '#' : [sprite('mushroom'), solid(), 'mushroom', body()],
            '!' : [sprite('blue-block'), solid(), scale(0.5)],
            '£' : [sprite('blue-brick'), solid(), scale(0.5)],
            'z' : [sprite('blue-evil-mushroom'), solid(), scale(0.5), 'dangerous'],
            '@' : [sprite('blue-surprise'), solid(), scale(0.5), 'coin-surprise'],
            'x' : [sprite('blue-steel'), solid(), scale(0.5)],
        }

        const gameLevel = addLevel(maps[level], levelCfg)

        const scoreLabel = add([
            text(score),
            pos(30, 6),
            layer('ui'),
            {
                value: score
            }
        ])

        add([text(' level ' + parseInt(level + 1)), pos(40, 6)])

        const player = add([
            sprite('mario', solid()),
            pos(30, 0),
            body(),
            big(),
            origin('bot')
        ])

        function big() {
            let timer = 0
            let isBig = false
            return {
                update() {
                    if(isBig) {
                        currentJumpForce = bigJumpForce
                        timer -= dt()
                        if (timer <= 0 ) {
                            this.smallify()
                        }
                    }
                },
                isBig() {
                    return isBig
                },
                smallify() {
                    this.scale = vec2(1)
                    currentJumpForce = jumpForce
                    timer = 0
                    isBig = false
                },
                biggify(time) {
                    this.scale = vec2(2)
                    timer = time
                    isBig = true    
                }
            }
        }

        player.on("headbump", (obj) => {
            if(obj.is('coin-surprise')) {
                gameLevel.spawn('$', obj.gridPos.sub(0,1))
                destroy(obj)
                gameLevel.spawn('}', obj.gridPos.add(0,0))
            }
            if(obj.is('mushroom-surprise')) {
                gameLevel.spawn('#', obj.gridPos.sub(0,1))
                destroy(obj)
                gameLevel.spawn('}', obj.gridPos.add(0,0))
            }
        })

        action('mushroom', (m) => {
            m.move(20,0)
        })

        player.collides('mushroom', (m) => {
            destroy(m)
            player.biggify(6)
        })

            player.collides('coin', (c) => {
                destroy(c)
                scoreLabel.value++
                scoreLabel.text = scoreLabel.value
            })

        actions('dangerous', (d) => {
            d.move(-enemySpeed, 0)
        })

        player.collides('dangerous', (d) => {
            if(isJumping) {
                destroy(d)
            } else {
                go('lose', { score: scoreLabel.value })
            }
        })

        player.action(() => {
            camPos(player.pos)
            if(player.pos.y >= fallDeath) {
                go('lose', { score: scoreLabel.value })
            }
        })

        player.collides('pipe', () => {
            keyPress('down', () => {
                go('game', {
                    level: ( level + 1) % maps.length,
                    score: scoreLabel.value
                })
            })
        })

        keyDown('left', () => {
            player.move(-moveSpeed, 0)
        })

        keyDown('right', () => {
            player.move(moveSpeed, 0)
        })

        player.action(() => {
            if(player.grounded()) {
                isJumping = false
            }
        })

        keyPress('space', () => {
            if(player.grounded()) {
                isJumping = true
                player.jump(currentJumpForce)
            }
        })

        scene('lose', ({ score }) => {
            add([text(score, 32), origin('center'), pos(width() / 2, height() / 2)])
        })

    })

    start("game", { level: 0, score: 0 })


}

startGame()

https://imgur.com/a/F8Jkryq 

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mario Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    
    <div id="modal" class="modal">
        <div class="button-container">
            <button id="register-button">Register</button>
            <button id="login-button" class="not-active">Login</button>
        </div>

        <form onsubmit="register(event)" id="register-form">
            <label for="register-email"></label>
            <input type="email" id="register-email" value="demo@example.com" required>
            <label for="register-password">Password</label>
            <input type="password" id="register-password" value="password" required pattern=".{6,}">
            <label for="register-username">Username</label>
            <input id="register-username" value="User" required>
            <br/>
            <input type="submit" value="Sign Up">
        </form>

        <form onsubmit="login(event)" id="login-form" class="hidden">
            <label for="login-email"></label>
            <input type="email" id="login-email" placeholder="demo@example.com" required>
            <label for="login-password">Password</label>
            <input type="password" id="login-password" placeholder="password" required pattern=".{6,}">         
            <br/>
            <input type="submit" value="Sign In">
        </form>
    </div>

    <div class="info-container">
        <button id="logout-button" class="hidden" onclick="logout()">Log out</button>
        <h3 id="username"></h3>
        <h3 id="highscore-tag" class="hidden">HighScore: <span id="highscore"></span></h3>
    </div>

<script src="https://kaboomjs.com/lib/0.5.0/kaboom.js"></script>
<script src="https://cdn.jsdelivr.net/npm/appwrite@11.0.0"></script>
<script src="game.js"></script>
</body>
</html>

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

game.js
const { Client, Account, Databases, ID, Query } = Appwrite
const projectId = '65087cc07844ae9e15b2'
const databaseId = '650b2fe269955675ae09' 
const collectionId = '650b30519a8feccf250f'

const client = new Client()
    .setEndpoint('https://cloud.appwrite.io/v1')
    .setProject(projectId)

const account = new Account(client)
const database = new Databases(client)

async function isLoggedIn() {
    return account.get().then(response => {
        if(response) {
            return true
        }
        return false
    }).catch(error => console.error(error))
}

function register(event) {
    account.create (
        ID.unique(),
        event.target.elements['register-email'].value,
        event.target.elements['register-password'].value,
        event.target.elements['register-username'].value
    ).then(response => {
        console.log(response)
        database.createDocument(
            databaseId,
            collectionId,
            response.$id,
            {
                "userId:": response.$id,
                "highscore": 0
            }
        )

        account.createEmailSession(
            event.target.elements['register-email'].value,
            event.target.elements['register-password'].value
        ).then(() => {
                showDisplay()
        })
    }).catch(error => console.error(error))
    event.preventDefault()
}

function login(event) {
    account.createEmailSession(
        event.target.elements['login-email'].value,
        event.target.elements['login-password'].value
    ).then(() => {
        alert('Session created successfully !')
        showDisplay()
        client.subscribe("account", (response) => {
            console.log(response)
        })
    }).catch(error => {
        alert('Failed to create session')
        console.error(error)
    })
    event.preventDefault()
}

function logout() {
    account.deleteSessions().then(() => {
        alert('Logged out')
        console.log('Current session deleted')
        showDisplay()
        const highScoreElement = document.getElementById('highscore')
        highScoreElement.textContent = ""
    }).catch(error => console.error(error))
}

function toggleModal(event) {
    const registerForm = document.getElementById('register-form')
    const loginForm = document.getElementById('login-form')
    const loginButton = document.getElementById('login-button')
    const registerForm = document.getElementById('register-button')

    if (event.srcElement.id === 'register-button') {
        registerForm.classList.remove('hidden')
        loginForm.classList.add('hidden')
        loginButton.classList.add('not-active')
        registerButton.classList.remove('not-active')
    }
    if (event.srcElement.id === 'login-button') {
        registerForm.classList.add('hidden')
        loginForm.classList.remove('hidden')
        loginButton.classList.remove('not-active')
        registerButton.classList.add('not-active')
    }
}

function showDisplay {
    const modalElement = document.getElementById('modal')
    modalElement.classList.add('hidden')
    isLoggedIn().then(isLogin => {
        if (isLogin) {
            const modalElement = document.getElementById('modal')
            modalElement.classList.add('hidden')
            const logoutButton = document.getElementById('logout-button')
            logoutButton.classList.remove('hidden')
            const highScoreTag = document.getElementById('highscore-tag')
            highScoreTag.classList.remove('hidden')
            startGame()
        } else {
            const modalElement = document.getElementById('modal')
            modalElement.classList.remove('hidden')
            const logoutButton = document.getElementById('logout-button')
            logoutButton.classList.add('hidden')
            const highScoreTag = document.getElementById('highscore-tag')
            highScoreTag.classList.add('hidden')
            startGame()
            const usernameElement = document.getElementById('username')
            usernameElement.textContent = ""
            const canvas = document.querySelector('canvas')
            if (canvas) canvas.remove()
        }
    }).catch(error => console.error(error))
}

showDisplay()

// Kaboom Game
function startGame() {
    kaboom({
        global: true,
        fullscreen: true,
        scale: 2
        clearColor: [0, 0, 0, 1]
    })    

    // Speed identifiers 
    const moveSpeed = 120
    const jumpForce = 360
    const bigJumpForce = 550
    let currentJumpForce = jumpForce
    const fallDeath = 400
    const enemySpeed = 20

    // Game logic 
    let isJumping = true

    loadRoot('https://i.imgur.com/')
    loadSprite('coin', 'wbKxhcd.png')
    loadSprite('evil-shroom', 'KPO3fR9.png')
    loadSprite('brick', 'pogC9x5.png')
    loadSprite('block', 'M6rwarW.png')
    loadSprite('mario', 'Wb1qfhK.png')
    loadSprite('mushroom', '0wMd92p.png')
    loadSprite('surprise', 'gesQ1KP.png')
    loadSprite('unboxed', 'bdrLpi6.png')
    loadSprite('pipe-top-left', 'ReTPiWY.png')
    loadSprite('pipe-top-right', 'hj2GK4n.png')
    loadSprite('pipe-bottom-left', 'c1cYSbt.png')
    loadSprite('pip-bottom-right', 'nqQ79eI.png')
    loadSprite('blue-block', 'fVscIbn.png')
    loadSprite('blue-brick', '3e5YRQd.png')
    loadSprite('blue-steel', 'gqVoI2b.png')
    loadSprite('blue-evil-mushroom', 'SvV4ueD.png')
    loadSprite('blue-surprise', 'RMqCc1G.png')

    scene("game", ({ level, score }) => {
        layers(["bg", "obj", "ui"], "obj")

        const maps = [
            [
                '                                      ',
                '                                      ',
                '                                      ',
                '                                      ',
                '                                      ',
                '      %    =*=%=                      ',
                '                                      ',
                '                             -+       ',
                '                 ^     ^    ()        ',
                '======================================'
            ],
            [
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£      @@@@@@                x x          £',
                '£                          x x x          £',
                '£                        x x x x   x    -+£',
                '£              z    z  x x x x x   x    ()£',
                '!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!'
            ]
        ]

        const levelCfg = {
            width : 20,
            height : 20,
            '=' : [sprite('block'), solid()],
            '$' : [sprite('coin'), 'coin'],
            '%' : [sprite('surprise'), solid(), 'coin-surprise'],
            '*' : [sprite('surprise'), solid(), 'mushroom-surprise'],
            '}' : [sprite('unboxed'), solid()],
            '(' : [sprite('pipe-bottom-left'), solid(), scale(0.5)],
            ')' : [sprite('pipe-bottom-right'), solid(), scale(0.5)],
            '-' : [sprite('pipe-top-left'), solid(), scale(0.5), 'pipe'],
            '+' : [sprite('pipe-top-right'), solid(), scale(0.5), 'pipe'],
            '^' : [sprite('evil-shroom'), solid(), 'dangerous'],
            '#' : [sprite('mushroom'), solid(), 'mushroom', body()],
            '!' : [sprite('blue-block'), solid(), scale(0.5)],
            '£' : [sprite('blue-brick'), solid(), scale(0.5)],
            'z' : [sprite('blue-evil-mushroom'), solid(), scale(0.5), 'dangerous'],
            '@' : [sprite('blue-surprise'), solid(), scale(0.5), 'coin-surprise'],
            'x' : [sprite('blue-steel'), solid(), scale(0.5)],
        }

        const gameLevel = addLevel(maps[level], levelCfg)

        const scoreLabel = add([
            text(score),
            pos(30, 6),
            layer('ui'),
            {
                value: score
            }
        ])

        add([text(' level ' + parseInt(level + 1)), pos(40, 6)])

        const player = add([
            sprite('mario', solid()),
            pos(30, 0),
            body(),
            big(),
            origin('bot')
        ])

        function big() {
            let timer = 0
            let isBig = false
            return {
                update() {
                    if(isBig) {
                        currentJumpForce = bigJumpForce
                        timer -= dt()
                        if (timer <= 0 ) {
                            this.smallify()
                        }
                    }
                },
                isBig() {
                    return isBig
                },
                smallify() {
                    this.scale = vec2(1)
                    currentJumpForce = jumpForce
                    timer = 0
                    isBig = false
                },
                biggify(time) {
                    this.scale = vec2(2)
                    timer = time
                    isBig = true    
                }
            }
        }

        player.on("headbump", (obj) => {
            if(obj.is('coin-surprise')) {
                gameLevel.spawn('$', obj.gridPos.sub(0,1))
                destroy(obj)
                gameLevel.spawn('}', obj.gridPos.add(0,0))
            }
            if(obj.is('mushroom-surprise')) {
                gameLevel.spawn('#', obj.gridPos.sub(0,1))
                destroy(obj)
                gameLevel.spawn('}', obj.gridPos.add(0,0))
            }
        })

        action('mushroom', (m) => {
            m.move(20,0)
        })

        player.collides('mushroom', (m) => {
            destroy(m)
            player.biggify(6)
        })

            player.collides('coin', (c) => {
                destroy(c)
                scoreLabel.value++
                scoreLabel.text = scoreLabel.value
            })

        actions('dangerous', (d) => {
            d.move(-enemySpeed, 0)
        })

        player.collides('dangerous', (d) => {
            if(isJumping) {
                destroy(d)
            } else {
                go('lose', { score: scoreLabel.value })
            }
        })

        player.action(() => {
            camPos(player.pos)
            if(player.pos.y >= fallDeath) {
                go('lose', { score: scoreLabel.value })
            }
        })

        player.collides('pipe', () => {
            keyPress('down', () => {
                go('game', {
                    level: ( level + 1) % maps.length,
                    score: scoreLabel.value
                })
            })
        })

        keyDown('left', () => {
            player.move(-moveSpeed, 0)
        })

        keyDown('right', () => {
            player.move(moveSpeed, 0)
        })

        player.action(() => {
            if(player.grounded()) {
                isJumping = false
            }
        })

        keyPress('space', () => {
            if(player.grounded()) {
                isJumping = true
                player.jump(currentJumpForce)
            }
        })

        scene('lose', ({ score }) => {
            add([text(score, 32), origin('center'), pos(width() / 2, height() / 2)])
        })

    })

    start("game", { level: 0, score: 0 })


}

startGame()

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mario Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    
    <div id="modal" class="modal">
        <div class="button-container">
            <button onclick="toggleModal(event)" id="register-button">Register</button>
            <button onclick="toggleModal(event)" id="login-button" class="not-active">Login</button>
        </div>

        <form onsubmit="register(event)" id="register-form">
            <label for="register-email"></label>
            <input type="email" id="register-email" value="demo@example.com" required>
            <label for="register-password">Password</label>
            <input type="password" id="register-password" value="password" required pattern=".{6,}">
            <label for="register-username">Username</label>
            <input id="register-username" value="User" required>
            <br/>
            <input type="submit" value="Sign Up">
        </form>

        <form onsubmit="login(event)" id="login-form" class="hidden">
            <label for="login-email"></label>
            <input type="email" id="login-email" placeholder="demo@example.com" required>
            <label for="login-password">Password</label>
            <input type="password" id="login-password" placeholder="password" required pattern=".{6,}">         
            <br/>
            <input type="submit" value="Sign In">
        </form>
    </div>

    <div class="info-container">
        <button id="logout-button" class="hidden" onclick="logout()">Log out</button>
        <h3 id="username"></h3>
        <h3 id="highscore-tag" class="hidden">HighScore: <span id="highscore"></span></h3>
    </div>

<script src="https://kaboomjs.com/lib/0.5.0/kaboom.js"></script>
<script src="https://cdn.jsdelivr.net/npm/appwrite@11.0.0"></script>
<script src="game.js"></script>
</body>
</html>

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

game.js
const { Client, Account, Databases, ID, Query } = Appwrite
const projectId = '65087cc07844ae9e15b2'
const databaseId = '650b2fe269955675ae09' 
const collectionId = '650b30519a8feccf250f'

const client = new Client()
    .setEndpoint('https://cloud.appwrite.io/v1')
    .setProject(projectId)

const account = new Account(client)
const database = new Databases(client)

function isLoggedIn() {
    return account.get().then(response => {
        if(response) {
            return true
        }
        return false
    }).catch(error => console.error(error))
}

function getUserId() {
    return account.get().then(response => {
        return response.$id
    }).catch(error => console.error(error))
}

function displayUserName() {
    account.get.then(response => {
        const usernameElement = document.getElementById('username')
        usernameElement.textContent = response.name
    }).catch(error => console.error(error))
}

function updateScore(score) {
    // Send a update to a document
    const currentHighScore = document.getElementById('highscore').textContent
    if (Number(score) > Number(currentHighScore)) {
        getUserId().then(userId => {
            database.updateDocument (
                databaseId,
                collectionId,
                userId
                {
                    "userId": userId,
                    "highscore": score
                }
            ).then(() => {
                showScore()
            }).then(error => console.error(error))
        })
    }
}

function showScore() {
    getUserId().then(userId => {
        console.log('userId', userId)
        database.listDocuments(
            databaseId,
            collectionId,
            [
                Query.equal("userId", userId)
            ]
        ).then(response => {
            const highScoreElement = document.getElementById('highscore')
            highScoreElement.textContent = response.documents[0].highscore
        })
    })
}

document.addEventListener('DOMContentLoaded', () => {
    displayUserName()
    showScore()
    showDisplay()
})

function register(event) {
    account.create (
        ID.unique(),
        event.target.elements['register-email'].value,
        event.target.elements['register-password'].value,
        event.target.elements['register-username'].value
    ).then(response => {
        console.log(response)
        database.createDocument(
            databaseId,
            collectionId,
            response.$id,
            {
                "userId:": response.$id,
                "highscore": 0
            }
        )

        account.createEmailSession(
            event.target.elements['register-email'].value,
            event.target.elements['register-password'].value
        ).then(() => {
                showDisplay()
                displayUserName()
                showScore()
        })
    }).catch(error => console.error(error))
    event.preventDefault()
}

function login(event) {
    account.createEmailSession(
        event.target.elements['login-email'].value,
        event.target.elements['login-password'].value
    ).then(() => {
        alert('Session created successfully !')
        showDisplay()
        displayUserName()
        showScore()
        client.subscribe("account", (response) => {
            console.log(response)
        })
    }).catch(error => {
        alert('Failed to create session')
        console.error(error)
    })
    event.preventDefault()
}

function logout() {
    account.deleteSessions().then(() => {
        alert('Logged out')
        console.log('Current session deleted')
        showDisplay()
        const highScoreElement = document.getElementById('highscore')
        highScoreElement.textContent = ""
    }).catch(error => console.error(error))
}

function toggleModal(event) {
    const registerForm = document.getElementById('register-form')
    const loginForm = document.getElementById('login-form')
    const loginButton = document.getElementById('login-button')
    const registerForm = document.getElementById('register-button')

    if (event.srcElement.id === 'register-button') {
        registerForm.classList.remove('hidden')
        loginForm.classList.add('hidden')
        loginButton.classList.add('not-active')
        registerButton.classList.remove('not-active')
    }
    if (event.srcElement.id === 'login-button') {
        registerForm.classList.add('hidden')
        loginForm.classList.remove('hidden')
        loginButton.classList.remove('not-active')
        registerButton.classList.add('not-active')
    }
}

function showDisplay {
    const modalElement = document.getElementById('modal')
    modalElement.classList.add('hidden')
    isLoggedIn().then(isLogin => {
        if (isLogin) {
            const modalElement = document.getElementById('modal')
            modalElement.classList.add('hidden')
            const logoutButton = document.getElementById('logout-button')
            logoutButton.classList.remove('hidden')
            const highScoreTag = document.getElementById('highscore-tag')
            highScoreTag.classList.remove('hidden')
            startGame()
        } else {
            const modalElement = document.getElementById('modal')
            modalElement.classList.remove('hidden')
            const logoutButton = document.getElementById('logout-button')
            logoutButton.classList.add('hidden')
            const highScoreTag = document.getElementById('highscore-tag')
            highScoreTag.classList.add('hidden')
            startGame()
            const usernameElement = document.getElementById('username')
            usernameElement.textContent = ""
            const canvas = document.querySelector('canvas')
            if (canvas) canvas.remove()
        }
    }).catch(error => console.error(error))
}

// Kaboom Game
function startGame() {
    kaboom({
        global: true,
        fullscreen: true,
        scale: 2
        clearColor: [0, 0, 0, 1]
    })    

    // Speed identifiers 
    const moveSpeed = 120
    const jumpForce = 360
    const bigJumpForce = 550
    let currentJumpForce = jumpForce
    const fallDeath = 400
    const enemySpeed = 20

    // Game logic 
    let isJumping = true

    loadRoot('https://i.imgur.com/')
    loadSprite('coin', 'wbKxhcd.png')
    loadSprite('evil-shroom', 'KPO3fR9.png')
    loadSprite('brick', 'pogC9x5.png')
    loadSprite('block', 'M6rwarW.png')
    loadSprite('mario', 'Wb1qfhK.png')
    loadSprite('mushroom', '0wMd92p.png')
    loadSprite('surprise', 'gesQ1KP.png')
    loadSprite('unboxed', 'bdrLpi6.png')
    loadSprite('pipe-top-left', 'ReTPiWY.png')
    loadSprite('pipe-top-right', 'hj2GK4n.png')
    loadSprite('pipe-bottom-left', 'c1cYSbt.png')
    loadSprite('pip-bottom-right', 'nqQ79eI.png')
    loadSprite('blue-block', 'fVscIbn.png')
    loadSprite('blue-brick', '3e5YRQd.png')
    loadSprite('blue-steel', 'gqVoI2b.png')
    loadSprite('blue-evil-mushroom', 'SvV4ueD.png')
    loadSprite('blue-surprise', 'RMqCc1G.png')

    scene("game", ({ level, score }) => {
        layers(["bg", "obj", "ui"], "obj")

        const maps = [
            [
                '                                      ',
                '                                      ',
                '                                      ',
                '                                      ',
                '                                      ',
                '      %    =*=%=                      ',
                '                                      ',
                '                             -+       ',
                '                 ^     ^    ()        ',
                '======================================'
            ],
            [
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£                                         £',
                '£      @@@@@@                x x          £',
                '£                          x x x          £',
                '£                        x x x x   x    -+£',
                '£              z    z  x x x x x   x    ()£',
                '!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!'
            ]
        ]

        const levelCfg = {
            width : 20,
            height : 20,
            '=' : [sprite('block'), solid()],
            '$' : [sprite('coin'), 'coin'],
            '%' : [sprite('surprise'), solid(), 'coin-surprise'],
            '*' : [sprite('surprise'), solid(), 'mushroom-surprise'],
            '}' : [sprite('unboxed'), solid()],
            '(' : [sprite('pipe-bottom-left'), solid(), scale(0.5)],
            ')' : [sprite('pipe-bottom-right'), solid(), scale(0.5)],
            '-' : [sprite('pipe-top-left'), solid(), scale(0.5), 'pipe'],
            '+' : [sprite('pipe-top-right'), solid(), scale(0.5), 'pipe'],
            '^' : [sprite('evil-shroom'), solid(), 'dangerous'],
            '#' : [sprite('mushroom'), solid(), 'mushroom', body()],
            '!' : [sprite('blue-block'), solid(), scale(0.5)],
            '£' : [sprite('blue-brick'), solid(), scale(0.5)],
            'z' : [sprite('blue-evil-mushroom'), solid(), scale(0.5), 'dangerous'],
            '@' : [sprite('blue-surprise'), solid(), scale(0.5), 'coin-surprise'],
            'x' : [sprite('blue-steel'), solid(), scale(0.5)],
        }

        const gameLevel = addLevel(maps[level], levelCfg)

        const scoreLabel = add([
            text(score),
            pos(30, 6),
            layer('ui'),
            {
                value: score
            }
        ])

        add([text(' level ' + parseInt(level + 1)), pos(40, 6)])

        const player = add([
            sprite('mario', solid()),
            pos(30, 0),
            body(),
            big(),
            origin('bot')
        ])

        function big() {
            let timer = 0
            let isBig = false
            return {
                update() {
                    if(isBig) {
                        currentJumpForce = bigJumpForce
                        timer -= dt()
                        if (timer <= 0 ) {
                            this.smallify()
                        }
                    }
                },
                isBig() {
                    return isBig
                },
                smallify() {
                    this.scale = vec2(1)
                    currentJumpForce = jumpForce
                    timer = 0
                    isBig = false
                },
                biggify(time) {
                    this.scale = vec2(2)
                    timer = time
                    isBig = true    
                }
            }
        }

        player.on("headbump", (obj) => {
            if(obj.is('coin-surprise')) {
                gameLevel.spawn('$', obj.gridPos.sub(0,1))
                destroy(obj)
                gameLevel.spawn('}', obj.gridPos.add(0,0))
            }
            if(obj.is('mushroom-surprise')) {
                gameLevel.spawn('#', obj.gridPos.sub(0,1))
                destroy(obj)
                gameLevel.spawn('}', obj.gridPos.add(0,0))
            }
        })

        action('mushroom', (m) => {
            m.move(20,0)
        })

        player.collides('mushroom', (m) => {
            destroy(m)
            player.biggify(6)
        })

            player.collides('coin', (c) => {
                destroy(c)
                scoreLabel.value++
                scoreLabel.text = scoreLabel.value
            })

        actions('dangerous', (d) => {
            d.move(-enemySpeed, 0)
        })

        player.collides('dangerous', (d) => {
            if(isJumping) {
                destroy(d)
            } else {
                go('lose', { score: scoreLabel.value })
            }
        })

        player.action(() => {
            camPos(player.pos)
            if(player.pos.y >= fallDeath) {
                go('lose', { score: scoreLabel.value })
            }
        })

        player.collides('pipe', () => {
            keyPress('down', () => {
                go('game', {
                    level: ( level + 1) % maps.length,
                    score: scoreLabel.value
                })
            })
        })

        keyDown('left', () => {
            player.move(-moveSpeed, 0)
        })

        keyDown('right', () => {
            player.move(moveSpeed, 0)
        })

        player.action(() => {
            if(player.grounded()) {
                isJumping = false
            }
        })

        keyPress('space', () => {
            if(player.grounded()) {
                isJumping = true
                player.jump(currentJumpForce)
            }
        })

        scene('lose', ({ score }) => {
            add([text(score, 32), origin('center'), pos(width() / 2, height() / 2)])
        })

    })

    start("game", { level: 0, score: 0 })


}

startGame()

Visual Studio Code
EXPLORER
OPEN EDITORS 
public
index.html
styles.css
game.js 
package-lock.json
package.json 
index.js

styles.css
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;600;700;800&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,200&family=VT323&display=swap');

* {
    font-family: 'VT323', monospace;
    font-size: xx-large;
}

body {
    margin: 0;
    overflow: hidden;
    background-color: #000;
    color: #fff;
}

.modal {
    width: 600px;
    margin: auto;
    margin-top: 100px;
}

form {
    display: flex;
    flex-direction: column;
    background-color: #0aad02;
    padding: 10px;
}

.button-container button {
    border: none;
    color: #fff;
    padding: 5px;
    background-color: #0aad02;
}

form input[type=submit] {
    background-color: #bb3333;
}

.button-container button.not-active {
    background-color: #808080;
}

.hidden {
    display: none;
}

.info-container {
    position: absolute;
    top: 10px;
    right: 10px;
    text-align: right;
}

h3 {
    color: #fff;
    margin: 2px;
}


