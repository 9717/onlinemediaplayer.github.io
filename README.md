<html>

<head>
    <title>Media Player</title>
    <style>
        video {
            border: 2px solid #888;
        }
        .container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    </style>
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
</head>

<body bgcolor='skyblue';>
<span style='color:black;font-family:Times New Roman;font-size:50;font-style:bold'> Welcome to Nandan's Media player</span>


 <div class="container">
        <video id="myVideo" width="520" height="380" controls autoplay poster=".png">
            <!-- <source src="video.mp4" type="video/mp4"> -->
        </video><br>
        <input type="file" accept="video/*"/>
    </div>
 

    <script>
        var vid = document.getElementById("myVideo");
        // Play/Pause
        document.addEventListener("keydown", function(event) {
            if (event.keyCode == 32) {
                if (vid.paused) {
                    vid.play();
                } else {
                    vid.pause();
                }
            }
        });
        // Speed Up
        document.addEventListener("keydown", function(event) {
            if (event.keyCode == 38) {
                vid.playbackRate += 0.1;
                console.log(vid.playbackRate);
            }
        });
        // Speed Down
        document.addEventListener("keydown", function(event) {
            if (event.keyCode == 40) {
                vid.playbackRate -= 0.1;
                console.log(vid.playbackRate);
            }
        });
        // Forward
        document.addEventListener("keydown", function(event) {
            if (event.keyCode == 39) {
                vid.currentTime += 10;
                console.log(this.currentTime);
            }
        });
        // Backward
        document.addEventListener("keydown", function(event) {
            if (event.keyCode == 37) {
                vid.currentTime -= 3;
                console.log(this.currentTime);
            }
        });
        // Full Screen
        function toggleFullScreen() {
            if (!document.mozFullScreen && !document.webkitFullScreen) {
                if (vid.mozRequestFullScreen) {
                    vid.mozRequestFullScreen();
                } else {
                    vid.webkitRequestFullScreen(Element.ALLOW_KEYBOARD_INPUT);
                }
            } else {
                if (document.mozCancelFullScreen) {
                    document.mozCancelFullScreen();
                } else {
                    document.webkitCancelFullScreen();
                }
            }
        };
        document.addEventListener("keydown", function(event) {
            if (event.keyCode == 70) {
                toggleFullScreen();
            }
        }, false);
        // Open File
        (function localFileVideoPlayer() {
            var URL = window.URL || window.webkitURL
            var playSelectedFile = function (event) {
                var file = this.files[0]
                var videoNode = document.querySelector('video')
                var fileURL = URL.createObjectURL(file)
                videoNode.src = fileURL
            }
            var inputNode = document.querySelector('input')
            inputNode.addEventListener('change', playSelectedFile, false)
        })()
    </script>
</body>

</htm>
