---
title: 웹 프로젝트 필수 항목 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95c9f7c530d50a7eb89ebe33fad3862f036972d1
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825622"
---
# <a name="web-project-essentials"></a>웹 프로젝트 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

웹 프로젝트는 웹 응용 프로그램을 만듭니다. 스마트 웹 페이지에 있는 웹 응용 프로그램을 만들려면 웹 프로젝트를 사용할 수 있습니다. 스마트 웹 페이지에는 필요에 따라 웹 페이지를 렌더링 하는 서버 쪽 코드를 있습니다.  
  
 와 같은 일반적인 프로그래밍 언어를 사용 하 여 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 또는 [!INCLUDE[csprcs](../../includes/csprcs-md.md)], 수집 및 사용자 로부터 정보를 처리 하 고, 데이터베이스에 저장 하 고 등 스마트 웹 페이지를 만들 수 있습니다.  
  
- 코드 숨김 모델을 파일 확장명이.aspx 또는.asmx 웹 페이지를 사용 하 여 종속 된 소스 코드 파일을 연결 합니다. 예를 들어 hello.aspx 종속 된 소스 코드 파일 hello.aspx.cs가 있을 수 있습니다.  
  
- 스마트 웹 페이지에 연결 된 서버 쪽 코드를 웹 사이트의 /bin 폴더에 있는 실행 파일로 컴파일됩니다.  
  
- 특정 웹 페이지를 사용 하 여 연관 된 도우미 클래스와 같은 추가 소스 코드 파일, 웹 사이트 /App_Code 폴더에 있습니다.  
  
  - 웹 사이트 프로젝트 (WSP) 스마트 각 웹 페이지에 대 한 하나의 실행 파일을 생성합니다. 추가 파일 /App_Code 폴더의 모든 소스 코드 파일에서 생성 됩니다.  

  - 웹 응용 프로그램 프로젝트 (WAP) /App_Code 폴더의 모든 소스 파일 뿐만 아니라 모든 스마트 웹 페이지에 대 한 코드를 결합 하는 단일 실행 파일을 생성 합니다.  
  
- 웹 프로젝트의 솔루션 파일은 웹 사이트 자체에서 별도로 있습니다. 기본적으로 솔루션 파일은 \Documents and 설정을\\*YourAccount*\My Documents\\ *\<Visual Studio # # # >* \Projects\\ *YourWebSite*합니다.  
  
    > [!NOTE]
    > 웹 사이트를 사용 하 여 솔루션 파일을 유지 하려는 경우만 해당 위치로 이동를 닫았다가 다시 합니다.  
  
- Visual Studio에서 솔루션 파일이 있는 웹 사이트를 열면 새 솔루션 파일에 대 한 자동으로 생성 됩니다.  
  
- 웹 프로젝트에 프로젝트 파일이 있습니다. 프로젝트 정보는 솔루션 파일, web.config 파일 및 다른 위치에 저장 됩니다.  
  
- 웹 프로젝트에 전역 속성을 자동으로 추가 웹 프로젝트 솔루션 폴더에 저장소 파일을 만듭니다.  
  
- 스마트 웹 페이지의 Page 지시문을 사용 하 여 서버 쪽 프로그래밍 언어를 사용 하 여 연결할 수 있습니다 또는 \<스크립트 runat = "server" > 태그입니다.  
  
- 또한 웹 페이지에는 모든 스크립팅 언어로 작성 된 클라이언트 쪽 스크립트 블록의 여러가 있을 수 있습니다.  
  
- 프로젝트 및 항목 템플릿 및 등록을 추가 하 여 웹 사이트 프로젝트 시스템은 구현는 [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] 프로젝트입니다.  
  
- WAP 시스템도 프로젝트 flavor 라는 프로젝트 하위 형식으로 구현 됩니다. [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] 프로젝트 WAP 시스템을 만들기 위해 WAP 하위 형식에 따라 지원 됩니다. 프로젝트 하위 형식에 대 한 자세한 내용은 참조 하세요. [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)합니다.  
  
- 스마트 웹 페이지는 서버 쪽 프로그래밍 언어를 사용 하 여 HTML을 결합합니다. 서버 쪽 언어에 포함 된 언어를 라고 합니다. 웹 프로젝트 시스템이 포함 된 언어를 지원 하기 위해 구현 해야 합니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 인터페이스 제품군입니다.  
  
  - 편집기에서 포함 된 언어를 지원 하려면 HTML 언어 서비스는 포함 된 언어 서비스에 포함 된 언어 코드를 표시 지연 해야 합니다.  

  - 항상 오류 표식 (빨간색 물결 모양)를 코드 편집기의 기본 버퍼에 만들어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [웹 프로젝트](../../extensibility/internals/web-projects.md)
