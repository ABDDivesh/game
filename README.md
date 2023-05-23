# game
game
class ChessGame:
    def __init__(self):
        self.board = self.create_board()
        self.current_player = 'white'
        self.game_over = False

    def create_board(self):
        board = {}
        pieces_order = ['rook', 'knight', 'bishop', 'queen', 'king', 'bishop', 'knight', 'rook']
        for i in range(8):
            for j in range(8):
                if i == 0:
                    board[(i, j)] = pieces_order[j]
                elif i == 1:
                    board[(i, j)] = 'pawn'
                elif i == 6:
                    board[(i, j)] = 'pawn'
                elif i == 7:
                    board[(i, j)] = pieces_order[j].capitalize()
                else:
                    board[(i, j)] = None
        return board

    def print_board(self):
        for i in range(8):
            for j in range(8):
                print(self.board[(i, j)], end=' ')
            print()

    def is_valid_move(self, start, end):
        # Check if the move is valid
        # You can implement the validation logic here
        return True

    def make_move(self, start, end):
        if self.is_valid_move(start, end):
            self.board[end] = self.board[start]
            self.board[start] = None
            self.current_player = 'black' if self.current_player == 'white' else 'white'
        else:
            print("Invalid move. Try again.")

    def play_game(self):
        while not self.game_over:
            self.print_board()
            print(f"It's {self.current_player}'s turn.")
            start = input("Enter the starting position (e.g., 'a2'): ")
            end = input("Enter the ending position (e.g., 'a4'): ")
            start = self.convert_position(start)
            end = self.convert_position(end)
            self.make_move(start, end)

    def convert_position(self, position):
        # Convert user input position to a tuple (e.g., 'a2' -> (1, 0))
        column_map = {'a': 0, 'b': 1, 'c': 2, 'd': 3, 'e': 4, 'f': 5, 'g': 6, 'h': 7}
        row = int(position[1]) - 1
        column = column_map[position[0]]
        return row, column


# Start the game
game = ChessGame()
game.play_game()

