# PODS 💾
Pack of Data    
By Dmitry Mitrofanov (@pixeye)

## What is it?
Easy to read and type text format for serialization and config files.  

## Why?
  Json may be used on projects both for serialization tasks and for writing configuration files. Despite the obvious advantages of Json as a format (it's intuitive, more or less good for data serialization and widely spread), it's harder to read and edit than, for example, Toml/Yaml. Toml is easy to read, but it's not designed for serialization, and Yaml, subjectively, is a complex format. I wanted to make a format with 3 things in mind:
  - easy to type and read
  - can be used both for configs and serialization with different visual and syntax output but still based on the same set of grammar rules
  - json-like as it's by far most widely used format and mostly everyone who know Json can use Pods 

  
## Examples 📗
  Pods can be written in several formats: Dense, Sparse and Compact (relatively)  
  The properties can be nested and can represent hierarchical data. 
Sparse format:
```
(
  Alain = (
    name    = 'Alain'
    pos     = (x=5,y=10,z=0)
    power   = 90
    cost    = 10
    kind    = 'Mage'
    items   = [['book'='Homilies and Meditations']];
    friends = ['Roland','Cuthbert']
    dead    = true
  )
  Cuthbert = (
    name    = 'Cuthbert'
    pos     = (x=10,y=10,z=0)
    power   = 100
    cost    = 10
    kind    = 'Range'
    items   = [['necklace'='The Lookout','weapon1'='carver','weapon2'='slingshot']]
    friends = ['Roland','Alain']
    dead    = true
  )
  Roland = (
    name    = 'Roland'
    pos     = (x=12,y=10,z=5)
    power   = 150
    cost    = 20
    kind    = 'Melee'
    items   = [['pet'='David']]
    friends = ['Cuthbert','Alain','Susan']
    dead    = false
  )
)
```
Dense format:
  ```
(
# Unit A
    Alain.name = 'Alain';
    Alain.pos.x = 5;;
    Alain.pos.y = 10;;
    Alain.pos.z = 0;;
    Alain.power = 90;
    Alain.cost = 10;
    Alain.kind = 'Mage';
    Alain.items = [['book'='Homilies and Meditations']];
    Alain.friends = ['Roland','Cuthbert'];
    Alain.dead = true;
# Unit B
    Cuthbert.name = 'Cuthbert';
    Cuthbert.pos.x = 10;;
    Cuthbert.pos.y = 10;;
    Cuthbert.pos.z = 0;;
    Cuthbert.power = 100;
    Cuthbert.cost = 10;
    Cuthbert.kind = 'Range';
    Cuthbert.items = [['necklace'='The Lookout','weapon1'='carver','weapon2'='slingshot']];
    Cuthbert.friends = ['Roland','Alain'];
    Cuthbert.dead = true;
# Unit C
    Roland.name = 'Roland';
    Roland.pos.x = 12;;
    Roland.pos.y = 10;;
    Roland.pos.z = 5;;
    Roland.power = 150;
    Roland.cost = 20;
    Roland.kind = 'Melee';
    Roland.items = [['pet'='David']];
    Roland.friends = ['Cuthbert','Alain','Susan'];
    Roland.dead = false;
)
  ```
Also valid format:
```
(
  Alain
    .name = 'Alain';
    .pos.x = 5;;
    .pos.y = 10;;
    .pos.z = 0;;
    .power = 90;
    .cost = 10;
    .kind = 'Mage';
    .friends = ['Cuthbert','Roland'];
    .inventory = [['book'='Homilies and Meditations']];
    .dead = true;
)
```
## Format rules 📘
Objects begin with `.` or `(` and ends with `;` or `)`
Arrays  begin with `[` and ends with `]`  
Tables  begin with `[[` and ends with `]]`  
Tables can take only string keys  
Strins are quoted with `'`  
Booleans `false`, `true`, `on`, `off`  
Null `null`  
Whitespaces ` `, `\t`, `\v`, `\r`, `\l`, `\f`  
End of line `\l`, `\r`  
Comments `#`


## Usage / Contribution 🦄
This is still mainly a personal project that I use to describe object definition or configurations in my game development routines. Though, potentially this format can be used everywhere. If you like the concept & idea
than documentation, bug reports, pull requests or any other contributions are strongly welcome! 


## Implementations ⚙️
Currently, only Nim language implementation is awailable, as this is my daily language and I originally wrote PODS using it. 
- Nim: https://github.com/PixeyeHQ/px.nim.pods
