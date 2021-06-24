# Создаем функцию, выводящую доску в консоли. Доска представляет собой список 3 на 3
# с соответсвующим индексом от 1 до 9
def display_board(board):

    print('   |   |')
    print(' ' + board[7] + ' | ' + board[8] + ' | ' + board[9])
    print('   |   |')
    print('-----------')
    print('   |   |')
    print(' ' + board[4] + ' | ' + board[5] + ' | ' + board[6])
    print('   |   |')
    print('-----------')
    print('   |   |')
    print(' ' + board[1] + ' | ' + board[2] + ' | ' + board[3])
    print('   |   |')

# Функция ввода, запрашивающая имена игроков
def greeting_and_names():
    global player1, player2
    player1 = input("Добро пожаловать в игру 'Крестики-Нолики'\nВведите имя первого игрока: ")
    player2 = input("Введите имя второго игрока: ")

# Функция запрашивающая у первого игрока выбор маркера (X или O)
def player_input():
    marker = ''

    while not (marker == 'X' or marker == 'O'):
        marker = input(f'{player1}: Вы хотите играть за X или O? ').upper()

    if marker == 'X':
        return 'X', 'O'
    else:
        return 'O', 'X'

# Пишем функцию, которая принимает в качестве аргументов (1) доску, (2) маркер и (3) индекс,
# и затем присваивает маркер соотвествующей клетке

def place_marker(board, marker, position):
    board[position] = marker

# Функция, проверяющая нет ли у кого-либо из игроков выигрышной комбинации
def win_check(board, mark):
    return ((board[7] == mark and board[8] == mark and board[9] == mark) or  # верхняя строка
            (board[4] == mark and board[5] == mark and board[6] == mark) or  # средняя строка
            (board[1] == mark and board[2] == mark and board[3] == mark) or  # нижняя строка
            (board[7] == mark and board[4] == mark and board[1] == mark) or  # первый столбец
            (board[8] == mark and board[5] == mark and board[2] == mark) or  # второй столбец
            (board[9] == mark and board[6] == mark and board[3] == mark) or  # третий столбец
            (board[7] == mark and board[5] == mark and board[3] == mark) or  # диагональ слева направо
            (board[9] == mark and board[5] == mark and board[1] == mark))  # диагональ справа налево

# Импортируем модуль random, для случаного выбора игорока ходящего первым помощью метода 'randint'
import random

def choose_first():
    if random.randint(0, 1) == 0:
        return f'{player2}'
    else:
        return f'{player1}'

# Функция, возвращающая булевое значение в результате проверки "свободности" клетки
def space_check(board, position):
    return board[position] == ' '

# Пишем функцию, которая проверяет, заполнена ли доска, и возвращает булевое значение.
# True, если заполнена, False если нет.
def full_board_check(board):
    for i in range(1,10):
        if space_check(board, i):
            return False
    return True

# Далее пишем функцию, которая просит игрока выбрать позицию от 1 до 9, а также прибегает к функции space_check для
# проверки доступности. В случае доступности, возвращает позицию для использования в дальнейшем
def player_choice(board):
    position = 0

    while position not in [1, 2, 3, 4, 5, 6, 7, 8, 9] or not space_check(board, position):
        position = int(input('Выберите позицию от 1 до 9: '))

    return position

# По завершении игры, выводим функцию предлагающую выграть ещё...
def replay():
    return input('Начать заново? y/n ').lower().startswith('y')

# Начало

while True:
    greeting_and_names()
    theBoard = [' '] * 10
    player1_marker, player2_marker = player_input()
    turn = choose_first()
    print(' Ход у ' + turn)

    play_game = input('Готовы? y/n ')

    if play_game.lower()[0] == 'y':
        game_on = True
    else:
        game_on = False

    while game_on:
        if turn == f'{player1}':
            # Player1's turn.

            display_board(theBoard)
            position = player_choice(theBoard)
            place_marker(theBoard, player1_marker, position)

            if win_check(theBoard, player1_marker):
                display_board(theBoard)
                print(f'Поздравляем! {player1} победил')
                game_on = False
            else:
                if full_board_check(theBoard):
                    display_board(theBoard)
                    print('Ничья!')
                    break
                else:
                    turn = f'{player2}'

        else:
            # Player2's turn.

            display_board(theBoard)
            position = player_choice(theBoard)
            place_marker(theBoard, player2_marker, position)

            if win_check(theBoard, player2_marker):
                display_board(theBoard)
                print(f'Поздравляем! {player2} победил')
                game_on = False
            else:
                if full_board_check(theBoard):
                    display_board(theBoard)
                    print('Ничья!')
                    break
                else:
                    turn = f'{player1}'

    if not replay():
        break
