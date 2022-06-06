# SQL
import mysql.connector

mydb = mysql.connector.connect(
    host="localhost",
    user="root",
    password="Astoria190"
)

print(mydb)
*SHOWS DATABASE

mycursor = mydb.cursor()
mycursor.execute("SHOW DATABASES")

for x in mycursor:
    print(x)
* SHOWS TABLES
mycursor = mydb.cursor()

mycursor.execute("SHOW TABLES")

for x in mycursor:
    print(x)

*INSERTS DATA
mycursor = mydb.cursor()

sql = "INSERT INTO pet ( name, owner, species, sex, birth, death)
val = [
    ('Fluffy', 'Harold', 'cat', 'f', '1993-02-04', None),
    ('Claws', 'Gwen', 'cat', 'm', '1993-02-04', None),
    ('Buffy', 'Harold', 'dog', 'f', '1993-02-04', None),
    ('Fang', 'Benny', 'dog', 'm', '1993-02-04', None),
    ('Bowser', 'Diane', 'dog', 'm', '1993-02-04', '1995-07-29'),
    ('Chirpy', 'Gwen', 'bird', 'f', '1993-02-04', None),
    ('Whistler', 'Gwen', 'cat', None, '1993-02-04', None),
    ('Slim', 'Benny', 'snake', 'm', '1993-02-04', None)
]


mycursor.executemany(sql, val)

mydb.commit()

print(mycursor.rowcount, "was inserted. ")

*SHOW FEMALE DOGS*

mycursor = mydb.cursor()

sql = "SELECT * FROM pet WHERE sex ='f'"

mycursor.execute(sql)

myresult = mycursor.fetchall()

for x in myresult:
   print(x)

*BIRTH OF PETS*

mycursor = mydb.cursor()

mycursor.execute("SELECT name, birth FROM pet")

myresult = mycursor.fetchall()

for x in myresult:
   print(x)

* numbers of pets each owner has *
mycursor = mydb.cursor()

sql = "SELECT owner, COUNT(*) FROM pet GROUP by owner"

mycursor.execute(sql)

myresult - mycursor.fetchall()

for x in myresult:
  print(x)
  
*WE USE THE COMMAND PROMPT TO SHOW TABLE WITH NAME, BIRTH, MONTH(BIRTH)*
mysql> SELECT name, birth, MONTH(birth) FROM pet;









    
