---
title: 프로젝트 출력에 대 한 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d14435917e982328220aa6b778d081a8837f0396
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443877"
---
# <a name="project-configuration-for-output"></a>출력에 대한 프로젝트 구성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모든 구성에는 실행 파일 또는 리소스 파일과 같은 출력 항목을 생성 하는 빌드 프로세스의 집합을 지원할 수 있습니다. 이러한 출력 항목은 사용자에 게 개인 및 관련된 형식의 실행 파일 (.exe,.dll,.lib) 및 원본 파일 (.idl,.h 파일)와 같은 출력을 연결 하는 그룹에 배치할 수 있습니다.  
  
 출력 항목을 통해 사용할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> 메서드를 열거 하 고는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> 메서드. 출력 항목을 그룹화 하려는 경우 프로젝트도 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 인터페이스입니다.  
  
 구현 하 여 개발 된 구문을 `IVsOutputGroup` 프로젝트 사용량에 따라 출력 그룹에 있습니다. 예를 들어 해당 프로그램 데이터베이스 (PDB)를 사용 하 여 DLL은 그룹화 할 수 있습니다.  
  
> [!NOTE]
> 디버깅 정보를 포함 하는 PDB 파일 및.dll 또는.exe를 빌드할 때 ' 디버그 정보 생성 ' 옵션을 지정 하는 경우 만들어집니다. .Pdb 파일 디버그 프로젝트 구성의 경우 일반적으로 생성 됩니다.  
  
 프로젝트 그룹 내에 포함 된 출력 수가 구성에서 구성 달라질 경우에, 지원 되는 각 구성에 대 한 그룹 수가 반환 해야 합니다. 예를 들어, 프로젝트 Matt의 DLL 디버그 구성에 mattd.dll 및 mattd.pdb 포함 되었지만 matt.dll 보려면 소매 구성을 포함 합니다.  
  
 그룹 수도 정식 이름, 표시 이름 및 그룹 정보 같은 동일한 식별자 정보 구성에서 구성 프로젝트 내에서. 이 일관성 배포 및 구성을 변경 하는 경우에 작동 하도록 하려면 패키지 있습니다.  
  
 그룹에는 의미를 가리키도록 패키징 바로 가기를 허용 하는 키 출력이 있을 수도 있습니다. 모든 그룹을 그룹의 크기에 대 한 어떠한가 정도 하지 만들어져 있으므로 지정 된 구성에서는 빈 수 있습니다. 모든 구성에서 각 그룹의 크기 (출력 수)는 동일한 구성에 다른 그룹의 크기와에서 다를 수 있습니다. 이 다른 구성에서 동일한 그룹의 크기와 다른 수도 있습니다.  
  
 ![출력 그룹 그래픽](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
출력 그룹  
  
 기본 용도 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> 인터페이스 빌드, 배포 및 관리 개체를 디버깅 및 프로젝트 그룹 출력 자유롭게 허용에 대 한 액세스를 제공 하는 것입니다. 이 인터페이스의 자세한 사용 방법은 참조 하세요 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)합니다.  
  
 이전 다이어그램에 따라서 출력 구성 (bD.exe 또는 b.exe)에서 키가 기본 제공 그룹 사용자가 기본 제공 바로 가기를 만드는 하 고 바로 가기는 배포 구성에 관계 없이 작동 하는지 알고 있어야 합니다. 그룹 원본 없으므로 출력에 키를 사용자에 바로 가기를 만들 수 없습니다. 디버그 그룹 작성 키 출력을 갖지만 소매 그룹 작성 하지 않습니다, 경우에 잘못 구현 될 것입니다. 그런 다음에 구성이 없는 출력을 포함 하는 그룹에 있고, 결과적으로, 키 파일이 없으면 다음 출력 포함 않는 해당 그룹을 사용 하 여 다른 구성 수 없습니다. 키 파일입니다. 설치 관리자 편집기 가정 정식 이름 및 키 파일의 존재 여부와 그룹의 표시 이름을 변경 하지 마십시오 구성에 기반 합니다.  
  
 프로젝트에 포함 하는 경우는 `IVsOutputGroup` 는는 패키지 또는 배포 하지 않습니다, 것으로 충분 그룹에 해당 출력을 포함 되지 않습니다. 출력 계속 열거할 수 일반적으로 구현 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> 구성의 출력 그룹화에 관계 없이 모든 반환 하는 메서드입니다.  
  
 자세한 내용은 참조 구현의 `IVsOutputGroup` 에서 사용자 지정 프로젝트 샘플 [프로젝트의 MPF](http://mpfproj12.codeplex.com)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [관리 구성 옵션](../../extensibility/internals/managing-configuration-options.md)   
 [빌드에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)   
 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
