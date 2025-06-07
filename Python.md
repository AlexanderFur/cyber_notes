# ABC -Formelen


```python
# Dette programmet kan løse annengradslikninger ved å oppgi A, B, og C

  

import math

  

print("Programmet skal løse andregradslikningen ")

print("ax**2 + bx + c = 0 ved hjelp av abc-formelen.")

print("Skriv inn verdiene for a, b og c.")

  

a = float(input("a = "))

b = float(input("b = "))

c = float(input("c = "))

  

d = b**2 - 4*a*c  # diskriminanten

  

# Hvis diskriminanten er positiv, har vi to forskjellige løsninger

if d > 0:

    x1 = round((-b + math.sqrt(d)) / (2 * a), 2)

    x2 = round((-b - math.sqrt(d)) / (2 * a), 2)

    print("Løsningen på andregradslikningen er:")

    print(f"x1 = {x1} og x2 = {x2}")

  

# Hvis diskriminanten er null, har vi én løsning (to like løsninger)

elif d == 0:

    x1 = round(-b / (2 * a), 2)

    print("Det er én løsning (to like løsninger):")

    print(f"x1 = x2 = {x1}")

  

# Hvis diskriminanten er negativ, finnes det ingen reelle løsninger

else:

    # Vi kan beregne de komplekse løsningene ved hjelp av imaginære tall

    real_part = round(-b / (2 * a), 2)

    imaginary_part = round(math.sqrt(-d) / (2 * a), 2)

    print("Det finnes ingen reelle løsninger, men de komplekse løsningene er:")

    print(f"x1 = {real_part} + {imaginary_part}i")

    print(f"x2 = {real_part} - {imaginary_part}i")

```

----------------------------------------------
