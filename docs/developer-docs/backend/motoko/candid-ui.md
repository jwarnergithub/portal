# 11: Using the Candid UI to test functions in a browser

## Overview
The canister interface description language—often referred to as Candid or more generally as the IDL—provides a common language for specifying the signature of a canister smart contract.

Candid provides a unified way for you to interact with canister smart contracts that are written in different languages or accessed using different tools.
For example, Candid provides a consistent view of a service whether the underlying program is native Rust, JavaScript, or any other programming language. 
Candid also enables different tools—such as the `dfx` command-line interface and the Network Nervous System dapp—to share a common description for a service.

Based on the type signature of the actor, Candid also provides a web interface that allows you to call canister functions for testing and debugging.

## Using Candid UI

After you have deployed your project in the local canister execution environment using the `dfx deploy` or `dfx canister install` command, you can access the Candid web interface endpoint in a browser. 

This web interface—the Candid UI—exposes the service description in a form, enabling you to quickly view and test functions and experiment with entering different data types without writing any front-end code.

To use the Candid web interface to test canister functions:

- #### Step 1: Find the Candid UI canister identifier associated with the current project using the `dfx canister id __Candid_UI` command. 

The command displays the canister identifier for the Candid UI with output similar to the following:

    r7inp-6aaaa-aaaaa-aaabq-cai


- #### Step 2: Copy the Candid UI canister identifier so that it is available in the clipboard. 

If you've stopped the local canister execution environment, restart it locally by running the following command:

    dfx start --background


- #### Step 3: Open a browser and navigate to the address and port number specified in the `dfx.json` configuration file. 

By default, the local canister execution environment binds to the `127.0.0.1:4943` address and port number.

- #### Step 4: Add the required `canisterId` parameter and the Candid UI canister identifier returned by the `dfx canister id __Candid_UI` command to the URL. 

For example, the full URL should look similar to the following but with the `CANDID-UI-CANISTER-IDENTIFIER` that was returned by the `dfx canister id __Candid_UI` command:

    http://127.0.0.1:4943/?canisterId=<CANDID-UI-CANISTER-IDENTIFIER>


For instance, with the example canister identifier for the Candid UI as shown above, this could look as follows:

    http://127.0.0.1:4943/?canisterId=r7inp-6aaaa-aaaaa-aaabq-cai


The browser then displays a form for you to specify a canister identifier or choose a Candid description (`.did`) file. 
Note that this field refers to the canister identifier of the canister you would like to interact with (as opposed to the canister identifier for the Candid UI that we used in the last step).

- #### Step 5: Specify the canister identifier of the canister you would like to test in the **Provide a canister ID** field, then click **Go** to display the service description.
    
If you aren’t sure which canister identifier to use, you can run the `dfx canister id` command to look up the identifier for a specific canister name. For instance, to get the canister identifier for a canister named `my_counter`, you would use:

    dfx canister id my_counter


- #### Step 6: Review the list of function calls and types defined in the dapp.

- #### Step 7: Type a value of the appropriate type for a function or click **Random** to generate a value, then click **Call** or **Query** to see the result.

:::info
Note that depending on the data type, the Candid interface might display additional configuration settings for testing functions.
:::

For example, if a function takes an array, you might need to specify the number of items in the array before entering values.


![Calculator functions](_attachments/candid-calc.png)
