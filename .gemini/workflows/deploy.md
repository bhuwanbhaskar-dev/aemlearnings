---
description: How to build and deploy the AEM project to local AEM Author instance
---

# Deploy AEM Project

Follow these steps to build and deploy the aemlearnings project to the local AEM Author instance.

## Prerequisites

- Jabba is installed and JDK 11 is available
- Local AEM Author instance is running at `http://localhost:4502`

## Steps

1. Switch to JDK 11 using Jabba
// turbo
```powershell
jabba use adopt@1.11.0-11
```

2. Verify Java version is 11
// turbo
```powershell
java -version
```

3. Run Maven build and deploy to localhost:4502
```powershell
cd i:\onPrem\Projects\aemlearnings
mvn clean install -PautoInstallSinglePackage -Daem.host=localhost -Daem.port=4502
```

4. Verify deployment by checking the AEM package manager at `http://localhost:4502/crx/packmgr/index.jsp`
