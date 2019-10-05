---
title: 소스 없음 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905221"
---
# <a name="no-source-available"></a>소스 없음
프로젝트에 보려고 하는 코드의 소스 코드가 포함되어 있지 않습니다. 일반적인 원인은 **호출 스택 창** 또는 **스레드 창**에서 소스 코드가 없는 모듈을 두 번 클릭했기 때문입니다. 디버깅을 계속할 수 있지만 소스 창에서 중단점을 설정하고 현재 위치에서 다른 작업을 수행할 수는 없습니다. 중단점을 설정해야 하는 경우에는 **디스어셈블리 창**을 대신 사용합니다.

 솔루션 속성 페이지에서 디버거가 소스 파일을 찾는 디렉터리를 변경하거나 디버거가 선택된 소스 파일을 무시하도록 지정할 수 있습니다. 참조 [디버그 소스 파일을 공용 속성, 솔루션 속성 페이지 대화 상자](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)합니다.

 **소스 코드 찾아서** 소스 코드를 검색할 수 있는 대화 상자를 열려면이 링크를 클릭 합니다.

 **디스어셈블리 표시** 시작 합니다 **디스어셈블리 창**합니다.

 **누락 된 소스 파일에 대 한 디스어셈블리를 항상 표시** 표시 하려면이 옵션을 선택 합니다 **디스어셈블리 창** 자동으로 소스가 없을 때 사용할 수 있습니다. 이 설정은 **옵션** 대화 상자, **디버깅** 범주, **일반** 페이지에서 **소스를 사용할 수 없을 경우 디스어셈블리 표시**를 선택하거나 선택 취소하여 변경할 수도 있습니다.

## <a name="see-also"></a>참고 항목
- [솔루션 속성 페이지 대화 상자, 공용 속성, 소스 파일 디버그](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll(SOS 디버깅 확장)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)