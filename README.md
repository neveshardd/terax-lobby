# Terax-Lobby

![Java](https://img.shields.io/badge/Language-Java-orange.svg)
![Gradle](https://img.shields.io/badge/Build-Gradle-02303A.svg)
![Minecraft](https://img.shields.io/badge/Platform-Minecraft%20(Spigot)-71C671.svg)
![License](https://img.shields.io/github/license/neveshardd/terax-lobby)

## Sobre o Projeto

**Terax-Lobby** é um plugin abrangente para Minecraft (Spigot/Bukkit), projetado para atuar como **hub central** de uma rede de servidores.  
Seu objetivo é oferecer uma experiência inicial envolvente, personalizável e integrada ao **Kiwizin Core**, permitindo navegação entre servidores, interação com NPCs e diversas funcionalidades próprias de lobbies modernos.

---

## Funcionalidades

- **Menu Interativo de Seleção de Servidor**  
- **NPCs Personalizáveis** (PlayNPC, DeliveryNPC)  
- **Hologramas Dinâmicos**  
- **Hotbar Configurável**  
- **Sistema Avançado de Tags de Jogador**  
- **Suporte a Múltiplos Lobbys**  
- **Comandos Administrativos** (/kl, /lobby)  
- **Integração com Kiwizin Core**  
- **Eventos Abrangentes** (jogador, inventário, entidades, chat)  

---

## Instalação

### Pré-requisitos
- Servidor Minecraft **Spigot/Paper 1.8.8+**  
- **Java 8** ou superior  

### Etapas
1. Baixe o **TeraxLobby.jar** na [página de releases](https://github.com/neveshardd/terax-lobby/releases)  
2. Instale dependências externas (se não incluídas):  
   - [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/)  
   - [Citizens2](https://www.spigotmc.org/resources/citizens.13811/) ou [NPCLib](https://github.com/JitseB/npclib)  
   - [HolographicDisplays](https://dev.bukkit.org/projects/holographic-displays) ou biblioteca similar  
3. Coloque os `.jar` na pasta `plugins/`  
4. Reinicie o servidor  
5. Configure os arquivos em `plugins/TeraxLobby/`  

---

## Compilando do Código Fonte

```bash
git clone https://github.com/neveshardd/terax-lobby.git
cd terax-lobby
./gradlew clean shadowJar
````

O JAR final estará em `build/libs/TeraxLobby.jar`.

---

## Uso

### Comandos Principais

* `/kl help` — Lista de comandos
* `/kl build [on/off]` — Ativar/desativar modo construção
* `/kl npcplay create <nome> <servidor>` — Criar NPC de seleção
* `/kl npcplay remove <id>` — Remover NPC de seleção
* `/kl npcdelivery create <nome>` — Criar NPC de entregas
* `/kl setspawn` — Definir spawn do lobby
* `/kl give <jogador> <id_item>` — Dar item configurado
* `/kl update` — Recarregar configurações

### Experiência do Jogador

* **Seleção de Servidor** via NPCs ou itens da hotbar
* **Hotbar Customizada** com atalhos rápidos
* **Lobby Protegido** (sem PvP, sem quebra de blocos)

---

## Arquivos de Configuração

* `config.yml` — Configurações gerais
* `language.yml` — Mensagens personalizáveis
* `hotbar.yml` — Itens e ações da hotbar
* `entries.yml` — Configurações de NPCs e menus
* `lobbies.yml` — Instâncias de lobby

---

## Stack Tecnológico

* **Linguagem**: Java
* **Build**: Gradle
* **API**: Bukkit/Spigot
* **Framework**: Kiwizin Core
* **Bibliotecas**: ProtocolLib, NPCLib, Citizens2, HologramLibrary

---

## Estrutura do Projeto

```
terax-lobby/
├── gradle/                       # Gradle wrapper
├── src/main/java/dev/slickcollections/kiwizin/lobby/
│   ├── cmd/                      # Comandos (/kl, /lobby)
│   ├── hook/                     # Integrações externas
│   ├── listeners/                # Listeners de eventos
│   ├── lobby/                    # Core do sistema de lobby (NPCs, entradas)
│   ├── menus/                    # Menus GUI
│   └── ...                       
├── src/main/resources/           # plugin.yml, configs YAML
└── build.gradle                  # Script de build
```

---

## Licença

Distribuído sob a **MIT License**. Consulte `LICENSE` para mais detalhes.

---

## Contato

Autor: [@neveshardd](https://github.com/neveshardd)
Repositório: [https://github.com/neveshardd/terax-lobby](https://github.com/neveshardd/terax-lobby)
