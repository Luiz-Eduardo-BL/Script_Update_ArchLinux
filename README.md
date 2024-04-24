# Documentação do Script de Atualização ArchLinux

<div align="center">
  
![Alt Text](https://media.giphy.com/media/hkqefnFjn2MWVl6xvq/giphy.gif)

</div>

Este repositório contém um script Bash projetado para automatizar o processo de atualização de um sistema Linux baseado em Arch (como o Arch Linux). O script também oferece a opção de limpar o cache e os pacotes do gerenciador de pacotes Pacman, bem como os pacotes Flatpak.

## Objetivo

O objetivo deste script é simplificar o processo de atualização do sistema, economizando tempo e esforço do usuário. Ele automatiza as seguintes tarefas:

1. Atualiza os pacotes do sistema usando o Pacman.
2. Atualiza os pacotes Flatpak instalados.
3. Oferece a opção de limpar pacotes desnecessários e o cache do Pacman.

## Uso

Para usar este script, siga os passos abaixo:

1. Clone ou baixe o repositório para o seu sistema.
2. Abra um terminal.
3. Navegue até o diretório onde o script `update.sh` está localizado.

Execute o script usando o seguinte comando:

```bash
./update.sh
```

O script irá guiá-lo durante o processo de atualização e limpeza, fornecendo opções ao longo do caminho.

## Adicionando comando personalizado

1. Edição do Arquivo .zshrc
Abra o arquivo `.zshrc` utilizando um editor de texto de sua preferência, como o Nano:
```bash
nano ~/.zshrc
```
2. Adição do Alias Correto
Dentro do arquivo, insira a seguinte linha para criar um alias chamado `update`:
```bash
alias update='/caminho/Update.sh'
```
Este alias permitirá que você execute o script diretamente.
3. Tornar o Script Executável
Conceda permissão de execução ao script com o comando:
```bash
chmod +x /caminho/Update.sh
```
4. Atualização do Terminal
Para que as alterações tenham efeito, atualize o terminal com o comando:
```bash
source ~/.zshrc
```
Ou, se preferir, reinicie o terminal.

Após esses passos, ao digitar `update` no terminal, o script `Update.sh` será executado. Lembre-se de que o uso de `sudo` no alias só é necessário se o script exigir permissões de superusuário para realizar determinadas operações. Caso contrário, inclua `sudo` dentro do próprio script ou modifique o alias para:
```bash
alias update='sudo /caminho/Update.sh'
```

## Detalhes do Script

O script é composto por várias etapas que são executadas sequencialmente:

1. **Atualização do Pacman**: O Pacman é usado para atualizar os pacotes do sistema. Ele executa `sudo pacman -Syyuu`, o que atualiza todos os pacotes do sistema.

2. **Atualização do Flatpak**: O script executa `flatpak update` para atualizar os pacotes Flatpak instalados no sistema.

3. **Limpeza do Pacman**: O script pergunta se você deseja limpar os pacotes desnecessários do Pacman e o cache. Se você concordar, ele executará `sudo pacman -Rs $(pacman -Qtdq)` para remover os pacotes órfãos e `sudo pacman -Sc` para limpar o cache.

4. **Atualizações Concluídas**: No final do processo, o script informa que as atualizações foram concluídas com sucesso.

## Personalização

Você pode personalizar este script de acordo com suas necessidades. Por exemplo, você pode adicionar ou remover comandos para executar tarefas adicionais após a atualização. Certifique-se de entender os comandos que está adicionando ou removendo para evitar problemas.

## Importante

- Este script é destinado a sistemas Arch Linux e pode não ser adequado para outras distribuições.
- Certifique-se de executar o script com privilégios de superusuário (sudo) para realizar atualizações e limpezas que exijam permissões elevadas.
- Use este script com cuidado, pois ele pode afetar o funcionamento do seu sistema se usado incorretamente.

**Lembre-se sempre de fazer backup dos seus dados importantes antes de executar qualquer script de sistema ou atualização.**

Este script é fornecido "no estado em que se encontra", sem garantia de qualquer tipo. O autor não assume qualquer responsabilidade por danos resultantes do uso deste script.
