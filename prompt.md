I'm getting extra space on scroll on x and y axis for mobile devices for the index.html. Attaching the code below:


index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jungle Flip</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            overflow-x: hidden;
            overflow-y: hidden;
            margin: 0%;
            padding: 0%;
            
        }

        .background {
            background-image: url('img1.jpeg');
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center;
            /* width: 100vw; */
            height: 100vh;
            display: flex;
            /* Enable vertical alignment */
            flex-direction: column;
            align-items: center;
            /* Center elements vertically */
            justify-content: center;
            /* Center elements horizontally (optional) */
        }

        .background img {
            display: block;
            /* Ensure image takes full width */
            max-width: 100%;
            /* Prevent image overflow */
            margin-bottom: 2rem;
            /* Add some spacing below image */
        }

        #play {
            /* Button styles (adjust as needed) */
            font-size: 35px;
            text-shadow: 3px 4px 3px #161414, 3px 4px 5px #22551b;
            box-shadow:springgreen;
            padding: 15px 30px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            color: white;
            background-color: #007bff;
            animation: blinkBackground 3s infinite, slideIn 1s forwards;
        }

        @keyframes blinkBackground {
            0% {
                background-color: #228B22;
            }

            50% {
                background-color: #2E8B57;
            }

            100% {
                background-color: #C4B454;
            }
        }

        @keyframes slideIn {
            0% {
                transform: translateX(100vw);
            }

            100% {
                transform: translateX(0)
            }
        }

        @media (max-width: 576px) {
            #play {
                padding: 10px 20px;
                font-size: 25px;
            }
        }
    </style>
</head>

<body>
    <div class="background">
        <img src="i1.gif" alt="Jungle Flip Heading">
        <button id="play">Welcome</button>
    </div>
    
    <audio id="background-music" src="jungleSound.mp3" loop></audio>
    <script>
       
        // for apply sound music
        document.addEventListener('DOMContentLoaded', () => {
            const backgroundMusic = document.getElementById('background-music');

            const playBackgroundMusic = () => {
                backgroundMusic.play().catch(() => {
                    // Ignore errors
                });
                localStorage.setItem('isPlaying', 'true');
                document.removeEventListener('mouseover', playBackgroundMusic);
            };

            document.addEventListener('mouseover', playBackgroundMusic);
        });

        // Link the second page
        document.getElementById('play').addEventListener('click', () => {
            window.location.href = "secondPage.html";
        });  
    </script>
</body>

</html>
```
