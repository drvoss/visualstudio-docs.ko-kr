---
title: VerifyFileHash 작업 | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf7738019680085020b9650094931d5860bc29b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62577364"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash 작업

파일이 예상 파일 해시와 일치하는지 확인합니다.

이 작업은 15.8에 추가되었지만 16.0 미만의 MSBuild 버전에 사용하려면 [해결 방법](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272)이 필요합니다.

## <a name="task-parameters"></a>작업 매개 변수

 다음 표에서는 `VerifyFileHash` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`File`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br />해시되고 유효성이 검사된 파일입니다.|
|`Hash`|필수 `String` 매개 변수입니다.<br /><br />파일의 예상 해시입니다.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br />파일 해시로 설정된 추가 메타데이터가 포함된 `Files` 입력입니다.|
|`Algorithm`|선택적 `String` 매개 변수입니다.<br /><br />알고리즘입니다. 허용되는 값: `SHA256`, `SHA384`, `SHA512`. 기본값은 `SHA256`입니다.|
|`HashEncoding`|선택적 `String` 매개 변수입니다.<br /><br />생성된 해시에 사용할 인코딩입니다. 기본값은 `hex`입니다. 허용되는 값은 `hex`, `base64`입니다.|

## <a name="example"></a>예제

다음 예제에서는 `VerifyFileHash` 작업을 사용하여 자체 체크섬을 확인합니다.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)