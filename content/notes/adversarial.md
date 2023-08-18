# Adversarial situation

-   Situations where there’s an obstacle between the goal and the current state, like an adversary in a game
-   Algorithms

    -   Minimax

        -   Every possible outcome has a value:
            -   Win -1, Tie 0, Lose 1
        -   `MAX` > Maximize score `min(result(s, a))`

            ```
            function MIN-VALUE(state):
            if TERMINAL(state):
            return UTILITY (state)
            v = infinity
            for action in ACTIONS(state):
            v = MIN(v, MAX-VALUE(RESULT(state, action)))
            return v
            ```

        -   `MIN` > Minimize score `max(result(s, a))`

            ```
            function MAX-VALUE(state):
            if TERMINAL(state):
            return UTILITY (state)
            v = -infinity
            for action in ACTIONS(state):
            v = MAX(v, MIN-VALUE(RESULT(state, action)))
            return v
            ```

        -   Game example
            -   Initial state
            -   Current player
            -   Legal moves
            -   State after move
            -   Check if game ends
            -   Checks final score
        -   Optimizations

            -   When there are several possible next moves we can take for granted the best possible solutions by discarding the ones that can’t be better than the ones we have

                ```
                GAME

                4
                |-4
                |-8
                |-5

                <=3
                |-9
                |-3
                |-?

                <=2
                |-2
                |-?
                |-?

                We’ll just need to check for values less than 4 to get an optimal decision
                ```

-   Depth-Limited Minimax
-   It acts like minimax but limiting the number of options to take in count
-   It uses an `evaluation function` to estimate the expected utility of the game from a given state
