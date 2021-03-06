---
title: 데코레이터의 속성
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0265146f5b8d03c7b3ac5f2b08b0cb384c3e45a5
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967105"
---
# <a name="properties-of-decorators"></a>데코레이터의 속성
데코레이터는 아이콘, 텍스트 또는 셰이프 또는 연결선 다이어그램에 표시할 수 있는 확장/축소 펼침 단추입니다. 다음 표에 세 종류의 데코레이터에 대 한 속성을 보여 줍니다. 속성의 일부 셰이프에 데코레이터 또는 커넥터 데코레이터에만 표시 됩니다.

 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 및 도메인 특정 언어 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)합니다.

## <a name="expandcollapse-decorator"></a>Decorator 확장/축소

|속성|설명|기본|
|-|-|-|
|DisplayName|생성된 된 디자이너에서 표시 되는 데코레이터의 이름입니다.|축소 Decorator 확장|
|이름|데코레이터의 이름입니다.|ExpandCollapseDecorator|
|노트|이 데코레이터와 연결 된 비공식 메모입니다.|\<없음 >|
|HorizontalOffset|인치에서 decorator의 기본 위치를 기준으로 가로 오프셋입니다. (셰이프에 합니다.)|0|
|VerticalOffset|인치에서 decorator의 기본 위치를 기준으로 세로 오프셋입니다. (셰이프에 합니다.)|0|
|OffsetFromLine|인치에서를 기본 위치를 기준으로 줄의 데코레이터 오프셋입니다. (에서 커넥터만 합니다.)|0|
|OffsetFromShape|인치에서를 기본 위치를 기준으로 도형에서 decorator의 오프셋입니다. (에서 커넥터만 합니다.)|0|
|위치|데코레이터 기본 위치입니다.|SourceTop|

## <a name="icon-decorator"></a>아이콘 Decorator

|속성|설명|기본|
|-|-|-|
|DefaultIcon|표시할 아이콘 또는 이미지 파일의 경로입니다.|\<없음 >|
|DisplayName|생성된 된 디자이너에 표시할 데코레이터의 이름입니다.|아이콘 Decorator|
|이름|데코레이터의 이름입니다.|IconDecorator|
|노트|데코레이터와 연결 된 비공식 메모입니다.|\<없음 >|
|HorizontalOffset|인치에서 decorator의 기본 위치를 기준으로 가로 오프셋입니다. (셰이프에 합니다.)|0|
|VerticalOffset|인치에서 decorator의 기본 위치를 기준으로 세로 오프셋입니다. (셰이프에 합니다.)|0|
|OffsetFromLine|인치에서를 기본 위치를 기준으로 줄의 데코레이터 오프셋입니다. (에서 커넥터만 합니다.)|0|
|OffsetFromShape|인치에서를 기본 위치를 기준으로 도형에서 decorator의 오프셋입니다. (에서 커넥터만 합니다.)|0|
|위치|데코레이터 기본 위치입니다.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|속성|설명|기본|
|-|-|-|
|DefaultText|기본 텍스트 표시입니다.|레이블|
|DisplayName|생성된 된 디자이너에 표시할 데코레이터의 이름입니다.|레이블|
|FontSize|데코레이터에 표시 되는 텍스트의 글꼴 크기입니다.|8|
|FontStyle|데코레이터에 표시 되는 텍스트의 글꼴 스타일입니다.|기본|
|이름|데코레이터의 이름입니다.|레이블|
|노트|데코레이터와 연결 된 비공식 메모입니다.|\<없음 >|
|HorizontalOffset|인치에서 decorator의 기본 위치를 기준으로 가로 오프셋입니다. (셰이프에 합니다.)|0|
|VerticalOffset|인치에서 decorator의 기본 위치를 기준으로 세로 오프셋입니다. (셰이프에 합니다.)|0|
|OffsetFromLine|인치에서를 기본 위치를 기준으로 줄의 데코레이터 오프셋입니다. (에서 커넥터만 합니다.)|0|
|OffsetFromShape|인치에서를 기본 위치를 기준으로 도형에서 decorator의 오프셋입니다. (에서 커넥터만 합니다.)|0|
|위치|데코레이터 기본 위치입니다.|TargetBottom|

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)