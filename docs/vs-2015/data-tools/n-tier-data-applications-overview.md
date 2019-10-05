---
title: N 계층 데이터 응용 프로그램 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d54d69a9aeda76c79208c2685efde94eaaab1017
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693778"
---
# <a name="n-tier-data-applications-overview"></a>N 계층 데이터 애플리케이션 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-계층 * 데이터 응용 프로그램은 여러 구분 되는 데이터 응용 프로그램 *계층*합니다. "분산된 응용 프로그램" 및 "다중 계층 응용 프로그램" 라고도 함, n 계층 응용 프로그램 클라이언트와 서버 간에 배포 된 개별 계층으로 처리를 구분 합니다. 데이터에 액세스 하는 응용 프로그램을 개발 하는 경우에 응용 프로그램을 구성 하는 다양 한 계층을 명확히 구분을 해야 합니다.  
  
 일반적인 N 계층 애플리케이션에는 프레젠테이션 계층, 중간 계층 및 데이터 계층이 포함됩니다. N 계층 응용 프로그램에서 다양 한 계층을 분리 하는 가장 쉬운 방법은 응용 프로그램에 포함 하려는 각 계층에 대 한 개별 프로젝트를 만드는 경우 예를 들어, 프레젠테이션 계층에서 데이터 액세스 논리 중간 계층에 있는 클래스 라이브러리를 수 있습니다 하지만 Windows Forms 응용 프로그램을 수 있습니다. 또한 프레젠테이션 계층 서비스와 같은 서비스를 통해 중간 계층에서 데이터 액세스 논리를 사용 하 여 통신할 수 있습니다. 애플리케이션 구성 요소를 별도의 계층으로 분리하면 애플리케이션의 유지 관리성과 확장성이 높아집니다. 이를 위해 전체 솔루션을 다시 설계 하지 않고도 단일 계층에 적용할 수 있는 새로운 기술 더 쉽게 도입할 수 있게 합니다. 또한 n 계층 응용 프로그램에서 중간 계층에서 프레젠테이션 계층에서 격리를 유지 관리 하는 중요 한 정보를 일반적으로 저장 합니다.  
  
 Visual Studio는 개발자가 n 계층 응용 프로그램을 만들 수 있도록 몇 가지 기능이 포함 되어 있습니다.  
  
- 데이터 집합 디자이너를 제공 된 **데이터 집합 프로젝트** 데이터 집합 (데이터 엔터티 계층) 할 수 있는 속성 및 `TableAdapter`s (데이터 액세스 계층)를 별도 프로젝트로 합니다.  
  
- 합니다 [LINQ to SQL 도구 Visual Studio에서](../data-tools/linq-to-sql-tools-in-visual-studio2.md) DataContext 및 데이터 클래스를 별도 네임 스페이스를 생성 하는 데 필요한 설정을 제공 합니다. 이 통해 데이터 액세스 및 데이터 엔터티 계층의 논리적 분리.  
  
- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) 제공은 <xref:System.Data.Linq.Table%601.Attach%2A> 메서드를 사용 하면 응용 프로그램에서 다른 계층에서 DataContext를 함께 가져올 수 있습니다. 자세한 내용은 [N 계층 응용 프로그램과 원격 linq to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)합니다.  
  
## <a name="presentation-tier"></a>프레젠테이션 계층  
 합니다 *프레젠테이션 계층* 사용자가 응용 프로그램 상호 작용 하는 계층입니다. 여기에 포함 된 추가 응용 프로그램 논리 수도 있습니다. 일반적인 프레젠테이션 계층 구성 요소는 다음과 같습니다.  
  
- 바인딩 구성 요소와 같은 데이터를 <xref:System.Windows.Forms.BindingSource> 고 <xref:System.Windows.Forms.BindingNavigator>입니다.  
  
- 같은 개체의 데이터를 표현 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) 프레젠테이션 계층에서 사용 하기 위해 엔터티 클래스입니다.  
  
  일반적으로 프레젠테이션 계층 서비스 참조를 사용 하 여 중간 계층에 액세스 (예를 들어, 한 [Windows Communication Foundation 서비스 및 Visual Studio의 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) 응용 프로그램). 프레젠테이션 계층 데이터 계층을 직접 액세스 하지는 않습니다. 프레젠테이션 계층은 중간 계층에서 데이터 액세스 구성 요소를 통해 데이터 계층을 사용 하 여 통신합니다.  
  
## <a name="middle-tier"></a>중간 계층  
 합니다 *중간 계층* 는 계층 프레젠테이션 계층과 데이터 계층을 사용 하 여 서로 통신할 수 있습니다. 일반적인 중간 계층 구성 요소는 다음과 같습니다.  
  
- 비즈니스 규칙 및 데이터 유효성 검사 등의 비즈니스 논리  
  
- 데이터 액세스 구성 요소와 같은 논리:  
  
  - [Tableadapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) 하 고 [Dataadapter 및 Datareader](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74)합니다.  
  
  - 같은 개체의 데이터를 표현 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) 엔터티 클래스입니다.  
  
  - 일반적인 응용 프로그램 서비스, 인증, 권한 부여 및 개인 설정 등.  
  
  다음 그림에서는 Visual Studio에서 사용할 수 있는 및 수 적합 한 위치 n 계층 응용 프로그램의 중간 계층에 있는 기술과 기능을 보여 줍니다.  
  
  ![중간 계층 구성 요소](../data-tools/media/ntiermid.png "NtierMid")  
  중간 계층  
  
  일반적으로 중간 계층 데이터 연결을 사용 하 여 데이터 계층에 연결 합니다. 이 데이터 연결의 데이터 액세스 구성 요소가 일반적으로 저장 됩니다.  
  
## <a name="data-tier"></a>데이터 계층  
 합니다 *데이터 계층* 는 기본적으로 응용 프로그램 데이터를 저장 하는 서버 (예를 들어, 실행 하는 서버 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).  
  
 다음 그림에서는 Visual Studio에서 사용할 수 있는 및 수 적합 한 위치 n 계층 응용 프로그램의 데이터 계층에 있는 기술과 기능을 보여 줍니다.  
  
 ![데이터 계층 구성 요소](../data-tools/media/ntierdatatier.png "ntierdatatier")  
데이터 계층  
  
 데이터 계층은 프레젠테이션 계층의 클라이언트에서 직접 액세스할 수 없습니다. 대신 중간 계층에서 데이터 액세스 구성 요소는 프레젠테이션 계층과 데이터 계층 간의 통신에 사용 됩니다.  
  
## <a name="help-for-n-tier-development"></a>N 계층 개발에 대 한 도움말  
 N 계층 응용 프로그램으로 작업 하는 방법에 대 한 정보를 제공 하는 다음 항목을 참조 합니다.  
  
 [데이터 집합 및 TableAdapter를 다른 프로젝트로 분리](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
 [연습: N 계층 데이터 애플리케이션 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
  
 [연습: N 계층 데이터 응용 프로그램에 유효성 검사 추가](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
  
 [LINQ to SQL을 사용한 N 계층 및 원격 응용 프로그램](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Data.Linq.ITable.Attach%2A>   
 [연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [계층적 업데이트](../data-tools/hierarchical-update.md)   
 [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)   
 [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
