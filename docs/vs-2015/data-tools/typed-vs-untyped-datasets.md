---
title: 형식화 되지 않은 데이터 집합 및 형식화 된 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d02f72a686d0f271e387e550122451db34c019a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192786"
---
# <a name="typed-vs-untyped-datasets"></a>형식화된 데이터 세트 및 형식화되지 않은 데이터 세트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

형식화 된 데이터 집합은 기본에서 파생 하는 데이터 집합 <xref:System.Data.DataSet> 클래스 및 다음 정보를 사용 하 여는 **데이터 집합 디자이너**, dataset 클래스를 강력한 새 생성 하는.xsd 파일에 저장 된 합니다. 정보 스키마 (테이블, 열 및 등)에서 생성 되 고이 새 데이터 집합 클래스 최고 수준의 개체 및 속성의 집합으로 컴파일됩니다. 형식화 된 데이터 집합 기본에서 상속 되므로 <xref:System.Data.DataSet> 기능의 모든 클래스, 형식화 된 가정 합니다 <xref:System.Data.DataSet> 클래스 및 인스턴스를 사용 하는 메서드를 사용 하 여 사용할 수는 <xref:System.Data.DataSet> 클래스를 매개 변수로.  
  
 형식화 되지 않은 데이터 집합을 해당 기본 제공 스키마를 반면에 있습니다. 형식화 된 데이터 집합에서와 같이 형식화 되지 않은 데이터 집합을 포함 테이블, 열 및 등-있지만 해당 컬렉션으로만 표시 됩니다. 그러나 (수동으로 만든 후 테이블 및 기타 데이터 요소 형식화 되지 않은 데이터 집합에서 내보낼 수 있습니다 데이터 집합의 구조를 스키마로 데이터 집합을 사용 하 여 <xref:System.Data.DataSet.WriteXmlSchema%2A> 메서드.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>대비 되는 형식화 및 형식화 되지 않은 데이터 집합의 데이터 액세스  
 형식화 된 데이터 집합에 대 한 클래스에는 해당 속성의 테이블 및 열을 실제 이름에 사용 되는 개체 모델 예를 들어 형식화 된 데이터 집합을 사용 하는 경우 다음과 같은 코드를 사용 하 여 열을 참조할 수 있습니다.  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 반면, 형식화 되지 않은 데이터 집합을 사용 하는 경우 해당 하는 코드는 다음과 같습니다.  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 형식화 된 액세스는만 더 읽기 쉽도록 아니라의 IntelliSense도 완벽 하 게 지원 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **코드 편집기**합니다. 형식화 된 데이터 집합에 대 한 구문을 쉽게 작업할 수 있을 뿐만 형식 검사가 컴파일 타임에 데이터 집합 멤버에 값을 할당할 때 오류가 발생할 가능성을 크게 줄일를 제공 합니다. 열 이름을 변경 하면 프로그램 <xref:System.Data.DataSet> 클래스 및 다음 응용 프로그램을 컴파일, 빌드 오류가 있습니다. 빌드 오류를 두 번 클릭 합니다 **작업 목록**, 이전 열 이름을 참조 하는 코드의 줄로 직접 이동할 수 있습니다. 테이블 및 형식화 된 열에 대 한 액세스 데이터 집합 이므로 런타임 시 약간 더 빠르게 액세스는 런타임 시 컬렉션을 통해서가 아니라 컴파일 타임에 결정 됩니다.  
  
 형식화 된 데이터 집합의 장점은 하는 경우에 형식화 되지 않은 데이터 집합을 다양 한 상황에서에서 유용 합니다. 가장 확실 한 경우 스키마가 없는 경우 데이터 집합을 사용할 수 있습니다. 이 경우 발생할 수 있습니다, 예를 들어, 응용 프로그램은 데이터 집합을 반환 하는 구성 요소와 상호 작용 하지만 알 수 없는 사전에 구조를 합니다. 마찬가지로, 정적, 예측 가능한 구조 없는 데이터로 작업할 때는 경우가 있습니다. 이 경우 하기가 어려운 형식화 된 dataset을 사용 하도록 변경할 때마다 데이터 구조를 사용 하 여 형식화 된 dataset 클래스를 다시 생성 해야 하기 때문에 합니다.  
  
 보다 일반적으로 사용 가능한 스키마 필요 없이 동적으로 데이터 집합을 만들 수 있습니다 하는 경우 많은 경우가 있습니다. 이 경우 데이터 집합 구조가 단순히 편리 하 게 정보를 유지할 수 있습니다으로 관계형 방식으로 데이터를 나타낼 수 있습니다. 이와 동시에 다른 프로세스에 전달할 또는 XML 파일을 작성 하는 정보를 serialize 하는 기능과 같은 데이터 집합의 기능을 활용을 걸릴 수 있습니다.
