---
title: DslTextTransform 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658456"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 명령
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform은 Textconvert.exe를 호출 하 고 일반적인 옵션을 사용 하 여 실행 하는 스크립트입니다. DslTextTransformation 함께 [!INCLUDE[dsl](../includes/dsl-md.md)] 프로젝트의 야간 빌드를 자동화할 수 있습니다. 자세한 내용은 [TextTransform 유틸리티를 사용 하 여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md)을 참조 하세요.

 다음 디렉터리에는 DslTextTransform이 있습니다.

 **\<Visual Studio SDK 설치 경로 > \VisualStudioIntegration\Tools\Bin**

 다음 인수를 DslTextTransform에 대 한 입력으로 지정할 수 있습니다.

- 도메인 모델 프로젝트의 출력 디렉터리입니다.

- 디자이너 정의 프로젝트의 출력 디렉터리입니다.

- 텍스트 템플릿 파일의 위치입니다.

  DslTextTransform은 기본 지시문 프로세서 및 어셈블리를 사용 하 여 지정 된 텍스트 템플릿 파일을 처리 합니다. 사용자 지정 지시문 프로세서를 만드는 경우 TextTransform를 호출 하는 고유한 배치 파일을 만들 수 있습니다. 이 배치 파일에서 어셈블리 및 연결 된 사용자 지정 지시문 프로세서를 지정할 수 있습니다.
