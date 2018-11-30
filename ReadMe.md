# Hubcap API docs

  - iwannaplay, getboard are GET
  - move is PUT
  - Parameters can be either headers or query string
  
## Endpoints

|Endpoint|Purpose|Parameters|Returns|Extra info|
|--------|-------|----------|-------|----------|
|api/game/iwannaplay|Queue you up to play a game|PlayerKey, (optional) opponent|The GameKey for the game you joined||
|api/game/getboard|Get the gameboard, will freeze request until it's your turn to perform a move|PlayerKey, GameKey|Current state of the game with provided GameKey||
|api/game/move|Update the state of the game|PlayerKey, GameKey, x, y|Error message if you did something wrong, otherwise OK|To skip turn send x = -1, y = -1|

## Bots

  - randy - The random bot
  
## Response models

### api/game/getboard

```cs
public class Response
{
    public int Turn { get; set; }
    public char YourToken { get; set; }
    public char[,] Board { get; set; }
    public string State { get; set; }
    public string PlayerOneScore { get; set; }
    public string PlayerTwoScore { get; set; }
    public List<Move> Moves { get; set; }
    
    public class Move
    {
        public char Disc { get; set; }
        public int X { get; set; }
        public int Y { get; set; }
    }
}
```

### api/game/iwannaplay
string

### api/game/move
string

## Samples...

  - api/game/iwannaplay?PlayerKey=asd&opponent=randy
  - api/game/getboard?PlayerKey=asd&GameKey=a329fe5e-6334-4073-975c-0e25054ca5db
  - api/game/move?PlayerKey=asd&GameKey=a329fe5e-6334-4073-975c-0e25054ca5db&x=1&y=4