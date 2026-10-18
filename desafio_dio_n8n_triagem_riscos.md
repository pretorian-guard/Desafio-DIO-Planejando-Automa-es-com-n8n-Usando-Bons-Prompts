# Desafio DIO — Planejando Automações com n8n Usando Bons Prompts

**Projeto:** Automação Inteligente de Triagem de Riscos Corporativos  
**Autor:** Aires dos Reis  
**Contexto:** Praetorium Securus — Inteligência Corporativa Estratégica em Segurança  
**Tipo de entrega:** Planejamento de automação por meio de prompt (não representa workflow implementado)

## Passo 1 — Definição da automação

**Tarefa repetitiva:** receber, validar, registrar e encaminhar solicitações de análise de riscos corporativos.

**Público:** equipes de inteligência corporativa, compliance, segurança empresarial e gestão de riscos.

**Resultado esperado:** registrar solicitações válidas em planilha, categorizar os pedidos e enviar confirmações e notificações por e-mail.

## Passo 2 — Contexto e regras

**Ferramentas:** n8n, n8n Form Trigger, Edit Fields, IF, Switch, Google Sheets e Gmail.

**Sequência:** formulário → padronização → validação → verificação de duplicidade → registro → categorização → notificações.

**Regras:** rejeitar campos obrigatórios ausentes e e-mails inválidos; evitar duplicidade; usar dados fictícios; não emitir juízos de culpabilidade; minimizar dados pessoais.

## Passo 3 — Prompt final

```text
Atue como um especialista em n8n, automação de processos, inteligência corporativa, compliance e gestão de riscos.

Crie uma proposta de automação para receber, validar, registrar e encaminhar solicitações de análise de riscos corporativos, reduzindo tarefas repetitivas e melhorando a organização das informações.

Público:
Equipes de inteligência corporativa, compliance, segurança empresarial e gestão de riscos.

Ferramentas envolvidas:
n8n, n8n Form Trigger, Edit Fields, IF, Switch, Google Sheets e Gmail.

Fluxo:
1. Receber uma solicitação por formulário contendo nome, e-mail, empresa, categoria do risco e descrição da ocorrência.
2. Padronizar os dados recebidos, removendo espaços desnecessários e organizando os campos.
3. Validar o preenchimento obrigatório e o formato do e-mail.
4. Encerrar o processamento dos registros inválidos.
5. Consultar a planilha para identificar solicitações duplicadas por identificador único.
6. Registrar solicitações válidas e não duplicadas no Google Sheets, incluindo data, hora e status inicial.
7. Utilizar o nó Switch para categorizar as solicitações em fraude corporativa, segurança da informação, risco reputacional ou outros.
8. Enviar um e-mail de confirmação ao solicitante.
9. Enviar uma notificação à equipe responsável, informando a categoria e o identificador da solicitação.

Regras:
- Não processar solicitações com campos obrigatórios ausentes.
- Rejeitar e-mails com formato inválido.
- Evitar registros duplicados.
- Utilizar dados fictícios nos testes.
- Respeitar a LGPD e o princípio da minimização de dados.
- Não divulgar informações sensíveis em notificações.
- Não classificar pessoas ou empresas como culpadas por meio da automação.
- Considerar a categorização apenas como triagem preliminar, sujeita à análise humana.
- Registrar erros operacionais para posterior verificação.

Resultado esperado:
Um workflow organizado e documentado, capaz de automatizar a triagem inicial de solicitações corporativas, reduzindo atividades manuais e facilitando o acompanhamento pela equipe responsável.

Explique quais nós do n8n devem ser utilizados, como configurá-los e como conectá-los em sequência.
Descreva a lógica de funcionamento, as condições de validação, os possíveis erros e os testes necessários.
Apresente um exemplo de entrada e saída em JSON com dados fictícios.
Por fim, explique como exportar o workflow em formato JSON e documentar o projeto para publicação no GitHub.
Não invente integrações, credenciais ou funcionalidades. Diferencie as configurações obrigatórias das opcionais.
```

## Fluxo conceitual

```text
Form Trigger → Edit Fields → IF (dados válidos?)
                                ├─ Não → Encerrar
                                └─ Sim → Google Sheets (verificar duplicidade)
                                           ├─ Duplicado → Encerrar
                                           └─ Novo → Google Sheets (registrar)
                                                       → Switch (categoria)
                                                       → Gmail (confirmação e aviso)
```

## Observações

Este repositório documenta um exercício de **planejamento por prompt**. Para executar a automação, será necessário implementar o workflow no n8n, configurar as credenciais, definir a chave de deduplicação e realizar testes. Não publique credenciais, dados reais de clientes ou segredos no GitHub.
