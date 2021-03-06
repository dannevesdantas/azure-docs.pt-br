---
title: Como usar o Twilio para voz e SMS (Java) | Microsoft Docs
description: Saiba como fazer uma chamada telefônica e enviar uma mensagem SMS com o serviço de API do Twilio no Azure. Exemplos de códigos escritos em Java.
services: ''
documentationcenter: java
author: georgewallace
ms.assetid: f3508965-5527-4255-9d51-5d5f926f4d43
ms.service: multiple
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: Java
ms.topic: article
ms.date: 11/25/2014
ms.author: gwallace
ms.custom: devx-track-java
ms.openlocfilehash: e7ff925534a9cab6523097f84a8ae199e9cb83eb
ms.sourcegitcommit: 5a999764e98bd71653ad12918c09def7ecd92cf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2021
ms.locfileid: "100548719"
---
# <a name="how-to-use-twilio-for-voice-and-sms-capabilities-in-java"></a>Como usar a Twilio para obter recursos de voz e SMS no Java
Este guia demonstra como executar tarefas comuns de programação com o serviço de API do Twilio no Azure. Os cenários abrangidos incluem fazer uma chamada telefônica e enviar uma mensagem serviço de mensagem curta (SMS). Para obter mais informações sobre o Twilio e o uso de voz e SMS em seus aplicativos, consulte a seção [Próximas etapas](#NextSteps) .

## <a name="what-is-twilio"></a><a id="WhatIs"></a>O que é Twilio?
Twilio é uma API do serviço Web de telefonia que permite usar os idiomas e as habilidades existentes de Web para criar aplicativos de voz e SMS. O Twilio é um serviço de terceiro (não é um recurso do Azure e não é um produto da Microsoft).

**Twilio Voice** permite que seus aplicativos façam e recebam chamadas telefônicas. **Twilio SMS** permite que seus aplicativos façam e recebam mensagens SMS. **Twilio Cliente** permite que seus aplicativos habilitem a comunicação de voz usando as conexões existentes com a Internet, incluindo conexões para celular.

## <a name="twilio-pricing-and-special-offers"></a><a id="Pricing"></a>Preços e ofertas especiais da Twilio
A informações sobre os preços do Twilio estão disponíveis em [Preços do Twilio][twilio_pricing]. Os clientes do Azure recebem uma [oferta especial][special_offer]: um crédito de 1.000 mensagens de texto gratuitas ou 1.000 minutos de entrada. Para se inscrever nesta oferta ou obter mais informações, visite [https://ahoy.twilio.com/azure][special_offer] .

## <a name="concepts"></a><a id="Concepts"></a>Conceitos
A API do Twilio é uma API RESTful que fornece os recursos de voz e SMS para aplicativos. As bibliotecas de cliente estão disponíveis em vários idiomas. Para obter uma lista, consulte [Bibliotecas de API do Twilio][twilio_libraries].

Principais aspectos da API do Twilio são Twilio verbos e linguagem de marcação de Twilio (TwiML).

### <a name="twilio-verbs"></a><a id="Verbs"></a>Verbos twilio
A API utiliza verbos twilio; por exemplo, o verbo **&lt; digamos &gt;** instrui o twilio a forma audível a entregar uma mensagem em uma chamada.

A seguir está uma lista de verbos do Twilio.

* **&lt; Discar &gt;**: conecta o chamador a outro telefone.
* **&lt; Coletar &gt;**: coleta dígitos numéricos inseridos no teclado do telefone.
* **&lt; Desligamento &gt;**: encerra uma chamada.
* **&lt; Play &gt;**: reproduz um arquivo de áudio.
* **&lt; Fila &gt;**: Adicione o a uma fila de chamadores.
* **&lt; Pausa &gt;**: aguarda silenciosamente por um número especificado de segundos.
* **&lt; Registro &gt;**: registra a voz do chamador e retorna uma URL de um arquivo que contém a gravação.
* **&lt; Redirect &gt;**: transfere o controle de uma chamada ou SMS para o TwiML em uma URL diferente.
* **&lt; Rejeitar &gt;**: rejeita uma chamada recebida para seu número de twilio sem cobrar você.
* **&lt; Digamos &gt;**: converte o texto em fala que é feito em uma chamada.
* **&lt; SMS &gt;**: envia uma mensagem SMS.

### <a name="twiml"></a><a id="TwiML"></a>TwiML
TwiML é um conjunto de instruções em XML com base nos verbos do Twilio que informam o Twilio como processar uma chamada ou SMS.

Por exemplo, o TwiML a seguir converteria o texto **Olá, mundo!** em fala.

```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <Response>
       <Say>Hello World!</Say>
    </Response>
```

Quando o aplicativo chama a API Twilio, um dos parâmetros a API é a URL que retorna a resposta TwiML. Para fins de desenvolvimento, você pode usar URLs fornecidos Twilio para fornecer as respostas de TwiML usadas por seus aplicativos. Você também pode hospedar seus próprio URLs para produzir as respostas TwiML e outra opção é usar o **TwiMLResponse** objeto.

Para obter mais informações sobre os verbos do Twilio, seus atributos e o TwiML, consulte [TwiML][twiml]. Para obter mais informações sobre a API do Twilio, consulte [API do Twilio][twilio_api].

## <a name="create-a-twilio-account"></a><a id="CreateAccount"></a>Criar uma conta do twilio
Quando estiver pronto para obter uma conta do Twilio, inscreva-se em [Experimentar o Twilio][try_twilio]. Você pode começar com uma conta gratuita e atualizá-la depois.

Quando você se inscrever para uma conta de Twilio, você receberá uma ID de conta e um token de autenticação. Eles serão necessários para fazer chamadas de API do Twilio. Para evitar o acesso não autorizado em sua conta, mantenha o token da autenticação seguro. A ID de sua conta e o token de autenticação estão visíveis no [Console do Twilio][twilio_console], nos campos rotulados **ACCOUNT SID** e **AUTH TOKEN**, respectivamente.

## <a name="create-a-java-application"></a><a id="create_app"></a>Criar um aplicativo Java
1. Obtenha o JAR do Twilio e adicione-o ao seu caminho de compilação do Java e seu assembly de implantação WAR. Em [https://github.com/twilio/twilio-java][twilio_java] , você pode baixar as fontes do GitHub e criar seu próprio jar ou baixar um jar predefinido (com ou sem dependências).
2. Certifique-se de que o armazenamento de chaves **cacerts** do JDK contém o certificado de Autoridade de Certificação Segura Equifax com impressão digital MD5 67:CB:9D:C0:13:24:8A:82:9B:B2:17:1E:D1:1B:EC:D4 (o número de série é 35:DE:F4:CF e a impressão digital SHA1 é D2:32:09:AD:23:D3:14:23:21:74:E4:0D:7F:9D:62:13:97:86:63:3A). Esse é o certificado de autoridade de certificação (CA) para o [https://api.twilio.com][twilio_api_service] serviço, que é chamado quando você usa APIs twilio.

Instruções detalhadas para usar a biblioteca de cliente do Twilio para Java estão disponíveis em [Como fazer uma chamada telefônica usando Twilio em um aplicativo Java no Azure][howto_phonecall_java].

## <a name="configure-your-application-to-use-twilio-libraries"></a><a id="configure_app"></a>Configurar seu aplicativo para usar bibliotecas Twilio
Dentro de seu código, você pode adicionar instruções de **importação** na parte superior dos seus arquivos de origem dos pacotes ou classes do Twilio que você deseja usar em seu aplicativo.

Para arquivos de origem Java:

```java
    import com.twilio.*;
    import com.twilio.rest.api.*;
    import com.twilio.type.*;
    import com.twilio.twiml.*;
```

Para arquivos de origem Java Server Page (JSP):

```java
    import="com.twilio.*"
    import="com.twilio.rest.api.*"
    import="com.twilio.type.*"
    import="com.twilio.twiml.*"
```

Dependendo dos pacotes ou classes do Twilio que você deseja usar, as instruções de **importação** podem ser diferentes.

## <a name="how-to-make-an-outgoing-call"></a><a id="howto_make_call"></a>Como fazer uma chamada externa
Abaixo é mostrado como fazer uma chamada externa usando a classe **Call**. Esse código também usa um site fornecido pelo Twilio para retornar a resposta TwiML (Linguagem de Marcação do Twilio). Substitua os valores dos números **de telefone de** e **para** e verifique se você verificou o número **de** telefone de sua conta do twilio antes de executar o código.

```java
    // Use your account SID and authentication token instead
    // of the placeholders shown here.
    String accountSID = "your_twilio_account_SID";
    String authToken = "your_twilio_authentication_token";

    // Initialize the Twilio client.
    Twilio.init(accountSID, authToken);

    // Use the Twilio-provided site for the TwiML response.
    URI uri = new URI("https://twimlets.com/message" +
            "?Message%5B0%5D=Hello%20World%21");

    // Declare To and From numbers
    PhoneNumber to = new PhoneNumber("NNNNNNNNNN");
    PhoneNumber from = new PhoneNumber("NNNNNNNNNN");

    // Create a Call creator passing From, To and URL values
    // then make the call by executing the create() method
    Call.creator(to, from, uri).create();
```

Para obter mais informações sobre os parâmetros passados para o método **Call.creator**, consulte [https://www.twilio.com/docs/api/rest/making-calls][twilio_rest_making_calls].

Como mencionado, esse código utiliza um site fornecido pelo Twilio para retornar a resposta de TwiML. Em vez disso, você pode usar seu próprio site para fornecer a resposta de TwiML; para obter mais informações, consulte [Como fornecer respostas de TwiML em um aplicativo Java no Azure](#howto_provide_twiml_responses).

## <a name="how-to-send-an-sms-message"></a><a id="howto_send_sms"></a>Como enviar uma mensagem de SMS
O conteúdo abaixo mostra como enviar uma mensagem SMS usando a classe **Message**. O número **de** , **4155992671**, é fornecido pelo twilio para contas de avaliação para enviar mensagens SMS. O número **de para** deve ser verificado para sua conta do twilio antes da execução do código.

```java
    // Use your account SID and authentication token instead
    // of the placeholders shown here.
    String accountSID = "your_twilio_account_SID";
    String authToken = "your_twilio_authentication_token";

    // Initialize the Twilio client.
    Twilio.init(accountSID, authToken);

    // Declare To and From numbers and the Body of the SMS message
    PhoneNumber to = new PhoneNumber("+14159352345"); // Replace with a valid phone number for your account.
    PhoneNumber from = new PhoneNumber("+14158141829"); // Replace with a valid phone number for your account.
    String body = "Where's Wallace?";

    // Create a Message creator passing From, To and Body values
    // then send the SMS message by calling the create() method
    Message sms = Message.creator(to, from, body).create();
```

Para obter mais informações sobre os parâmetros passados para o método **Message.creator**, consulte [https://www.twilio.com/docs/api/rest/sending-sms][twilio_rest_sending_sms].

## <a name="how-to-provide-twiml-responses-from-your-own-website"></a><a id="howto_provide_twiml_responses"></a>Como fornecer respostas TwiML de seu próprio site
Quando o aplicativo iniciar uma chamada para a API do Twilio, por exemplo, por meio do método **CallCreator.create**, o Twilio enviará a solicitação para uma URL que deverá retornar uma resposta em TwiML. O exemplo acima usa a URL fornecida pelo twilio [https://twimlets.com/message][twimlet_message_url] . (O TwiML destina-se ao uso pelos serviços Web, mas você pode exibir o TwiML no seu navegador. Por exemplo, clique [https://twimlets.com/message][twimlet_message_url] para ver um elemento **&lt; Response &gt;** vazio; como outro exemplo, clique [https://twimlets.com/message?Message%5B0%5D=Hello%20World%21][twimlet_message_url_hello_world] para ver um elemento **&lt; Response &gt;** que contém um elemento **&lt; digamos &gt;** .)

Em vez de contar com a URL fornecida pela Twilio, você pode criar seu próprio site URL que retorna respostas HTTP. Você pode criar o site em qualquer linguagem que retorna respostas HTTP; este tópico pressupõe que você hospedará a URL em uma página JSP.

A página JSP seguinte resulta em uma resposta em TwiML que diz **Hello World!** na chamada.

```xml
    <%@ page contentType="text/xml" %>
    <Response>
        <Say>Hello World!</Say>
    </Response>
```

A página JSP seguinte resulta em uma resposta de TwiML que diz algum texto, tem várias pausas e diz informações sobre a versão de API do Twilio e o nome da função do Azure.

```xml
    <%@ page contentType="text/xml" %>
    <Response>
        <Say>Hello from Azure!</Say>
        <Pause></Pause>
        <Say>The Twilio API version is <%= request.getParameter("ApiVersion") %>.</Say>
        <Say>The Azure role name is <%= System.getenv("RoleName") %>.</Say>
        <Pause></Pause>
        <Say>Good bye.</Say>
    </Response>
```

O parâmetro **ApiVersion** está disponível nas solicitações de voz do Twilio (não nas solicitações de SMS). Para ver os parâmetros de solicitação disponíveis para solicitações de voz e SMS do Twilio, consulte <https://www.twilio.com/docs/api/twiml/twilio_request> e <https://www.twilio.com/docs/api/twiml/sms/twilio_request>, respectivamente. A variável de ambiente **RoleName** está disponível como parte de uma implantação do Azure. (Se você deseja adicionar variáveis de ambiente personalizadas para que elas possam ser detectadas de **System.getenv**, consulte a seção variáveis de ambiente em [Diversos parâmetros de configuração de função][misc_role_config_settings].)

Após você definir a página JSP para fornecer respostas TwiML, use a URL da página JSP conforme a URL passada para o método **Call.creator**. Por exemplo, se você tiver um aplicativo Web chamado MyTwiML implantado em um serviço hospedado do Azure e o nome da página JSP for mytwiml.jsp, a URL poderá ser passada para **Call.creator** conforme mostrado a seguir:

```java
    // Declare To and From numbers and the URL of your JSP page
    PhoneNumber to = new PhoneNumber("NNNNNNNNNN");
    PhoneNumber from = new PhoneNumber("NNNNNNNNNN");
    URI uri = new URI("http://<your_hosted_service>.cloudapp.net/MyTwiML/mytwiml.jsp");

    // Create a Call creator passing From, To and URL values
    // then make the call by executing the create() method
    Call.creator(to, from, uri).create();
```

Outra opção para responder com TwiML é por meio da classe **VoiceResponse**, que está disponível no pacote **com.twilio.twiml**.

Para obter informações adicionais sobre como usar Twilio no Azure com Java, consulte [Como fazer uma chamada telefônica usando Twilio em um aplicativo Java no Azure][howto_phonecall_java].

## <a name="how-to-use-additional-twilio-services"></a><a id="AdditionalServices"></a>Como Usar os Serviços Adicionais do Twilio
Além dos exemplos mostrados aqui, o Twilio oferece APIs baseadas na Web que podem ser usadas para aproveitar a funcionalidade adicional do Twilio do aplicativo Azure. Para obter detalhes completos, consulte a [Documentação da API do Twilio][twilio_api_documentation].

## <a name="next-steps"></a><a id="NextSteps"></a>Próximas etapas
Agora que você já conhece os princípios do serviço Twilio, acesse estes links para saber mais:

* [Diretrizes de segurança do Twilio][twilio_security_guidelines]
* [Código de Exemplo e Procedimentos do Twilio][twilio_howtos]
* [Tutoriais do Guia de início rápido do Twilio][twilio_quickstarts]
* [Twilio no GitHub][twilio_on_github]
* [Fale com o suporte do Twilio][twilio_support]

[twilio_java]: https://github.com/twilio/twilio-java
[twilio_api_service]: https://api.twilio.com
[howto_phonecall_java]: partner-twilio-java-phone-call-example.md
[misc_role_config_settings]: /previous-versions/azure/hh690945(v=azure.100)
[twimlet_message_url]: https://twimlets.com/message
[twimlet_message_url_hello_world]: https://twimlets.com/message?Message%5B0%5D=Hello%20World%21
[twilio_rest_making_calls]: https://www.twilio.com/docs/api/rest/making-calls
[twilio_rest_sending_sms]: https://www.twilio.com/docs/api/rest/sending-sms
[twilio_pricing]: https://www.twilio.com/pricing
[special_offer]: https://ahoy.twilio.com/azure
[twilio_libraries]: https://www.twilio.com/docs/libraries
[twiml]: https://www.twilio.com/docs/api/twiml
[twilio_api]: https://www.twilio.com/api
[try_twilio]: https://www.twilio.com/try-twilio
[twilio_console]:  https://www.twilio.com/console
[verify_phone]: https://www.twilio.com/console/phone-numbers/verified#
[twilio_api_documentation]: https://www.twilio.com/docs
[twilio_security_guidelines]: https://www.twilio.com/docs/security
[twilio_howtos]: https://www.twilio.com/docs/howto
[twilio_on_github]: https://github.com/twilio
[twilio_support]: https://www.twilio.com/help/contact
[twilio_quickstarts]: https://www.twilio.com/docs/quickstart
