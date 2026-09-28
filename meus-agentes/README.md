# meus-agentes

Marketplace de plugins para o Claude Code.

## Plugin: planejamento-estrategico

Conduz o dono da empresa por um planejamento estratégico em 8 etapas. Cada etapa é uma conversa guiada, com perguntas simples, e grava o resultado em `planejamento/` para a etapa seguinte usar.

| Etapa | Comando | Arquivo gerado |
|---|---|---|
| 1. Cultura | `/planejamento-estrategico:1-cultura` | `01-cultura.md` |
| 2. Vitórias e Desafios | `/planejamento-estrategico:2-vitorias-e-desafios` | `02-vitorias-e-desafios.md` |
| 3. SWOT (com estratégias cruzadas TOWS) | `/planejamento-estrategico:3-swot` | `03-swot.md` |
| 4. Curva de Valor | `/planejamento-estrategico:4-curva-de-valor` | `04-curva-de-valor.md` e `.html` (gráfico) |
| 5. 5 Forças de Porter | `/planejamento-estrategico:5-cinco-forcas-de-porter` | `05-cinco-forcas-de-porter.md` |
| 6. Metas, OKRs e KPIs | `/planejamento-estrategico:6-metas-okrs-kpis` | `06-metas-okrs-kpis.md` |
| 7. Plano de Ação (5W2H, riscos e primeiros 30 dias) | `/planejamento-estrategico:7-plano-de-acao` | `07-plano-de-acao.md` e `07-relatorio-plano-de-acao.md` |
| 8. Relatório Final | `/planejamento-estrategico:8-relatorio-final` | `08-relatorio-final.md` e `.html` |

Todos os arquivos ficam na pasta `planejamento/` do diretório onde o Claude Code foi aberto. Ao terminar cada etapa, o Claude orienta o usuário a chamar a próxima. Como cada etapa grava e lê arquivos, dá para interromper e retomar em outra sessão sem perder nada.

A etapa 8 confere a coerência do plano (por exemplo, se cada meta tem ação, responsável e prazo, e se os riscos cobrem as ameaças do SWOT) e consolida tudo em um relatório final, com uma versão em HTML que o navegador salva como PDF.

### Instalação

```
/plugin marketplace add SEU-USUARIO/meus-agentes
/plugin install planejamento-estrategico@meus-agentes
```

Para testar localmente, antes de publicar:

```
/plugin marketplace add ./meus-agentes
/plugin install planejamento-estrategico@meus-agentes
```

### Como usar

Abra o Claude Code na pasta onde os arquivos do planejamento devem ficar e digite `/planejamento-estrategico:1-cultura`. Também dá para dizer "quero começar o planejamento estratégico da minha empresa".

### Personalizar

Cada etapa é um arquivo `plugins/planejamento-estrategico/skills/<etapa>/SKILL.md`. Edite o texto para mudar perguntas, tom ou o formato da entrega. O bloco "Arquivo de saída" de cada etapa define o padrão que as etapas seguintes leem; se mudar um, ajuste os outros. Se adicionar ou remover uma etapa, renumere os comandos e os arquivos.

### Publicar e atualizar

1. Troque `Seu Nome` nos dois manifestos.
2. Suba o repositório no GitHub.
3. Ao mudar qualquer etapa, aumente `version` em `plugin.json` (senão quem já instalou continua com a cópia antiga), faça push e peça aos usuários `/plugin marketplace update`.

### Sobre a confidencialidade

Cada etapa traz a instrução de não revelar o conteúdo dela. Isso não impede que quem instalar o plugin abra os arquivos. Para manter as instruções privadas, deixe o repositório privado e restrito às pessoas autorizadas.
