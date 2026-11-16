[README_n8n.md](https://github.com/user-attachments/files/34939013/README_n8n.md)
# Automações com n8n

Coleção de workflows desenvolvidos com **n8n**, JavaScript, integrações HTTP, Telegram e agentes de IA. O objetivo deste repositório é documentar soluções práticas para monitoramento de informações, notificações e rotinas personalizadas.

> **Estado dos projetos:** os workflows abaixo foram desenvolvidos ou exportados para compartilhamento. A presença de um JSON no repositório não significa que a versão pública esteja ativa ou pronta para uso sem configuração.

## Workflows

| Projeto | Objetivo | Principais tecnologias | Situação |
| --- | --- | --- | --- |
| 🎟️ **Monitor de ingressos** | Detectar indícios de anúncios e vendas para River Plate x Inter Miami | n8n, JavaScript, HTTP Request, HTML, Telegram | Workflow desenvolvido; detecção sujeita a validação |
| 🏋️ **Bot de treinos** | Montar e enviar treinos personalizados conforme a rotina semanal | n8n, Data Table, agente de IA, Telegram | Workflow desenvolvido; requer configuração na importação |
| 🎓 **Monitor de pós-graduações em TI** | Acompanhar oportunidades de formação e enviar notificações | n8n, pesquisa web, modelo de IA, filtros, Telegram | Workflow desenvolvido; execução não verificada nesta versão pública |

## 1. 🎟️ Monitor de ingressos — River Plate x Inter Miami

Monitora páginas públicas relacionadas ao confronto **River Plate x Inter Miami**, previsto para **19 de janeiro de 2027**, buscando menções ao jogo e expressões relacionadas à venda de ingressos.

**Fluxo:** `Schedule Trigger → Code (URLs) → HTTP Request → HTML → Code (análise) → IF → Telegram`

- Consulta programada a cada **30 minutos**.
- Fontes: páginas de notícias e ingressos do River Plate e do Inter Miami.
- Extração de texto e links de páginas HTML.
- Filtragem com JavaScript e envio de alertas pelo Telegram.
- **Limitação:** palavras-chave encontradas na página não comprovam que a venda esteja aberta. Notícias antigas, menus e outros jogos podem causar falsos positivos. A confirmação deve ser feita no canal oficial.
- Alertas repetidos são possíveis; o fluxo não possui deduplicação.

## 2. 🏋️ Bot de treinos

Workflow para gerar uma rotina diária de exercícios, usando dados estruturados e um agente de IA.

- Acionamento diário, configurado originalmente para **10h no fuso America/Maceio**.
- Consulta a uma tabela de exercícios e consolida os dados para o agente.
- Agente **Personal** com orientações para musculação, corrida e progressão.
- Produção de treino com exercícios, séries, repetições, descanso e caminhada.
- Envio do treino pelo Telegram.

**Atenção:** na versão pública, identificadores do agente, tabela e Telegram devem ser substituídos pelos recursos da própria instância.

## 3. 🎓 Monitor de pós-graduações em TI

Workflow de acompanhamento de oportunidades de especialização e capacitação em tecnologia, com foco em áreas como dados e inteligência artificial.

- Pesquisa periódica de oportunidades de pós-graduação, incluindo modalidades EAD.
- Análise e filtragem dos resultados com modelo de IA.
- Estruturação das informações encontradas.
- Notificação pelo Telegram.

**Atenção:** a versão compartilhável precisa ser configurada com as credenciais e serviços correspondentes. A execução desta exportação não foi validada aqui.

## Projetos em planejamento

Estes projetos fazem parte do roadmap e **não devem ser confundidos com workflows concluídos**:

- ✈️ **Monitor de passagens aéreas:** comparar tarifas para Buenos Aires em datas flexíveis e avisar sobre preços-alvo.
- 🎬 **Produção automatizada de vídeos curtos:** pesquisa, roteiro, narração, edição com FFmpeg e etapas de publicação.
- 🧹 **Limpeza de metadados de vídeos:** processamento com FFmpeg integrado ao n8n.
- 🤖 **Agentes de atendimento para pequenas empresas:** atendimento, qualificação de leads e automações comerciais.

## Tecnologias

`n8n` · `JavaScript` · `HTTP Request` · `HTML` · `Telegram Bot API` · `Data Table` · `Agentes de IA` · `Docker` · `Coolify`

Alguns workflows utilizam apenas parte dessa stack.

## Como importar um workflow

1. Instale ou acesse sua instância do **n8n**.
2. Abra o editor e selecione a opção de **importar workflow de arquivo**.
3. Escolha o JSON do projeto desejado.
4. Configure suas próprias credenciais, IDs de tabelas, agentes e demais parâmetros necessários.
5. Execute os nós individualmente, valide os resultados e só então ative o agendamento.

## Segurança e privacidade

- Nunca publique tokens, chaves de API, senhas ou IDs pessoais de conversas.
- Utilize **credenciais do n8n** para segredos; não os inclua em nós Code nem em URLs versionadas.
- Revise os JSONs exportados, prints, logs e histórico de commits antes de publicar.
- As versões compartilháveis devem usar placeholders em campos específicos de cada usuário.
- Não considere um resultado de busca ou uma palavra-chave como confirmação de disponibilidade de ingressos ou passagens.

## Estrutura sugerida

```text
n8n-automations/
├── README.md
├── ingressos/
│   └── workflow.json
├── bot-treino/
│   └── workflow.json
└── pos-graduacoes-ti/
    └── workflow.json
```

> Os caminhos acima são uma **estrutura sugerida**. Inclua cada arquivo `workflow.json` apenas depois de revisar e sanitizar sua exportação.

## Licença

Defina uma licença antes de permitir reutilização e redistribuição. Nenhuma licença específica é presumida neste README.
