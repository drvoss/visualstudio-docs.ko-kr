---
title: 전용 갤러리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 097d666a839f67e657610b34641ed29da91797be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193998"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

컨트롤, 템플릿 및 게시 하도록 하 여 개발 하는 도구를 공유할 수 있습니다는 *전용 갤러리* 다음과 같은 조직에 대 한 인트라넷에서:  
  
- Atom (RSS) 피드를 인트라넷에 적절 하 게 구성 된 중앙 위치 (리포지토리)를 만듭니다. 자세한 내용은 [방법: Atom를 만드는 개인 갤러리에 대 한 피드](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)합니다.  
  
- 전용 갤러리를 설명 하는.pkgdef 파일을 배포 합니다. 전용 갤러리를 동시에 여러 컴퓨터에 연결 하려는 관리자에 대 한이 구성을 사용 하는 것이 좋습니다.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>확장 및 업데이트 Visual Studio에서 전용 갤러리 추가  
 전용 갤러리를 사용할 수 있는 경우에 추가할 수 있습니다 **확장 및 업데이트** Visual Studio에서.  
  
 ![확장 관리자 추가 대화 상자](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>확장 및 업데이트 전용 갤러리를 추가 하려면  
  
1. 메뉴 모음에서 **도구**, **옵션**을 선택합니다.  
  
2. 에 **환경을** 노드를 선택 **확장 및 업데이트**합니다.  
  
3. **추가** 단추를 선택합니다.  
  
4. 에 **이름을** 필드에, 예를 들어 개인 갤러리에 대 한 이름을 입력 `My Gallery`합니다.  
  
5. 에 **URL** 필드는 Atom 피드 또는 전용 갤러리를 호스트 하는 SharePoint 사이트의 URL을 입력 합니다.  
  
    1. 호스트는 Atom 피드 개인 갤러리에 연결 하는 경우 URL이 유사: http://www.mywebsite/mygallery/atom.xml 합니다.  이 URL은 파일 또는 네트워크 경로 참조할 수 있습니다.  
  
    2. URL이 유사 호스트 SharePoint 사이트인 경우: http://mysharepoint/sites/mygallery/forms/AllItems.aspx 합니다.  
  
### <a name="managing-private-galleries"></a>전용 갤러리 관리  
 관리자로 가능 전용 갤러리 사용 가능한 여러 컴퓨터에 동시에 각 컴퓨터에서 시스템 레지스트리를 수정 하 여 합니다. 이렇게 하려면 새 레지스트리 키와 값을 설명 하는.pkgdef 파일을 만듭니다.  이 파일의 형식은 다음과 같습니다.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 자세한 내용은 [방법: 레지스트리 설정을 사용 하 여 개인 갤러리 관리](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)합니다.  
  
## <a name="installing-extensions-from-a-private-gallery"></a>전용 갤러리에서 확장 설치  
 검색 하 고 개인 갤러리에서 Visual Studio 확장을 설치할 수 있습니다 **확장 및 업데이트**합니다. 명명 된 전용 갤러리를 사용 하 여 다음 단계를 `My Gallery`입니다.  
  
 ![전용 갤러리를 설치 하는 확장 관리자](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>검색 하 고 개인 갤러리에서 확장을 설치 하려면  
  
1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.  
  
2. 왼쪽된 창에서 선택 **온라인 확장**를 선택한 후 **내 갤러리**합니다.  
  
3. 선택한 후 오른쪽 창에서 확장을 선택 합니다 **다운로드** 단추입니다.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>전용 갤러리에서 확장 업데이트  
 새 버전의 Visual Studio 확장 개인 갤러리에 게시 되는 대로 사용자가 설치한 확장을 업데이트할 수 있습니다. 명명 된 전용 갤러리를 사용 하 여 다음 단계를 `My Repository`입니다.  
  
 ![확장명 관리자 전용 갤러리 업데이트](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>전용 갤러리에서 설치 된 확장을 업데이트 하려면  
  
1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.  
  
2. 왼쪽된 창에서 선택 **업데이트**를 선택한 후 **내 리포지토리**합니다.  
  
3. 선택한 후 오른쪽 창에서 확장을 선택 합니다 **업데이트** 단추입니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 확장명 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
