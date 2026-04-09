<template>
    <div class="topNav">
        <div class="rightTopNav navItem">
            <a href="/"><img src="/imgs/blueKing.png" alt="Calc Logo"></a>
        </div>
        <div class="purse">
            <p class="tagPurse">Purse:</p>
            <div id="purseAmount"><p>{{ purseAmount || 'Loading...' }} Loonies</p></div>
        </div>
        <div class="leftTopNav navItem">
            <a href="/market/">Market</a>
        </div>
    </div>
</template>


<style scoped>
    .navItem{
        width: 100px;
    }

    .topNav{
        width: 100vw;
        height: 100px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 10px;
        border-bottom: 1px solid var(--solidLine);
    }
    .tagPurse{
        font-size: .8rem;
    }
    .purse{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        width: 8rem;
    }
    #purseAmount {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid var(--solidLine);
        border-radius: 10px;
        padding: 5px;
    }
    .rightTopNav > a > img {
        width: auto;
        height: 90px;        
        margin-left: 10px;
    }

    .leftTopNav {
        display: flex;
        gap: 10px;
        margin-right: 10px;
    }

    .leftTopNav a {
        transition: .2s;
        text-decoration: none;
        color: var(--solidLine);
    }

    .leftTopNav > a:hover {
        animation: bigSmall .6s forwards;
    }

    @keyframes bigSmall {
        0% {
            transform: scale(1);
        }
        50% {
            transform: scale(1.15);
        }
        100% {
            transform: scale(1.1);
        }
    }

</style>

<script setup>
import { ref, onMounted, watch } from 'vue'

const purseAmount = ref('')

onMounted(() => {
  const pathSegments = window.location.pathname.split('/')
  const idFromUrl = pathSegments[pathSegments.length - 1]
  const stored = localStorage.getItem('purseAmount')
  
  if (stored) {
    purseAmount.value = stored
  } else {
    purseAmount.value = idFromUrl || '111'
    localStorage.setItem('purseAmount', purseAmount.value)
    console.log('Set purseAmount:', purseAmount.value)
  }

  if (!window.localStoragePatched) {
    const originalSetItem = localStorage.setItem
    localStorage.setItem = function(key, value) {
      const event = new CustomEvent('local-storage', { detail: { key, value } })
      window.dispatchEvent(event)
      originalSetItem.apply(this, arguments)
    }
    window.localStoragePatched = true
  }

  window.addEventListener('local-storage', (e) => {
    if (e.detail.key === 'purseAmount') {
      purseAmount.value = e.detail.value
    }
  })

  // Listen to cross-tab updates natively
  window.addEventListener('storage', (e) => {
    if (e.key === 'purseAmount' && e.newValue) {
      purseAmount.value = e.newValue
    }
  })
})

// Auto-sync changes
watch(purseAmount, (newAmount) => {
  if (newAmount) localStorage.setItem('purseAmount', newAmount)
})
</script>