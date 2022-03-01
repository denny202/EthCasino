<script >
    import { ethers } from "ethers";


    const provider = new ethers.providers.Web3Provider(window.ethereum);
    const signer = provider.getSigner();
    async function clear(){
        await provider.send("eth_requestAccounts", []);
        let user= await signer.getAddress();
        console.log(user)

    }
 clear();
</script>
