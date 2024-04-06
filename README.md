# SME-Assignment
The original GameService.cpp file had an issue in the initializeVariables() function. The code was trying to access the getGameWindow() function of the GraphicService before the ServiceLocator was fully initialized. This resulted in the game not being able to compile and start.

To fix this issue, I've made the following changes:-
* Moved the initialization of the game_window variable from the initializeVariables() function to the initialize() function. This ensures that the ServiceLocator is fully initialized and the GraphicService is 
  available before trying to access the getGameWindow() function.
* Rearranged the order of function calls in the initialize() function. The ServiceLocator::initialize() call is now made before the initializeVariables() and showSplashScreen() calls. This guarantees that all the 
  necessary services are properly set up before the game state is initialized.

The key points of the implementation are:-

Delayed Initialization of game_window:- By moving the initialization of the game_window variable to the initializeVariables() function, which is called after the ServiceLocator is fully initialized, we ensure that the GraphicService is available and can provide the game window reference.
Proper Initialization Sequence:- Rearranging the order of function calls in the initialize() method ensures that the initialization process follows the correct sequence: first, the ServiceLocator is initialized; then, the game-specific variables are set up; and finally, the splash screen is displayed.
This fix should resolve the issue with the game not being able to compile and start, as it addresses the root cause of the problem - the premature access to the GraphicService before it was fully initialized.
