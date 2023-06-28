Evmos Installation in Cosmos

To install Evmos, a Cosmos-SDK module that enables Ethereum Virtual Machine (EVM) compatibility within a Cosmos network, you can follow these steps:

1. Set up a Cosmos-SDK environment:
   - Make sure you have Go installed on your system. You can download it from the official Go website (https://golang.org/dl/).
   - Set up your Go workspace by defining the `GOPATH` environment variable and adding the workspace's `bin` directory to your `PATH`. For example:
     ```
     export GOPATH=$HOME/go
     export PATH=$PATH:$GOPATH/bin
     ```
   - Create the necessary directory structure for your Go workspace:
     ```
     mkdir -p $GOPATH/src/github.com/cosmos
     cd $GOPATH/src/github.com/cosmos
     ```

2. Clone the Cosmos-SDK repository:
   ```
   git clone https://github.com/cosmos/cosmos-sdk.git
   cd cosmos-sdk
   ```

3. Checkout the version of Cosmos-SDK that is compatible with Evmos:
   ```
   git checkout v0.44.0
   ```

4. Install the necessary dependencies:
   ```
   make tools
   make install
   ```

5. Clone the Evmos repository:
   ```
   cd $GOPATH/src/github.com/cosmos
   git clone https://github.com/tharsis/evmos.git
   cd evmos
   ```

6. Install the Evmos module:
   ```
   make install
   ```

7. Update the configuration files:
   - Add the Evmos module to the list of modules in the `app/app.go` file:
     ```go
     // app/app.go

     app.ModuleBasics.RegisterModule(evm.Module{})
     ```

   - Update the `config/app.toml` file to include the Evmos module:
     ```toml
     # config/app.toml

     [modules]
     evm = true
     ```

   - Update the `config/genesis.json` file to include the Evmos module:
     ```json
     {
       "app_state": {
         "evm": {}
       }
     }
     ```

8. Build and initialize your Cosmos-SDK project:
   ```
   make install
   evmosd init <moniker> --chain-id <chain-id>
   ```

   Replace `<moniker>` with a name for your node, and `<chain-id>` with the desired chain ID for your network.

9. Run your Evmos-enabled Cosmos-SDK node:
   ```
   evmosd start
   ```

Congratulations! You have successfully installed Evmos in your Cosmos-SDK project. You can now interact with the EVM-compatible functionality provided by Evmos in your Cosmos network.
