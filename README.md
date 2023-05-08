Download Link: https://assignmentchef.com/product/solved-tic-tac-toe
<br>
<a href="https://www.youtube.com/playlist?list=PLhOuww6rJJNObtig0Kr-jgTJly1x04jgz" rel="nofollow">https://www.youtube.com/playlist?list=PLhOuww6rJJNObtig0Kr-jgTJly1x04jgz</a>

Create a Python program called <code>tictactoe.py</code> that will play a single round of the game Tic-Tac-Toe. The program should accept the following parameters:

<ul>

 <li><code>-b</code>|<code>--board</code>: The optional state of the board for the play. This will be a string of 9 characters representing the 9 cells of the 3×3 board. The string should be composed only of <code>X</code> and <code>O</code> to denote a player occupying that cell or <code>.</code> to show that the cell is open. The default is 9 ‘.’ as all cells are open.</li>

 <li><code>-p</code>|<code>--player</code>: An optional player which must be either <code>X</code> or <code>O</code>.</li>

 <li><code>-c</code>|<code>--cell</code>: An optional cell which must be in the range 1-9 (inclusive).</li>

</ul>

Here is the usage the program should print for <code>-h</code> or <code>--help</code>:

<pre><code>$ ./tictactoe.py -husage: tictactoe.py [-h] [-b str] [-p str] [-c int]Tic-Tac-Toeoptional arguments:  -h, --help            show this help message and exit  -b str, --board str   The state of the board (default: .........)  -p str, --player str  Player (default: None)  -c int, --cell int    Cell 1-9 (default: None)</code></pre>

The program will print the state of the board plus any modifications to the state made by <code>--player</code> and <code>--cell</code> along with the final outcome of the game which can either be “No winner” or “{player} has won.”

When run with no arguments, it should print a blank Tic-Tac-Toe board and “No winner”:

<pre><code>$ ./tictactoe.py-------------| 1 | 2 | 3 |-------------| 4 | 5 | 6 |-------------| 7 | 8 | 9 |-------------No winner.</code></pre>

Given a valid <code>--player</code> trying to take an unoccupied <code>--cell</code>, the program should modify the state before printing the board and deciding the outcome:

<pre><code>$ ./tictactoe.py -p X -c 1-------------| X | 2 | 3 |-------------| 4 | 5 | 6 |-------------| 7 | 8 | 9 |-------------No winner.</code></pre>

The program should error out for a bad <code>--board</code>:

<pre><code>$ ./tictactoe.py -b ABC......usage: tictactoe.py [-h] [-b str] [-p str] [-c int]tictactoe.py: error: --board "ABC......" must be 9 characters of ., X, O</code></pre>

Or a bad <code>--cell</code>:

<pre><code>$ ./tictactoe.py -p X -c 10usage: tictactoe.py [-h] [-b str] [-p str] [-c int]tictactoe.py: error: argument -c/--cell: invalid choice: 10 (choose from 1, 2, 3, 4, 5, 6, 7, 8, 9)</code></pre>

Or a bad <code>--player</code>:

<pre><code>$ ./tictactoe.py -p A -c 1usage: tictactoe.py [-h] [-b str] [-p str] [-c int]tictactoe.py: error: argument -p/--player: invalid choice: 'A' (choose from 'X', 'O')</code></pre>

Or in the event a <code>--player</code> is trying to take an occupied <code>--cell</code>:

<pre><code>$ ./tictactoe.py -b X........ -p O -c 1usage: tictactoe.py [-h] [-b str] [-p str] [-c int]tictactoe.py: error: --cell "1" already taken</code></pre>

Or if only <code>--player</code> or <code>--cell</code> is provided:

<pre><code>$ ./tictactoe.py --player Xusage: tictactoe.py [-h] [-b board] [-p player] [-c cell]tictactoe.py: error: Must provide both --player and --cell</code></pre>

The program should detect a winning state:

<pre><code>$ ./tictactoe.py -b .XX....OO -p X -c 1-------------| X | X | X |-------------| 4 | 5 | 6 |-------------| 7 | O | O |-------------X has won!</code></pre>

The program should pass all tests:

<pre><code>$ make testpytest -xv test.py============================= test session starts ==============================...collected 15 itemstest.py::test_exists PASSED                                              [  6%]test.py::test_usage PASSED                                               [ 13%]test.py::test_no_input PASSED                                            [ 20%]test.py::test_bad_board PASSED                                           [ 26%]test.py::test_bad_player PASSED                                          [ 33%]test.py::test_bad_cell_int PASSED                                        [ 40%]test.py::test_bad_cell_str PASSED                                        [ 46%]test.py::test_both_player_and_cell PASSED                                [ 53%]test.py::test_good_board_01 PASSED                                       [ 60%]test.py::test_good_board_02 PASSED                                       [ 66%]test.py::test_mutate_board_01 PASSED                                     [ 73%]test.py::test_mutate_board_02 PASSED                                     [ 80%]test.py::test_mutate_cell_taken PASSED                                   [ 86%]test.py::test_winning PASSED                                             [ 93%]test.py::test_losing PASSED                                              [100%]============================== 15 passed in 2.12s ==============================</code></pre>