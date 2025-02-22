# startup

This package is responsible for handling the loading and installation of models during the application's startup process. It interacts with galleries to search for models, downloads them if necessary, and installs them in the specified directory.

## Project package structure:
- model_preload.go
- model_preload_test.go
- startup_suite_test.go
- pkg/startup/model_preload.go

## Code summary:
The `InstallModels` function is the main entry point for this package. It takes a list of model URLs or local file paths, a model path, and a download status function. The function then iterates through the list of models and calls the `installModel` function for each one.

The `installModel` function searches for a model in the given galleries and installs it if found. If the model is not found, it attempts to download it from the remote library. The function takes a list of galleries, a model name, a model path, a download status function, and a boolean indicating whether to force a scan for models.

## Relations between code entities:
The `InstallModels` function relies on the `installModel` function to handle the actual installation of each model. The `installModel` function, in turn, interacts with the galleries and the remote library to locate and download the models.

## Unclear places:
It is unclear how the download status function is used to display the progress of model downloads.

## Dead code:
None found.

