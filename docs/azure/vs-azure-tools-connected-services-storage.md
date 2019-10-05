---
title: 연결된 서비스를 사용하여 Azure Storage 추가 | Microsoft Docs
description: Visual Studio 연결된 서비스 추가 대화 상자를 사용하여 Azure Storage를 앱에 추가
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 649f99911726e562f9602fe6697591ec6cfb96eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561015"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio 연결 서비스를 사용하여 Azure Storage 추가

Visual Studio를 사용하면 **연결된 서비스 추가** 대화 상자에서 Azure Storage에 다음을 연결할 수 있습니다.

- C# 클라우드 서비스
- .NET 백 엔드 모바일 서비스
- ASP.NET 웹 사이트 또는 서비스
- ASP.NET Core 서비스
- Azure WebJob 서비스

연결된 서비스 기능은 필요한 모든 참조와 연결 코드를 프로젝트에 추가하고 구성 파일을 적절하게 수정합니다.

완료되면 **연결된 서비스 추가** 대화 상자에 Blob Storage, 큐, 테이블 작업을 시작하는 데 필요한 단계를 자세히 설명하는 설명서가 자동으로 표시됩니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 연결된 서비스](/visualstudio/mac/connected-services)를 참조하세요.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>연결된 서비스 대화 상자를 사용하여 Azure Storage에 연결

1. Visual Studio에서 프로젝트 열기

1. **솔루션 탐색기**에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **연결된 서비스 추가**를 선택합니다.

    ![Azure 연결된 서비스 추가](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. **연결된 서비스** 페이지에서 **Azure Storage의 클라우드 스토리지**를 선택합니다.

    ![Azure Storage 추가](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **Azure Storage** 대화 상자에서, 기존 스토리지 계정을 선택한 다음 **추가**를 선택합니다.

    스토리지 계정을 만들어야 하는 경우 다음 단계로 이동합니다. 그렇지 않은 경우, 6단계로 건너뜁니다.

    ![프로젝트에 기존 스토리지 계정 추가](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. 스토리지 계정을 만들려면

   1. 대화 상자 아래쪽에 있는 **새 Storage 계정 만들기**를 선택합니다.

   1. **Storage 계정 만들기** 대화 상자를 채운 다음 **만들기**를 선택합니다.

       ![새 Azure Storage 계정](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. **Azure Storage** 대화 상자가 표시되면 새 스토리지 계정이 목록에 나타납니다. 목록에서 새 스토리지 계정을 선택하고 **추가**를 선택합니다.

1. 연결된 스토리지 서비스가 프로젝트의 **서비스 참조** 노드 아래에 나타납니다.

## <a name="how-your-project-is-modified"></a>프로젝트를 수정하는 방법

대화 상자를 완료하면 Visual Studio는 참조를 추가하고 특정 구성 파일을 수정합니다. 특정 변경 내용은 프로젝트 형식에 따라 달라집니다.

- ASP.NET 프로젝트 - [변경된 내용 – ASP.NET 프로젝트](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core 프로젝트 - [변경된 내용 – ASP.NET 5 프로젝트](http://go.microsoft.com/fwlink/p/?LinkId=513124)
- 클라우드 서비스 프로젝트(웹 역할 및 작업자 역할) - [변경된 내용 – 클라우드 서비스 프로젝트](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- WebJob 프로젝트 - [변경된 내용 -WebJob 프로젝트](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="see-also"></a>참고 항목

- [MSDN 포럼: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Microsoft Azure Storage 팀 블로그](http://blogs.msdn.com/b/windowsazurestorage/)
- [Azure Storage 설명서](https://docs.microsoft.com/azure/storage/)
- [연결된 서비스(Mac용 Visual Studio)](/visualstudio/mac/connected-services)
