---
title: 64 비트 디버거 COM 클래스 등록 마이그레이션 | Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433697"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 비트 디버거 COM 클래스 등록 마이그레이션

COM 등록 하는 디버거 확장에 대 한 클래스의 HKEY_CLASSES_ROOT regasm을 regsvr32를 사용 하 여 레지스트리 및 로드를 직접 작성 *msvsmon.exe* (원격 디버거) 아니며 이제이 제공할 수 HKEY_CLASSES_ROOT 쓸 필요 없이 msvsmon에 등록 합니다. 레거시.NET 디버거 식 계산기 또는 디버그 엔진을 로드 하도록 구성 된이 영향을 줍니다 합니다 *msvsmon.exe* 프로세스입니다.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

이 기법을 사용 하려면 추가 된  **.msvsmon-comclass-def.json* msvsmon 옆에 있는 파일 (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

다음은 관리 되는 하나를 등록 하는 예제 msvsmon-comclass-def 파일 및 하나의 기본 클래스입니다.

FileName: *MyCompany.MyExample.msvsmon-comclass-def.json*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
