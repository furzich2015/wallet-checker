<template>
    <div class="home" v-if="isDataLoaded">
      <div class="min-w-full header pb-4 pt-4">
        <h1 class="text-3xl">FurZich Team</h1>
    
        <table class="w-full border">
          <thead>
            <tr>
              <th class="border">Network</th>
              <th class="border">Wallets Count</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="border">ZkSync</td>
              <td class="border">{{ data.zksync_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">Starknet</td>
              <td class="border">{{ data.starknet_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">Layerzero</td>
              <td class="border">{{ data.layerzero_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">Zora</td>
              <td class="border">{{ data.zora_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">Aptos</td>
              <td class="border">{{ data.aptos_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">Linea</td>
              <td class="border">{{ data.linea_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">Scroll</td>
              <td class="border">{{ data.scroll_wallets.length }}</td>
            </tr>
            <tr>
              <td class="border">EVM / Balances</td>
              <td class="border">{{ data.evm_wallets.length }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </template>
  

<script>

export default {
    data() {
        return {
            data: [],
            isDataLoaded: false,
        }
    },
    created() {
        this.loadData()
    },
    methods: {
        loadData() {
            this.$axios.get('/api/stats').then((response) => {
                this.data = response.data
                this.isDataLoaded = true
            }).catch((error) => {
                console.error('Ошибка при загрузке данных:', error)
            })
        },
    },
}
</script>
