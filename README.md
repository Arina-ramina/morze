# morze
# the program will convert words to morse code and then check the answers


import random

words = ['pink', 'yellow', 'blue', 'green', 'white']

answers = []


def morse_encode(word):
  '''
  Получаем рандомное слово и переводим его по азбуке морзе.
  Выводим на печать
  '''
  morze = {
    "0": "-----",
    "1": ".----",
    "2": "..---",
    "3": "...--",
    "4": "....-",
    "5": ".....",
    "6": "-....",
    "7": "--...",
    "8": "---..",
    "9": "----.",
    "a": ".-",
    "b": "-...",
    "c": "-.-.",
    "d": "-..",
    "e": ".",
    "f": "..-.",
    "g": "--.",
    "h": "....",
    "i": "..",
    "j": ".---",
    "k": "-.-",
    "l": ".-..",
    "m": "--",
    "n": "-.",
    "o": "---",
    "p": ".--.",
    "q": "--.-",
    "r": ".-.",
    "s": "...",
    "t": "-",
    "u": "..-",
    "v": "...-",
    "w": ".--",
    "x": "-..-",
    "y": "-.--",
    "z": "--..",
    ".": ".-.-.-",
    ",": "--..--",
    "?": "..--..",
    "!": "-.-.--",
    "-": "-....-",
    "/": "-..-.",
    "@": ".--.-.",
    "(": "-.--.",
    ")": "-.--.-"
    }
  encoded_word = ''
  for w in word:
    if w in morze:
        encoded_word += morze[w]+' '
  return encoded_word



def get_word():
  '''
  выбираем рандомное слово из списка и возвращаем его,
  чтобы работать с ним дальше
  '''
  word = random.choice(words)
  return word




def print_statistics(answers):
  '''
  Подсчитываем количество вопросов, а так же верные и неверные ответы.
  '''
  total_questions = len (answers)
  correct_answers = 0
  wrong_answers = 0

  for answer in answers:
     if answer:
        correct_answers += 1
     else:
         wrong_answers += 1

  print(f'Всего задачек: {total_questions}')
  print(f'Отвечено верно: {correct_answers}')
  print(f'Отвечено неверно: {wrong_answers}')


#Приветствие пользователя, начало работы
print ('''
Сегодня мы потренируемся расшифровывать морзянку.
Нажмите Enter и начнем
''')
print(input())

#Запускаем цикл вопрос и добавляет bool значение в список answer
for _ in range (5):
    word = get_word()
    encoded_word = morse_encode(word)

    print(f'Слово {encoded_word}')
    user_input = input().lower()
    if user_input == word:
        answers.append (True)
        print(f'Верно, {word} !')
    else:
        answers.append (False)
        print(f'Неверно, {word} !')

print()
print_statistics(answers)









