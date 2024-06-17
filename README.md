# Move-to-get-out-
It's a game. You have to move in the maze to get out of it 
def print_maze(maze, player_pos):
    for r in range(len(maze)):
        for c in range(len(maze[r])):
            if (r, c) == player_pos:
                print("P", end=" ")
            else:
                print(maze[r][c], end=" ")
        print()
    print()

def get_new_position(player_pos, move, maze):
    row, col = player_pos
    if move == "north" and row > 0:
        row -= 1
    elif move == "south" and row < len(maze) - 1:
        row += 1
    elif move == "east" and col < len(maze[0]) - 1:
        col += 1
    elif move == "west" and col > 0:
        col -= 1
    return (row, col)

def main():
    # Define the maze (2D list)
    maze = [
        ["#", "#", "#", "#", "#"],
        ["#", " ", " ", " ", "#"],
        ["#", " ", "#", " ", "#"],
        ["#", " ", "#", " ", "#"],
        ["#", " ", " ", "E", "#"],
        ["#", "#", "#", "#", "#"]
    ]

    player_pos = (1, 1)  # Starting position

    print("Welcome to the maze game!")
    print("Your goal is to reach the exit (E).")
    print("You can move north, south, east, or west.")
    print("Enter 'quit' to exit the game.")
    print()

    while True:
        print_maze(maze, player_pos)
        move = input("Enter your move: ").strip().lower()

        if move == "quit":
            print("Thanks for playing!")
            break

        if move in ["north", "south", "east", "west"]:
            new_pos = get_new_position(player_pos, move, maze)
            if maze[new_pos[0]][new_pos[1]] == "#":
                print("You can't move there, it's a wall!")
            else:
                player_pos = new_pos
                if maze[player_pos[0]][player_pos[1]] == "E":
                    print("Congratulations! You've found the exit!")
                    break
        else:
            print("Invalid move. Please enter north, south, east, or west.")

if __name__ == "__main__":
    main()
