---
title: Vspackage의 리소스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696082"
---
# <a name="resources-in-vspackages"></a>VSPackage의 리소스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

자체 관리 되는 VSPackage 또는 네이티브 위성 UI Dll을 관리 되는 위성 Dll에서에서 지역화 된 리소스를 포함할 수 있습니다.  
  
 Vspackage의 일부의 리소스를 포함할 수 없습니다. 관리 되는 유형은 포함할 수 있습니다.  
  
- 문자열  
  
- 패키지 로드 키 (또한 문자열)  
  
- 도구 창 아이콘  
  
- 컴파일된 명령 테이블 출력 (CTO) 파일  
  
- CTO 비트맵  
  
- 명령줄 도움말  
  
- 대화 상자 데이터에 대 한  
  
  리소스 관리 되는 패키지의 리소스 id 선택 예외는 CTO 파일이 며, CTMENU 이름을 지정 해야 합니다. CTO 파일 리소스 테이블에 표시 해야 합니다는 `byte[]`합니다. 다른 모든 리소스 항목 유형으로 식별 됩니다.  
  
  사용할 수는 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 특성에 알리기 위해 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 관리 되는 리소스는 사용할 수 있습니다.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  설정 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 나타냅니다 이렇게에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 검색할 때 리소스에 대 한 예를 들어, 사용 하 여 관리 되지 않는 위성 Dll을 무시할지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>합니다. 경우 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 동일한 리소스 id는 두 개 이상의 리소스를 발견 하면 찾은 첫 번째 리소스를 사용 합니다.  
  
## <a name="example"></a>예제  
 다음 예제는 관리 되는 도구 창 아이콘을 표시 합니다.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 다음 예제에서는 CTMENU 이름이 cto 인 바이트 배열에 포함 하는 방법을 보여 줍니다.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>구현 참고 사항  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 가능 하면 Vspackage의 지연 로드 합니다. VSPackage에서 CTO 파일 포함의 결과 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 를 설치 하는 경우 병합된 명령 테이블을 작성 하는 동안 메모리에서 이러한 모든 Vspackage를 로드 해야 합니다. VSPackage에서 코드를 실행 하지 않고 메타 데이터를 검사 하 여 VSPackage의 리소스를 추출할 수 있습니다. VSPackage의 성능 손실은 최소 이므로 지금은 초기화 되지 않았습니다.  
  
 때 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 설치가 VSPackage의 리소스 요청을 해당 패키지 이므로 이미 로드 되 고 초기화 하는 일을 할 성능 저하는 미미 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [관리 되는 Vspackage](../../misc/managed-vspackages.md)   
 [Vspackage 관리](../../extensibility/managing-vspackages.md)   
 [MFC 애플리케이션의 지역화된 리소스: 위성 Dll](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [관리되는 VSPackage](../../misc/managed-vspackages.md)
