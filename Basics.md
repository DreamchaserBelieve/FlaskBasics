#MySQL and Flask

import mysql.connector

db = mysql.connector.connect(
    host="localhost",
    user="root",
    passwd="*****",
    database="FlaskData"
)



mycursor = db.cursor()

def InsertBlob(Filename):
    with open(Filename, "rb") as File:
        BinaryData = File.read()
        SQLStatement = "INSERT INTO UserInfo(Image) VALUES (%s) WHERE Username=input_name"
        mycursor.execute(SQLStatement, (BinaryData, ))
        db.commit()

input_name = input("Enter your username:")
UserFile = input("Enter Image name:")
InsertBlob(UserFile)
