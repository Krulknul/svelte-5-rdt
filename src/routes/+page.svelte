<script lang="ts">
    import { RadixDappToolkit } from "@radixdlt/radix-dapp-toolkit";

    let rdt;
    $effect(() => {
        rdt = RadixDappToolkit({
            dAppDefinitionAddress:
                "account_rdx16xdanhhgzzyen33q3fq3ljhekjh0ezh2gnu6z0gcrtsn9u29s2rwu7",
            networkId: 1,
            applicationName: "example-dapp",
        });
    });
</script>

<radix-connect-button></radix-connect-button>

<style>
    radix-connect-button {
        position: fixed;
        top: 10x;
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
