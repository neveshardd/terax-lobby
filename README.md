

Terax Lobby

O projeto terax-lobby é um plugin abrangente para Minecraft/Bukkit/Spigot, projetado para servir como um lobby ou hub central para uma rede de servidores. Seu principal objetivo é proporcionar uma experiência inicial envolvente e altamente personalizável para os jogadores, facilitando a navegação entre diferentes modos de jogo ou instâncias de servidor, além de oferecer diversos elementos interativos dentro do mundo do lobby. Ele se integra profundamente com o framework personalizado Kiwizin, sugerindo que faz parte de um ecossistema maior da organização 'slickcollections'.

Funcionalidades

Menu Interativo de Seleção de Servidor: Troca de servidor fluida através de um menu no jogo totalmente personalizável (MenuLobbies).

NPCs Personalizáveis: Crie e gerencie Personagens Não Jogadores (NPCs) com skins únicas, itens na mão e ações configuráveis (ex.: PlayNPC para seleção de servidores, DeliveryNPC para entrega de itens).

Hologramas Dinâmicos: Exibe textos flutuantes acima de NPCs ou em locais específicos para fornecer informações ou efeitos visuais.

Barra de Atalhos Personalizável: Defina e personalize os itens da hotbar dos jogadores com ações associadas (ex.: abrir menus, conectar a servidores).

Sistema Avançado de Tags de Jogador: Gerencie nome, prefixos e sufixos dos jogadores, possivelmente utilizando o sistema de times do Bukkit.

Configuração Extensiva: Diversas opções para comportamento do plugin, mensagens personalizáveis e elementos do jogo via arquivos YAML.

Suporte a Múltiplos Lobbys: Suporte nativo a múltiplas instâncias de lobby e entradas de servidor, ideal para redes com BungeeCord ou Velocity.

Comandos Administrativos: Gerenciamento fácil dentro do jogo de NPCs, pontos de spawn e configurações do plugin (ex.: /kl build, /kl npcplay, /kl setspawn, /kl give).

Integração com o Kiwizin Core: Utiliza um framework central (Kiwizin Core) para funcionalidade e gerenciamento de dados consistentes na rede.

Tratamento Abrangente de Eventos: Gerencia uma ampla variedade de interações de jogadores, chats, inventários e comportamento de entidades específicas do ambiente de lobby.


Instalação

Para instalar e executar o plugin Terax Lobby em seu servidor Minecraft, siga estes passos:

Pré-requisitos

Um servidor Minecraft em execução (Spigot, Paper, Purpur ou fork compatível) na versão 1.8.8 ou superior (verifique o build.gradle para compatibilidade exata).

Java 8 ou mais recente.


Etapas

1. Baixe o Plugin:

Obtenha o arquivo TeraxLobby.jar mais recente na página de lançamentos (ou compile você mesmo, veja "Compilando a Partir do Código Fonte").



2. Instale os Plugins Externos Necessários (se não incluídos):

Embora muitas dependências possam estar incluídas no JAR principal, alguns plugins essenciais geralmente precisam ser instalados separadamente:

ProtocolLib: Necessário para manipulação avançada de pacotes, usado no sistema de hologramas.

Citizens2 / NPCLib: Essencial para o sistema de NPCs personalizados.

HolographicDisplays (ou biblioteca de hologramas similar): Possivelmente usado para o sistema de hologramas, embora a HologramLibrary possa ser uma abstração interna.


Coloque esses arquivos .jar na pasta plugins/ do seu servidor.



3. Adicione o Terax Lobby:

Arraste e solte o arquivo TeraxLobby.jar na pasta plugins/ do seu servidor.



4. Reinicie o Servidor:

Reinicie seu servidor Minecraft para carregar o plugin e gerar os arquivos de configuração padrão.



5. Configure:

Após o primeiro início, os arquivos de configuração serão gerados em plugins/TeraxLobby/.

Edite os arquivos config.yml, language.yml, hotbar.yml, entries.yml e lobbies.yml para personalizar o plugin conforme as necessidades do seu servidor.




