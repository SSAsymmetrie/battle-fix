      elif (int(guess_row) == ship_row and int(guess_col) == ship_col_1)or \
           (int(guess_row) == ship_row and int(guess_col) == ship_col_2)or \
           (int(guess_row) == ship_row and int(guess_col) == ship_col_3) or \
           (int(guess_row) == ship_row_2 and int(guess_col) == fourth_col):  
        if (tries%2==0 or tries%2!=0) and multi ==1:
            print "Congratulations, You sunk my battleship!!"
        elif tries%2==0:
            print "Congratulations "+player1+"! You sunk my battleship!!"

        elif tries%2!=0:
            print "Congratulations "+player2+"! You sunk my battleship!!"

        guess_row = int(guess_row)-1
        guess_col = int(guess_col)-1
        
        board[ship_row-1][ship_col_1-1] = "O "
        board[ship_row-1][ship_col_2-1] = "O "
        board[ship_row-1][ship_col_3-1] = "O "
        board[ship_row_2-1][fourth_col-1] = "O "
        board[guess_row][guess_col]='* '   
        print_board(board)
        break
      else:
        guess_row = int(guess_row)-1
        guess_col = int(guess_col)-1
        if guess_row < 0 or guess_row > len(board) or guess_col < 0 or guess_col > len(board)-1:
          print "Oops, that's not even in the ocean."
        elif(board[guess_row][guess_col] == "X"):
          print "You guessed that one already."          
        else:
          print "You missed my battleship!"
          board[guess_row][guess_col] = "\033[1;32mX\033[1;m"
          print_board(board)
          print "Number of tries you have left! "+ str(tries - 1) #Checks to see if sting subtracted all integers
          tries = tries - 1
          if  tries < 1:
              
              board[ship_row-1][ship_col_1-1] = "O "
              board[ship_row-1][ship_col_2-1] = "O "
              board[ship_row-1][ship_col_3-1] = "O "
              board[ship_row_2-1][fourth_col-1] = "O "
              print_board(board)
              print "Game Over!!"
              print
              break
