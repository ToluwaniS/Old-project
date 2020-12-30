# Old-project

myFile = open("leaderboard.txt","a")

from termcolor import colored
import random
import time

Player1_Cards = []
Player2_Cards = []
Pass1 = "admin"
Pass2 = "admin1"
P1_Points = 0
P2_Points = 0
Chosen_Cards = []
P1_Cards = []
P2_Cards = []

Cards =["R1","R2","R3","R4","R5","R6","R7","R8","R9","R10","B1","B2","B3","B4","B5","B6","B7","B8","B9","B10","Y1","Y2","Y3","Y4","Y5","Y6","Y7","Y8","Y9","Y10"]

for card in range(len(Cards)):
  selCard = random.choice(Cards)
  Chosen_Cards.append(selCard)
  Cards.remove(selCard)

print("GENERIC PASSWORD PLAYER 1 - admin")
print("GENERIC PASSWORD PLAYER 2 - admin1")
print()
#print(Chosen_Cards)
#print(Cards)

#time.sleep(1)
Player1_UN = input("Please enter a username (P1): ").title()
Player1_Pass = input("Enter generic password for player1: ")
while Player1_Pass != Pass1:
  print("Please enter correct password: ")
  print()
  Player1_Pass = input("Enter generic password for player 1: ")
  print()

Player2_UN = input("Please enter username (P2): ").title()
Player2_Pass = input("Enter generic password for player 2: ")
while Player2_Pass != Pass2:
  print("Please enter correct password: ")
  print()
  Player2_Pass = input("Enter generic password for player 2: ")
  print()

print(P1_Points)
print(P2_Points)

print("------------------")
print("| STARTING GAME |")
print("------------------")


while len(Chosen_Cards) > 0:
  print(colored(Player1_UN,'green'),":",Chosen_Cards[0])
  #print(Player1_UN,":",Chosen_Cards[0])
  P1_Cards.append(Chosen_Cards[0])
  Player1_Cards.append(Chosen_Cards[0])
  Chosen_Cards.remove(Chosen_Cards[0])

  print(colored(Player2_UN,'blue'),":",Chosen_Cards[0])
  #print(Player2_UN,":",Chosen_Cards[0])
  P2_Cards.append(Chosen_Cards[0])
  Player2_Cards.append(Chosen_Cards[0])
  Chosen_Cards.remove(Chosen_Cards[0])


  if P1_Cards[0][0] == P2_Cards[0][0]:
    if P1_Cards[0][1] > P2_Cards[0][1]:
      print(Player1_UN,":","keeps the cards")
      P1_Points = P1_Points + 1
      #print(P1_Points)
      print()
      time.sleep(1)
    else:
      print(Player2_UN,"keeps the cards")
      P2_Points = P2_Points + 1
      #print(P2_Points)
      print()
      time.sleep(1)

  elif P1_Cards[0][0] == "R" and P2_Cards[0][0] == "B":
    print(Player1_UN,"keeps the cards")
    P1_Points = P1_Points + 1
    #print(P1_Points)
    print()
    time.sleep(1)

  elif P1_Cards[0][0] == "B" and P2_Cards[0][0] == "R":
    print(Player2_UN,"keeps the cards")
    P2_Points = P2_Points + 1
    #print(P2_Points)
    print()
    time.sleep(1)

  elif P1_Cards[0][0] == "Y" and P2_Cards[0][0] == "R":
    print(Player1_UN,"keeps the cards")
    P1_Points = P1_Points + 1
    #print(P1_Points)
    print()
    time.sleep(1)

  elif P1_Cards[0][0] == "R" and P2_Cards[0][0] == "Y":
    print(Player2_UN,"keeps the cards")
    P2_Points = P2_Points + 1
    #print(P2_Points)
    print()
    time.sleep(1)

  elif P1_Cards[0][0] == "B" and P2_Cards[0][0] == "Y":
    print(Player1_UN,"keeps the cards")
    P1_Points = P1_Points + 1
    #print(P1_Points)
    print()
    time.sleep(1)

  elif P1_Cards[0][0] == "Y" and P2_Cards[0][0] == "B":
    print(Player2_UN,"keeps the cards")
    P2_Points = P2_Points + 1
    #print(P2_Points)
    print()
    time.sleep(1)

  P1_Cards = []
  P2_Cards = []
print("---------------")
print("|GAME FINISHED|")
print("---------------")

if P1_Points > P2_Points:
  print(Player1_UN,"WINS")
  print("Points:",P1_Points)
  with open ("leaderboard.txt","a") as myFile:
    myFile.write(Player1_UN + ", " + str(P1_Points)+ "\n")
    print("WINNING CARDS ARE.....")
  for i in Player1_Cards:
    print (i)
elif P2_Points > P1_Points:
  print(Player2_UN,"WINS")
  print(P2_Points)
  with open ("leaderboard.txt","a") as myFile:
    myFile.write(Player2_UN + ", " + str(P2_Points)+ "\n")
    print("WINNING CARDS ARE.....")
  for i in Player2_Cards:
    print(i)
elif P1_Points == P2_Points:
  print("DRAW")

with open ("leaderboard.txt","r") as myFile:
  scores = [i.split(',') for i in myFile if i.strip()]
scores = [(name.strip(), int(score)) for name, score in scores]
scores.sort(key = lambda s: s[1], reverse=True )

print()
print("LEADERBOARD")  
print()
list = []
for name, score in scores:
  s = (name,score)
  list.append(s)
for i in list[0:5]:
  print(i)
  

