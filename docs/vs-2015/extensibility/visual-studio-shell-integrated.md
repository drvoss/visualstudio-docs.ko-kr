---
title: Visual Studio Shell (통합) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 664363740737eb72213b4818b104aa14c3667a14
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690921"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (통합)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 통합 셸에 통합된 개발 환경 (IDE), 디버거 및 소스 제어 통합을 포함합니다. 프로그래밍 언어가 포함 되어 있습니다. 그러나 integrated shell는 프로그래밍 언어를 추가할 수 있는 프레임 워크를 제공 합니다.  
  
 Visual Studio 통합 셸에 실제로 Visual Studio 격리 셸 및 통합된 셸 특정 구성 요소를 포함 하는 추가 설치를 조합 합니다.  통합된 셸 응용 프로그램 모두는 isolated shell 재배포 가능 패키지에서 포함할지 [Microsoft Visual Studio Shell (격리) 재배포 가능 패키지](http://go.microsoft.com/fwlink/?LinkId=616022) 통합된 셸 재배포 가능 패키지 [Microsoft Visual Studio Shell (통합된) 재배포 가능 패키지](http://go.microsoft.com/fwlink/?LinkId=616021)합니다.  
  
> [!NOTE]
> 격리 및 통합 셸 재배포 가능 패키지에 액세스 하려면, 먼저 간단한 고객 설문 조사를 묻는 메시지가 나타납니다.  설문 조사을 채운 후 재배포 가능 패키지 다운로드 링크를 사용 하 여 Visual Studio 연결 페이지로 이동 됩니다.  Visual Studio Connect 사이트를 방문할에서 다운로드 링크를 찾을 수 있습니다 합니다 **프로그램 &#124; VISUAL STUDIO 2015 통합 및 격리 셸** 탭 합니다.  
  
 전체 버전의 Visual Studio와 동일한 컴퓨터에서 통합된 셸에 응용 프로그램을 설치 하는 경우 응용 프로그램의 구성 요소는 Visual Studio에 직접 통합 될 예정입니다.  
  
## <a name="features-in-the-integrated-shell"></a>Integrated Shell에는 기능  
  
|||  
|-|-|  
|기능 영역|기능|  
|언어 지원|-None|  
|IDE|<ul><li>설정<br /><br /> <ul><li>설정 만들기</li><li>설정 가져오기 및 내보내기</li><li>설정 다시 설정</li></ul></li><li>**도구 상자** 통합</li><li>**작업 목록** 통합</li><li>도움말 통합</li><li>**옵션** 대화 상자</li><li>글꼴 및 색 관리</li><li>**출력** 창</li><li>**명령** 창</li><li>창 관리</li><li>메뉴 명령과 키 바인딩</li><li>도메인 특정 언어 (DSL) 런타임</li></ul>|  
|프로젝트 시스템 및 프로젝트 형식|-솔루션 및 솔루션 폴더<br />솔루션 구성 관리자<br />항목 관리<br />-단일 프로젝트 및 다중 프로젝트 솔루션<br />응용 프로그램 디자이너 (간소화 된 프로젝트 속성)<br />--웹 참조를 추가 하는 중<br />--서비스 참조를 추가 하는 중<br />-단일 프로젝트<br />-웹 사이트 프로젝트 형식<br />-웹 응용 프로그램 프로젝트|  
|빌드|-IDE에서 사용자 지정 빌드 단계<br />-IP (지적재산권) 보호를 위해 미리 컴파일<br />코드 서명<br />     MSBuild|  
|편집기|-코드 (통합된 찾기, 원본 정의 inheritance) 도구를 검색 합니다.<br />코드 탐색<br />-   IntelliSense<br />-   SmartTags<br />-리팩터링<br />-깔끔한 목록<br />IntelliSense 필터링<br />-   **코드 정의** 창|  
|Designer|-Windows Presentation Foundation 디자이너<br />-Windows Forms 디자이너<br />-웹 디자이너와 HTML 편집기|  
|데이터|-   **서버 탐색기** (간체: 데이터만). 참고 1을 참조하세요.<br />-   **데이터 원본** 창<br />-전체 집합이 데이터 컨트롤<br />XML 편집기<br />로컬 데이터 소스에 데이터 바인딩 (합니다. MDF 또는 합니다. MDB)<br />개체에 데이터 바인딩<br />웹 서비스에 데이터 바인딩<br />로컬 데이터베이스 서버에 데이터 바인딩<br />원격 데이터베이스 서버에 데이터 바인딩<br />원격 데이터에 대 한 DDL 도구<br />-   **서버 탐색기** 확장성 ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 샘플)|  
|디버거|-로컬 디버깅 합니다. 참고 2 참조 하세요.<br />관리 디버깅<br />-로컬 디버깅<br />-로컬 프로세스에 연결 합니다.<br />-원격 프로세스에 연결 합니다.<br />익명 대리자<br />응용 프로그램 도메인<br />-ASPX 디버깅<br />-특성<br />-Func 평가 하는 동안 중단 합니다.<br />-중단점<br />중단점 제약 조건<br />-호출 스택<br />-   **명령** 창<br />-크로스 스레드 디버깅<br />데이터 팁<br />데이터 시각화 도우미<br />관리 디버깅 도우미 (Mda)에 대 한 디버거 지원<br />형식 전달 자가 대 한 디버거 지원<br />-DTEEvents OTB에 대 한 지원<br />-JMC 스텝 퍼<br />디버거가 AppID 테스트 (DBGCLR)<br />디버거가 프로필<br />-디버거 도구 및 옵션<br />--반복기를 디버깅 하는 중<br />-디자인 타임 식 계산<br />-C# 식 계산기<br />-디스어셈블리<br />-편집 하며 계속 하기<br />식 계산기 windows (조사식, 지역, 자동)<br />예외 도우미<br />-예외<br />-   Execution<br />-   제네릭<br />-올바른 소스를 시작합니다.<br />-HPC/클러스터 디버깅<br />통합 된 다국어 디버깅<br />-InterOp 디버깅<br />--Just-in-time 디버깅<br />-로컬 디버깅<br />관리 디버깅<br />-수동 컨트롤 (프로세스 창)<br />내 메모리<br />-미니 덤프 지원<br />-모듈<br />-다중 프로세스 디버깅<br />네이티브 디버깅<br />-새 디버그 엔진 지원<br />-최적화 된 코드 디버깅<br />-출력 창을 필터링<br />-프로세스 호스트에 관리 되는 디버깅<br />-프로세스<br />-간략 한 조사식<br />-등록<br />스택의 등록<br />-원격 디버깅<br />-값을 반환 합니다.<br />스크립트 디버깅<br />소스 서비스 지원<br />-보안<br />---나란히<br />-   SQL<br />-기호 서버<br />추적 지점<br />-   Thread<br />-시각화<br />-Extensible Stylesheet Language Transformations (XSLT) 디버거|  
|64 비트 지원|-관리 및 네이티브 코드, 모든 언어에 대 한 64 비트 디버깅<br />-네이티브 x64 지원|  
|소스 코드 제어 SCC)|-기본 SCC 통합입니다. 참고 3을 참조하세요.<br />-도구 옵션 확인|  
|확장성|--Vspackage 및 MEF 구성 요소를 사용 하는 중|  
  
