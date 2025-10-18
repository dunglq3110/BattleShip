# Battleship PVE Game

A web-based Battleship game built with Blazor Server (.NET 9) and MudBlazor, featuring Player vs Computer gameplay with intelligent AI opponent.

## 🎮 Game Features

### Core Gameplay
- **7x7 Grid Battle System**: Classic Battleship gameplay on a compact 7x7 grid
- **3 Ships Per Player**:
  - 1-cell ship (Destroyer)
  - 2-cell ship (Cruiser)
  - 3-cell ship (Battleship)
- **Turn-Based Combat**: Alternating turns between player and computer
- **Visual Feedback**:
  - Red "X" marker for successful hits
  - Yellow highlight for missed shots
  - Blue ships visible on player's grid only

### Intelligent AI Opponent (Anlq)
The computer opponent features sophisticated targeting logic:
- **Hunt Mode**: Random cell selection when no ships are hit
- **Target Mode**: Prioritizes adjacent cells after scoring a hit
- **Orientation Detection**: Identifies ship direction after consecutive hits
- **Smart Cleanup**: Removes irrelevant targets after sinking a ship
- **Adaptive Strategy**: Adjusts targeting based on remaining ship sizes

### User Experience
- **Ship Placement**: Random ship placement with unlimited randomization
- **Turn Counter**: Track game progress
- **Game Over Dialog**: Displays winner, turn count, and rematch options
- **Responsive Design**: Works on desktop and mobile devices

## 🎯 How to Play

1. **Navigate to `/pve`** route to start a new game
2. **Click "Ready"** to generate initial ship placements
3. **Click "Randomize Ships"** to adjust your ship positions (optional)
4. **Click "Play"** when satisfied with ship placement
5. **Select cells** on Anlq's grid (right side) to shoot
6. **Alternating turns** - Computer shoots automatically after your turn
7. **Win condition** - Sink all enemy ships first!
8. **Game Over** - Choose to rematch or return to title

## 🎨 Visual Guide

### Game States

**Setup Phase**:
- Player can see their ships (blue cells)
- Computer ships are hidden
- Randomize button available

**Battle Phase**:
- Red X = Hit
- Yellow background = Miss
- Gray = Untargeted cell
- Blue = Player's ships

**End Game**:
- Dialog shows winner and statistics
- Options to rematch or return home

## 🧠 AI Algorithm

The computer opponent uses a multi-tiered targeting system:

1. **Priority Queue System**: Maintains a list of high-value targets
2. **Hit Response**: Adds all adjacent cells to priority queue
3. **Pattern Recognition**: Detects horizontal/vertical ship orientation
4. **Elimination Strategy**: Removes invalid targets after sinking ships
5. **Fallback Random**: Uses random targeting when no priorities exist

## 🔧 Customization

### Grid Size
Change grid dimensions in `Pve.razor`:
```csharp
private Cell[,] playerGrid = new Cell[7, 7]; // Change 7 to desired size
```

### Ship Configuration
Modify ship sizes in `PlaceShipsRandomly` method:
```csharp
int[] shipSizes = { 3, 2, 1 }; // Add or modify ship sizes
```

### Styling
Adjust colors in `GetCellStyle` method:
```csharp
return baseStyle + " background-color: #your-color;";
```

## 🐛 Troubleshooting

### MudBlazor not loading
- Ensure CSS and JS references are in `App.razor`
- Check that MudBlazor service is registered in `Program.cs`

### Game not responding
- Check browser console for JavaScript errors
- Verify Blazor Server connection is active

### Ships overlapping
- The placement algorithm includes collision detection
- If issues persist, check `CanPlaceShip` method logic

## 📝 Future Enhancements

- [ ] Multiplayer mode (PVP)
- [ ] Difficulty levels for AI
- [ ] Sound effects and animations
- [ ] Score tracking and leaderboards
- [ ] Custom ship placement (drag & drop)
- [ ] Game replay system
- [ ] Save/load game state
- [ ] Mobile touch optimization

## 🤝 Contributing

Feel free to fork this project and submit pull requests for improvements!

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

Created with ❤️ for Battleship enthusiasts

## 🙏 Acknowledgments

- Built with [Blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor)
- UI Components by [MudBlazor](https://mudblazor.com/)
- Inspired by the classic Battleship board game

---

**Enjoy the game! 🚢💥**
