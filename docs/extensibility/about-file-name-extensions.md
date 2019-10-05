---
title: 파일 이름 확장명에 대 한 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60a721581c3deb4588df59974768c634c2e9515f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313724"
---
# <a name="about-file-name-extensions"></a>파일 이름 확장명에 대 한
버전을 사용 하 여 연결 하는 VSPackage의 파일 확장명을 등록 하면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 이 중요 한 경우 둘 이상의 버전이 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 컴퓨터에 설치 됩니다.

 아래에 Vspackage에 대 한 파일 확장명 등록 되며 **HKEY_CLASSES_ROOT** 는 연결 된 ProgID (프로그래밍 식별자)를 가리키는 기본값을 사용 하 여 키입니다.

 다음 예제에 대 한 등록 정보를 표시 합니다 *.vcproj* 파일 확장명:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 연결 된 파일 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 와 같은 버전이 지정 된 ProgID를 있어야 `VisualStudio.vcproj.8.0`합니다. 버전이 지정 된 ProgID 제품 버전 간 파일 확장명 연결을 유지 하기 위해 제품-나란히 설치할 수 있습니다. 버전별 ProgID 있습니다 열기, 편집 및 다른 응용 프로그램이 나 다양 한 덮어쓰이지의 영향을 받지 않는 등의 표준 동사를 사용 하 여 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]입니다.

 특정 경우에는 파일 확장명과 연결 된 ProgID는 변경 되어야 합니다. 예를 들어의 ProgID를 합니다 *.htm* 파일 확장명 (progid htmlfile =) 하드 코드 된 운영 체제에서 자릿수 이며 널리 알려진 및에서 사용 되는 연결 *.htm* 및 *.html* 파일입니다.

## <a name="see-also"></a>참고자료
- [Side-by-side-배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [파일 이름 확장명에 대 한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md)