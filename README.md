# Install-Evmos-in-Cosmos
To install the Evmos module into a clean Cosmos SDK, you would need to follow these general steps:

1. Set up a clean Cosmos SDK: Start by setting up a new Cosmos SDK project or a clean working directory. You can find instructions on how to set up a new Cosmos SDK project in the official documentation.

2. Add Evmos module dependency: In your clean Cosmos SDK project, you'll need to add the Evmos module as a dependency. You can do this by adding the module's repository URL to the `go.mod` file of your project. Here's an example of how you can add the Evmos module using `go get` command:

   ```shell
   go get github.com/tharsis/ethermint@v0.6.3
   ```

   This command fetches the Evmos module at version `v0.6.3` from the official repository.

3. Register the Evmos module: After adding the Evmos module as a dependency, you need to register it in the Cosmos SDK. Locate the `app/app.go` file in your project, and find the `MakeEncodingConfig` function. In that function, register the Evmos module by adding the following line:

   ```go
   evmos.ModuleBasics.RegisterLegacyAminoCodec(cdc.Amino)
   ```

4. Import and configure the Evmos module: In your application's `app/app.go` file, import the necessary Evmos packages. Here's an example of how you can import the required packages:

   ```go
   import (
   	"github.com/tharsis/ethermint/x/evm"
   	"github.com/tharsis/ethermint/x/evm/types"
   )
   ```

   Additionally, add the Evmos module to the application's module list. Locate the `defaultGenesis()` function and add the Evmos module to the module list as follows:

   ```go
   app.ModuleBasics.RegisterModule(evm.Module{})
   ```

   Finally, ensure that the Evmos module is included in the application's `app.toml` file under the `enabled` modules section.

5. Build and run your application: Once you have completed the above steps, you can build and run your Cosmos SDK application with the Evmos module. Use the appropriate commands based on your project's setup, such as `make`, `go build`, or any other build command specific to your project.

Please note that the above steps provide a general overview of how to integrate the Evmos module into a clean Cosmos SDK project. The exact steps and configuration might vary based on the specific versions of the Cosmos SDK and Evmos module you are using. It's always recommended to refer to the official documentation and repositories of Cosmos SDK and Evmos for the most up-to-date and accurate instructions.
