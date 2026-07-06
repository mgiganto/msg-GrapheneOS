## Integrating appsScopes

Once you have verified a clean, functional GrapheneOS build, follow these steps to integrate `appsScopes`.

### Step 1: Fetch and Apply Base Patch
1. Clone the repository:
   ```bash
   git clone [https://github.com/mgiganto/msg-GrapheneOS](https://github.com/mgiganto/msg-GrapheneOS)
   cd msg-GrapheneOS
   ```
2.  Unpack and apply the base patch from the repository directory:
   ```bash
   $ git am patches/0001-Actualizar-AppsScopes-a-implementacion-v1.7.2-FULL.patch
   ```


### Step 2: Apply Subproject Patches
The patches represent specific subprojects (subfolders) of the GrapheneOS source code. You can list the available patches using:
   ```bash
   find variantes/ -type f
   ```
Apply each individual patch to its corresponding directory within your GrapheneOS source tree (<grapheneos_src>) using the following commands:
   ```bash
   # Connectivity
   git -C <grapheneos_src>/packages/modules/Connectivity/ am variantes/parches/appsScopes/packages/modules/Connectivity/0001-AppsScopes-v1.7.2-Network.patch
  
   # Launcher3
   git -C <grapheneos_src>/packages/apps/Launcher3/ am variantes/parches/appsScopes/packages/apps/Launcher3/0001-AppsScopes-Integrate-shortcut-v1.7.2-20260622-Android-17.patch
  
   # Settings
   git -C <grapheneos_src>/packages/apps/Settings/ am variantes/parches/appsScopes/packages/apps/Settings/0001-AppsScope-Integrar-configuracion-en-Settings-v1.7.2-20260622-Android-17.patch
  
   # Framework Base
   git -C <grapheneos_src>/frameworks/base/ am variantes/parches/appsScopes/frameworks/base/0001-AppsScopes-implementacion-v1.7.2-20260623-Android-17.patch
   ```


### Step 3: Recompile
Perform the final build of your GrapheneOS system to include the appsScopes modifications.
