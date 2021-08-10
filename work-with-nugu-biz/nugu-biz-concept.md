# 주요 개념

NUGU biz kit에서 사용되는 개념은 다음과 같습니다.

## NUGU 디바이스\(NUGU device\)

인공지능 서비스 NUGU를 이용할 수 있는 기기들입니다. 현재 Biz Kit에서 활용 가능한 NUGU 디바이는 아래와 같으며, 추후 다른 기기들이 확대될 예정입니다.

**Biz 사용자 이용 가능 디바이스**

* 제한 없음



**Biz 전용 디바이스로 등록 가능한 디바이스 \(디바이스 Setup Tool 등록 가능 디바이스\)**

| 기기명 | 모델명 |
| :--- | :--- |
| NUGU | NU100 |
| NUGU mini | NU200 |
| NUGU candle | NU110 |

**Biz API Announcement 수신 가능 디바이스**

| 기기명 | 모델명 |
| :--- | :--- |
| NUGU | NU100 |
| NUGU mini | NU200 |
| NUGU candle | NU110 |
| NUGU nemo | NU300 |

## Biz 전용 디바이스

공용 공간에서 불특정 다수가 사용할 수 있도록 설치한 NUGU 디바이스입니다.

NUGU 디바이스를 사업장/영업장 등과 같은 공용 공간에서 누구나 사용할 수 있도록 설정하는 기능입니다., 해당 공간의 사용 목적에 적합한 Private Play를 제공하고 , Announcement 메세지를 보낼 수 있습니다.

## 디바이스 그룹 \(Biz 전용 디이스\)

전용 디바이스가 설치될 물리적 위치와 사용 목적을 그룹으로 생성하여 등록합니다. 예를 들어 건물의 회의실, 로비, 호텔 객실 등에 전용 디바이스를 설치해야 할 때 회의실, 로비, 객실의 디바이스 그룹을 생성하고, 생성된 그룹에 디바이스를 할당하여 매핑할 수 있습니다.

## 디바이스 Setup Tool \(Biz 전용 디바이스\)

NUGU 디바이스를 전용 디바이스로 등록하고, Wi-Fi 네트워크를 설정할 수 있도록 지원하는 윈도우 기반 응용 프로그램입니다. Windows 7 이상에서 사용하실 수 있습니다.

## 사용 제외 Play \(Biz 전용 디이스\)

전용 디바이스에서 NUGU 디바이스에서 제공하는 특정 기본 서비스를 제외 할 수 있는 설정입니다. 공공장소나 Biz 사용 목적에 적합하지 않은 기본 서비스들을 사용 불가하도록 제외 처리 할 수 있습니다. 

## Biz 사용자 관리

NUGU play kit에서 개발한 Private Play를 특정 개인 또는 기업\(단체\) 구성원만 사용할 수 있도록 하고,  사용자의 디바이스로 Announcement를 보낼 수 있도록, 사용자를 초대하고 등록하여 권한을 부여하는 기능입니다.

## Biz 사용자 초대 유형 \(Biz Service, Private Play\)

Biz 사용자를 초대 할때, 초대를 수락한 유저의 유형입니다.  

* Private Play :   Play 단위로만 초대한 케이스입니다. 다른 Play를 새로 부여할 경우, 재초대를 하여 승인받아야합니다.
* Biz Service :    퍼블리셔가 제공하는 서비스 단위로 초대한 케이스입니다. 해당 유형으로 수락한 경우, 퍼블리셔가 새로운 그룹이나 Play를 할당하는 경우, 별도의 재초대 없이 사용자를 등 관리 할 수 있습니다.

체험판에서는 Private Play 단위 초대만 지원합니다.

## Private Play

NUGU biz의 전용 디바이스와 등록된 사용자\(이용 권한을 획득한 사용자\)만 이용할 수 있는 Play입니다. Private Play는 NUGU App에서 확인할 수 있으며, 일반 사용자에게는 노출되지 않습니다.

## Biz API

NUGU biz kit의 정식판에서는 퍼블리셔에서 Biz 전용 디바이스와 Biz 사용자 관리에 유용한 API를 추가적으로 제공합니다. 자세한 내용은 Biz API의 설명을 참고하세요.

* [Biz 사용자 API](biz-api/api-enrolleduser/)
* [Biz 전용 디바이스 조회 API](biz-api/api-shareddevice/)
* [API 발송 \(Announcement\)](biz-api/api-announcement/)

## Annoucement

Biz API에서 지원하는 기능으로, Biz 전용 디바이스나 Biz 사용자의 디바이스에 토큰을 기준으로 Announcement 메세지 \(tts, image\)를 전송 할 수 있습니다. 자세한 내용은 [API 발송 \(Announcement\)](biz-api/api-announcement/)의 설명을 참고하세요.
