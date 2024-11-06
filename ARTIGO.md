## Azure OpenAI em VNet: Segurança e Integração de Rede

GPTs são modelos de linguagem poderosos, hospedados por diferentes provedores, como o Microsoft Azure. Apesar de os modelos em si serem os mesmos, existem diversas diferenças entre as ofertas de cada provedor, incluindo:

* Custo
* Funcionalidades
* Tipos e versões de modelos
* Localização geográfica
* Segurança
* Suporte
* Etc.

Em ambientes corporativos, a segurança é um dos aspectos mais importantes a considerar. O Azure OpenAI permite que você utilize recursos de segurança de rede do Azure para consumir o serviço dentro de uma VNet, garantindo que nenhuma informação seja transmitida publicamente.

### Implementação Exemplar

O repositório de amostras do Azure fornece arquivos Bicep para implementar o Azure OpenAI em um ambiente VNet.

**GitHub:** openai-enterprise-iac

As principais funcionalidades utilizadas pelo Bicep incluem:

* VNet
* Integração VNet para Web App
* Ponto de extremidade privado para Azure OpenAI
* Ponto de extremidade privado para Pesquisa Cognitiva
* Zona DNS Privada

Utilizando esses recursos, todo o tráfego de saída do Web App é direcionado para dentro da VNet e todos os nomes são resolvidos para endereços IP privados. OpenAI e Pesquisa Cognitiva desativam o endereço IP público, tornando o endpoint de interface pública indisponível.

### Implantação

O arquivo Bicep implanta os seguintes recursos do Azure:

**Arquitetura**

Para testar, crie um grupo de recursos na região Leste dos EUA.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f .\infra\main.bicep
```

Após executar o comando acima, a implantação será iniciada. Aguarde até que a implantação seja concluída.

**Implantação**

### Teste

Verifique se a implantação foi bem-sucedida.

**Azure OpenAI**

Primeiramente, tente o acesso público. Você poderá criar uma implantação sem problemas, mas ao tentar acessar pelo Playground de Chat no Portal do Azure, receberá o seguinte erro:

**Erro de Chat**

E quanto ao acesso via API Web?

Utilize uma ferramenta avançada do App Service para fazer login em uma sessão Bash. Primeiro, execute um ping no URL do serviço:

**Imagem**

O endereço IP privado atribuído ao Ponto de Extremidade Privado será retornado.

Em seguida, utilize o comando `curl` para enviar uma solicitação ao endpoint.

**Tradução para Português (em formato Markdown):**

## Azure OpenAI em VNet: Segurança e Integração de Rede

Modelos de linguagem GPT são poderosos e estão disponíveis em diversos provedores, como o Microsoft Azure. Apesar de os modelos em si serem os mesmos, cada provedor oferece funcionalidades e características diferentes, como:

* Custo
* Funcionalidades
* Tipos e versões de modelos
* Localização geográfica
* Segurança
* Suporte
* Etc.

Em ambientes corporativos, a segurança é crucial. O Azure OpenAI permite que você utilize recursos de segurança de rede do Azure para consumir o serviço dentro de uma VNet, garantindo que nenhuma informação seja transmitida publicamente.

### Implementação de Exemplo

O repositório de amostras do Azure fornece arquivos Bicep para implementar o Azure OpenAI em um ambiente VNet.

**GitHub:** openai-enterprise-iac

As principais funcionalidades utilizadas pelo Bicep incluem:

* VNet
* Integração VNet para Web App
* Ponto de extremidade privado para Azure OpenAI
* Ponto de extremidade privado para Pesquisa Cognitiva
* Zona DNS Privada

Utilizando esses recursos, todo o tráfego de saída do Web App é direcionado para dentro da VNet e todos os nomes são resolvidos para endereços IP privados. OpenAI e Pesquisa Cognitiva desativam o endereço IP público, tornando o endpoint de interface pública indisponível.

### Implantação

O arquivo Bicep implanta os seguintes recursos do Azure:

**Arquitetura**

Para testar, crie um grupo de recursos na região Leste dos EUA.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f .\infra\main.bicep
```

Após executar o comando acima, a implantação será iniciada. Aguarde até que a implantação seja concluída.

**Implantação**

### Teste

Verifique se a implantação foi bem-sucedida.

**Azure OpenAI**

Primeiramente, tente o acesso público. Você poderá criar uma implantação sem problemas, mas ao tentar acessar pelo Playground de Chat no Portal do Azure, receberá o seguinte erro:

**Erro de Chat**

E quanto ao acesso via API Web?

Utilize uma ferramenta avançada do App Service para fazer login em uma sessão Bash. Primeiro, execute um ping no URL do serviço:

**Imagem**

O endereço IP privado atribuído ao Ponto de Extremidade Privado será retornado.

Em seguida, utilize o comando `curl` para enviar uma solicitação ao endpoint.
