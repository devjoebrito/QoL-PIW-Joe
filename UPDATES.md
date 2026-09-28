# Atualizações do PIW-QOL — Joe's Version

Este arquivo reúne as notas de cada versão e o procedimento usado para publicar uma atualização do userscript.

As versões seguem o formato `MAJOR.MINOR.PATCH`:

- **MAJOR:** alteração grande ou incompatível;
- **MINOR:** nova função ou revisão importante;
- **PATCH:** correção pequena sem mudança relevante de uso.

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

## 10.1.1 — base herdada do PIW-QOL

- Auto-reconnect da hunt usando `leave-hunt` e `enter-hunt` no mesmo local.
- Imagens dos Pokémon na lista de venda.
- Compatibilidade da busca de hunts com as abas visuais de regiões do mapa.
- Porcentagem de potencial desativada por padrão.
- Uso dos cadeados nativos do jogo.
- Melhorias de desempenho em rotinas executadas durante hunts.

Consulte também o [projeto original de JulianoCLI](https://github.com/JulianoCLI/PIW-QOL) para o histórico anterior desta base.

## 10.1.0 — cadeados nativos

- Removida a lista paralela de proteção por cadeado.
- O script passou a usar o sistema de cadeados oferecido pelo próprio jogo.

## Como publicar uma nova versão

### 1. Escolha o novo número

Exemplos:

- correção pequena: `10.3.0` → `10.3.1`;
- nova função: `10.3.0` → `10.4.0`;
- mudança incompatível: `10.3.0` → `11.0.0`.

### 2. Atualize os arquivos

1. Altere `@version` no cabeçalho de `Poke Idle World - Quality of Life (PIW-QOL) - Joe's Version.js`.
2. Atualize o badge e a menção da versão mais recente no `README.md`.
3. Adicione a nova versão no topo deste arquivo.
4. Atualize a documentação das funções que mudaram.

O Tampermonkey só oferece a atualização quando o valor de `@version` é maior que o instalado.

### 3. Valide o userscript

No PowerShell, a partir da pasta do repositório:

```powershell
node --check "Poke Idle World - Quality of Life (PIW-QOL) - Joe's Version.js"
git diff --check
```

Depois, teste manualmente no jogo pelo menos:

- carregamento do script;
- abertura do mapa e das configurações;
- teleporte por favorita e por Quest/Task;
- uma compra ou janela de confirmação sem concluir uma operação desnecessária;
- Hunt Analyzer durante uma hunt;
- auto-reconnect com o console aberto;
- proteção durante uma boss, quando houver ambiente seguro para o teste.

### 4. Revise os metadados de atualização

Confirme que estas linhas continuam apontando para o arquivo da branch `main`:

```text
@updateURL
@downloadURL
```

Depois do push, abra o [arquivo raw do userscript](https://raw.githubusercontent.com/devjoebrito/QoL-PIW-Joe/main/Poke%20Idle%20World%20-%20Quality%20of%20Life%20%28PIW-QOL%29%20-%20Joe%27s%20Version.js) e confira se o novo `@version` aparece no cabeçalho.

### 5. Commit, tag e push

Exemplo para a versão `10.3.0`:

```powershell
git add "Poke Idle World - Quality of Life (PIW-QOL) - Joe's Version.js" README.md UPDATES.md
git commit -m "Release 10.3.0"
git tag -a v10.3.0 -m "PIW-QOL Joe's Version 10.3.0"
git push origin main
git push origin v10.3.0
```

O push da branch `main` atualiza o arquivo consultado pelo Tampermonkey. A tag preserva um ponto fixo para a versão publicada.

### 6. Crie a Release no GitHub

Na página do repositório:

1. abra **Releases**;
2. escolha **Draft a new release**;
3. selecione a tag criada;
4. use o título `PIW-QOL Joe's Version X.Y.Z`;
5. copie a entrada correspondente deste arquivo para a descrição;
6. publique a Release.

## Modelo de notas para a próxima versão

Copie este bloco para o topo do arquivo e substitua os campos:

```markdown
## X.Y.Z — DD/MM/AAAA

### Adicionado

- Nova função.

### Alterado

- Comportamento revisado.

### Corrigido

- Problema resolvido.

### Segurança e desempenho

- Proteção ou otimização aplicada.

### Observações de atualização

- Informe se o jogador precisa reabrir uma janela, limpar alguma preferência ou recarregar a página.
```

## Checklist rápido de release

- [ ] `@version` foi incrementado.
- [ ] `README.md` mostra a versão correta.
- [ ] `UPDATES.md` possui as notas da nova versão.
- [ ] `node --check` passou.
- [ ] `git diff --check` passou.
- [ ] As funções alteradas foram testadas no jogo.
- [ ] Os links `@updateURL` e `@downloadURL` continuam válidos.
- [ ] O commit e a tag usam o mesmo número de versão.
- [ ] O arquivo raw exibe a versão publicada.
- [ ] A Release do GitHub foi criada.
