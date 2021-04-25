# Index Generator
Automatically generate index / barrel files with all the exports needed for your library.

## Usage

1. Add in your `pubspec.yaml`:
```yaml
dev_dependicies:
  index_generator: ^0.0.0
# ...
index_generator:
  filters:
    - black: .*.g.dart$
  # Define the paths of the folders in which to generate the index files
  folders:
    - path: lib
```

2. You can generate index files with one of the following two commands:
  - `flutter pub run index_generator:main`
  - `dart run index_generator:main`

## Advance Usage

```yaml
index_generator:
  # You can define the default name of the index file
  index_name: barrel
  # You can define general filters for all folders
  filters:
    - black: .*\.g$
  folders:
    - path: lib
      # You can define specific filters for this folder
      filters:
        - white: .*\include.g$
    - path: generator
      # You can define the name of the index file
      index_name: main
      # You can define the name of the library to use within the index
      library: index_generator
```

- **index_name**: Prioritize ownership in folders, otherwise it will use the one defined in the generator.
  If it is missing, if the folder is `lib` it will use the package name otherwise the folder name
- **filters**: You can define `black` filters that remove files from the index but `white` filters will add them back
  You can use [RegExp] expressions

## Features and bugs

Please file feature requests and bugs at the [issue tracker][tracker].

[tracker]: http://example.com/issues/replaceme