## <a name="notes"></a>노트  
  
#### <a name="1-data-tools"></a>1. 데이터 도구  
 데이터 확장성 지원 및 간소화 된 같은 데이터베이스 개발 도구를 포함 하는 통합된 된 셸에 **솔루션 탐색기**합니다. 그러나 SQL Server Express, SQL 보고 및 Crystal Reports integrated shell에서 제외 됩니다.  
  
#### <a name="2-debugging-support"></a>2. 디버깅 지원  
 Integrated shell 커뮤니티 버전의 Visual Studio에 포함 된 동일한 디버깅 엔진을 포함 합니다. 디버깅 엔진 실행, 연결, 중단점 설정, 편집 하며 계속 하기, 다른 사용자와 같은 관리 코드 및 관련된 기능에 대 한 일반적인 디버거를 포함 합니다. 그러나 디버깅 엔진은 SQL Server 데이터베이스 디버깅을 지원 하지 않습니다.  
  
 하지만 지 원하는 추가 언어를 지원 하도록 확장할 수 없습니다는 기본 디버거 패키지에 포함 된 네이티브 디버깅에 대 한 합니다.  
  
#### <a name="3-source-code-control-integration"></a>3. 소스 코드 제어 통합  
 Integrated shell 소스 코드 제어 (SCC)를 구현 하 고 일반적인 MSSCCI 기반 소스 제어 통합 구성 요소를 제공 하기 위한 Api를 제공 합니다.  
  
 SCC 통합 Pro 버전의 Visual Studio의 일반 기능 하지는 않지만 SCC 통합 integrated shell에서 제공 됩니다.  
  
#### <a name="4-build-support"></a>4. 빌드 지원  
 Integrated shell에는 빌드 지원을 제공합니다. 빌드에 대 한 정보를 찾을 수 있습니다 합니다 [MSBuild 참조](../msbuild/msbuild-reference.md)합니다.  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Integrated Shell에 포함 되지 않은 기능  
 다음은 integrated shell에 포함 되지 않은 기능 목록입니다.  
  
- 클래스 디자이너  
  
- PreEmptive Protection - Dotfuscator  
  
- 언어 기능  
  
- VSHost  
  
- Visual Studio 언어 없음 또는 해당 관련된 프로젝트 템플릿 또는 프로젝트 항목 템플릿을 integrated shell에 포함 됩니다. 다른 기능의 언어별 구현할 필요 없이 예에서는 Visual Basic 코드 조각에 대 한 포함 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 개요 확장](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)