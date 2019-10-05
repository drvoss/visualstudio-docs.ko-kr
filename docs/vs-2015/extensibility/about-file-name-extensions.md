---
title: 파일 이름 확장명에 대 한 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148028"
---
# <a name="about-file-name-extensions"></a>파일 확장명 정보
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

버전을 사용 하 여 연결 하는 VSPackage의 파일 확장명을 등록 하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 이 중요 한 경우 둘 이상의 버전이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 컴퓨터에 설치 됩니다.  
  
 Vspackage에 대 한 파일 확장명은 연결 된 ProgID (프로그래밍 식별자)를 가리키는 기본값을 사용 하 여 키 HKEY_CLASSES_ROOT 아래 등록 됩니다.  
  
 다음은.vcproj 파일 확장명에 대 한 등록 정보의 예입니다.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 연관 된 파일 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 와 같은 버전이 지정 된 ProgID를 있어야 `VisualStudio.vcproj.8.0`, 제품 버전 간 파일 확장명 연결을 유지 하기 위해 제품의 side-by-side-설치를 허용 하도록 합니다. 버전별 ProgID 있습니다 열기, 편집 및 다른 응용 프로그램이 나 다양 한 덮어쓰이지의 영향을 받지 않는 등의 표준 동사를 사용 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]입니다.  
  
 특정 경우에는 파일 확장명과 연결 된 ProgID는 변경 되어야 합니다. 예를 들어,.htm 파일 확장명에 대 한 ProgID (progid htmlfile =).htm 및.html 파일을 사용 하 여 널리 알려진 및에서 사용 되는 연결 이며 여러 운영 체제에서 위치에에서 하드 코드 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [Side-by-side-배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [파일 이름 확장명에 대한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
