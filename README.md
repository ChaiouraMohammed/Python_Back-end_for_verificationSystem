# Python_Back-end_for_verificationSystem
This back-end system is a prototype used for account verification using E-mail 

## How does it work ?
This system allows a verification code to be sent to the user by email, after sending the code, the user will enter the code received in the email. finally, code verification at application level.
## Libraries 
```
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
import random
```
## Function to get a random numerical characters

```
def generateCode():
  return str(random.randint(100000 , 999999))
```
## Function to send mails 
```
def send_email(receiver_email, verification_code):
    sender_email = "YourCompanyMail" 
    password = "PasswordCompanyMail"  
    message = MIMEMultipart()
    message['From'] = sender_email
    message['To'] = receiver_email
    message['Subject'] = "Code de vérification"

    body = f"Votre code de vérification est : {verification_code}"
    message.attach(MIMEText(body, 'plain'))

    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(sender_email, password)
    server.send_message(message)
    server.quit()
```
## Main program
```
email = input("Entrez votre adresse e-mail : ")
code = generateCode()
send_email(email, code)
print("Un e-mail de vérification a été envoyé à votre adresse.")
userInput = input("Entrez le code de vérification reçu par e-mail : ")
if userInput == code:
     print("Code correct. Vérification réussie !")
else:
     print("Code incorrect. Vérification échouée.")
```
## Outcomes 
![image](https://github.com/ChaiouraMohammed/Python_Back-end_for_verificationSystem/assets/91562298/a1dbbcd1-227a-412c-bdc9-aefb175bf807)


![image](https://github.com/ChaiouraMohammed/Python_Back-end_for_verificationSystem/assets/91562298/44d11a68-0750-4c10-a1f9-8641686e41d6)


![image](https://github.com/ChaiouraMohammed/Python_Back-end_for_verificationSystem/assets/91562298/a47998ca-c7e9-4754-a523-8d9df8724c0a)


