---
title: '방법: ClickOnce 응용 프로그램에 대 한 파일 연결 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697697"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션에 대한 파일 연결 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 사용자가 이러한 형식의 파일을 열면 자동으로 시작 될 됩니다 있도록 응용 프로그램은 하나 이상의 파일 이름 확장명을 사용 하 여 연결할 수 있습니다. 에 파일 이름 확장명 지원을 추가 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 간단 합니다.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce 응용 프로그램에 대 한 파일 연결을 만들려면  
  
1. 만들기는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 일반적으로 사용 하 여 기존 또는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다.  
  
2. 응용 프로그램 매니페스트를 텍스트 편집기 또는 메모장과 같은 XML 편집기를 엽니다.  
  
3. `assembly` 요소를 찾습니다. 자세한 내용은 [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)를 참조하세요.  
  
4. 자식으로는 `assembly` 요소를 추가 `fileAssociation` 요소입니다. `fileAssociation` 요소에는 네 개의 특성이:  
  
   - `extension`: 응용 프로그램과 연결할 파일 이름 확장명입니다.  
  
   - `description`: Windows 셸에 표시 되는 파일 형식의 설명입니다.  
  
   - `progid`: 레지스트리에서 표시할 파일 형식을 고유 하 게 식별 하는 문자열입니다.  
  
   - `defaultIcon`: 이 파일 형식을 사용 하는 아이콘입니다. 아이콘은 응용 프로그램 매니페스트에서 파일 리소스로 추가 되어야 합니다. 자세한 내용은 [방법: ClickOnce 애플리케이션에 데이터 파일 포함](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)을 참조하세요.  
  
     예는 `file` 하 고 `fileAssociation` 요소를 참조 하세요 [ \<fileAssociation > 요소](../deployment/fileassociation-element-clickonce-application.md)합니다.  
  
5. 응용 프로그램을 사용 하 여 둘 이상의 파일 형식 연결 하려는 경우 추가 `fileAssociation` 요소입니다. `progid` 특성 마다 달라 야 합니다.  
  
6. 응용 프로그램 매니페스트를 사용 하 여 마친 후에 매니페스트에 다시 서명 합니다. Mage.exe를 사용 하 여 명령줄에서 수행할 수 있습니다.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    자세한 내용은 [Mage.exe(매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) 참조  
  
## <a name="see-also"></a>참고 항목  
 [\<fileAssociation > 요소](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)   
 [Mage.exe(매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
