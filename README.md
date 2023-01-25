# Quantum Cryptography Simulation

Welcome to my Quantum Cryptography Simulation. This is a summative I have worked on for my Grade 12 Physics class. This simulation is based off the BB84 Protocol. This protocol was made by Charles Bennnett and Gilles Brassard. We are going to use the way light travels through vertical and horizontal states to send encrypted messages using an algorithm similar to this:

![image](https://user-images.githubusercontent.com/113077964/214464300-072a5798-edf5-4e5d-9025-3c8621e34541.png)

# Thinking Process

![IMG_E0012](https://user-images.githubusercontent.com/113077964/214472721-835c1eaa-db26-4b82-b255-e10782ad9856.JPG)

# First Code Sample

```
import random 

# Gathers input from user, finding if they want a simulation with or without a hacker
codeLength = int(input("How long would you like your message to be? : "))
print()

inputVar = int(input("Type '1' for without hacker. Type '2' For with hacker. : "))
print()

# These variables were made for testing and checking
horizontalAmount = 0
verticalAmount = 0
randomAmount = 0
plusFourFive = 0
minusFourFive = 0
horizontalAmountRec = 0
verticalAmountRec = 0
randomAmountRec = 0
plusFourFiveRec = 0
minusFourFiveRec = 0

# Finding the Bits that are being sent, using a for loop and an array
  print("Bits Sent")
  bitSent = []
  for x in range(codeLength):
    randomNum = random.randint(0,1)
    bitSent.append(randomNum)
    print(bitSent[x], end=", ")
  print(" ")
  print( )
  
  # Finding the basis of the bits sent, either H or V, or + or - 45 degrees
  print("Bit Sent Basis")
  bitBasis = []
  for y in range(codeLength):
    randomNess = random.randint(0,1)
    bitBasis.append(randomNess)
    if bitBasis[y] == 0:
      print("H/V", end=", ")
    else:
      print("+/-45", end=", " )
  print(" ")
  print() 
  
  # Reading the bits that were sent, identifying what they really mean. 
  print("Bits Reading")
  readingBasis = []
  for z in range(codeLength):
    randomNumbers = random.randint(0, 1)
    readingBasis.append(randomNumbers)
    if readingBasis[z] == 0 and bitBasis[z] == 0:
      print("H", end=", ")
      horizontalAmount= horizontalAmount + 1
    elif readingBasis[z] == 1 and bitBasis[z] == 1:
      print("V", end=", ")
      verticalAmount = verticalAmount + 1
    elif readingBasis[z] == 1 and bitBasis[z] == 0:
      print("+45", end=", ")
      plusFourFive = plusFourFive + 1
    elif readingBasis[z] == 0 and bitBasis[z] == 1:
      print("-45", end=", ")
      minusFourFive = minusFourFive + 1
    else:
      print("R", end=", ")
      randomAmount = randomAmount + 1
  print(" ")
  print( )
  
  # Seeing what the receiver received. 
  print("Receiver Basis")
  receiverBase = []
  for a in range(codeLength):
    randomBig = random.randint(0,1)
    receiverBase.append(randomBig)
    if receiverBase[a] == 0:
      print("H/V", end=", ")
    else: 
      print("+/-45", end=", ")
  print(" ")
  print( )
  
  print("Receiver Readings")
  receiverReads = []
  for b in range(codeLength):
    if receiverBase[b] == 0 and bitBasis[b] == 0 and bitSent[b] == 0:
      print("H", end=", ")
      horizontalAmountRec = horizontalAmountRec + 1
    elif receiverBase[b] == 1 and bitBasis[b] == 1 and bitSent[b] == 1:
      print("V", end=", ")
      verticalAmountRec = verticalAmountRec + 1
    elif receiverBase[b] == 1 and bitBasis[b] == 0 and bitSent[b] == 0:
      print("+45", end=", ")
      plusFourFiveRec = plusFourFiveRec + 1
    elif receiverBase[b] == 0 and bitBasis[b] == 1 and bitSent[b] == 1:
      print("-45", end=", ")
      minusFourFiveRec = minusFourFiveRec + 1
    else:
      print("R", end=", ")
      randomAmountRec = randomAmountRec + 1
  print(" ")
  print( )
  
  print("Comparing Results")
  for c in range(codeLength):
    if receiverBase[c] == 0 and bitBasis[c] == 0 and bitSent[c] == 0:
      print("1", end=", ")
    elif receiverBase[c] == 1 and bitBasis[c] == 1 and bitSent[c] == 1:
      print("0", end=", ")
    elif receiverBase[c] == 1 and bitBasis[c] == 0 and bitSent[c] == 0:
      print("1", end=", ")
    elif receiverBase[c] == 0 and bitBasis[c] == 1 and bitSent[c] == 1:
      print("0", end=", ")
    else:
      print("R", end=", ")
  print(" ")
  print( )
  
  finalResult = []
  for d in range(codeLength):
    if receiverBase[d] == 0 and bitBasis[d] == 0 and bitSent[d] == 0:
      finalResult.append(1)
    elif receiverBase[d] == 1 and bitBasis[d] == 1 and bitSent[d] == 1:
      finalResult.append(0)
    elif receiverBase[d] == 1 and bitBasis[d] == 0 and bitSent[d] == 0:
      finalResult.append(1)
    elif receiverBase[d] == 0 and bitBasis[d] == 1 and bitSent[d] == 1:
      finalResult.append(0)
    
  print(finalResult)
  print(" ")
  print( )
  
  length = len(finalResult)
  used = codeLength - length
  print("You used " + str(used) + " out of " + str(codeLength) + " bits.")
  
  print(" ")
  print( )
  
  ```
