# Web architecture examples

The same attendance API implemented using three-layer architecture and Clean
Architecture with MediatR. Both applications use in-memory repositories; data
resets when the application restarts.

## Requirements

- .NET 10 SDK (10.0.100 or later in the 10.0 SDK series).
- C# 14, the default language version for the .NET 10 targets.

`global.json` selects an installed .NET 10 SDK and permits newer feature bands
within the 10.0 series.

## Build and run

From the repository root:

```sh
dotnet build WebArchitecturesExamples.sln --configuration Release
```

Run either application, or run both in separate terminals:

```sh
dotnet run --project ThreeLayered.Presentation --launch-profile http
dotnet run --project Clean.Presentation --launch-profile http
```

| Example | Swagger UI | API prefix |
| --- | --- | --- |
| Three-layer architecture | http://localhost:5082/swagger | `/api/attendance` |
| Clean Architecture | http://localhost:5100/swagger | `/api/clean/attendance` |

In Swagger, start a session with `courseId: 1001` and `durationMinutes: 15`.
Use the returned `sessionId` to mark attendance for `studentId: 1`, then inspect
the session summary and course statistics. Course 1001 has three seeded students
(IDs 1–3); course 1002 has two (IDs 4–5).
