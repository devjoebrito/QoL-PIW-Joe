# Atualizações do PIW-QOL — Joe's Version

Este arquivo reúne as notas de cada versão e o procedimento usado para publicar uma atualização do userscript.

As versões seguem o formato `MAJOR.MINOR.PATCH`:

- **MAJOR:** alteração grande ou incompatível;
- **MINOR:** nova função ou revisão importante;
- **PATCH:** correção pequena sem mudança relevante de uso.

## 10.5.0 — 07/10/2026

### Filtros persistentes no mapa de hunts

- A ordenação escolhida, como **Preço: Menor → Maior**, permanece selecionada ao fechar e abrir novamente a tela de hunts.
- Os filtros de tipo, acesso e estado de captura também são lembrados pelo navegador.
- Valores salvos inválidos ou incompatíveis são descartados com segurança e substituídos pelos padrões.

## 10.4.5 — 28/09/2026

### Nome do userscript

- O nome exibido pelo Tampermonkey passa a ser **Poke Idle World - Quality of Life (PIW-QOL) - Joe's Version**.

## 10.4.4 — 28/09/2026

### Instalação pelo Tampermonkey

- O arquivo principal foi renomeado de `.js` para `.user.js`, formato reconhecido automaticamente pelos gerenciadores de userscripts.
- Os botões de instalação agora apontam diretamente para o novo arquivo raw.
- `@updateURL` e `@downloadURL` foram atualizados para o caminho `.user.js`.
- A versão foi incrementada para `10.4.4` para que a correção seja identificada como uma nova atualização.

## 10.4.3 — 28/09/2026

### Créditos do userscript

- O campo `@author` agora apresenta exclusivamente **Desjunior (JulianoCLI)**.
- **JoeBrito** foi movido para o novo campo `@updater`, separando a autoria original da manutenção desta versão.

## 10.4.2 — 28/09/2026

### Auto-reconnect em batalhas lentas

- O tempo sem atividade necessário para considerar uma hunt travada aumentou de 10 para 30 segundos.
- Depois de uma tentativa de reentrada, o script agora aguarda até 30 segundos por uma nova mensagem de progresso; antes, aguardava 8 segundos.
- A mudança reduz falsos positivos quando Pokémon de fases iniciais demoram mais para derrotar o adversário.
- Mensagens, descrições de configuração e documentação foram atualizadas para refletir os novos limites.

## 10.4.1 — 28/09/2026

### Visibilidade por local revisada

- Lojas/Mercado e Depot voltam a ficar ocultos durante hunts.
- Os mesmos botões permanecem visíveis nas cidades, no mapa de Mercado e em qualquer outro local que não seja identificado como hunt.
- A janela do Depot é fechada automaticamente ao entrar em uma hunt e sua abertura direta também é bloqueada nesse contexto.
- O antigo lançador **Mercado Global nas hunts** e sua opção de configuração foram removidos.
- Links nativos de Mercado/Depot encontrados na barra de captura também são ocultados durante a hunt.
- A detecção agora confirma hunts por marcador conhecido ou pela interface de batalha, evitando classificar o mapa de Mercado como hunt.

### Atalho da cidade

- O ícone ilustrado foi substituído pelo emoji **🏠**.
- O botão continua usando o tamanho padrão de 36 × 36 pixels dos demais atalhos.
- O arquivo externo do ícone deixou de ser necessário.

## 10.4.0 — 28/09/2026

### Mercado e Depot fora de Cerulean

- A barra lateral deixa de ocultar Lojas e Depot durante hunts e nos mapas de acesso ao Mercado.
- O Depot portátil deixa de exigir que o HUD identifique uma cidade para abrir.
- O bloqueio preventivo permanece apenas enquanto o local atual ainda não foi identificado.
- A janela do Depot não é mais fechada ao alternar entre uma cidade e uma hunt reconhecida.

### Retorno rápido à cidade

