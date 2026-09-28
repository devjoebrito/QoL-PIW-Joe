# 🎮 Poke Idle World - Quality of Life (PIW-QOL) — Joe's Version

Userscript gratuito para [Pokémon Idle World](https://poke.idleworld.online/play) com atalhos de navegação, mapa aprimorado, lojas portáteis, melhorias no Hunt Analyzer e recuperação automática de hunts.

[![Versão](https://img.shields.io/badge/vers%C3%A3o-10.4.5-blue?style=for-the-badge)](UPDATES.md)
[![Instalar](https://img.shields.io/badge/instalar-userscript-brightgreen?style=for-the-badge)](https://raw.githubusercontent.com/devjoebrito/QoL-PIW-Joe/main/Poke%20Idle%20World%20-%20Quality%20of%20Life%20%28PIW-QOL%29%20-%20Joe%27s%20Version.user.js)
[![Atualizações](https://img.shields.io/badge/notas-UPDATES.md-orange?style=for-the-badge)](UPDATES.md)

> Este é um projeto da comunidade e não é uma ferramenta oficial dos desenvolvedores do Pokémon Idle World.

## O que o script faz?

O PIW-QOL melhora a interface do jogo e concentra funções que normalmente exigiriam várias janelas ou deslocamentos. Entre os principais recursos estão:

- mapa simplificado com busca, filtros, favoritos e ordenação;
- teleporte para uma hunt favorita, para a última hunt ou diretamente pelas Quests/Tasks;
- lojas, Mercado Global, vendas e Depot em painéis integrados;
- melhorias na Loja do Mark, inventário, Pokédex e listas de Pokémon;
- comparação e histórico de hunts no Hunt Analyzer;
- estimativa opcional de potencial dos Pokémon;
- auto-reconnect com confirmação do servidor, backoff e proteção para bosses;
- configurações persistidas localmente no navegador.

A versão **10.4.5** usa o nome oficial **Poke Idle World - Quality of Life (PIW-QOL) - Joe's Version** no Tampermonkey, além de manter a instalação direta por `.user.js` e as melhorias recentes. Consulte o [histórico de atualizações](UPDATES.md).

> O script não joga sozinho. Compras, vendas, teletransportes e movimentações de inventário continuam dependendo das ações do jogador. O auto-reconnect apenas tenta restaurar a hunt que já estava ativa.

## Instalação

### 1. Instale um gerenciador de userscripts

Escolha apenas um:

| Navegador | Extensão recomendada |
|---|---|
| Chrome, Brave ou Arc | [Tampermonkey para Chrome](https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) |
| Microsoft Edge | [Tampermonkey para Edge](https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd) |
| Firefox ou Zen | [Tampermonkey para Firefox](https://addons.mozilla.org/pt-BR/firefox/addon/tampermonkey/) |

### 2. Instale o PIW-QOL

1. Abra o link **[Instalar PIW-QOL — Joe's Version](https://raw.githubusercontent.com/devjoebrito/QoL-PIW-Joe/main/Poke%20Idle%20World%20-%20Quality%20of%20Life%20%28PIW-QOL%29%20-%20Joe%27s%20Version.user.js)**.
2. O Tampermonkey mostrará o código e os dados do userscript.
3. Clique em **Instalar**.
4. Abra ou atualize `https://poke.idleworld.online/play`.

Se tudo estiver correto, os novos controles aparecerão na interface do jogo.

## Barra de atalhos por local

A versão Joe adapta os botões ao local atual para evitar operações incompatíveis.

### Na cidade

- **★ ou ↺ — Teleporte rápido:** usa a hunt favorita principal ou a última hunt, conforme a configuração escolhida.
- **🏪 — Lojas:** abre o Mercado Global, a Loja de Poké Bolas ou a janela de vendas.
- **📦 — Depot:** abre o painel de itens, Pokémon e, quando disponível, o depósito da família.

### Durante uma hunt

- **★ — Hunt favorita:** continua disponível para trocar rapidamente de hunt;
- **🏠 — Voltar para Cerulean:** abre o mapa e seleciona diretamente a cidade principal;
- os botões de **Lojas/Mercado** e **Depot** ficam ocultos;
- clicar com o botão direito na estrela permite trocar a favorita principal quando houver mais de uma.

Em cidades, no mapa de Mercado e nos demais locais que não sejam hunts, os botões de Lojas/Mercado e Depot permanecem visíveis. O botão 🏠 aparece somente durante hunts.

## Mapa e hunts

### Mapa simplificado

O mapa pode ser apresentado como uma lista organizada. Cada hunt pode exibir:

- nome, nível e acesso permitido ou bloqueado;
- Pokémon encontrado e seus tipos;
- experiência e valor de venda;
- efetividade do Pokémon ativo;
- drops da hunt;
- indicador da hunt atual;
- estado de captura no Pokédex;
- estrela de favorito.

A lista oferece busca por nome de Pokémon ou drop, filtros de tipo, acesso, vantagem, favoritos e capturados, além de ordenação por preço, efetividade e experiência.

### Capturados e não capturados

Os botões **✓ Capturados** e **✗ Não Capturados** restringem as hunts de acordo com o Pokédex. O filtro pode ser combinado com tipo, acesso, favoritos e busca.

### Favoritos

Clique na estrela de uma hunt para salvá-la. Se existirem várias favoritas, o primeiro uso do teleporte solicitará uma favorita principal. A seleção permanece salva no navegador.

### Visualização de drops

- **Ícone (?):** mostra os drops pelo ícone da hunt.
- **Hover:** mostra os drops ao passar o cursor pela hunt.
- **Oculto:** remove a prévia da lista.

### Verificar melhor hunt

O botão abre o [PIW Tools](https://www.piwtools.com.br/) e preenche os dados necessários do Pokémon principal, como nível, atributos, clã e objetivo de rota. O cálculo da melhor hunt é realizado pelo PIW Tools; cookies, senha e tokens não são enviados.

## Quests e Tasks

Tarefas de derrotar ou capturar um Pokémon recebem o botão **🗺️ Ir para a hunt** quando a criatura pode ser identificada no catálogo do jogo.

Ao clicar, o script localiza o marcador correspondente e usa o mesmo fluxo seguro de teleporte do mapa. Tarefas sem uma hunt conhecida não recebem o botão.

## Loja de Poké Bolas

A loja portátil mostra dinheiro atual, preço, estoque e valor total antes da confirmação. Os atalhos permitem comprar:

- `+1`;
- `+10`;
- `+100`;
- `+1.000`;
- `+10.000`.

Idle Ball, Master Ball e produtos que não podem ser comprados normalmente não são exibidos.

## Venda de itens e Pokémon

### Itens

A janela informa nome, quantidade, valor unitário e total selecionado. Itens protegidos por cadeado ou incluídos na lista de confirmação não entram silenciosamente em uma venda em massa.

### Pokémon

A lista pode mostrar imagem, IV, qualidade, potencial estimado e preço. Ela oferece filtros de nome, Shiny/normal, IV e qualidade. Ao mudar os filtros, Pokémon ocultados são desmarcados para reduzir o risco de venda acidental.

A proteção de raridade pode impedir que Pokémon Lendários, Míticos e Divinos sejam selecionados em massa.

## Loja do Mark

As melhorias da loja normal do Mark incluem:

- quantidade atual em estoque;
- compras de `1`, `10`, `100`, `1.000` e `10.000`;
- custo calculado antes da compra;
- seletor múltiplo de qualidades;
- proteções e confirmações de venda;
- atualização de quantidades sem reconstruir continuamente a janela.

## Mercado Global

O painel possui abas de itens e Pokémon. Conforme a aba, é possível filtrar ou ordenar por:

- nome e categoria;
- tipo do Pokémon;
- qualidade e IV;
- preço;
- Dólar ou Diamantes;
- anúncios de oferta sem preço definido.

Os anúncios são carregados ao abrir a janela ou clicar em **Atualizar**. O nome do vendedor é omitido da lista simplificada.

## Depot

O Depot fica disponível pela barra nas cidades, no mapa de Mercado e nos demais locais que não sejam hunts. Durante uma hunt, o botão fica oculto e a abertura é bloqueada preventivamente.

### Itens

- mostra Mochila e Depot lado a lado;
- pesquisa itens por nome nos dois lados ao mesmo tempo, ignorando diferenças de acentuação e maiúsculas/minúsculas;
- permite guardar ou retirar quantidades;
- usa os ícones oficiais do jogo;
- informa quantidades e espaços ocupados.

### Pokémon

- mostra Equipe e Box;
- permite mover Pokémon entre os dois lados;
- oferece busca e filtros mínimos/máximos de IV e qualidade.

### Família

Quando a conta pertence a uma família, aparecem as abas **Família: Itens** e **Família: Pokémon**. A aba de itens possui sua própria pesquisa por nome, aplicada simultaneamente à mochila e ao depósito familiar. O script respeita o limite diário e o estado de congelamento informado pelo jogo.

## Inventário

O inventário não fecha ao clicar fora, pode ser redimensionado e reorganiza as colunas mantendo os slots com tamanho fixo. Use o botão `X` para fechá-lo.

## Hunt Analyzer

O script acrescenta:

- **Reduzir/Expandir**;
- exibição opcional de **Drops**;
- botão **Comparar**;
- horário e tempo desde a última captura;
- quantidade de Poké Bolas usadas;
- histórico das 20 sessões válidas mais recentes.

O comparador apresenta até 10 sessões recentes e pode comparar saldo, saldo/hora, experiência, experiência/hora, derrotas/hora, duração e total derrotado.

Na versão Joe, o acompanhamento do Analyzer é limitado a uma atualização por segundo. O antigo `visibilitychange` sintético, que podia forçar a remontagem repetida da cena, foi removido.

### Qualidade e potencial

Quando ativado, o potencial é uma estimativa do script:

- 75% do peso vem da qualidade;
- 25% vem do IV total;
- o IV é normalizado entre 0 e 192;
- o teto de qualidade é ×1.8 para capturas selvagens comuns e ×4.0 para Shiny ou breeding.

Essa porcentagem não é um valor oficial do jogo e, por isso, vem **desativada por padrão**.

## Auto-reconnect da hunt

O auto-reconnect vem **desativado**. Ative em **Configurações → Script Mods → Hunts → Auto-reconnect da hunt**.

### Detecção

O script acompanha mensagens de progresso da hunt no WebSocket e mudanças relevantes na barra de captura. Após 30 segundos sem atividade, a hunt é considerada travada. Esse intervalo maior evita que Pokémon de fases iniciais, que podem demorar para derrotar um adversário, provoquem uma reconexão indevida.

### Reentrada confirmada

1. O local atual do HUD é convertido para o slug oficial pelos marcadores do mapa.
2. O slug de fallback fica no `sessionStorage`, isolado por aba.
3. O script envia `leave-hunt`.
4. Depois de 500 ms, envia `enter-hunt` para o mesmo slug.
5. A reentrada só é considerada concluída quando uma nova mensagem de progresso chega pelo WebSocket, dentro de 30 segundos.

Se o HUD indicar uma cidade ou outro marcador não reconhecido como hunt, nenhum comando de reentrada é enviado.

### Falhas e backoff

Se o WebSocket continuar aberto, mas o servidor não confirmar a reentrada:

- depois da primeira falha, aguarda 10 segundos;
- depois da segunda, aguarda 20 segundos;
- depois da terceira, aguarda 40 segundos;
- depois da quarta falha, recarrega a página.

Se a hunt responder antes do reload, o reload pendente é cancelado e o contador de falhas volta a zero.

### WebSocket fechado

Quando o próprio WebSocket fecha, o script não tenta enviar `leave-hunt` ou `enter-hunt`. Ele espera 45 segundos pela reconexão nativa do jogo e, se ela não ocorrer, recarrega a página.

O contexto anterior da hunt é mantido temporariamente mesmo se a queda remover o HUD, permitindo que o reload ainda aconteça em abas deixadas em segundo plano.

### Proteção de bosses

Durante uma boss, o script nunca envia `leave-hunt`, pois isso poderia abandonar a luta e consumir o token. Mensagens e componentes específicos de boss suspendem o watchdog.

Se a interface de boss permanecer congelada por cinco minutos, ou o socket continuar indisponível nesse contexto, o script usa um reload seguro sem enviar `leave-hunt`. Anúncios, rankings, mercado e itens com "Boss" no nome não são tratados como uma luta.

### Diagnóstico

Os eventos são registrados no console com o prefixo:

```text
[PIW-QOL] Auto-reconnect:
```

Para abrir o console, normalmente use `F12` e selecione a aba **Console**.

## Pokédex

A Pokédex recebe filtros de **Todos**, **Capturados** e **Não capturados**, além da ordenação por menor valor.

Com o **Pokédex Fast Travel** ativado, clicar em um Pokémon procura sua hunt e inicia o teleporte.

## Configurações do script

Abra a engrenagem do jogo e selecione **Script Mods**.

| Categoria | Opção | Função |
|---|---|---|
| 🗺️ Mapa e navegação | Mapa simplificado | Alterna entre a lista do script e o mapa original |
| 🗺️ Mapa e navegação | Visualização de drops | Escolhe Ícone, Hover ou Oculto |
| 🗺️ Mapa e navegação | Ação do teleporte | Escolhe Favorita, Última hunt ou Desativado na cidade |
| 🗺️ Mapa e navegação | Pokédex Fast Travel | Permite teleportar pela Pokédex |
| ⚔️ Hunts | Auto-reconnect da hunt | Recupera uma hunt que parou de responder |
| ⚔️ Hunts | Comparação de hunts | Exibe o comparador do Hunt Analyzer |
| ⚔️ Hunts | Compras em grande quantidade | Controla botões adicionais de compra |
| ⚔️ Hunts | Venda nas hunts | Controla os recursos portáteis de venda |
| 🏪 Loja do Mark | Compras rápidas | Mostra os atalhos de quantidade |
| 🏪 Loja do Mark | Seletor de qualidades | Agrupa qualidades num seletor múltiplo |
| 🏪 Loja do Mark | Melhorias da loja | Liga ou desliga as modificações da loja |
| 🐾 Pokémon | Porcentagem de potencial | Mostra a estimativa de qualidade + IV |
| 🛡️ Proteções e vendas | Proteção de raridade | Evita seleção em massa de raridades altas |
| 🛡️ Proteções e vendas | Confirmação de venda | Escolhe itens que exigem confirmação |
| 🪟 Interface | Scrollbars minimalistas | Substitui as barras brancas |
| 🪟 Interface | Exibir chat | Mostra ou oculta o chat |
| 🔤 Fontes | Fonte do jogo | Seleciona uma fonte ou arquivo próprio |
| 🔤 Fontes | Fonte unificada | Aplica a fonte aos controles e janelas |

As preferências ficam salvas no navegador. O auto-reconnect e a porcentagem de potencial exigem ativação manual.

## Atualizações

O userscript possui `@updateURL` e `@downloadURL` apontando para este repositório. O Tampermonkey pode verificar novas versões comparando o campo `@version`.

Para verificar manualmente:

1. abra o painel do Tampermonkey;
2. localize **Poke Idle World - Quality of Life (PIW-QOL) - Joe's Version**;
3. escolha **Verificar atualizações**;
4. recarregue a página do jogo.

Também é possível abrir novamente o [link de instalação](https://raw.githubusercontent.com/devjoebrito/QoL-PIW-Joe/main/Poke%20Idle%20World%20-%20Quality%20of%20Life%20%28PIW-QOL%29%20-%20Joe%27s%20Version.user.js).

As notas de cada versão e o procedimento de publicação estão em [UPDATES.md](UPDATES.md).

## Solução de problemas

### Os botões não apareceram

1. Confirme que o Tampermonkey e o userscript estão ativados.
2. Use `Ctrl + F5` na página do jogo.
3. Verifique se a URL começa com `https://poke.idleworld.online/play`.

### Lojas ou Depot não aparecem durante a hunt

Na versão 10.4.5, isso é intencional. Durante hunts, Lojas/Mercado e Depot ficam ocultos; use o botão 🏠 para voltar a Cerulean. Esses serviços continuam visíveis no mapa de Mercado e nos demais locais que não sejam hunts.

### O auto-reconnect não foi executado

- confirme que ele foi ativado em **Script Mods**;
- durante bosses, o recurso entra em espera;
- se o local não puder ser identificado como hunt, nenhum comando é enviado;
- procure mensagens com `[PIW-QOL] Auto-reconnect:` no console.

### O Mercado Global está vazio

Limpe os filtros, marque as moedas desejadas, permita ofertas e clique em **Atualizar**.

### Um item ou Pokémon não foi selecionado por "Marcar tudo"

O objeto pode estar protegido por cadeado, raridade, filtro ou pela lista de confirmação.

### O teleporte rápido não funciona

- marque ao menos uma hunt como favorita;
- no modo Última hunt, visite uma hunt pela lista primeiro;
- se os marcadores do mapa não carregarem, atualize a página.

## Privacidade e segurança

- Configurações, favoritas e histórico ficam no navegador.
- O slug usado pelo auto-reconnect fica no `sessionStorage` da aba.
- O script não envia preferências para serviços de terceiros.
- Lojas, mercado, teleporte e Depot reutilizam a sessão aberta do jogo.
- O PIW Tools recebe somente os atributos necessários para a consulta solicitada.
- Nunca compartilhe cookies, tokens ou arquivos do perfil do navegador.
- Revise quantidades, valores e seleções antes de confirmar compras ou vendas.

## Créditos

- Projeto original e README-base: **Desjunior / [JulianoCLI](https://github.com/JulianoCLI/PIW-QOL)**.
- Atualizador desta versão: **[JoeBrito](https://github.com/devjoebrito)**.
- Cálculo do recurso **Verificar melhor hunt**: **[PIW Tools](https://www.piwtools.com.br/)**.
- Desenvolvimento realizado para a comunidade do Pokémon Idle World.

Sugestões e problemas podem ser registrados nas [Issues deste repositório](https://github.com/devjoebrito/QoL-PIW-Joe/issues).

---

**[Instalar o script](https://raw.githubusercontent.com/devjoebrito/QoL-PIW-Joe/main/Poke%20Idle%20World%20-%20Quality%20of%20Life%20%28PIW-QOL%29%20-%20Joe%27s%20Version.user.js)** · **[Ver atualizações](UPDATES.md)** · **[Abrir o jogo](https://poke.idleworld.online/play)**
