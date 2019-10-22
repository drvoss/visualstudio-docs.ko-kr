---
title: 일반 프로젝트 속성(Android C++ 메이크파일) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b7fa1b91951e7a3fb145cc26275016037d1b5f2b
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950573"
---
# <a name="general-project-properties-android-c-makefile"></a>일반 프로젝트 속성(Android C++ 메이크파일)

속성 | 설명 | 선택 항목
--- | ---| ---
출력 디렉터리 | 출력 파일 디렉터리에 대한 상대 경로를 지정하며 환경 변수를 포함할 수 있습니다.
중간 디렉터리 | 중간 파일 디렉터리에 대한 상대 경로를 지정하며 환경 변수를 포함할 수 있습니다.
빌드 로그 파일 | 빌드 로깅을 사용하도록 설정된 경우 작성할 빌드 로그 파일을 지정합니다.
구성 형식 | 이 구성에서 생성하는 출력 형식을 지정합니다. | **동적 라이브러리(.so)** - 동적 라이브러리( *.so*)<br>**정적 라이브러리(.a)** - 정적 라이브러리( *.a*)<br>**유틸리티** - 유틸리티<br>**메이크파일** - 메이크파일<br>
