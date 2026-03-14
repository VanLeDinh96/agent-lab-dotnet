# Project Guidelines

## Code Style
- PascalCase, `#nullable enable`, `ImplicitUsings`
- Namespace: `SocOps.{Layer}`
- JSInterop: `_ = SaveGameStateAsync()`
- Components: `OnStateChanged += StateHasChanged`, unsubscribe in `Dispose()`
- See [BingoSquare.razor](SocOps/Components/BingoSquare.razor) for CSS composition

## Architecture
Blazor WebAssembly, two-service pattern:
- **BingoGameService**: Stateful, localStorage, events
- **BingoLogicService**: Pure logic, immutable operations

State routing: StartScreen → GameScreen → BingoModal
See [Home.razor](SocOps/Pages/Home.razor)

## Build and Test
```bash
dotnet build SocOps/SocOps.csproj
dotnet run --project SocOps
dotnet publish -c Release -o ../publish
```
.NET 10 SDK. GitHub Actions deploys to Pages.

## Conventions
- Immutable data: Return new `List<T>`; mutations break UI
- localStorage: Use `STORAGE_VERSION` for changes
- CSS: Custom utilities in [app.css](SocOps/wwwroot/css/app.css), no externals
- Components: Prefer parameters over global state
- Board: 5×5, 24 questions + free space; update CENTER_INDEX for changes

See [BingoGameService.cs](SocOps/Services/BingoGameService.cs)</content>
<parameter name="filePath">f:\projects\BiKipVoCong\agent-lab-dotnet\.github\copilot-instructions.md