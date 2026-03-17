# Validação Automatizada de CNPJs e Dados Cadastrais (Excel + API)

Este projeto é uma recriação simplificada de uma automação utilizada em ambiente logístico para validação de dados cadastrais de empresas.

## 📌 Contexto

Durante minha atuação na área de logística, era comum receber grades de envio contendo diversos CNPJs e dados cadastrais de clientes.  
Antes do processamento dos pedidos, era necessário realizar um double check das informações para garantir que os dados estavam corretos no sistema e alinhados com os dados oficiais da empresa.

Esse processo envolvia a validação de:

- CNPJ
- Razão social
- Endereço
- Cidade e estado

Inicialmente essa conferência era feita de forma manual, o que demandava tempo e aumentava o risco de erros operacionais.

Para otimizar esse processo, desenvolvi uma planilha de validação automatizada em Excel, capaz de comparar dados de diferentes fontes e indicar rapidamente a ação necessária para cada registro.

## ⚙️ Como a solução funciona

A planilha realiza a validação cruzando três fontes de dados:

1. Planilha enviada pelo cliente  
2. Dados oficiais do CNPJ consultados via API pública  
3. Dados cadastrados no sistema interno  

Com base nessas informações, a planilha executa comparações automáticas e retorna um status operacional, indicando a ação recomendada.

### Exemplo de retornos

| Resultado | Ação recomendada |
|---|---|
| CNPJ ok | Continuar envio |
| Acionar Cliente | Solicitar correção cadastral |
| Atualizar Sistema | Corrigir cadastro interno |
| Validar Manualmente | Conferir divergência |

## 🔗 Consulta de dados via API

A validação utiliza uma API de consulta de CNPJ para obter dados oficiais das empresas, como razão social e endereço cadastral.

No ambiente operacional original, era utilizada uma API paga, que permitia consultas em massa, possibilitando a validação simultânea de grandes volumes de CNPJs.

Para este projeto de demonstração, foi utilizada uma API gratuita, que possui limitação no número de consultas por requisição.  
Por esse motivo, os exemplos incluídos na planilha utilizam apenas um pequeno conjunto de CNPJs.

## 🧠 Funcionamento no ambiente real

No ambiente operacional da empresa, o processo funcionava de forma um pouco diferente desta versão demonstrativa.

Os dados do sistema interno não eram inseridos manualmente na planilha.  
O relatório era exportado diretamente do sistema e salvo em uma pasta padronizada, sendo então referenciado pela planilha através de vínculo externo.

Dessa forma, bastava substituir o arquivo do relatório na pasta correta para que a planilha atualizasse automaticamente as comparações.

Nesta versão do projeto, os dados do sistema foram incluídos diretamente na planilha apenas para facilitar a visualização e compreensão da lógica de validação.

## 🔎 Lógica de validação

Na prática operacional, as validações eram realizadas comparando cada campo separadamente, como por exemplo:

- razão social
- rua
- bairro
- cidade
- estado

Isso permitia identificar exatamente onde ocorria a divergência cadastral.

Para simplificar a estrutura desta versão demonstrativa, algumas comparações foram consolidadas em validações mais diretas, mantendo a lógica principal do processo.

## 🛠 Tecnologias utilizadas

- Microsoft Excel
- Funções avançadas do Excel
- PROCX
- SES
- SEERRO
- Formatação condicional
- API de consulta de CNPJ

## 📊 Estrutura da planilha

A planilha é composta pelas seguintes abas principais:

- **Instruções**  
  Contém orientações de uso da ferramenta.

- **Planilha de Envio Cliente**  
  Contém os dados recebidos para processamento.

- **Consulta API CNPJ**  
  Realiza a consulta dos dados oficiais da empresa.

- **Sistema Empresa**  
  Simula os dados cadastrados no sistema interno.

- **Validação de CNPJs**  
  Realiza as comparações e apresenta o resultado final da validação.

## 📁 Estrutura do projeto

```text
cnpj-data-validation-automation/
├── README.md
├── cnpj_validation_tool.xlsx
└── validacao.png
