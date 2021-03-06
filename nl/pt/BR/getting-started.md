---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutorial Introdução
{: #getting-started}

O {{site.data.keyword.cfee_full}} (CFEE) é uma plataforma em nuvem para hospedar aplicativos e serviços na nuvem. O {{site.data.keyword.cfee_full_notm}} torna mais fácil escalar apps conforme o consumo cresce, simplificando o tempo de execução, o middleware e a infraestrutura para que você possa se concentrar em desenvolver apps.
{: shortdesc}

Este tutorial de introdução mostra como criar um {{site.data.keyword.cfee_full_notm}}, incluir usuários, criar uma organização e espaços, implementar apps e ligar esses apps aos serviços.

## Entendendo Permissões
{: #permissions}

Políticas de acesso corretas são necessárias antes da criação de instâncias do {{site.data.keyword.cfee_full_notm}}. Para obter mais informações, consulte  [ Permissões ](https://console.bluemix.net/docs/cloud-foundry/permissions.html).

## Etapa 1: Certifique-se de que a conta {{site.data.keyword.Bluemix_notm}} possa criar recursos de infraestrutura
{: #accountprep-environment}

As instâncias do CFEE são implementadas nos nós do trabalhador do Kubernetes por meio do Kubernetes Service. [Prepare sua conta do IBM Cloud](https://console.bluemix.net/docs/cloud-foundry/prepare-account.html)
para assegurar-se de que ela possa criar os recursos de infraestrutura necessários para uma instância do CFEE.

## Etapa 2: Criar sua instância do CFEE
{: #create-environment}

Antes de criar seu CFEE, certifique-se de estar na conta do {{site.data.keyword.Bluemix_notm}} em que
deseja criar o ambiente e ter as políticas de acesso necessárias (etapa 1 acima).

1.  Abra o  {{site.data.keyword.Bluemix_notm}}  [ catálogo ](https://console.bluemix.net/catalog).

2.  Localize o serviço {{site.data.keyword.cfee_full_notm}} no catálogo e clique nele para abrir a página de visão geral para o serviço.  Essa primeira página fornece uma visão geral dos principais recursos do serviço. Clique em **Continue**.

3.  Configure a instância do CFEE a ser criada:
    * Selecione um dos planos disponíveis.
    * Insira um **Nome** para a instância do CFEE.
    * Selecione um **Grupo de recursos** sob o qual o ambiente está agrupado. Somente os grupos de recursos aos quais você tem acesso na conta do IBM Cloud atual serão listados no menu suspenso _Grupos de recursos_, o que significa que você precisa ter permissão para acessar pelo menos um grupo de recursos na conta para poder criar um CFEE.
    * Selecione a **Geografia** e **Localização** em que a instância de serviço deve
ser fornecida. Veja lista de [locais de provisionamento e os data centers disponíveis](https://console.bluemix.net/docs/cloud-foundry/index.html#provisioning-targets){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") por geografia para o CFEE e serviços de apoio. 

4.  Nos campos **Compose for PostgreSQL**, selecione uma das organizações públicas e, em seguida, selecione um dos espaços disponíveis nessa organização. A instância do Compose for PostgreSQL será provisionada no espaço selecionado. O Compose for PostgreSQL é uma dependência necessária do serviço CFEE.

**Nota:** Em _Compose for PostgreSQL_ estão disponíveis para seleção apenas as organizações na localização em que você
pretende fornecer a instância do CFEE (etapa 4 acima) e às quais você tem acesso. Dentro de uma organização específica, somente os espaços para os quais você tem acesso de _desenvolvedor_ estão disponíveis para seleção. 

5. Configure a capacidade do CFEE:
    * Selecione o **Número de células** para o CFEE. 
    * Selecione o **Tamanho do nó*, que determina o tamanho das células do Cloud Foundry (CPU e memória).

6.  Opcionalmente, abra a seção **Infraestrutura** para ver as propriedades do cluster Kubernetes que suporta a instância do CFEE. Observe que o **Número de nós do trabalhador** é igual ao número de células mais 2 (dois dos nós do trabalhador do Kubernetes provisionados suportam o plano de controle do CFEE).
O cluster do Kubernetes no qual o ambiente é implementado aparece no [painel](https://console.bluemix.net/dashboard/apps/) do {{site.data.keyword.Bluemix_notm}}. Para obter mais informações, veja [Documentação do Serviço Kubernetes](https://console.bluemix.net/docs/containers/cs_why.html#cs_ov).

**Nota:** recomendamos que o VLAN Spanning seja ativado se os nós do trabalhador no cluster do Kubernetes forem provisionados em sub-redes diferentes.  Os nós do trabalhador em sub-redes diferentes poderão evitar a conectividade entre eles se o VLAN Spanning estiver desativado.  Veja a documentação do [VLAN Spanning](https://console.bluemix.net/docs/containers/cs_subnets.html#vlan-spanning) para obter mais informações.

7.  O **Resumo da ordem** no lado direito da página reflete o custo da instância do CFEE e os serviços auxiliares, juntamente com o total mensal estimado.

8.  Clique em **Criar**, que abre o painel do ambiente e indica o progresso da criação e o status.

**Nota:** após o início do processo de criação, uma linha da tabela para o CFEE
é mostrada no painel do {{site.data.keyword.Bluemix_notm}}, na _Lista de recursos_ e no
[painel Ambientes do Cloud Foundry](https://console.bluemix.net/dashboard/cloudfoundry?filter=cf_environments).  O status na linha da tabela indica quando a criação está concluída.

O processo automatizado que cria o ambiente implementa a infraestrutura em um cluster do Kubernetes e a configura para torná-la pronta para uso. O processo leva de 90 a 120 minutos.

Depois que o CFEE for criado, você receberá múltiplos e-mails confirmando o fornecimento do CFEE e os serviços de
suporte, bem como e-mails notificando o status dos pedidos correspondentes.

Ao criar uma instância do CFEE, há três instâncias de serviço de suporte adicionais criadas na mesma conta do IBM Cloud. Essas instâncias de serviço de suporte são nomeadas após o nome da instância do CFEE. Portanto, a criação de um CFEE
resulta em um total de quatro instâncias de serviço criadas na conta do IBM Cloud:
* Instância do CFEE ("_cfeename_").
* Cluster Kubernetes ("_cfeename_-cluster"). O cluster fornece a infraestrutura na qual a instância do
CFEE é fornecida.
* Instância do Cloud Object Storage ("_cfeename_-cos"). A instância é usada para armazenar dados gerados
durante a criação de contêineres de aplicativo do CFEE (por exemplo, pacotes de aplicativos transferidos por upload,
buildpacks e executáveis compilados).
* Instância do Compose for PosgreSQL ("_cfeename_-postgres"). A instância é usada para armazenar dados do
Cloud Foundry na instância do CFEE (por exemplo, a implementação do aplicativo de auditoria e os eventos de início e
de encerramento e, ao mesmo tempo, manter os registros de participação do usuário, organizações, espaços, aplicativos e
conexões de serviço do CFEE). 

## Etapa 3: Criar organizações e espaços
{: #create-orgsandspaces}

Depois de criar o {{site.data.keyword.cfee_full_notm}}, consulte [Criando organizações e espaços](https://console.bluemix.net/docs/cloud-foundry/orgs-spaces.html) para obter informações sobre como estruturar o ambiente criando organizações e espaços. Os apps em um {{site.data.keyword.cfee_full_notm}} têm o escopo definido em espaços específicos. Por sua vez, existe um espaço dentro de uma organização específica. Os membros de uma organização compartilham um plano de cota, apps, instâncias de serviços e domínios customizados.

**Nota:** a página _Organizações do Cloud Foundry_ disponível no menu **_Gerenciar > Conta > Organizações do Cloud Foundry_** localizado no cabeçalho superior do IBM Cloud é destinada exclusivamente para organizações públicas do IBM Cloud, **não para organizações do CFEE**. As organizações do CFEE são gerenciadas na página _Organizações_ de uma instância do CFEE.  Abra a interface com o usuário do CFEE e clique na página **_Organizações_** para criar e gerenciar organizações para esse CFEE.

## Etapa 4: Incluir usuários em organizações e espaços
{: #add-users}

[Inclua usuários](https://console.bluemix.net/docs/cloud-foundry/add-users.html) nessas organizações e espaços sob designações de função específicas que controlam seu nível de acesso.  Para que os usuários possam ser incluídos como membros de organizações e espaços em um CFEE, esses usuários devem ter acesso anterior à instância do CFEE. Consulte  [ Permissões ](https://console.bluemix.net/docs/cloud-foundry/permissions.html).

## Etapa 5: Implementar e visualizar aplicativos
{: #deploy-apps}

Quando você estiver pronto, será possível [implementar o app](https://console.bluemix.net/docs/cloud-foundry/deploy-apps.html) com a interface da linha de comandos do {{site.data.keyword.Bluemix_notm}}.  Visualize a lista de aplicativos implementados na interface com o usuário, seja no contexto de um espaço específico do CFEE ou globalmente em todas as instâncias do CFEE.  Também é possível iniciar, parar ou excluir aplicativos dessas visualizações.

## Etapa 6: Criar ou incluir instâncias de serviço do IBM Cloud em espaços do CFEE
{: #service-instances}

[Criar serviços](https://console.bluemix.net/docs/cloud-foundry/add-serv-inst.html#workingwith-services#creating-services-inspace) ou [Incluir serviços existentes](https://console.bluemix.net/docs/cloud-foundry/add-serv-inst.html#workingwith-services#adding-services-inspace) disponíveis na conta do IBM Cloud.  Depois que uma instância de serviço estiver disponível em um espaço do CFEE, será possível ligá-lo aos aplicativos CFEE implementados nesse espaço.

## Etapa 7: Ligar aplicativos às instâncias de serviço
{: #bind-apps}

[Ligue seu app](https://console.bluemix.net/docs/cloud-foundry/binding.html) a um alias da instância de serviço para usar as funções do serviço.

No [painel do Cloud Foundry](https://console.bluemix.net/dashboard/cloudfoundry/overview){: new_window} ![Ícone delink externo](../icons/launch-glyph.svg "Ícone de link externo"), é possível ver uma visualização consolidada de todos os aplicativos e serviços, tanto

*públicos* quanto *corporativos*. Uma vez no painel do Cloud Foundry, clique em *Públicos* na área de janela de navegação à esquerda para ver os aplicativos públicos e os serviços disponíveis na conta do IBM Cloud.  Clique
em *Corporativo* para ver todos os ambientes do CFEE, os aplicativos implementados nos espaços do
CFEE e os serviços disponíveis para os espaços do CFEE.
{:tip}

## Etapa 8: Ativar a auditoria e a persistência de criação de log (opcional)
{: #enable-auditingandlogging}

Ative o ambiente para os
[eventos de
auditoria](https://console.bluemix.net/docs/cloud-foundry/auditing-logging.html#auditing-logging#auditing) e
[persistência de criação de log](https://console.bluemix.net/docs/cloud-foundry/auditing-logging.html#logging).

## Etapa 9: Criar e proteger domínios do Cloud Foundry (opcional)
{: #create-domains}

Crie [domínios](https://console.bluemix.net/docs/cloud-foundry/domains.html#domains) para todos os
aplicativos no CFEE (domínios compartilhados) ou para uma organização específica (domínios privados) e proteja-os com
os certificados SSL.


## Etapa 10: Instale o Stratos Console para gerenciar aplicativos (opcional)
{: #install-stratos}

O Stratos Console é uma ferramenta baseada na web de software livre para trabalhar com o Cloud Foundry. O aplicativo Stratos Console pode ser instalado opcionalmente e usado em um ambiente específico do CFEE para gerenciar suas organizações, espaços e aplicativos.

Os usuários com as funções de administrador ou editor do IBM Cloud na instância do CFEE podem instalar o aplicativo Stratos Console nessa instância do CFEE.

Para instalar o aplicativo Stratos Console:

1. Abra a instância do CFEE na qual você deseja instalar o Stratos Console.
2. Clique em **Instalar o Stratos Console** na página de visão geral. O botão fica visível somente para usuários com permissões de administrador ou de editor para essa instância do CFEE.
3. No diálogo Instalar o Stratos Console, selecione uma opção de instalação. É possível instalar o aplicativo Stratos em
uma célula do Cloud Foundry ou no cluster Kubernetes. Selecione uma versão do Stratos Console e o número de instâncias do aplicativo a ser instalado. Se
você instalar o aplicativo Stratos Console em uma célula do Cloud Foundry, será solicitado que você forneça a organização
e o espaço nos quais o aplicativo será implementado.
4. Clique em **Instalar**.

O aplicativo leva cerca de 5 minutos para ser instalado. Quando a instalação estiver concluída, um botão **Stratos Console** aparecerá no lugar do botão _ Instalar o Stratos Console_ na página de visão geral. O botão _Stratos Console_ ativa o console e está disponível para todos os usuários com acesso à instância do CFEE. As designações de associação de organização e de espaço podem limitar o que um usuário pode ver e gerenciar no Stratos Console.

Para iniciar o console Stratos:

1. Abra a instância do CFEE na qual o Stratos Console foi instalado.
2. Clique em **Stratos Console** na página de visão geral.
3. O Stratos Console é aberto em uma guia do navegador separada. Quando você abre o console pela primeira vez, é solicitado que aceite dois avisos consecutivos por causa de certificados autoassinados.
4. Clique em  ** Login **  para abrir o console. Nenhuma credencial é necessária, uma vez que o aplicativo usa suas credenciais do {{site.data.keyword.Bluemix_notm}}.


## Recursos adicionais
{: #additional-resources}

É possível executar algumas tarefas de administração em um CFEE usando os comandos da CLI `ibmcloud CFEE`. Os comandos permitem obter as informações sobre uma instância do CFEE, bem como gerenciar suas organizações e espaços. Consulte [Referência de comando do CFEE da CLI do IBM Cloud](https://console.cloud.ibm.com/docs/cli/reference/ibmcloud/cli_cfee.html#ibmcloud_commands_cfee){: new_window}
![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

É possível localizar vídeos com discussões e demonstrações aprofundadas sobre vários tópicos do CFEE na [Lista de execução de vídeos do CFEE](https://ibm.biz/CFEE-Playlist){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

As informações sobre a API do CFEE estão na [documentação da API
do CFEE](https://console.bluemix.net/apidocs/cfaas){: new_window} ![Ícone
de link externo](../icons/launch-glyph.svg "Ícone de link externo").
