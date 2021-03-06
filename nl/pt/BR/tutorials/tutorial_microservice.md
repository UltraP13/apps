---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Criando um microsserviço
{: #tutorial-microservice}

É possível criar um app por meio de um Iniciador básico de microsserviço. Use esses iniciadores para construir um microsserviço de backend para Node, Java ou Python com uma opção de estruturas da web. É possível ver como instalar as ferramentas necessárias, criar e executar o app localmente e implantá-lo na nuvem.
{: shortdesc}

## Etapa 1. Instale as ferramentas
{: #prereqs-microservice}

* Instale as [ferramentas do desenvolvedor](/docs/cli/index.html#overview).
* O Docker é instalado como parte das ferramentas do desenvolvedor. O Docker deve estar em execução para que os comandos de construção funcionem. Deve-se criar uma conta do Docker, executar o app Docker e conectar-se.
* Se você planeja implementar o seu app no [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), deverá [preparar a sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Etapa 2. Criar um app
{: #create-microservice}

Crie um app no  {{site.data.keyword.cloud}}  {{site.data.keyword.dev_console}}:

1. Na página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}, selecione um Kit do iniciador para sua linguagem. Por exemplo, para um aplicativo Node.js, acesse **Microsserviço Express.js** e clique em **Selecionar kit do iniciador**.
2. Insira o nome de seu app. Para este tutorial, use `MicroserviceProject`.
3. Insira um nome de host exclusivo, por exemplo, `abc-devhost`. Esse nome do host é a rota de seu app, `abc-devhost.cloud.ibm.com`
4. Opcional. Forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources/tagging_resources.html#tag).
5. Selecione a linguagem e a estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
6. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
7. Clique em **Criar**.

## Etapa 3. Incluir recursos (opcional)
{: #resources-microservice}

É possível incluir recursos que aprimoram seu app com o poder cognitivo do Watson, incluir serviços móveis ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na janela de serviço do app, clique em **Incluir recurso**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
4. Clique em **Criar**.

## Etapa 4. Criar uma cadeia de ferramentas do DevOps
{: #toolchain-microservice}

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente de laboratório Git dedicado e a um pipeline de entrega contínua. Eles serão customizados para o ambiente de implementação que você escolher, quer ele seja [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) ou [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Todas as cadeias de ferramentas criadas por meio de um Painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

1. Na página Detalhes do app, clique em **Implementar na nuvem**.
2. Selecione um método de implementação. Configure o método de implementação de acordo com as instruções para o método escolhido:
  * **Implemente no [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Essa opção cria um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativo altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** ou do **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, que é possível usar para criar e gerenciar ambientes isolados para hospedar aplicativos do Cloud Foundry exclusivamente para a sua empresa.
  * **Implemente em um [Servidor virtual](/docs/apps/vsi-deploy.html#vsi-deploy)**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para você.

## Etapa 5. Criar e executar o app localmente
{: #build-run-microservice}

A implementação de seu app na nuvem na última etapa criou uma cadeia de ferramentas. Uma cadeia de ferramentas cria um repositório Git para seu app no qual é possível localizar o código. Siga estas etapas para acessar o repositório. É possível construir o app localmente para teste antes de enviá-lo por push para a nuvem.

1. Na janela de serviço do app, clique em **Fazer download do código** ou **Clonar seu repositório** para trabalhar com seu código localmente.
2. Importe o app para seu ambiente de desenvolvimento integrado.
3. Modifique o código.
4. Configure a [Autenticação Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) incluindo um token de acesso pessoal.
5. Efetue login na interface da linha de comandos do {{site.data.keyword.cloud_notm}}. Se a sua organização usar logins federados, use a opção `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Configure seus destinos de organização e espaço.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtenha as credenciais.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Verifique se o Docker está executando e crie seu app em um contêiner de desenvolvimento local do diretório.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Execute seu app em um contêiner de desenvolvimento local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Abra seu navegador para `http://localhost:3000`. Seu número de porta pode ser diferente, dependendo do tempo de execução escolhido.

## Etapa 6. Implementar seu app
{: #deploy-microservice}

### Implementar usando uma cadeia de ferramentas
{: #deploy-microservice-toolchain}

É possível implementar seu app no {{site.data.keyword.cloud_notm}} de várias maneiras, mas uma cadeia de ferramentas do DevOps é a melhor maneira de implementar apps de produção. Com uma cadeia de ferramentas do DevOps, é possível automatizar facilmente implementações para muitos ambientes e incluir rapidamente serviços de monitoramento, criação de log e alerta para ajudar a gerenciar seu app à medida que ele cresce.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção-implementação se inicia automaticamente com cada mesclagem na ramificação Principal em seu repositório. Todas as cadeias de ferramentas criadas por meio de um painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Na janela Detalhes do app, clique em **Visualizar cadeia de ferramentas**.

2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e o histórico.

### Implementar usando o {{site.data.keyword.dev_cli_short}}
{: #deploy-microservice-cli}

Para implementar seu app para o Cloud Foundry, insira o comando a seguir:

```
ibmcloud dev deploy
```
{: pre}

Para implementar seu app em um cluster do Kubernetes, insira o comando a seguir:

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Etapa 7. Verificar se o app está em execução
{: #verify-microservice}

Após você implementar o seu app, o Delivery Pipeline ou a linha de comandos apontará a você a URL para o seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do aplicativo:

    No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, você pode ver uma linha no arquivo de log que é semelhante a `urls: my-app-devhost.cloud.ibm.com` ou `View the application health at: http://<ipaddress>:<port>/health`.

4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.
