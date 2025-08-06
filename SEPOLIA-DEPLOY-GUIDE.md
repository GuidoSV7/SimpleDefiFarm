# 🚀 GUÍA DE DESPLIEGUE EN SEPOLIA TESTNET

## 📋 PRERREQUISITOS

### 1. **MetaMask configurado con Sepolia**
- Instala MetaMask
- Agrega la red Sepolia:
  - Nombre: Ethereum Sepolia
  - RPC URL: https://sepolia.infura.io/v3/YOUR_INFURA_ID
  - Chain ID: 11155111
  - Símbolo: ETH
  - Explorer: https://sepolia.etherscan.io

### 2. **ETH de prueba en Sepolia**
Consigue ETH gratis en estos faucets:
- https://sepoliafaucet.com/
- https://faucet.sepolia.dev/
- https://faucet-sepolia.rockx.com/

### 3. **APIs necesarias**

#### **Infura (para conectar a Sepolia)**
1. Ve a https://infura.io
2. Crea una cuenta gratuita
3. Crea un nuevo proyecto
4. Copia el Project ID

#### **Etherscan (para verificar contratos)**
1. Ve a https://etherscan.io/apis
2. Crea una cuenta
3. Genera un API Key gratuito

## 🔧 CONFIGURACIÓN

### 1. **Configurar variables de entorno**
Edita el archivo `.env` con tus datos reales:

```env
# Tu clave privada de MetaMask (sin 0x)
PRIVATE_KEY=abc123def456...

# Tu Project ID de Infura
INFURA_PROJECT_ID=12345678-1234-1234-1234-123456789abc

# URL completa de Sepolia
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/12345678-1234-1234-1234-123456789abc

# Tu API Key de Etherscan
ETHERSCAN_API_KEY=ABC123DEF456GHI789JKL012MNO345PQR
```

**⚠️ IMPORTANTE:** 
- Nunca subas el archivo `.env` a GitHub
- Usa una wallet de pruebas, no tu wallet principal
- Solo pon ETH de prueba, nunca ETH real

### 2. **Exportar clave privada de MetaMask**
1. Abre MetaMask
2. Click en los 3 puntos → Account details
3. Click en "Export Private Key"
4. Ingresa tu contraseña
5. Copia la clave (sin el prefijo 0x)

## 🚀 DESPLIEGUE

### **Paso 1: Compilar contratos**
```bash
npm run compile
```

### **Paso 2: Desplegar en Sepolia**
```bash
npm run deploy:sepolia
```

El script hará:
- ✅ Verificar que tienes suficiente ETH
- ✅ Desplegar DAppToken
- ✅ Desplegar LPToken  
- ✅ Desplegar TokenFarm
- ✅ Configurar permisos
- ✅ Mintear tokens de prueba
- ✅ Guardar direcciones en `deployed-addresses-sepolia.json`

## 🔍 VERIFICACIÓN DE CONTRATOS

Después del despliegue, verifica los contratos en Etherscan:

```bash
# Verificar DAppToken
npx hardhat verify --network sepolia [DAPP_TOKEN_ADDRESS]

# Verificar LPToken
npx hardhat verify --network sepolia [LP_TOKEN_ADDRESS]

# Verificar TokenFarm
npx hardhat verify --network sepolia [TOKEN_FARM_ADDRESS] "[DAPP_TOKEN_ADDRESS]" "[LP_TOKEN_ADDRESS]"
```

Las direcciones exactas aparecerán en la terminal después del despliegue.

## ✅ VERIFICACIÓN DE ÉXITO

### **1. En la terminal verás:**
```
🎉 ¡DESPLIEGUE EN SEPOLIA COMPLETADO!
📋 Resumen de contratos:
   • DAppToken: 0x...
   • LPToken: 0x...
   • TokenFarm: 0x...
```

### **2. En Sepolia Etherscan:**
- Ve a https://sepolia.etherscan.io
- Busca las direcciones de tus contratos
- Deberías ver las transacciones de despliegue

### **3. Contratos verificados mostrarán:**
- ✅ Código fuente visible
- ✅ ABI disponible
- ✅ Función de lectura/escritura

## 🔗 INTERACTUAR CON LOS CONTRATOS

### **Opción 1: Hardhat Console**
```bash
npm run console:sepolia
```

### **Opción 2: MetaMask + Etherscan**
1. Ve a la página del contrato en Etherscan
2. Click en "Write Contract"
3. Conecta tu MetaMask
4. Ejecuta funciones directamente

### **Opción 3: Frontend/DApp**
Usa las direcciones del archivo `deployed-addresses-sepolia.json` en tu aplicación.

## 📊 FUNCIONALIDADES DESPLEGADAS

### **DAppToken** (Token de recompensas)
- ✅ ERC20 estándar
- ✅ Función mint() para el owner
- ✅ Transferible

### **LPToken** (Token para staking)
- ✅ ERC20 estándar  
- ✅ Representa LP tokens
- ✅ Minteable por el owner

### **TokenFarm** (Contrato principal)
- ✅ Staking de LP tokens
- ✅ Recompensas proporcionales
- ✅ Sistema de fees configurable
- ✅ Rewards variables por bloque
- ✅ Modifiers de seguridad
- ✅ Struct para datos de usuarios

## 🆘 SOLUCIÓN DE PROBLEMAS

### **Error: "insufficient funds"**
- Necesitas más ETH en Sepolia
- Ve a los faucets mencionados arriba

### **Error: "invalid private key"**
- Verifica que la clave privada esté correcta
- No incluyas el prefijo "0x"
- Usa exactamente 64 caracteres

### **Error: "network not found"**  
- Verifica tu INFURA_PROJECT_ID
- Confirma que la URL de Sepolia sea correcta

### **Error de verificación**
- Espera unos minutos después del despliegue
- Verifica que uses las direcciones exactas
- Usa los parámetros del constructor correctos

## 🎉 ¡ÉXITO!

Si todo salió bien, tendrás:
- ✅ Contratos desplegados en Sepolia
- ✅ Contratos verificados en Etherscan
- ✅ Código fuente público y auditable
- ✅ DeFi Farm completamente funcional

**¡Tu proyecto ya está PUBLICADO y VERIFICADO en blockchain!** 🌟

---

## 📞 SOPORTE

Si tienes problemas:
1. Revisa los logs de error
2. Verifica las variables de entorno
3. Confirma que tengas ETH suficiente
4. Consulta la documentación de Hardhat
