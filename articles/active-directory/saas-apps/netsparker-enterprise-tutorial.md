---
title: 'Tutorial: Integração do SSO (logon único) do Azure Active Directory ao Netsparker Enterprise | Microsoft Docs'
description: Saiba como configurar o logon único entre o Azure Active Directory e o Netsparker Enterprise.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: CelesteDG
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 11/13/2020
ms.author: jeedes
ms.openlocfilehash: ccf96ddc2d223b4643c280acaa1fd7b6e734ad85
ms.sourcegitcommit: d22a86a1329be8fd1913ce4d1bfbd2a125b2bcae
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96181927"
---
# <a name="tutorial-azure-active-directory-single-sign-on-sso-integration-with-netsparker-enterprise"></a>Tutorial: Integração do SSO (logon único) do Azure Active Directory ao Netsparker Enterprise

Neste tutorial, você aprenderá a integrar o Netsparker Enterprise ao Azure AD (Azure Active Directory). Quando você integra o Netsparker Enterprise ao Azure AD, você pode:

* Controlar, no Azure AD, quem tem acesso ao Netsparker Enterprise.
* Permitir que os usuários sejam conectados automaticamente ao Netsparker Enterprise com as contas do Azure AD deles.
* Gerenciar suas contas em um local central: o portal do Azure.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você precisará dos seguintes itens:

