import random
import time
import numpy as np

def delay(teks, delay_time=0.1):
    for karakter in teks:
        print(karakter, end='', flush=True)
        time.sleep(delay_time)
    print()

def generate_password():
    uppercase = "ABCDEFGHJKLMNPQRSTUVWXYZ"
    lowercase = "abcdefghijkmnpqrstuvwxyz"
    numeral = "23456789"  
    symbol = "!#$%&()*+-/:;<=>?@[]^_{}~"
    
    for i in range(9):
        build = [
            random.choice(uppercase),
            random.choice(uppercase),
            random.choice(lowercase),
            random.choice(lowercase),
            random.choice(numeral),
            random.choice(numeral),
            random.choice(symbol),
            random.choice(symbol),
        ]
        random.shuffle(build)
        password = ''.join(build)
        for char in password:
            print(char, end='', flush=True)
            time.sleep(0.05)
        print("    ", end='', flush=True)
        if (i+1) % 3 == 0:
            delay("\n", 0.05)

def count_discount(name):
    delay(f"\nAlright let's counting discount\n...\nPlease input the number of items you purchased, the discount and the price " + name.capitalize(), 0.05)
    while True:
        try:
            barang = int(input("Number of Items: "))
            harga_b = int(input("Price of Items: "))
            discount_b = float(input("Discount of Items: "))
            if barang < 1:
                delay("\nMinimum purchase is 1", 0.05)
                continue
            harga = barang * harga_b
            if barang > 1:
                diskon = harga * (discount_b / 100)
                total = harga - diskon
                delay(f"\nPurchase: \n-----------------------\nItems: {barang}\nDiscount: {discount_b}\nTotal Price (before discount): {harga}\nTotal Price (after discount): {total}    \n-----------------------\nPurchase Successful", 0.05)
            else:
                delay(f"\nPurchase: \n-----------------------\nItems: {jumlah}\nTotal Price: {harga}\n-----------------------\nPurchase Successful", 0.05)
            break
        except ValueError:
            delay("\nInvalid Input\nTry again", 0.05)
            
def even_orodd():
    angka = int(input("\nCek bilangan Ganjil atau Genap\nMasukkan nilai: "))
    if angka % 2 == 0:
       delay("Ini adalah Bilangan Genap", 0.05)
    else:
       delay("Ini adalah Bilangan Ganjil", 0.05)
       
def secret():
    message = input("\nPesan Rahasia\nMasukkan Pesan: ").lower()
    encode = []
    for char in message:
        if "a" <= char <= "z":
            pos = ord(char) - ord("a")
            new_char = chr(ord("z") - pos )
            encode.append(new_char)
        else:
            encode.append(char)
    encoded_message = "".join(encode)
    delay("\nPesan telah di konversi: ", 0.05)
    for char in encoded_message:
        print(char, end='', flush=True)
        time.sleep(0.05)
    print()
    
def valentine_1(char_delay=0.02, line_delay=0.3):
    a = np.array([
        [0,0,0,4,4,4,4,0,0,0,0,0,0,0,0,4,4,4,4],
        [0,0,4,2,3,1,5,4,0,0,0,0,0,4,1,2,3,4,4],
        [0,4,2,3,1,5,6,1,4,0,0,0,4,1,2,3,4,5,4],
        [4,2,3,1,5,6,1,2,3,4,4,3,1,2,3,4,5,6,4],
        [4,3,2,5,6,1,2,3,4,5,6,1,2,3,4,5,6,1,4],
        [4,3,5,6,1,2,3,4,5,6,1,2,3,4,5,6,1,2,4],
        [4,5,6,1,2,3,4,5,6,1,2,3,4,5,6,1,2,3,4],
        [0,4,1,2,3,4,5,6,1,2,3,4,5,6,1,2,3,4,0],
        [0,0,4,3,6,5,6,1,2,3,4,5,6,1,2,3,4,0,0],
        [0,0,0,4,5,6,1,2,3,4,5,6,1,2,3,4,0,0,0],
        [0,0,0,0,4,1,2,3,4,5,6,1,2,3,4,0,0,0,0],
        [0,0,0,0,0,4,3,4,5,6,1,2,3,4,0,0,0,0,0],
        [0,0,0,0,0,0,4,5,6,1,2,3,4,0,0,0,0,0,0],
        [0,0,0,0,0,0,0,4,1,2,3,4,0,0,0,0,0,0,0],
        [0,0,0,0,0,0,0,0,4,3,4,0,0,0,0,0,0,0,0],
        [0,0,0,0,0,0,0,0,0,4,0,0,0,0,0,0,0,0,0],
    ])

    flowers = {
        0: ' ',
        1: '✿',
        2: '❀',
        3: '✾',
        4: '❁',
        5: '⚘',
        6: '♣'
    }

    for row in a:
        line = ''.join(flowers[num] for num in row)
        delay(line, char_delay)
        time.sleep(line_delay)
           
def login():
    delay("Hallow (>v<)\n I'm Bella 😙", 0.05)
    greetings = {"hallow", "hellow", "yow", "its me", "ha?", "halo", "Hello", "Hi"}
    names = {"ray", "aulia", "lillie", "irva"}
    answers = {"yes", "sure", "yup"}
    
    user_greeting = input("Greet Her: ").lower()
    if user_greeting not in greetings:
        delay("Sorry..., I can't identify who you are", 0.05)
        return
    else:
        delay("\nCan I know your name?..", 0.05)

    name = input("Enter your name: ").lower()
    if name not in names:
        delay("Sorry..., I can't remember who you are", 0.05)
        return

    delay("\nOwh..\nwait....\nI remember that's you " + name.capitalize(), 0.05)
    delay("Welcome Back!\nIts nice to see you again\nWhat will you do today?\n a. Generate Password\n b. Counting Discount\n c. Distinguishing odd or even numbers\n d. Secret Messages", 0.05)
    while True:
        choice = input("\nEnter options: ").lower()
        if choice == "a":
            delay("\nAlright according to your choice:\n", 0.05)
            generate_password()
            break
        elif choice == "b":
            count_discount(name)
            break
        elif choice == "c":
            even_orodd()
            break
        elif choice == "d":
            secret()
            break
        else:
            print("Invalid option. Please enter a, b, c, or d.")
            
    delay("\nDo you want to see something special??", 0.05)
    answer = input(" ").lower()
    if answer in answers:
        delay("\nHere you go!!", 0.05)
        time.sleep(0.5)
        valentine_1()
        return
    else:
        delay("\nWell.. alright then", 0.05)
    delay("\nJust that what can I do, I am in the development stage 😊", 0.05)
            
login()
