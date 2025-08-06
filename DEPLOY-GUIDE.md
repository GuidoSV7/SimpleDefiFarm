#!/usr/bin/env node

console.log(`
🚀 GUÍA DE DESPLIEGUE LOCAL - SIMPLE DEFI FARM
${"=".repeat(50)}

Para desplegar y usar los contratos localmente, sigue estos pasos:

📋 PRERREQUISITOS:
   • Node.js instalado
   • NPM o Yarn
   • Git (opcional)

🔧 INSTALACIÓN:
   1. npm install
   2. npx hardhat compile

🌐 DESPLIEGUE LOCAL:

   PASO 1: Iniciar nodo local
   ----------------------
   En una terminal, ejecuta:
   → npm run node
   
   Esto iniciará un nodo de Hardhat local en http://127.0.0.1:8545
   ¡DEJA ESTA TERMINAL ABIERTA!

   PASO 2: Desplegar contratos
   --------------------------
   En OTRA terminal, ejecuta:
   → npm run deploy:local
   
   Esto desplegará:
   • DAppToken (token de recompensas)
   • LPToken (token para staking)
   • TokenFarm (contrato principal)

   PASO 3: Probar interacción (opcional)
   ------------------------------------
   → npm run interact
   
   Esto ejecutará un ejemplo completo de staking y rewards.

🧪 COMANDOS ÚTILES:

   • npm run test           → Ejecutar todas las pruebas
   • npm run test:farm      → Ejecutar solo pruebas de TokenFarm
   • npm run console        → Consola interactiva de Hardhat
   • npm run compile        → Compilar contratos
   • npm run clean          → Limpiar artifacts

🔗 DESPUÉS DEL DESPLIEGUE:

   Las direcciones de los contratos se guardan en:
   → deployed-addresses.json

   Puedes usar estas direcciones para:
   • Conectar desde frontend (React, Vue, etc.)
   • Interactuar desde scripts personalizados
   • Usar en consola de Hardhat

📱 CONECTAR METAMASK (opcional):

   1. Agregar red personalizada en MetaMask:
      • Nombre: Hardhat Local
      • RPC URL: http://127.0.0.1:8545
      • Chain ID: 31337
      • Símbolo: ETH
   
   2. Importar cuenta de testing:
      Las cuentas aparecen en la terminal cuando ejecutes "npm run node"

🆘 SOLUCIÓN DE PROBLEMAS:

   • Error de compilación → npm run clean && npm run compile
   • Error de red → Verificar que el nodo esté ejecutándose
   • Error de gas → Reiniciar el nodo (Ctrl+C y volver a ejecutar)

🎯 FUNCIONALIDADES IMPLEMENTADAS:

   ✅ Staking de LP tokens
   ✅ Rewards proporcionales
   ✅ Modifiers de seguridad
   ✅ Struct para info de usuarios
   ✅ Rewards variables por bloque
   ✅ Sistema de comisiones (fees)
   ✅ Pruebas completas

💡 EJEMPLO DE USO RÁPIDO:

   Terminal 1: npm run node
   Terminal 2: npm run deploy:local
   Terminal 3: npm run interact

¡Listo para usar tu DeFi Farm! 🌾
`);
