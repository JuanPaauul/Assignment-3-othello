# Othello
## Installation guide
You will need Visual studio code ass well as git installed.
- Zip downloading
    1. You can simply click on the green button "code" and the click on Download ZIP
    2. Open the notebooks using jupyper
- Git clone
    1. Go to the directory you want to have this project
    2. Open git
    3. Insert the following code
        ```
        > git clone https://github.com/JuanPaauul/Assignment-3-othello.git
        > code .
        ```
- Description
    We tried with the alpha beta prunning algoritm to find the best move in the game. As we tried to make it work, we noticed that the algorithm is not working for a reason that we dont found.<br>
    We tried to find a solution but we just noticed that making the algorithm work step-by-step workd perfectly, but when we implement it to the alpha beta algoritm, it does not work.<br>
    The heuristic we implemented, is the number of enemy pieces taken by a single move. Is the player is max, the heuristic will increase +1. In the case it is min's turn, it will decrese -1.<br>
    ```
    return self.move_up_right(next_position, board, player_piece, utility+player_piece,enemy_positions)#enemy found
    ```
    We had in mind that a great houristic would occuping the corner cell because that cells make the piece invensible.<br>
- Experiments made
    We tried making some experiments in the way the algorith finds the possible moves according to who the turn is. In the code, you can see that we hace some "can_ move_to..." that help us to know where we have the border, ally piece, enemy piece or just an empty cell.<br>
    ```
    def can_move_up(self, piece, board, player_piece)
    def can_move_down(self, piece, board, player_piece)
    def can_move_right(self, piece, board, player_piece)
    def can_move_left(self, piece, board, player_piece)
    ```
    When we finished making those algorithms, we experiment mergin those states which have the same destin so with a single move, some origin can go to the same destin taking more enemies with the move. So we made a method that merges those states previusly mentioned.<br>
    ```
    new_states = simplify_repited_destins(new_states, self.board)
    ```
    ![image](https://github.com/JuanPaauul/Assignment-3-othello/Merge_origins.png?raw=true)
- Conclutions
    Depending on the player (min or max), alpha beta prunning will always try to find the best move in less time than min max algorithm by cutting of the game-tree. As the algorithm works, it will play with the utility value to work properly.
    A good way to improve the time of execution is to implement a max_depth value on the alpha beta prunning. The main reason for this is the size of the game-tree. It will get bigger and bigger depending on the ammount of pieces and the ammount of possible moves. By cutting it according with a specific depth, we will still get a great move and we will also improve the performance of the IA.