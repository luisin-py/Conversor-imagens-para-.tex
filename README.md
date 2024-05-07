# Conversor imagens para .tex


Este script utiliza a API do Google Generative AI para converter imagens em código LaTeX. Ele recebe o caminho de uma imagem como entrada e tenta gerar o código LaTeX correspondente à estrutura visual da imagem.

**Requisitos:**

* Python 3.x
* Biblioteca `google-generativeai` (instale com `pip install google-generativeai`)
* Chave de API do Google Generative AI (configure seguindo as instruções da documentação)

**Como usar:**

1. **Configure sua chave de API:**
    * Substitua `"AIzaSyCCzqq1DrII6NW-1bpyTpF1EJQQ8qf5Zsk"` no script pela sua chave de API do Google Generative AI.
2. **Execute o script:**
    * Abra um terminal e execute o script com o caminho da imagem como argumento:
    ```bash
    python transforme_latex.py /caminho/para/sua/imagem.png
    ```
3. **Obtenha o código LaTeX:**
    * O código LaTeX gerado será impresso no terminal.

**Explicação do código:**

* **`transforme_latex(path_imagem)`:**
    * Função principal que recebe o caminho da imagem e realiza a conversão para LaTeX.
* **Importações:**
    * `pathlib` - Para manipulação de caminhos de arquivos.
    * `hashlib` - Para gerar um hash único para cada arquivo.
    * `google.generativeai` - Para interagir com a API do Google Generative AI.
* **Configuração da API:**
    * `genai.configure(api_key="...")` - Define a chave de API para acesso à API.
* **Configurações de geração:**
    * `generation_config` - Define parâmetros como criatividade, probabilidade de tokens e tamanho máximo da saída.
* **Configurações de segurança:**
    * `safety_settings` - Define filtros para evitar conteúdo impróprio na geração.
* **Inicialização do modelo:**
    * `model = genai.GenerativeModel(...)` - Cria uma instância do modelo generativo com as configurações definidas.
* **`upload_if_needed(pathname)`:**
    * Função auxiliar que verifica se o arquivo já foi carregado na API e, caso contrário, faz o upload.
* **Criação do prompt:**
    * `prompt_parts` - Define o texto de instrução e inclui o arquivo da imagem.
* **Geração do conteúdo:**
    * `response = model.generate_content(prompt_parts)` - Gera o código LaTeX a partir do prompt.
* **Impressão do resultado:**
    * `print(response.text)` - Imprime o código LaTeX gerado.
* **Remoção de arquivos:**
    * `genai.delete_file(...)` - Remove os arquivos carregados após a geração do código.

**Observações:**

* O modelo generativo ainda está em desenvolvimento e a qualidade do código LaTeX gerado pode variar dependendo da complexidade da imagem.
* Ajuste as configurações de geração e segurança conforme necessário para obter melhores resultados. 
* Este script é apenas um exemplo básico e pode ser adaptado para diferentes cenários de uso. 
