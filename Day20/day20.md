Day 20 – Face Puzzle Game with Claude
Objective

The objective of this task was to learn how Claude can generate a complete browser-based game using a single prompt. The application uses the webcam to capture the user's photo, converts it into puzzle pieces, and creates an interactive drag-and-drop puzzle game with timers, move tracking, and a local leaderboard.

What Browser Game Development Is

Browser game development is the process of creating games that run directly inside a web browser using technologies such as HTML, CSS, and JavaScript. These games do not require installation and can be played instantly on desktop or mobile devices. Modern browser games can include animations, graphics, camera access, local storage, and interactive gameplay.

What Web Camera APIs Are

Web Camera APIs allow websites to access a device's camera through the browser after the user grants permission. Using the getUserMedia() API, developers can capture live video, take photos, and use the captured images inside web applications such as games, video calls, identity verification systems, and AI-powered tools.

What Image Processing Means

Image processing is the technique of manipulating or analyzing images using software. In this project, the captured selfie is processed by dividing it into multiple equal-sized pieces based on the selected puzzle difficulty. These pieces are then shuffled to create a playable puzzle that the user must solve.

Features of the Face Puzzle Game

The generated application includes several interactive features:

Live webcam access using the browser camera.
Capture a selfie directly inside the application.
Option to upload a photo if camera access is unavailable.
Difficulty selection with 3×3, 4×4, and 5×5 puzzle grids.
Automatic image slicing into puzzle pieces.
Random puzzle generation with drag-and-drop gameplay.
Mouse and touch support for desktop and mobile devices.
Live timer and move counter.
Correct piece indicator with green highlights.
Automatic win detection.
Results screen displaying completion time, moves, and difficulty.
Local leaderboard that stores the top five best scores using browser Local Storage.
Responsive user interface with modern animations and visual effects.
How the Puzzle Works

The game begins by requesting camera permission. After capturing a selfie, I selected a puzzle difficulty level. The application divided the image into multiple square pieces and randomly shuffled them across the puzzle board. My task was to drag each piece into its correct position. As pieces were placed correctly, they were highlighted, making it easier to track progress. Once every piece was correctly arranged, the game automatically detected completion and displayed the final results.

Timer and Move Counter

The timer started automatically as soon as the puzzle began and continuously displayed the elapsed time throughout the game. Every time I swapped two puzzle pieces, the move counter increased by one. These statistics helped measure both speed and efficiency while solving the puzzle.

Leaderboard Functionality

After completing the puzzle, my final time, total moves, puzzle difficulty, and completion date were automatically saved in the browser using Local Storage. The leaderboard displays the five best performances, allowing players to compare their previous attempts without requiring an online database or account.

My Experience

Building this application with Claude was impressive because a single prompt generated an entire working browser game. The application combined camera access, image processing, drag-and-drop mechanics, responsive design, local data storage, and animations without requiring manual coding. Testing the game helped me understand how modern browser technologies can work together to create interactive applications.

Biggest Insight

The biggest insight I gained was that AI can generate complete, functional applications rather than just code snippets. Claude was able to combine multiple web technologies into one integrated project, significantly reducing development time while producing a polished and interactive user experience.

What I Learned
How browser games are built using HTML, CSS, and JavaScript.
How Web Camera APIs enable live image capture in web applications.
How images can be processed into puzzle pieces using JavaScript.
How drag-and-drop interactions work in browser-based games.
The importance of timers and move counters in game mechanics.
How Local Storage can save game results without a backend.
How responsive UI design improves usability across different devices.
How AI can rapidly generate complete software projects from detailed prompts.
Screenshots Included

The following screenshots are included in the Day20 folder:

Camera permission screen
Live webcam preview
Captured photo
Difficulty selection screen
Puzzle gameplay
Timer and move counter
Completed puzzle results
Leaderboard
Responsive interface
Conclusion

This project demonstrated how Claude can accelerate browser game development by generating a complete, interactive application from a single prompt. The Face Puzzle Game combined camera integration, image processing, drag-and-drop functionality, timers, local storage, and responsive design into one polished application. It showed how AI can significantly simplify the software development process while producing high-quality results suitable for learning, experimentation, and portfolio projects.