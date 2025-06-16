# BuildingBlocks.Infrastructure

A set of reusable building blocks for implementing the Infrastructure layer in .NET solutions, following Clean Architecture and CQRS principles.

## Features

- **Interceptors**: For auditable entities and distaptching domain events

## Usage Example

### Using Interceptors

```csharp
    builder.Services.AddScoped<ISaveChangesInterceptor, AuditableEntityInterceptor>();
    builder.Services.AddScoped<ISaveChangesInterceptor, DispatchDomainEventsInterceptor>();

    builder.Services.AddDbContext<ApplicationDbContext>((sp, options) =>
    {
        options.AddInterceptors(sp.GetServices<ISaveChangesInterceptor>());
    });
```

## Getting Started

1. Reference the `NetBlueprints.BuildingBlocks.Infrastructure` project in your solution.
2. Register the provided Interceptors.

## License

This project is licensed under the MIT License. See the LICENSE file for details.