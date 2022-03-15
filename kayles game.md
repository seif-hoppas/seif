
lst = []
num_list = int(input("Please, enter the last number of the list : "))
empty_list = ['-' for i in range(20)]
for i in range(1, num_list + 1):
    lst.append(i % 10)
# to input the list
print("list = ", lst)
player = 1
# for player 1
while True:

   while True:
        n1 = int(input(f"Player{player} How many numbers to remove 1 or 2?"))
        # checking for invalid numbers
        if n1 == 1 or n1 == 2:
            break
        else:
            print("Invalid numbers , enter another numbers")
    if n1 == 1:
        # if the player chosen 1 number
        player1 = int(input(f"player {player} , enter the number"))
        # checking if u put a number bigger than the last number in the list
        if player1 >= num_list :
            print("invalid number")
            continue
        del lst[player1 - 1]
        # delete the index of the list , if player1 = 5 , delete index 4
        lst.insert(player1 - 1, "-")
        # go to the index and replace it by '-'
        print(*lst)
        if lst == empty_list:
            print(f"Player {player} wins!")
            exit()
            # checking for winning
    elif n1 == 2:
        # if the player chosen 2 numbers
        while True:
            player1 = int(input(f"player {player} , enter first number: "))
            if player1 >= num_list:
                print("invalid number")
                continue
            player2 = int(input(f"player {player} , enter second number: "))
            if player2 >= num_list:
                print("invalid number")
                continue
            if player1 - player2 == 1 or player1 - player2 == -1:
                break
            else:
                print("Numbers aren't adjacent")
        del lst[player1 - 1]
        lst.insert(player1 - 1, '-')
        del lst[player2 - 1]
        lst.insert(player2 - 1, '-')
        print(*lst)
        if lst == empty_list:
            print(f"Player {player} wins!")
            exit()
    # player 1 already played so let player 2 plays
    if player == 1:
        player = 2
    elif player == 2:
        player = 1