* Uma assinatura do Azure AD. Caso você não tenha uma assinatura, obtenha uma [conta gratuita](https://azure.microsoft.com/free/).
* Assinatura do Netsparker Enterprise habilitada para SSO (logon único).

## <a name="scenario-description"></a>Descrição do cenário

Neste tutorial, você configurará e testará o SSO do Azure AD em um ambiente de teste.

* O Netsparker Enterprise é compatível com o SSO iniciado por **SP e IdP**
* O Netsparker Enterprise é compatível com o provisionamento de usuário **just-in-time**

> [!NOTE]
> O identificador desse aplicativo é um valor de cadeia de caracteres fixo; portanto apenas uma instância pode ser configurada em um locatário.


## <a name="adding-netsparker-enterprise-from-the-gallery"></a>Como adicionar o Netsparker Enterprise da galeria

Para configurar a integração do Netsparker Enterprise com o Azure AD, será necessário adicionar o Netsparker Enterprise da galeria à sua lista de aplicativos SaaS gerenciados.

1. Entre no portal do Azure usando uma conta corporativa ou de estudante ou uma conta pessoal da Microsoft.
1. No painel de navegação esquerdo, escolha o serviço **Azure Active Directory**.
1. Navegue até **Aplicativos Empresariais** e, em seguida, escolha **Todos os Aplicativos**.
1. Para adicionar um novo aplicativo, escolha **Novo aplicativo**.
1. Na seção **Adicionar da galeria**, digite **Netsparker Enterprise** na caixa de pesquisa.
1. Selecione **Netsparker Enterprise** no painel de resultados e, em seguida, adicione o aplicativo. Aguarde alguns segundos enquanto o aplicativo é adicionado ao seu locatário.


## <a name="configure-and-test-azure-ad-sso-for-netsparker-enterprise"></a>Configurar e testar o SSO do Azure AD para o Netsparker Enterprise

Configure e teste o SSO do Azure AD com o Netsparker Enterprise usando um usuário de teste chamado **B.Simon**. Para que o SSO funcione, é necessário estabelecer uma relação de vínculo entre um usuário do Azure AD e o usuário relacionado do Netsparker Enterprise.

Para configurar e testar o SSO do Azure AD com o Netsparker Enterprise, execute as seguintes etapas:

1. **[Configurar o SSO do Azure AD](#configure-azure-ad-sso)** – para permitir que os usuários usem esse recurso.
    1. **[Criar um usuário de teste do Azure AD](#create-an-azure-ad-test-user)** para testar o logon único do Azure AD com B.Fernandes.
    1. **[Atribuir o usuário de teste do Azure AD](#assign-the-azure-ad-test-user)** – para permitir que B.Fernandes use o logon único do Azure AD.
1. **[Configurar o SSO do Netsparker Enterprise](#configure-netsparker-enterprise-sso)** : para definir as configurações de logon único no lado do aplicativo.
    1. **[Criar um usuário de teste do Netsparker Enterprise](#create-netsparker-enterprise-test-user)** : para ter um equivalente de B.Fernandes no Netsparker Enterprise vinculado à representação de usuário do Azure AD.
1. **[Testar o SSO](#test-sso)** – para verificar se a configuração funciona.

## <a name="configure-azure-ad-sso"></a>Configurar o SSO do Azure AD

Siga estas etapas para habilitar o SSO do Azure AD no portal do Azure.

1. No portal do Azure, na página de integração de aplicativos do **Netsparker Enterprise**, localize a seção **Gerenciar** e selecione **logon único**.
1. Na página **Selecionar um método de logon único**, escolha **SAML**.
1. Na página **Configurar o logon único com o SAML**, clique no ícone de edição/caneta da **Configuração Básica do SAML** para editar as configurações.

   ![Editar a Configuração Básica de SAML](common/edit-urls.png)

1. Na seção **Configuração Básica do SAML**, caso deseje configurar o aplicativo no modo iniciado por **IDP**, digite os valores dos seguintes campos:

    Na caixa de texto **URL de Resposta**, digite uma URL usando o seguinte padrão: `https://www.netsparkercloud.com/account/assertionconsumerservice/?spId=<SPID>`

1. Clique em **Definir URLs adicionais** e execute o passo seguinte se quiser configurar a aplicação no modo **SP** iniciado:

    Na caixa de texto **URL de Logon**, digite a URL: `https://www.netsparkercloud.com/account/ssosignin/`

    > [!NOTE]
    > O valor de URL de Resposta não é real. Atualize o valor com a URL de Resposta real. Entre em contato com a [equipe de suporte ao Cliente do Netsparker Enterprise](mailto:support@netsparker.com) para obter o valor. Você também pode consultar os padrões exibidos na seção **Configuração Básica de SAML** no portal do Azure. 

1. Na página **Configurar o logon único com o SAML**, na seção **Certificado de Autenticação SAML**, localize **Certificado (Base64)** e selecione **Baixar** para baixar o certificado e salvá-lo no computador.

    ![O link de download do Certificado](common/certificatebase64.png)

1. Na seção **Configurar o Netsparker Enterprise**, copie as URLs apropriadas de acordo com suas necessidades.

    ![Copiar URLs de configuração](common/copy-configuration-urls.png)
### <a name="create-an-azure-ad-test-user"></a>Criar um usuário de teste do Azure AD

Nesta seção, você criará um usuário de teste no portal do Azure chamado B.Fernandes.

1. No painel esquerdo do portal do Azure, escolha **Azure Active Directory**, **Usuários** e, em seguida, **Todos os usuários**.
1. Selecione **Novo usuário** na parte superior da tela.
1. Nas propriedades do **Usuário**, siga estas etapas:
   1. No campo **Nome**, insira `B.Simon`.  
   1. No campo **Nome de usuário**, insira username@companydomain.extension. Por exemplo, `B.Simon@contoso.com`.
   1. Marque a caixa de seleção **Mostrar senha** e, em seguida, anote o valor exibido na caixa **Senha**.
   1. Clique em **Criar**.

### <a name="assign-the-azure-ad-test-user"></a>Atribuir o usuário de teste do Azure AD

Nesta seção, você permitirá que B.Fernandes use o logon único do Azure permitindo a ela acesso ao Netsparker Enterprise.

1. No portal do Azure, selecione **Aplicativos empresariais** e, em seguida, selecione **Todos os aplicativos**.
1. Na lista de aplicativos, selecione **Netsparker Enterprise**.
1. Na página de visão geral do aplicativo, localize a seção **Gerenciar** e escolha **Usuários e grupos**.
1. Escolha **Adicionar usuário** e, em seguida, **Usuários e grupos** na caixa de diálogo **Adicionar Atribuição**.
1. Na caixa de diálogo **Usuários e grupos**, selecione **B.Fernandes** na lista Usuários e clique no botão **Selecionar** na parte inferior da tela.
1. Se você estiver esperando que uma função seja atribuída aos usuários, escolha-a na lista suspensa **Selecionar uma função**. Se nenhuma função tiver sido configurada para esse aplicativo, você verá a função "Acesso Padrão" selecionada.
1. Na caixa de diálogo **Adicionar atribuição**, clique no botão **Atribuir**.

## <a name="configure-netsparker-enterprise-sso"></a>Configurar o SSO do Netsparker Enterprise

1.  Faça logon no Netsparker Enterprise como administrador.

1. Acesse as **Configurações > Logon Único**.

1. Na janela **Logon Único**, selecione a guia **Azure Active Directory**. 

1. Execute as etapas abaixo na página a seguir.

    ![Guia Azure Active Directory](./media/netsparker-enterprise-tutorial/configure-sso.png)

    a. Copie o valor **Identificador**, cole esse valor na caixa de texto **Identificador** na seção **Configuração Básica de SAML** no portal do Azure.

    b. Copie o valor **URL do Serviço SAML 2.0**, cole este valor na caixa de texto **URL de Resposta** na seção **Configuração Básica do SAML** no portal do Azure.

    c. Cole o valor **Identificador**, que você copiou do portal do Azure para o campo **Identificador IdP**.

    e. Cole o valor **URL de Resposta**, que você copiou do portal do Azure para o campo **Ponto de Extremidade do SAML 2.0**.

    f. Abra o **Certificado (Base64)** baixado do portal do Azure para o Bloco de Notas e cole o conteúdo na caixa de texto **Certificado x.509**.

    g. Marque **Habilitar Provisionamento Automático** e **Exigir que as declarações SAML sejam criptografadas** conforme necessário.

    h. Clique em **Salvar Alterações**.

### <a name="create-netsparker-enterprise-test-user"></a>Criar um usuário de teste do Netsparker Enterprise

Nesta seção, uma usuária chamada Brenda Fernandes será criada no Netsparker Enterprise. O Netsparker Enterprise é compatível com o provisionamento de usuário just-in-time, que é habilitado por padrão. Não há itens de ação para você nesta seção. Se um usuário ainda não existir no Netsparker Enterprise, um será criado após a autenticação.

## <a name="test-sso"></a>Testar o SSO 

Nesta seção, você testará a configuração de logon único do Azure AD com as opções a seguir. 

#### <a name="sp-initiated"></a>Iniciado por SP:

* Clique em **Testar este aplicativo** no portal do Azure. Isso redirecionará você à URL de Logon do Netsparker Enterprise, na qual você poderá iniciar o fluxo de logon.  

* Acesse diretamente a URL de Logon do Netsparker Enterprise e inicie o fluxo de logon de lá.

#### <a name="idp-initiated"></a>Iniciado por IdP:

* Clique em **Testar este aplicativo** no portal do Azure e você será conectado automaticamente ao Netsparker Enterprise para o qual configurou o SSO 

Use também o Painel de Acesso da Microsoft para testar o aplicativo em qualquer modo. Quando você clicar no bloco do Netsparker Enterprise no Painel de Acesso, se ele estiver configurado no modo SP, você será redirecionado à página de logon do aplicativo para iniciar o fluxo de logon e, se ele estiver configurado no modo IdP, você será conectado automaticamente ao Netsparker Enterprise para o qual configurou o SSO. Para saber mais sobre o Painel de Acesso, veja [Introdução ao Painel de Acesso](../user-help/my-apps-portal-end-user-access.md).


## <a name="next-steps"></a>Próximas etapas

Depois de configurar o Netsparker Enterprise, você poderá impor o controle de sessão, que fornece proteção contra a exfiltração e infiltração dos dados confidenciais da sua organização em tempo real. O controle da sessão é estendido do acesso condicional. [Saiba como impor o controle de sessão com o Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-any-app).