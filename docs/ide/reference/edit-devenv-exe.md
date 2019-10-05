---
title: -Edit(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f0eb7cab3b1bc764f663cd647811928510281e8
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432008"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Visual Studio의 기존 인스턴스에 지정된 파일을 엽니다.

## <a name="syntax"></a>구문

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>인수

- *File1*

  선택 사항입니다. Visual Studio의 기존 인스턴스에서 열 파일입니다. Visual Studio의 인스턴스가 없으면 간소화된 창 레이아웃으로 새 인스턴스가 만들어지고 *File1*이 새 인스턴스에서 열립니다.

- *FileN*

  선택 사항입니다. Visual Studio의 기존 인스턴스에서 열 1개 이상의 추가 파일입니다.

## <a name="remarks"></a>주의

파일이 지정되지 않으면 기존 Visual Studio 인스턴스가 포커스를 받습니다. 파일이 지정되지 않고 Visual Studio 인스턴스가 없으면 간소화된 창 레이아웃으로 인스턴스가 만들어집니다.

기존 Visual Studio 인스턴스가 모달 상태인 경우 Visual Studio가 모달 상태를 종료하면 파일이 기존 인스턴스에서 열립니다. 예를 들어 이 경우는 [[옵션] 대화 상자](../../ide/reference/options-dialog-box-visual-studio.md)가 열릴 때 발생할 수 있습니다.

Visual Studio의 인스턴스를 둘 이상 연 경우 가장 최근에 열린 인스턴스에서 파일이 열립니다.

## <a name="example"></a>예제

첫 번째 예제에서는 기존 Visual Studio 인스턴스에서 `MyFile.cs` 파일을 엽니다. Visual Studio 인스턴스가 없으면 파일이 새 인스턴스에서 열립니다. 두 번째 예제는 단 하나의 파일이 아니라 3개 파일을 여는 것을 제외하고는 유사합니다.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
