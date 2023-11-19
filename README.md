<!DOCTYPE html>
<html lang="en">

<body style="font-family: 'Arial', sans-serif; display: flex; align-items: center; justify-content: center; height: 100vh; margin: 0; overflow: hidden; text-align: center; position: relative;">

    <label for="answer">Do you love me?</label>
    <input type="text" id="answer" placeholder="Type 'yes' or 'no'">
    <button onclick="checkAnswer()" style="font-size: 18px; padding: 10px 20px; cursor: pointer;">Submit</button>

    <div id="lovePopup" style="display: none; position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background-color: #fff; padding: 20px; border: 1px solid #ccc; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);">
        <p>🎉🎈 Yayy you are my everything lith te emo muchoooooo tooooooo! 🎈🎉</p>
        <button onclick="hideLovePopup()">Close</button>
    </div>

    <div id="sadPopup" style="display: none; position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background-color: #fff; padding: 20px; border: 1px solid #ccc; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);">
        <p>😢 I'm going to spoil friends for you now</p>
        <button onclick="hideSadPopup()">Close</button>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/animejs"></script>
    <script>
        function checkAnswer() {
            const userAnswer = document.getElementById('answer').value.toLowerCase();
            if (userAnswer === 'yes') {
                showLovePopup();
            } else if (userAnswer === 'no') {
                showSadPopup();
            } else {
                alert('Please type "yes" or "no".');
            }
        }

        function showLovePopup() {
            document.getElementById('lovePopup').style.display = 'block';
            animateFallingElements('🎈', 50, 'balloon');
            animateFallingElements('🎀', 50, 'ribbon');
        }

        function showSadPopup() {
            document.getElementById('sadPopup').style.display = 'block';
        }

        function hideLovePopup() {
            document.getElementById('lovePopup').style.display = 'none';
        }

        function hideSadPopup() {
            document.getElementById('sadPopup').style.display = 'none';
        }

        function animateFallingElements(symbol, count, className) {
            for (let i = 0; i < count; i++) {
                const element = document.createElement('span');
                element.innerHTML = symbol;
                element.className = className;
                document.body.appendChild(element);

                anime({
                    targets: element,
                    translateX: anime.random(-500, 500),
                    translateY: [anime.random(-100, 0), window.innerHeight + 100],
                    scale: [0.5, 1],
                    opacity: [0.5, 1],
                    easing: 'linear',
                    duration: anime.random(1000, 2000),
                    complete: function (anim) {
                        document.body.removeChild(element);
                    }
                });
            }
        }
    </script>

</body>

</html>
