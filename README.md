# DAA-Code
def is_valid(board):
    # Check if the board configuration is valid. No two queens should attack each other.
    n = len(board)
    for i in range(n):
        for j in range(i + 1, n):
            if board[i] == board[j] or abs(board[i] - board[j]) == j - i:
                return False
    return True

def base_n_to_digits(num, base, length):
    # Convert a decimal number to a list of digits in base-N.
    digits = []
    for _ in range(length):
        digits.insert(0, num % base)
        num //= base
    return digits

def has_unique_digits(digits):
    # Ensure no repeated digits (no queens in same row).
    return len(digits) == len(set(digits))

def solve_n_queens_prediction(n):
    # Solve N-Queens using a prediction-based filtering method.
    solutions = []
    max_val = n ** n  # Total permutations in base-N
    step = n  # Step size (simple prediction logic)

for i in range(0, max_val, step):
        board = base_n_to_digits(i, n, n)
        if has_unique_digits(board):
            if is_valid(board):
                solutions.append(board)
return solutions

def print_board(board):
    # Display the board in a human-readable format.
    n = len(board)
    for row in board:
        line = ['.'] * n
        line[row] = 'Q'
        print(' '.join(line))
    print("\n")

if __name__ == "__main__":
    try:
        n = int(input("Enter the size of the board (N): "))
        results = solve_n_queens_prediction(n)
        print(f"\nFound {len(results)} solution(s) for {n}-Queens.\n")

 # Display all solutions
  for idx, sol in enumerate(results, start=1):
  print(f"Solution {idx}: {sol}")
  print_board(sol)

  except ValueError:
  print("Please enter a valid integer.")
  
Output:        
Enter the size of the board (N): 5
Found 2 solution(s) for 5-Queens.
Solution 1: [2, 4, 1, 3, 0]
. . Q . .
. . . . Q
. Q . . .
. . . Q .
Q . . . .

Solution 2: [3, 1, 4, 2, 0]
. . . Q .
. Q . . .
. . . . Q
. . Q . .
Q . . . .
