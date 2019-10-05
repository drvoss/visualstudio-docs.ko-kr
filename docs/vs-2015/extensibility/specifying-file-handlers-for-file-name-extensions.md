---
title: 파일 이름 확장명에 대 한 파일 처리기 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fe2f26a959fc6a185bf244bfa4571846b7991a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447180"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>파일 이름 확장명에 대한 파일 처리기 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다양 한 방법으로 특정 파일 확장명을 가진 파일을 처리 하는 응용 프로그램을 확인할 수 있습니다. OpenWithList 및 Openwithprogid 동사에는 파일 확장명에 대 한 레지스트리 항목에서 파일 처리기를 지정 하려면 두 가지 있습니다.  
  
## <a name="openwithlist-verb"></a>OpenWithList 동사  
 Windows 탐색기에서 파일을 마우스 오른쪽 단추로 클릭할 때 표시 된 **열려** 명령입니다. 둘 이상의 제품에 확장을 사용 하 여 연결 된 경우 표시는 **연결 프로그램** 하위 메뉴.  
  
 파일 확장명에 대 한 OpenWithList 키 HKEY_CLASSES_ROOT에서 설정 하 여 확장을 열고 다른 응용 프로그램을 등록할 수 있습니다. 파일 확장명에 대 한이 키 아래에 나열 된 응용 프로그램 아래에 표시를 **프로그램 권장** 제목에 **연결** 대화 상자. 다음 예제에서는.vcproj 파일 확장명을 열려면 등록 된 응용 프로그램을 표시 합니다.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
> HKEY_CLASSES_ROOT\Applications 아래의 목록에서 키는 응용 프로그램을 지정 합니다.  
  
 OpenWithList 키에 추가 하 여 다른 응용 프로그램 확장의 소유권을 갖습니다 하는 경우에 응용 프로그램 파일 확장명을 지원함을 선언 합니다. 응용 프로그램 또는 다른 응용 프로그램의 이후 버전 수 있습니다.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 프로그래밍 방식 식별자 (Progid)는 응용 프로그램 또는 COM 개체의 버전을 식별 하는 Classid의 친숙 한 버전입니다. 모든 공동 creatable 개체는 고유한 progid가 있어야 합니다. VisualStudio.DTE.10.0 시작 되는 동안 Visual Studio.NET 2003 VisualStudio.DTE.7.1 시작 하는 예를 들어 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 프로젝트 형식 또는 프로젝트 항목 형식의 소유자에 파일 확장명에 대 한 버전별 ProgID를 만들어야 합니다. 이 Progid 둘 이상의 ProgID는 동일한 응용 프로그램을 시작할 수 있다는 점에서 중복 될 수 있습니다. 자세한 내용은 [파일 이름 확장명에 대 한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)합니다.  
  
 버전 관리 파일 Progid에 대 한 다른 공급 업체의 등록을 사용 하 여 중복을 방지 하려면 다음 명명 규칙을 사용 합니다.  
  
|파일 확장명|버전이 지정 된 ProgID|  
|--------------------|----------------------|  
|.extension|ProductName. extension.versionMajor.versionMinor|  
  
 특정 파일 확장명을 HKEY_CLASSES_ROOT를 값으로 버전이 지정 된 Progid를 추가 하 여 열 수 있는 다른 응용 프로그램을 등록할 수 있습니다\\*\<확장 >* \OpenWithProgids 키입니다. 이 레지스트리 키에는 파일 확장명과 연결 된 대체 Progid의 목록을 포함 합니다. 나열 된 Progid와 관련 된 응용 프로그램에 표시 합니다 **열기**_Product Name_ 하위 메뉴. 동일한 응용 프로그램 모두에 지정 된 경우는 `OpenWithList` 및 `OpenWithProgids` 운영 체제 키 중복 항목을 병합 합니다.  
  
> [!NOTE]
> `OpenWithProgids` 키 Windows XP 에서만 지원 됩니다. 다른 운영 체제에서이 키를 무시 하기 때문에 사용 하지 마십시오 것만 등록이 파일 처리기. 이 키를 사용 하 여 Windows XP에서 더 나은 사용자 환경을 제공 합니다.  
  
 REG_NONE 형식의 값으로 원하는 Progid를 추가 합니다. 다음 코드에서는 파일 확장명에 대 한 Progid를 등록 하는 예 (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 파일 확장명에 대 한 기본값은 기본 파일 처리기로 지정 된 ProgID입니다. 이전 버전과 함께 제공 되는 파일 확장명에 대 한 ProgID를 수정 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 또는 다른 응용 프로그램을 통해 수행할 수 있는 다음 등록 해야 합니다는 `OpenWithProgids` 에 파일 확장명에 대 한 키와 함께 목록에 새 ProgID를 지정 이전 Progid를 지원 합니다. 예를 들어:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 이전 ProgID에 동사를 사용 하 여 연결 된 경우 이러한 동사도 아래에 나타납니다 **연결 프로그램** *Product Name* 바로 가기 메뉴에서.  
  
## <a name="see-also"></a>참고 항목  
 [파일 이름 확장명에 대 한](../extensibility/about-file-name-extensions.md)   
 [파일 이름 확장명에 대한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)
