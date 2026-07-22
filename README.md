# ilkersevim_type_safe_bloc

Type-safe `flutter_bloc` helpers: `BuildContext` extensions and thin widgets
around `BlocSelector`, `BlocBuilder`, `BlocListener`, and `BlocConsumer`.

## Why use this package?

- Make each Cubit/BLoC and state relationship explicit at compile time.
- Replace repeated context lookup and widget generic boilerplate with one
  consistent API.
- Use nullable lookup helpers when a provider is optional, while retaining
  fail-fast access for required providers.

License: [Apache-2.0](LICENSE). Issues:
[github.com/redjadet/ilkersevim_type_safe_bloc/issues](https://github.com/redjadet/ilkersevim_type_safe_bloc/issues).

## Installation

```yaml
dependencies:
  ilkersevim_type_safe_bloc: ^0.1.2
```

Requires Flutter `>=3.38.0`, Dart `>=3.12.0`, `flutter_bloc` ^9.1.1.

## Context extensions

```dart
import 'package:ilkersevim_type_safe_bloc/ilkersevim_type_safe_bloc.dart';

final counterCubit = context.cubit<CounterCubit>();
final count = context.watchState<CounterCubit, CounterState>().count;
```

## TypeSafeBlocSelector

```dart
TypeSafeBlocSelector<CounterCubit, CounterState, int>(
  selector: (state) => state.count,
  builder: (context, count) => Text('Count: $count'),
)
```

## API stability

Public type names and method signatures are a semantic-versioned contract.
Breaking changes require a major version bump.

## Publishing

Releases are tagged `vX.Y.Z` matching `pubspec.yaml`. Automated publishing uses
GitHub Actions OIDC with the protected `pub.dev` Environment (reviewer:
`redjadet`).