Compilando a Partir do Código Fonte (para Desenvolvedores)

Se quiser compilar o plugin manualmente:

1. Clone o Repositório:

git clone https://github.com/neveshardd/terax-lobby.git
cd terax-lobby


2. Compile com Gradle:

./gradlew clean shadowJar


3. Encontre o JAR Gerado:

O arquivo JAR compilado estará no diretório build/libs/, geralmente com o nome TeraxLobby.jar.




Uso

Após a instalação e reinício do servidor, o plugin Terax Lobby estará ativo.

Comandos Administrativos

O comando principal para administração é /kl (também pode ser usado como /lobby, conforme definido no plugin.yml).

/kl help: Exibe os comandos disponíveis.

/kl build [on/off]: Ativa ou desativa o modo construção para administradores no mundo do lobby.

/kl npcplay create <nome> <chave_servidor>: Cria um novo NPC do tipo "Play" para seleção de servidor.

/kl npcplay remove <id>: Remove um NPC do tipo "Play" existente.

/kl npcdelivery create <nome>: Cria um novo NPC do tipo "Delivery".

/kl npcdelivery remove <id>: Remove um NPC do tipo "Delivery" existente.

/kl setspawn: Define o ponto de spawn principal do lobby.

/kl give <jogador> <id_item>: Dá um item específico a um jogador (normalmente um item personalizado da hotbar).

/kl update: Recarrega as configurações ou atualiza componentes do plugin.


Experiência do Jogador

Seletor de Servidor: Os jogadores podem acessar o seletor de servidor (geralmente via item da hotbar ou comando específico) para navegar entre modos de jogo.

NPCs Interativos: Jogadores podem interagir com PlayNPCs para entrar em servidores específicos ou com DeliveryNPCs para ações especiais.

Hotbar Personalizada: Os jogadores recebem uma hotbar personalizada com itens configurados pelo servidor, oferecendo acesso rápido a menus, warps, entre outros.

Ambiente do Lobby: O plugin gerencia aspectos do mundo do lobby, como bloqueio de interações indesejadas (quebrar blocos, PvP etc.) e tratamento de entradas/saídas de jogadores.


Arquivos de Configuração

config.yml: Configurações principais e gerais do plugin.

language.yml: Mensagens personalizáveis para localização e identidade visual do servidor.

hotbar.yml: Define os itens da hotbar dos jogadores e suas ações.

entries.yml: Configura as entradas de servidor, incluindo hologramas, skins e itens na mão para NPCs ou menus.

lobbies.yml: Define diferentes instâncias de lobby e suas propriedades.


Stack Tecnológico

Linguagem: Java

Ferramenta de Build: Gradle

API do Minecraft: Bukkit/Spigot API

Framework Interno: Kiwizin (framework personalizado da 'slickcollections')

Bibliotecas/APIs Externas:

ProtocolLib (manipulação avançada de pacotes, usada no HologramAdapter)

NPCLib (criação e gerenciamento de NPCs)

HologramLibrary (gerenciamento de hologramas no jogo)



Estrutura do Projeto

O projeto está organizado em diversos pacotes, refletindo um design modular:

terax-lobby/
├── gradle/                  # Arquivos do wrapper do Gradle
├── src/
│   └── main/
│       ├── java/
│       │   └── dev/slickcollections/kiwizin/lobby/
│       │       ├── cmd/             # Registro de comandos personalizados e subcomandos (ex.: /kl build, /kl npcplay)
│       │       ├── hook/            # Integrações com sistemas externos (ProtocolLib, Kiwizin Core, Hotbar)
│       │       ├── listeners/       # Manipuladores de eventos de jogador, entidade e servidor
│       │       ├── lobby/           # Funcionalidades centrais do lobby: NPCs (PlayNPC, DeliveryNPC), entradas de servidor, gerenciamento de lobby
│       │       ├── menus/           # Menus GUI interativos (ex.:

