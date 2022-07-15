---
depth_order: 3
---

# 대화 흐름 디자인

사용자와 NUGU간 대화의 유형은 크게 ‘Single-turn 대화’와 ‘Multi-turn 대화’로 구분할 수 있습니다.

* **Single-turn 대화**

  사용자가 발화한 요청에 대해 NUGU가 답변하여 대화가 종료되는 대화 유형

* **Multi-turn 대화**

  사용자와 NUGU가 대화를 2회 이상 주고받는 대화 유형

## Single-turn 대화 유형 살펴보기

### 명령 실행

사용자의 의도에 맞춰 서비스를 지원할 수 있는 경우입니다.

{% alerts style="info" %}
**사용자**: 핫한 음악 틀어줘.
**NUGU**: 멜론 Top 100을 들려드릴게요. (음악 재생)
{% endalerts %}

명령 실행 시 실행의 결과가 사용자에게 명확하게 인지될 수 있고, 답변이 오히려 번거로울 수 있는 경우 Prompt 없이 해당 동작만 실행할 수도 있습니다.

{% alerts style="info" %}
**사용자**: (음악 재생 중) 음악 그만  
**NUGU**: (음악 재생 종료)
{% endalerts %}

{% alerts style="info" %}
음성으로 응답하는 것을 Prompt 응답, 동작을 실행하는 것을 Directive 응답이라고 합니다.  
자세한 내용은 [Response 사용하기](../create-plays-with-play-builder/define-an-action/use-responses)를 참고하세요.
{% endalerts %}

### 명령의 대안 실행

사용자의 의도에 100% 부합하는 결과를 낼 수는 없지만 요청을 받아들일 수 있는 대안이 준비된 경우입니다.

{% alerts style="info" %}
**사용자**: 아이유 재즈 음악 들려줘.  
**NUGU**: 재즈 음악을 들려드릴게요.
{% endalerts %}

{% alerts style="info" %}
다음 경우는 입력된 Entity 간의 우선 순위 정책을 미리 설계해야 합니다.

* 한 번에 여러 Entity가 입력된 경우 복합 검색을 지원하지 않는 경우
* 모든 Entity에 부합하는 검색 결과를 찾지 못한 경우

예) "어제 본 영화 틀어줘" 명령에 대하여 어제 본 영화가 없는 경우 "영화 틀어줘"와 동일한 동작을 수행
{% endalerts %}

### 미지원 안내

사용자의 의도는 파악되었으나 서비스의 지원 범위에 벗어난 경우를 말합니다.

서비스 지원 여부를 인지하지 못한 사용자는 지원되지 않는 기능에 대한 시도를 계속할 수 있으므로 지원할 수 없는 서비스에 대해 명확히 안내합니다.

{% alerts style="info" %}
**사용자**: 어제 날씨 알려줘.  
**NUGU**: 저는 오늘 이전의 날씨 정보는 가지고 있지 않아요.
{% endalerts %}

지원 가능한 다른 기능에 대해 추가적으로 안내하는 것도 좋습니다.

{% alerts style="info" %}
**사용자**: 코끼리가 중국어로 뭐야?  
**NUGU**: 지금은 한영사전만 찾아보실 수 있어요. 영어 단어를 찾아보시려면, “팅커벨, 영어로 코끼리가 뭐야?”라고 말씀해보세요.
{% endalerts %}

{% alerts style="info" %}
서비스 지원 범위를 벗어나는 요청에 대한 응답을 많이 설계할수록 개발 범위가 넓어지므로 유의해야 합니다.
{% endalerts %}

### 연결오류 안내

네트워크의 연결 상태나 서버에 문제가 발생한 경우입니다.

오류(Error) 상황에 대해 지나치게 자세히 설명할 필요는 없으나 원인에 대해 안내를 하는 것이 좋으며, 응답 없이 상황을 종료하거나 거짓으로 안내해서는 안 됩니다.

간결하고 직관적으로 오류에 대해 안내하도록 하며, 가능하다면 사용자가 시도할 수 있는 다음 단계를 안내하는 것이 좋습니다.

{% alerts style="info" %}
**사용자**: 날씨 알려줘  
**NUGU**: (날씨 서버 연결 오류 상태) 지금 날씨 정보를 가져올 수 없어요. 잠시 후 다시 말씀해주세요.

**사용자**: 멜론 틀어줘  
**NUGU**: (멜론 서버 연결 오류 상태) 지금 멜론 서비스에서 음악을 가져올 수 없어요. 잠시 후 다시 말씀해주세요.
{% endalerts %}

### 서비스 도움말

사용자는 Play 안에 다른 어떤 기능들이 있는지 알기가 어렵습니다.

사용자가 다양한 기능을 활용할 수 있도록, "도움말" 이나 "사용방법 알려줘"와 같은 발화에 대하여 서비스 도움말을 제공할 수 있습니다.  
도움말로 제공할 안내가 많을 경우, 한번에 모든 정보를 제공하기 보다는 주요 기능별로 분리하여 제공하는 것이 좋습니다.

또한 사용자가 도움말을 직접 요청하지 않더라도, 필요에 따라 자연스러운 흐름을 방해하지 않는 선에서 첫 진입 시 혹은 응답 중에 필요한 도움말(예: 다른 기능을 소개)을 제공하는 것도 고려해 볼 수 있습니다.

예를 들어, 로그인이 필요한 서비스에서 로그인하지 않고 해당 서비스 명령을 한 경우, 로그인이 필요하다는 안내와 함께 로그인 방법에 대한 가이드를 제공하는 것이 좋습니다.

## Multi-turn 대화 유형 살펴보기

### Slot-filling

사용자의 의도는 파악하였으나 추가 정보가 필요해 다시 묻는 경우입니다.

요청 이행을 위한 Entity가 누락되었을 경우에는 사용자에게 부족한 Entity 정보를 더 얻은 후 서비스를 제공합니다.

{% alerts style="info" %}
**사용자**: 알람 설정해줘.  
**NUGU**: 몇 시로 설정할까요? ← Slot-filling  
**사용자**: 7시.  
**NUGU**: 내일 오전 7시로 알람을 설정했어요.
{% endalerts %}

“언제로 할까요?” 보다는 “몇 시로 설정할까요?”가 더 명확합니다.

Slot-filling 시에는 누락된 Entity에 해당하는 사용자 발화만 받아들이며, 그 외 발화에 대해서는 잘못된 명령임을 안내합니다.  
2회 연속 잘못된 명령이 입력되거나, 미발화 상태가 7초 간 유지될 경우 대화가 종료(play 종료)됩니다.

{% alerts style="info" %}
**사용자**: 아리아, 알람 맞춰줘  
**NUGU**: 몇 시로 맞춰드릴까요? ← Slot-filling  
**사용자**: 몹시 흥분  
**NUGU**: 원하는 시는 알람 시간을 이해하지 못했습니다. 시간을 다시 말씀해주세요. ← 필요한 Entity로 인식을 1회 실패  
**사용자**: 서울시  
**NUGU**: 원하는 시는 알람 시간을 이해하지 못했습니다. ‘아리아, 오전 또는 오후 몇시 알람 설정해줘’ 라고 말씀해주세요. ← 필요한 Entity 인식을 2회 실패, Slot-filling 더 시도하지 않고 Idle 상태가 됨
{% endalerts %}

Slot-filling 문장 작성 시에는 아래의 항목들을 고려해야 합니다.

* 사용자가 질문을 확실히 인지할 수 있도록 문장을 구성합니다.
* 실행 가능한 기능에 대해서만 질문합니다.
* 사용자에게서 얻고자 하는 답변이 ‘예/아니오’인지, 추가 정보인지에 따라 질문을 구성합니다.
* 부족한 필수 Entity(Required Entity)에 대해서만 Slot-filling하며, 선택적인 Entity(Optional Entity)에 대해서는 기본값으로 설정하여 Slot-filling의 횟수를 최소화하도록 합니다.

{% alerts style="success" %}
Slot-filling 구현에 대한 자세한 내용은 [필수 Entity 정의하기(Slot-Filling Prompt)](../create-plays-with-play-builder/define-an-action/use-parameters/slot-filling-prompt)를 참고하세요
{% endalerts %}

### 다음 명령 요청

사용자 발화에 대해 동작 후 다시 마이크를 열고 사용자의 새 명령을 기다리는 경우입니다.

이때는 앞서 수행한 Play의 컨텍스트를 유지하고, Listening-passive 상태로 진입합니다. Slot-filling과 마찬가지로 2회 연속 잘못된 명령이 입력되거나 미발화 상태가 7초 간 유지될 경우 대화가 종료(Play 종료)됩니다.

{% alerts style="info" %}
**사용자**: 배송차량 도착시간 알려줘  
**NUGU**: 상온 배송차량이 아직 물류센터를 출발하지 않았습니다. ← 답변  
무엇을 더 도와드릴까요? (Listening 상태) ← 다음 명령 요청
{% endalerts %}

수행할 수 없는 명령을 한 경우에는 한 번 더 사용자에게 묻는 것도 고려해 볼 수 있습니다.

{% alerts style="info" %}
**사용자**: 모짜르트의 애국가 들려줘.  
**NUGU**: 제가 처리할 수 없는 조합이네요. ← 답변  
다시 한번 말씀해주시겠어요? (Listening 상태) ← 다음 명령 요청
{% endalerts %}

{% alerts style="success" %}
Action 구현에 대한 자세한 내용은 [Action 정의하기](../create-plays-with-play-builder/define-an-action)를 참고하세요.
{% endalerts %}
