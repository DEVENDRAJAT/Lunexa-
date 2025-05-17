# Lunexa-<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Simple Chess Game</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chessboard.js/1.0.0/css/chessboard.min.css" />
  <style>
    #board {
      width: 400px;
      margin: 20px auto;
    }
  </style>
</head>
<body>

<h2 style="text-align: center;">Simple Chess Game</h2>
<div id="board"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/chess.js/0.13.4/chess.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/chessboard.js/1.0.0/js/chessboard.min.js"></script>
<script>
  const game = new Chess();

  const board = Chessboard('board', {
    draggable: true,
    position: 'start',
    onDrop: (source, target) => {
      const move = game.move({
        from: source,
        to: target,
        promotion: 'q'
      });

      if (move === null) return 'snapback';
    },
    onSnapEnd: () => {
      board.position(game.fen());
    }
  });
</script>

</body>
</html>