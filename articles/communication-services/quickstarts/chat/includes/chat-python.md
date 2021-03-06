---
title: incluir arquivo
description: incluir arquivo
services: azure-communication-services
author: mikben
manager: mikben
ms.service: azure-communication-services
ms.subservice: azure-communication-services
ms.date: 9/1/2020
ms.topic: include
ms.custom: include file
ms.author: mikben
ms.openlocfilehash: 0225c948fddf65b9312c689144ecc567a70aa27e
ms.sourcegitcommit: c27a20b278f2ac758447418ea4c8c61e27927d6a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101749972"
---
## <a name="prerequisites"></a>Pré-requisitos
Antes de começar, é preciso:

- Criar uma conta do Azure com uma assinatura ativa. Para obter detalhes, confira [Criar uma conta gratuitamente](https://azure.microsoft.com/free/?WT.mc_id=A261C142F). 
- Instalar o [Python](https://www.python.org/downloads/)
- Criar um recurso dos Serviços de Comunicação do Azure. Para obter detalhes, confira [Criar um recurso de comunicação do Azure](../../create-communication-resource.md). Você precisará registrar o **ponto de extremidade** do recurso para este guia de início rápido
- Um [token de acesso do usuário](../../access-tokens.md). Defina o escopo como "chat" e anote a cadeia de caracteres do token, bem como a cadeia de caracteres da userId.

## <a name="setting-up"></a>Configurando

### <a name="create-a-new-python-application"></a>Criar um novo aplicativo Python

Abra o terminal ou a janela de comando para criar um diretório para seu aplicativo e navegue até ele.

```console
mkdir chat-quickstart && cd chat-quickstart
```

Use um editor de texto para criar um arquivo chamado **start-chat.py** no diretório raiz do projeto e adicione a estrutura do programa, incluindo o tratamento básico de exceções. Você adicionará todo o código-fonte deste guia de início rápido a esse arquivo nas seções a seguir.

```python
import os
# Add required client library components from quickstart here

try:
    print('Azure Communication Services - Chat Quickstart')
    # Quickstart code goes here
except Exception as ex:
    print('Exception:')
    print(ex)
```

### <a name="install-client-library"></a>Instalar a biblioteca de clientes

```console

pip install azure-communication-chat

```

## <a name="object-model"></a>Modelo de objeto

As classes e as interfaces a seguir lidam com alguns dos principais recursos da biblioteca de clientes de chat dos Serviços de Comunicação do Azure para Python.

| Name                                  | Descrição                                                  |
| ------------------------------------- | ------------------------------------------------------------ |
| ChatClient | Essa classe é necessária para a funcionalidade de chat. Crie uma instância dela com suas informações de assinatura e use-a para criar, obter e excluir conversas. |
| ChatThreadClient | Essa classe é necessária para a funcionalidade de conversa de chat. Obtenha uma instância por meio de ChatClient e use-a para enviar/receber/atualizar/excluir mensagens, adicionar/remover/obter usuários e enviar notificações de digitação e confirmações de leitura. |

## <a name="create-a-chat-client"></a>Criar um cliente de chat

Para criar um cliente de chat, você usará o ponto de extremidade do Serviço de Comunicação e o `Access Token` que foi gerado como parte das etapas de pré-requisito. Saiba mais sobre os [tokens de acesso do usuário](../../access-tokens.md).

Este guia de início rápido não abrange a criação de uma camada de serviço para gerenciar tokens no seu aplicativo de chat, embora isso seja recomendado. Confira a documentação a seguir para obter mais detalhes sobre a [Arquitetura de Chat](../../../concepts/chat/concepts.md)

```console
pip install azure-communication-administration
```

```python
from azure.communication.chat import ChatClient, CommunicationTokenCredential, CommunicationTokenRefreshOptions

endpoint = "https://<RESOURCE_NAME>.communication.azure.com"
refresh_options = CommunicationTokenRefreshOptions(<Access Token>)
chat_client = ChatClient(endpoint, CommunicationTokenCredential(refresh_options))
```

## <a name="start-a-chat-thread"></a>Iniciar uma conversa de chat

Use o método `create_chat_thread` para criar uma conversa de chat.

- Use `topic` para fornecer um tópico a essa conversa; o tópico pode ser atualizado depois que a conversa de chat é criada por meio da função `update_thread`.
- Use `thread_participants` para listar o `ChatThreadParticipant` a ser adicionado à conversa de chat; o `ChatThreadParticipant` usa o tipo `CommunicationUserIdentifier` como `user`, que você obteve após a criação por meio de [Criar um usuário](../../access-tokens.md#create-an-identity)
- Use `repeatability_request_id` para direcionar que a solicitação é repetível. O cliente pode fazer a solicitação várias vezes com a mesma Repeatability-Request-ID e receber uma resposta apropriada sem que o servidor execute a solicitação várias vezes.

A resposta `chat_thread_client` é usada para executar operações na conversa de chat recém-criada, como adicionar participantes a ela, enviar mensagens, excluir mensagens etc. Ela contém uma propriedade `thread_id`, que é a ID exclusiva da conversa de chat.

#### <a name="without-repeatability-request-id"></a>Sem Repeatability-Request-ID
```python
from datetime import datetime
from azure.communication.chat import ChatThreadParticipant

topic="test topic"
participants = [ChatThreadParticipant(
    user=user,
    display_name='name',
    share_history_time=datetime.utcnow()
)]

chat_thread_client = chat_client.create_chat_thread(topic, participants)
```

#### <a name="with-repeatability-request-id"></a>Com Repeatability-Request-ID
```python
from datetime import datetime
from azure.communication.chat import ChatThreadParticipant

topic="test topic"
participants = [ChatThreadParticipant(
    user=user,
    display_name='name',
    share_history_time=datetime.utcnow()
)]

repeatability_request_id = 'b66d6031-fdcc-41df-8306-e524c9f226b8' # some unique identifier
chat_thread_client = chat_client.create_chat_thread(topic, participants, repeatability_request_id)
```

## <a name="get-a-chat-thread-client"></a>Obter um cliente de conversa de chat
O método `get_chat_thread_client` retorna um cliente de conversa para uma conversa que já existe. Ele pode ser usado para executar operações na conversa criada: adicionar participantes, enviar mensagens etc. A thread_id é a ID exclusiva da conversa de chat existente.

```python
thread_id = chat_thread_client.thread_id
chat_thread_client = chat_client.get_chat_thread_client(thread_id)
```

## <a name="list-all-chat-threads"></a>Listar todas as conversas de chat
O método `list_chat_threads` retorna um iterador do tipo `ChatThreadInfo`. Ele pode ser usado para listar todas as conversas de chat.

- Use `start_time` para especificar o ponto mais antigo no tempo e obter conversas de chat desde esse ponto.
- Use `results_per_page` para especificar o número máximo de conversas de chat retornadas por página.

```python
from datetime import datetime, timedelta
import pytz

start_time = datetime.utcnow() - timedelta(days=2)
start_time = start_time.replace(tzinfo=pytz.utc)
chat_thread_infos = chat_client.list_chat_threads(results_per_page=5, start_time=start_time)

for chat_thread_info_page in chat_thread_infos.by_page():
    for chat_thread_info in chat_thread_info_page:
        # Iterate over all chat threads
        print("thread id:", chat_thread_info.id)
```

## <a name="delete-a-chat-thread"></a>Excluir uma conversa de chat
O `delete_chat_thread` é usado para excluir uma conversa de chat.

- Use `thread_id` para especificar a thread_id de uma conversa de chat existente que precisa ser excluída

```python
thread_id = chat_thread_client.thread_id
chat_client.delete_chat_thread(thread_id)
```

## <a name="send-a-message-to-a-chat-thread"></a>Enviar uma mensagem para uma conversa de chat

Use o método `send_message` para enviar uma mensagem para uma conversa de chat recém-criada, identificada por thread_id.

- Use `content` para fornecer o conteúdo da mensagem de chat;
- Use `chat_message_type` para especificar o tipo do conteúdo da mensagem. Os valores possíveis são "Text" e "HTML"; se nenhum for especificado, o valor padrão de "Text" será atribuído.
- Use `sender_display_name` para especificar o nome de exibição do remetente;

A resposta é uma "id" do tipo `str`, que é a ID exclusiva dessa mensagem.

#### <a name="message-type-not-specified"></a>Tipo de mensagem não especificado
```python
chat_thread_client = chat_client.create_chat_thread(topic, participants)

content='hello world'
sender_display_name='sender name'

send_message_result_id = chat_thread_client.send_message(content=content, sender_display_name=sender_display_name)
```

#### <a name="message-type-specified"></a>Tipo de mensagem especificado
```python
from azure.communication.chat import ChatMessageType

content='hello world'
sender_display_name='sender name'

# specify chat message type with pre-built enumerations
send_message_result_id_w_enum = chat_thread_client.send_message(content=content, sender_display_name=sender_display_name, chat_message_type=ChatMessageType.TEXT)

# specify chat message type as string
send_message_result_id_w_str = chat_thread_client.send_message(content=content, sender_display_name=sender_display_name, chat_message_type='text')
```

## <a name="get-a-specific-chat-message-from-a-chat-thread"></a>Obter uma mensagem de chat específica de uma conversa de chat
A função `get_message` pode ser usada para recuperar uma mensagem específica, identificada por uma message_id

- Use `message_id` para especificar a ID da mensagem.

A resposta do tipo `ChatMessage` contém todas as informações relacionadas à mensagem exclusiva.

```python
message_id = send_message_result_id
chat_message = chat_thread_client.get_message(message_id)
```

## <a name="receive-chat-messages-from-a-chat-thread"></a>Receber mensagens de chat de uma conversa de chat

Recupere mensagens de chat sondando o método `list_messages` em intervalos especificados.

- Use `results_per_page` para especificar o número máximo de mensagens retornadas por página.
- Use `start_time` para especificar o ponto mais antigo no tempo e obter mensagens desde esse ponto.

```python
chat_messages = chat_thread_client.list_messages(results_per_page=1, start_time=start_time)
for chat_message_page in chat_messages.by_page():
    for chat_message in chat_message_page:
        print('ChatMessage: ', chat_message)
        print('ChatMessage: ', chat_message.content.message)
```

`list_messages` retorna a última versão da mensagem, incluindo as edições ou as exclusões que ocorreram na mensagem usando `update_message` e `delete_message`. Para as mensagens excluídas, `ChatMessage.deleted_on` retorna um valor de datetime indicando quando a mensagem foi excluída. Para as mensagens editadas, `ChatMessage.edited_on` retorna um datetime indicando quando a mensagem foi editada. A hora original da criação da mensagem pode ser acessada usando `ChatMessage.created_on`, que pode ser usado para ordenar as mensagens.

`list_messages` retorna diferentes tipos de mensagens que podem ser identificadas por `ChatMessage.type`. Esses tipos são:

- `ChatMessageType.TEXT`: mensagem de chat regular enviada por um participante do thread.

- `ChatMessageType.HTML`: mensagem de chat em HTML enviada por um participante da conversa.

- `ChatMessageType.TOPIC_UPDATED`: mensagem do sistema que indica que o tópico foi atualizado.

- `ChatMessageType.PARTICIPANT_ADDED`: mensagem do sistema que indica que um ou mais participantes foram adicionados ao thread do chat.

- `ChatMessageType.PARTICIPANT_REMOVED`: mensagem do sistema que indica que um participante foi removido do thread de chat.

Para obter mais detalhes, confira [Tipos de mensagem](../../../concepts/chat/concepts.md#message-types).

## <a name="update-topic-of-a-chat-thread"></a>Atualizar o tópico de uma conversa de chat
Você pode atualizar o tópico de uma conversa de chat usando o método `update_topic`

```python
topic = "updated thread topic"
chat_thread_client.update_topic(topic=topic)
updated_topic = chat_client.get_chat_thread(chat_thread_client.thread_id).topic
print('Updated topic: ', updated_topic)
```

## <a name="update-a-message"></a>Atualizar uma mensagem
Você pode atualizar o conteúdo de uma mensagem existente usando o método `update_message`, identificado por message_id

- Use `message_id` para especificar a message_id
- Use `content` para definir o novo conteúdo da mensagem

```python
content = 'Hello world!'
send_message_result_id = chat_thread_client.send_message(content=content, sender_display_name=sender_display_name)

content = 'Hello! I am updated content'
chat_thread_client.update_message(message_id=send_message_result_id, content=content)

chat_message = chat_thread_client.get_message(send_message_result_id)
print('Updated message content: ', chat_message.content.message)
```

## <a name="send-read-receipt-for-a-message"></a>Enviar confirmação de leitura para uma mensagem
O método `send_read_receipt` pode ser usado para postar um evento de confirmação de leitura em uma conversa, em nome de um usuário.

- Use `message_id` para especificar a ID da mensagem mais recente lida pelo usuário atual.

```python
message_id=send_message_result_id
chat_thread_client.send_read_receipt(message_id=message_id)
```

## <a name="list-read-receipts-for-a-chat-thread"></a>Listar as confirmações de leitura de uma conversa de chat
O método `list_read_receipts` pode ser usado para obter confirmações de leitura em uma conversa.

- Use `results_per_page` para especificar o número máximo de confirmações de leitura de mensagem de chat a serem retornadas por página.
- Use `skip` para especificar que as confirmações de leitura de mensagem de chat sejam ignoradas até uma posição específica na resposta.

```python
read_receipts = chat_thread_client.list_read_receipts(results_per_page=2, skip=0)

for read_receipt_page in read_receipts.by_page():
    for read_receipt in read_receipt_page:
        print('ChatMessageReadReceipt: ', read_receipt)
```

## <a name="send-typing-notification"></a>Enviar uma notificação de digitação
O método `send_typing_notification` pode ser usado para postar um evento de digitação em uma conversa, em nome de um usuário.

```python
chat_thread_client.send_typing_notification()
```

## <a name="delete-message"></a>Excluir mensagem
O método `delete_message` pode ser usado para excluir uma mensagem, identificada por uma message_id

- Use `message_id` para especificar a message_id

```python
message_id=send_message_result_id
chat_thread_client.delete_message(message_id=message_id)
```

## <a name="add-a-user-as-participant-to-the-chat-thread"></a>Adicionar um usuário como participante ao thread de chat

Depois que uma conversa de chat é criada, você pode adicionar e remover usuários nela. Ao adicionar usuários, você permite a eles acesso para poderem enviar mensagens à conversa de chat e adicionar/remover outros participantes. Antes de chamar `add_participant` método, adquira um novo token de acesso e uma identidade para esse usuário. O usuário precisará desse token de acesso para inicializar o cliente de chat.

Use o método `add_participant` para adicionar participantes à conversa identificada por thread_id.

- Use `thread_participant` para listar os participantes a serem adicionados à conversa de chat.
- `user`, obrigatório, é o `CommunicationUserIdentifier` que você criou pelo `CommunicationIdentityClient` em [Criar um usuário](../../access-tokens.md#create-an-identity)
- `display_name`, opcional, é o nome de exibição do participante do thread.
- `share_history_time`, opcional, é a hora a partir da qual o histórico de chats é compartilhado com o participante. Para compartilhar o histórico desde o início da conversa de chat, defina essa propriedade como qualquer data igual ou inferior à hora de criação da conversa. Para não compartilhar nenhum histórico anterior ao momento em que o participante foi adicionado, defina-a como a data atual. Para compartilhar o histórico parcial, defina-a como uma data intermediária.

```python
new_user = identity_client.create_user()

from azure.communication.chat import ChatThreadParticipant
from datetime import datetime

new_chat_thread_participant = ChatThreadParticipant(
    user=new_user,
    display_name='name',
    share_history_time=datetime.utcnow())

chat_thread_client.add_participant(new_chat_thread_participant)
```

Vários usuários também podem ser adicionados à conversa de chat usando o método `add_participants`, desde que o novo token de acesso e a identificação sejam disponibilizados a todos os usuários.

```python
from azure.communication.chat import ChatThreadParticipant
from datetime import datetime

new_chat_thread_participant = ChatThreadParticipant(
        user=self.new_user,
        display_name='name',
        share_history_time=datetime.utcnow())
thread_participants = [new_chat_thread_participant] # instead of passing a single participant, you can pass a list of participants
chat_thread_client.add_participants(thread_participants)
```


## <a name="remove-user-from-a-chat-thread"></a>Remover um usuário de uma conversa de chat

Assim como adicionar um participante, você também pode remover participantes de uma conversa. Para removê-los, acompanhe as IDs dos participantes que você adicionou.

Use o método `remove_participant` para remover o participante da conversa identificada por threadId.
- `user` é o `CommunicationUserIdentifier` a ser removido da conversa.

```python
chat_thread_client.remove_participant(new_user)
```

## <a name="run-the-code"></a>Executar o código

Execute o aplicativo do seu diretório de aplicativo com o comando `python`.

```console
python start-chat.py
```
