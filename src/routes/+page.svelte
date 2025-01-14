<script lang="ts">
    import {
        DataRequestBuilder,
        RadixDappToolkit,
        type WalletDataState,
    } from "@radixdlt/radix-dapp-toolkit";

    let rdt: RadixDappToolkit;
    let walletData: WalletDataState | null = $state(null);
    $effect(() => {
        // Initialize the toolkit
        rdt = RadixDappToolkit({
            dAppDefinitionAddress:
                "account_rdx16xdanhhgzzyen33q3fq3ljhekjh0ezh2gnu6z0gcrtsn9u29s2rwu7",
            networkId: 1,
            applicationName: "example-dapp",
        });
        // Require one account when the user logs in
        rdt.walletApi.setRequestData(DataRequestBuilder.accounts().exactly(1));
        // bridge the wallet data to Svelte reactive state
        rdt.walletApi.walletData$.subscribe((data) => {
            walletData = data;
        });
    });
    // Log changes to the wallet data
    $inspect(walletData);
</script>

<radix-connect-button></radix-connect-button>

<style>
    radix-connect-button {
        position: fixed;
        top: 10px;
        right: 10px;
        --radix-connect-button-border-radius: 5px;
        --radix-connect-button-width: 36px;
    }
    @media (min-width: 640px) {
        radix-connect-button {
            --radix-connect-button-width: 140px;
        }
    }
</style>
