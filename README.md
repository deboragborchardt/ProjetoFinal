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

----

* Instruções para executar o projeto.
* Exemplos de perguntas que o agente consegue responder.
* Exemplos de respostas geradas pelo agente.
