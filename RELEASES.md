# ZG ZoneChants — releases and compatibility

Current source and protected release file: **1.4.0** (10 October 2026), author Elgochogms, All Rights Reserved. Uploaded to CurseForge as file **9124295** on 10 October; malware scanning was in progress at 20:44 ET. Project approval and public download remain pending.

- Minecraft 1.20.1, tested on dedicated Forge 47.4.10.
- Distribution layout: **server**.
- Required dependency from current source metadata: **ZoneCore** `[2.1.1,3)`. The protected candidate was smoke tested with protected ZoneCore 2.1.3.
- One CurseForge page per functional mod. Client and server files, when present, are uploaded to that same page and labeled with their compatible pair.
- Do not install `-dev`, fixture, test, source or unprotected build JARs.
- Protected candidate SHA-256: `FEE632E30295C999A77A8F62FC6F828E32C07EE3F051BB77E5247B8A78C666A8`.
- Forge smoke test: server started with both protected JARs, loaded four designs, `/za diseno listar` listed them, `/zonecore reload` reloaded the TOML, and server stopped cleanly. Prior 137 fixture checks were run against the original 1.4.0 build, not this protected JAR. Full modpack, graphical client, multiplayer and production hosting were not tested with the protected JAR.
- Check the final CurseForge file changelog, SHA-256 and dependency ranges before deploying to a persistent world.

## Español

El archivo protegido es **1.4.0**, con autor Elgochogms y licencia All Rights Reserved. SHA-256: `FEE632E30295C999A77A8F62FC6F828E32C07EE3F051BB77E5247B8A78C666A8`. Con ZoneCore 2.1.3 protegido arrancó en Forge 47.4.10, mostró cuatro diseños, respondió a `/za diseno listar` y recargó mediante `/zonecore reload`. Las 137 pruebas anteriores corresponden al JAR original, no a este artefacto protegido. Falta probar modpack completo, cliente gráfico, multijugador y hosting. Se cargó como archivo CurseForge **9124295**, todavía en análisis/revisión; espera aprobación pública. No instales JAR `-dev` ni de pruebas.

