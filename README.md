# Binary_Decimal
#Binary_decimal converter



storage = []

k = 0
while k != 1:

    number = input("Proszę wprowadź liczbę oraz format do wykonania obliczeń: ")

    storage = number.split()  # wprowadzenie dwóch elementów do listy bez zbędnych znaków np spacji

    if len(storage) == 2:

        first_element = storage[0]
        second_element = storage[1]

        if first_element.isdigit() and second_element.isdigit():
            if second_element == "2" or second_element == "10":
                k = 1

            else:
                print("Wrong try to calculate number from \"" + second_element + "\" format.\n")

        else:
            print("Something goes wrong, first or second element is not a number.")

    storage = []


if second_element == "10":

    first_element = int(first_element)

    binary = ""
    x = 0
    add_binary = 0

    add_binary = int(add_binary)

    if first_element == 0:
        binary += "0"

    while first_element != 0:

        add_binary = first_element % 2

        if add_binary == 1:
            first_element = first_element - 1

        first_element = int(first_element / 2)

        binary += str(add_binary)

    change_the_way_of_calculating = ""
    for i in range(len(binary)):  # odwrócenie łańcucha
        change_the_way_of_calculating += binary[-i - 1]

    binary = change_the_way_of_calculating
    print("/" + "-" * (len(binary) + 7) + "\\")
    print("| " + change_the_way_of_calculating + " | " + "2" + "  |")
    print("\\" + "-" * (len(binary) + 7) + "/")


else:

    good_or_not = ""

    for i in first_element:  # Sprawdza czy w poprawnym formacie została wprowadzona liczba binarna

        if i != "0" and i != "1":
            good_or_not = "fail"

    if good_or_not != "fail":

        change_the_way_of_calculating = ""

        for i in range(len(first_element)):  # odwrócenie łańcucha by czytał od prawej do lewej
            change_the_way_of_calculating += first_element[-i - 1]

        first_element = change_the_way_of_calculating

        for i in range(len(first_element)):  # ustalenie indeksów do potęgowania
            if first_element[i] == "1":
                storage.append(i)

        new_number = 0

        for i in storage:
            x = i

            add_value_to_new_number = 2

            while x != 1 and x > 0:
                x -= 1
                add_value_to_new_number *= 2

            if i == 0:  # obsługa wyjątku gdy 2 do potęgi zerowej
                add_value_to_new_number = 1

            new_number += add_value_to_new_number

        new_number = str(new_number)
        print("/" + "-" * (len(new_number) + 7) + "\\")
        print("| " + new_number + " | " + "10" + " |")
        print("\\" + "-" * (len(new_number) + 7) + "/")

    else:
        print("wprowadziłeś zły format liczby binarnej")


#
