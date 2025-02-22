# pkg/model

This package provides functionality for loading and managing models.

## pkg/model/loader_test.go
This file contains tests for the ModelLoader component. The ModelLoader is responsible for loading and managing models. The tests cover various aspects of the ModelLoader, including creating a new instance, checking if a model exists in the model path, listing all valid model files, loading a model, and shutting down a loaded model. The tests use mock objects to simulate the behavior of the underlying model loading mechanism. The tests verify that the ModelLoader functions correctly in different scenarios, such as when a model is successfully loaded, when a model fails to load, and when a model is shut down.

## pkg/model/model_suite_test.go
This file contains a single function, TestModel, which is used to run the Ginkgo test suite for the LocalAI model. The function registers a custom fail handler and then runs the test suite.

## pkg/model/filters.go
This file contains functions for filtering models.

## pkg/model/initializers.go
This file contains functions for initializing models.

## pkg/model/loader.go
This file contains the ModelLoader component, which is responsible for loading and managing models.

## pkg/model/loader_options.go
This file contains options for the ModelLoader component.

## pkg/model/model.go
This file contains the Model struct, which represents a loaded model.

## pkg/model/process.go
This file contains functions for processing models.

## pkg/model/watchdog.go
This file contains functions for monitoring models.

