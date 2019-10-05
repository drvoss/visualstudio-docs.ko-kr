---
title: Vspackage의 보안 모범 사례 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697276"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage의 보안 모범 사례
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

설치 하는 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 컴퓨터에서 관리자 자격 증명을 사용 하 여 컨텍스트 실행 수. 보안 및 배포의 기본 단위를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 응용 프로그램은 합니다 [Vspackage](../../extensibility/internals/vspackages.md)합니다. 사용 하 여 VSPackage를 등록 해야 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 관리자 자격 증명도 필요 합니다.  
  
 관리자에는 레지스트리 및 파일 시스템에 작성 하 고 모든 코드를 실행할 수 모든 권한을 가집니다. 개발, 배포 하 고, VSPackage를 설치 하려면 이러한 권한이 있어야 합니다.  
  
 설치 하는 즉시 VSPackage는 완전히 신뢰할 수 있는 합니다. VSPackage와 사용 하 여 연결 된 사용 권한의이 높은 수준으로 인해 실수로 악의적인 의도 포함 된 VSPackage를 설치 하는 것이 같습니다.  
  
 사용자가 Vspackage 신뢰할 수 있는 원본 에서만에서 설치 해야 합니다. Vspackage를 개발 하는 회사를 해야 합니다. 강력한 이름을 서명 되도록 사용자는 변조 방지 됩니다. Vspackage 개발 회사와 같은 웹 서비스 및 원격 설치를 평가 하 고 보안 문제를 해결 하는 외부 종속성을 확인 해야 합니다.  
  
 자세한 내용은.NET Framework에 대 한 보안 코딩 지침 참조 ([https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>참고 항목  
 [추가 기능 보안](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 보안](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
