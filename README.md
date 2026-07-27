<b>Projeto Final Challenge Alura Agente - Tech AI Builder</b>

<b>Descrição do Projeto:</b>

Construção de um agente inteligente do e-commerce BimBam Buy.
Ele será capaz de responder perguntas com base nos documentos em PDF fornecidos.
Informações sobre: Manual de Garantia, Perguntas Frequentes, Politica de Reembolso, Reembolso e Devolução, Programa de afiliados. Caso tenha alguma pergunta que ele não tenha a informação, ele deve dizer que não possue a informação.

<b>Tecnologias e Ferramentas Utilizadas:</b>

1. Linguagem e Ambiente de Execução
Python: Linguagem principal utilizada no script.
Google Colab: Ambiente de desenvolvimento em nuvem onde o script foi rodado, utilizado também para o gerenciamento seguro das chaves de API (ChaveGemini).

2. Frameworks de Inteligência Artificial & LLM
LangChain: Framework para orquestração da solução de IA. Foi utilizado para gerenciar a carga de documentos e integrar com o modelo de linguagem.
LangChain Google GenAI: Integração do LangChain com a API do Google Gemini.
Google Gemini 2.5 Flash: Modelo de Linguagem (LLM) da Google responsável por processar o contexto e gerar as respostas das dúvidas dos clientes.

3. Processamento de Documentos e Dados
PyPDF: Biblioteca para fazer o download e extração textual de arquivos PDF via URL.
GitHub: Hospedagem remota dos arquivos PDF da loja (utilizado como repositório de dados/documentos fonte).

4. Interface de Usuário (UI)
Gradio: Biblioteca para criação rápida de interfaces web interativas de chat e geração do link publicável.

<b>Arquitetura da Solução</b>

A solução segue um padrão de Atendimento Baseado em Contexto , estruturada nas seguintes etapas:


Detalhamento das Camadas da Arquitetura:
1. Camada de Ingestão e Processamento de Dados 
1. Fonte de Dados: O sistema consome 5 arquivos PDF hospedados no GitHub (Guia de Prazos, Manual de Garantia, FAQs, Política de Reembolso e Programa de Afiliados).
2. Extração: O PyPDFLoader faz o fetch das URLs e extrai o conteúdo textual página a página.
3. Agregação de Contexto: Todo o texto extraído é concatenado em uma única variável global na memória (textoDocumentos).

2. Camada do Agente e Lógica de Negócio (LLM )
1. Configuração de Persona & Regras: A função assistenteRespostas cria um System Prompt dinâmico que define:
    * Persona: Atendente da loja BimBam Buy.
    * Base de Conhecimento: Limita o conhecimento estritamente ao texto extraído dos PDFs.
    * Guardrails (Restrições): Instruções explícitas de que o robô não consulta pedidos específicos e deve responder "Não possuo essa informação." caso o assunto não esteja contido nos documentos.
2. Invocação do Modelo: Envia o contexto agrupado junto à pergunta do usuário ao gemini-2.5-flash via llm.invoke().

3. Camada de Apresentação (Interface)
1. Interação com Usuário: O gr.ChatInterface do Gradio captura a mensagem do usuário e envia para a função responder_chat.
2. Exibição: O Gradio renderiza a interface web e retorna a resposta gerada pelo Gemini em tempo real na tela do usuário.

<b> Exemplos de perguntas que o agente consegue responder </b>

O agente consegue responder perguntas como:
Qual a politica de troca?
Como funciona o programa de afiados?
Métodos de pagamentos aceitos?

No geral informações sobre:
Guia de prazo e custos, Perguntas Frequentes, Politica de Reembolso, Garantia e Programa de Afiliados.

O Agente não consegue consultar algum pedido específico, nem abrir chamados. O agente está preparado somente para responder perguntas gerais com base nos documentos fornecidos sem consulta a banco de dados.

<b> Exemplos de respostas geradas pelo agente. </b>

Pergunta:
Quantos dias eu tenho para devolver um produto?

Resposta:
Os prazos para solicitar uma devolução dependem do motivo:
• Arrependimento de compra: Você pode solicitar a devolução dentro de 10 dias corridos após o recebimento do pedido.
• Produto incorreto, faltante ou dano visível: A solicitação deve ser feita em até 48 horas após a entrega.
• Falha de funcionamento: A solicitação deve ser feita dentro do período de garantia aplicável ao produto.

Pergunta: Quais as formas de pagamento do site?

Resposta:
A BimBam Buy pode aceitar as seguintes formas de pagamento, dependendo do país e da configuração operacional:
• Cartão de crédito
• Cartão de débito
• Transferência bancária / PIX
• Pagamento em dinheiro em pontos habilitados (ex: Boleto)
• Carteiras digitais disponíveis por país
• Parcelamento ou financiamento, quando aplicável

Pergunta: Gostaria de saber mais sobre programa de afiliados.

Resposta:
O Programa de Afiliados da BimBam Buy permite que criadores, mídias, comunidades e parceiros comerciais promovam produtos da marca e recebam uma comissão por vendas validamente atribuídas.
Elegibilidade:
Podem se candidatar:
• Criadores de conteúdo
• Sites de cupons
• Mídias digitais
• Comunidades de compras
• Educadores ou avaliadores de produtos o Parceiros de conteúdo com audiência na LATAM

Pergunta: Gostaria de informações sobre troca de produtos.

Resposta:
Olá! Na BimBam Buy, a "troca" é a substituição do produto por outro igual ou equivalente, conforme a disponibilidade.
As trocas podem ser aplicadas nos seguintes casos:
• Erro de despacho: Se você recebeu um produto diferente do que comprou. A solicitação deve ser feita em até 48 horas após a entrega.
• Produto danificado: Se o produto apresentar dano visível ao ser recebido e for registrado dentro de 48 horas após a entrega.
• Falha coberta por garantia: Se o produto apresentar um defeito de fabricação ou mau funcionamento dentro do período de garantia aplicável.
Condições para aceitar uma devolução para troca:
• O produto deve ter comprovante de compra ou número do pedido.
• A solicitação deve ser apresentada dentro do prazo aplicável.
• O produto deve estar completo, com acessórios, manuais e brindes promocionais, se houver.
• Não deve mostrar sinais de uso incompatíveis com a revisão solicitada.
• Deve manter a embalagem original ou proteção equivalente (quando aplicável).
• Não deve ter sido submetido a reparo externo não autorizado.
Se o erro for atribuível à BimBam Buy (como produto incorreto ou defeito de garantia, custo de coleta ou devolução para a troca será assumido pela empresa.

<b> Instruções para executar o projeto </b>
O projeto funciona em uma pagina web ou executado no GoogleColab.


