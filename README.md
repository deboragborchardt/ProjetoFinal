<b>Projeto Final Challenge Alura Agente - Tech AI Builder</b>

<b>Descrição do Projeto:</b>

Construção de um agente inteligente da loja BimBam Buy.
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

<b> Exemplos de respostas geradas pelo agente. </b>

<b> Instruções para executar o projeto </b>


