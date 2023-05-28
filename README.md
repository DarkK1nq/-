# -import random

print("Добро пожаловать в игру Виселица!")

# список слов для угадывания
words = ["яблоко", "банан", "груша", "апельсин", "манго", "арбуз", "слива"]

# случайно выбираем слово
word = random.choice(words)

# переменная для хранения угаданных букв
correct_letters = []

# переменная для хранения неправильных угадываний
incorrect_guesses = 0

# основной цикл игры
while True:
    # выводим текущее состояние игры
    print()
    for letter in word:
        if letter in correct_letters:
            print(letter, end=" ")
        else:
            print("_", end=" ")
    print()

    # проверяем, не угадали ли все буквы
    if set(word) == set(correct_letters):
        print("Поздравляем, вы выиграли!")
        break

    # проверяем, не проиграли ли
    if incorrect_guesses >= 6:
        print("У вас закончились попытки. Вы проиграли.")
        break

    # запрашиваем у пользователя следующую букву
    guess = input("Угадайте букву: ").lower()

    # проверяем, есть ли такая буква в слове
    if guess in word:
        correct_letters.append(guess)
        print("Правильно!")
    else:
        incorrect_guesses += 1
        print("Неправильно.")

    # выводим количество оставшихся попыток
    print("Осталось попыток:", 6 - incorrect_guesses)