- Adicionado um botão de Cidade visível durante hunts.
- O botão usa o ícone fornecido para esta versão, ajustado ao mesmo espaço de 36 × 36 pixels dos demais atalhos.
- Ao clicar, o script abre o mapa e seleciona Cerulean, reutilizando o fluxo seguro de teleporte já existente.
- O atalho fica oculto quando o jogador já está em uma cidade ou quando o local ainda é desconhecido.

### Pesquisa de itens

- Adicionada pesquisa por nome na aba **Itens** do Depot, filtrando Mochila e Depot simultaneamente.
- Adicionada pesquisa independente na aba **Família: Itens**, filtrando a mochila e o depósito familiar.
- A comparação ignora acentos e diferenças entre letras maiúsculas e minúsculas.
- Itens familiares recebem nome e ícone do catálogo quando a resposta do servidor contém apenas o identificador.
- As pesquisas possuem botão **Limpar** e mantêm o foco durante a digitação.

### Distribuição e documentação

- O userscript foi atualizado para `10.4.0`.
- O novo arquivo `assets/city-return.png` passa a fazer parte da distribuição.
- O `README.md` foi revisado com o comportamento da barra, do Depot e dos novos filtros.

## 10.3.0 — 27/09/2026

### Auto-reconnect revisado

- A reentrada deixou de considerar o simples envio de `enter-hunt` como sucesso.
- O script agora espera até 8 segundos por uma nova mensagem de progresso da hunt.
- Foram adicionadas tentativas progressivas com esperas de 10, 20 e 40 segundos.
- Depois da quarta falha sem confirmação, a página é recarregada.
- Uma resposta tardia da hunt cancela o reload pendente e reinicia o contador de falhas.
- Erros síncronos de envio são tratados sem deixar a rotina presa.

### Conexão e contexto

- O WebSocket ativo é escolhido pelas mensagens reconhecidas do protocolo do jogo.
- O slug da hunt passou de `localStorage` compartilhado para `sessionStorage` isolado por aba.
- O HUD continua tendo prioridade sobre o slug salvo.
- O contexto da hunt é preservado temporariamente se uma queda remover toda a interface.
- Cidades novas podem ser reconhecidas pelos metadados do marcador, sem depender apenas de uma lista fixa de nomes.
- Se o WebSocket permanecer fechado por 45 segundos, a página é recarregada.

### Bosses

- O script continua sem enviar `leave-hunt` durante bosses.
- Uma interface de boss congelada deixa de suspender o watchdog indefinidamente.
- Depois de cinco minutos num contexto comprovadamente preso, o script faz reload sem enviar `leave-hunt`.
- O teto não é aplicado apenas porque o TTL de uma boss longa ainda não expirou; a interface precisa continuar visível ou o socket precisa estar fechado.

### Interface e distribuição

- A descrição da opção Auto-reconnect foi atualizada.
- Desativar o recurso cancela timers e reloads pendentes.
- Foram restaurados `@updateURL` e `@downloadURL`, agora apontando para o repositório da versão Joe.
- Adicionados `@homepageURL` e `@supportURL` para abrir o projeto e suas Issues pelo gerenciador de userscripts.
- Criados `README.md` e `UPDATES.md` específicos desta versão.

## 10.2.2 — versão-base da Joe's Version

### Quests e Tasks

- Adicionado o botão **🗺️ Ir para a hunt** nas tarefas de derrotar ou capturar Pokémon.
- A criatura é validada pelo catálogo antes que o botão seja exibido.

### Barra por local

- A barra passou a distinguir cidade, hunt e local desconhecido.
- Fora da cidade, Lojas e Depot ficam ocultos.
- Durante hunts, a estrela de teleporte para a favorita permanece acessível.
- O Depot rejeita a abertura quando o HUD não identifica uma cidade.

### Hunt Analyzer

- Removido o evento `visibilitychange` sintético que forçava remontagens periódicas da cena.
- O acompanhamento do Analyzer foi limitado a uma execução por segundo.
- Reduzido o consumo de CPU e as sincronizações visuais durante hunts.

### Compatibilidade

- O `@match` passou a aceitar variações e parâmetros depois de `/play`.
