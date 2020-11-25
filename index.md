<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <link rel="icon" href="favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta name="description" content="of course they're real flamingos" />
    <title>flamingos</title>

    <style>
        * {
            box-sizing: border-box;
        }

        html,
        body {
            height: 100%;
        }

        body {
            margin: 0;
        }

        img {
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 100%;
        }

        #flamingos-img {
            opacity: 0;
        }

        button {
            position: absolute;
            top: 5%;
            left: 5%;
            z-index: 2;
            font-size: 1.5rem;
            padding: 0.5rem 1rem;
            color: white;
            border: 2px solid white;
            background: transparent;
            cursor: pointer;
        }

        video {
            opacity: 0;
            position: absolute;
            top: 1%;
            left: 50%;
            transform: translate(-50%);
            max-width: 95%;
            z-index: 1;
            transition: all 0.3s ease-in-out;
            border: 10px solid rgba(0, 0, 0, .5);
        }
    </style>
</head>

<body>
    <button id="play-button">?</button>
    <img id="low-res-flamingos" src="flamingos_low-res.gif" alt="dancing flamingos">
    <img id="flamingos-img" src="flamingos.gif" onload="removeLowResImg()" alt="dancing flamingos">
    <video id="flamingos-vid">
        <source src="flamingos.mp4" type="video/mp4">
    </video>

    <script>
        function removeLowResImg() {
            document.getElementById("low-res-flamingos").style.display = "none";
            document.getElementById("flamingos-img").style.opacity = "1";
        }

        let button = document.getElementById("play-button");
        let flamingo = document.getElementById("flamingos-vid");

        flamingo.onended = function () {
            button.style.opacity = "1";
            flamingo.style.opacity = "0";
        };
        
        button.addEventListener("click", function () {
            flamingo.style.opacity = "1";
            button.style.opacity = "0";
            if (flamingo.paused) {
                flamingo.play();
            }
            else {
                flamingo.currentTime = 0;
            }
        }); 
    </script>
</body>

</html>
