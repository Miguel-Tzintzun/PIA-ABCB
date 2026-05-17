# PIA-ABCB
Proyecto Final de Aplicaciones Basadas en Cadenas de Bloques
"El proyecto se encuentra en la sección master"


# Registro Inmutable de Auditorías de Ciberseguridad (DApp)

**Producto Integrador de Aprendizaje (PIA) - Aplicaciones Basadas en Cadenas de Bloques**

---

## Descripción del Proyecto

Esta es una Aplicación Descentralizada (DApp) diseñada para gestionar un registro inmutable de auditorías de ciberseguridad. El sistema permite:

* **Transparencia:** Cualquier usuario puede consultar los reportes de auditoría existentes.
* **Inmutabilidad:** Los reportes se guardan en la blockchain, por lo que no pueden ser borrados ni modificados.
* **Gestión de Identidad:** Solo auditores autorizados mediante su wallet pueden registrar nuevos reportes.
* **Monetización:** Las empresas pueden solicitar auditorías prioritarias mediante un pago de **0.01 ETH**.

---

## Requisitos Previos

Asegúrate de tener instalado lo siguiente:

1. **Node.js:** (Versión LTS recomendada).
2. **MetaMask:** Extensión instalada en tu navegador.
3. **Visual Studio Code:** O tu editor de texto preferido.

---

## Instrucciones de Instalación y Ejecución

Sigue estos pasos detallados para configurar el entorno de desarrollo local.

### Paso 1: Descargar el proyecto e Instalar Dependencias

1. Clona este repositorio o descarga el código fuente:
`git clone <URL DEL REPOSITORIO>`
2. Abre una terminal en la carpeta raíz del proyecto (donde se encuentra el archivo `hardhat.config.ts`) e instala las dependencias de Hardhat:
`npm install`
3. Ahora, entra a la carpeta del frontend e instala las dependencias de React:
`cd mi-dapp`
`npm install`

### Paso 2: Iniciar la Blockchain Local

1. Regresa a la terminal de la **carpeta raíz** (fuera de `mi-dapp`).
2. Ejecuta el nodo local de Hardhat:
`npx hardhat node`
*(Nota: Verás una lista de cuentas y llaves privadas. Mantén esta terminal abierta siempre que uses la aplicación).*

### Paso 3: Configurar MetaMask

1. Abre MetaMask y selecciona "Agregar red" -> "Agregar una red manualmente".
2. Introduce los siguientes datos:
* **Nombre de la red:** Hardhat Local
* **Nueva URL de RPC:** [http://127.0.0.1:8545](https://www.google.com/search?q=http://127.0.0.1:8545)
* **ID de cadena:** 31337
* **Símbolo de moneda:** ETH


3. **Importar Cuenta:** Copia una de las "Private Keys" de la terminal del Paso 2, ve a MetaMask -> Importar cuenta y pégala. Ahora tendrás ETH de prueba.

### Paso 4: Desplegar el Smart Contract

1. Abre Remix IDE (remix.ethereum.org).
2. Crea un archivo `AuditRegistry.sol` y pega el código del contrato.
3. Compila el contrato en la pestaña "Solidity Compiler".
4. En la pestaña "Deploy", cambia el **Environment** a **Dev - Hardhat Provider**.
5. Haz clic en **Deploy**. Al terminar, copia la dirección del contrato desplegado.

### Paso 5: Vincular el Contrato con el Frontend

1. En Visual Studio Code, abre `mi-dapp/src/App.jsx`.
2. En la línea 6, actualiza la dirección del contrato:
`const contractAddress = "TU_DIRECCION_DE_REMIX_AQUI";`
3. Copia el **ABI** desde Remix (pestaña Compiler, hasta abajo) y pégalo en el archivo `mi-dapp/src/AuditRegistryABI.json`.

### Paso 6: Ejecutar la Aplicación

1. Abre una nueva terminal dentro de la carpeta `mi-dapp`.
2. Inicia el servidor de desarrollo:
`npm run dev`
3. Abre el enlace proporcionado (ej. http://localhost:5173) y conecta tu MetaMask.

---

## Solución de Problemas (Troubleshooting)

**Error: "Nonce too high" o Transacción fallida**
Si reinicias el comando `npx hardhat node`, debes resetear MetaMask para limpiar el historial de la red:

1. Ve a MetaMask -> Configuración -> Avanzado.
2. Haz clic en **Borrar datos de actividad de la pestaña** (Resetear cuenta).

**Error: "BrowserProvider is undefined"**
Asegúrate de haber ejecutado `npm install ethers` dentro de la carpeta `mi-dapp`. Este proyecto utiliza la versión más reciente de Ethers.js.
