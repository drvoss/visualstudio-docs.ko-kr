---
title: 데이터를 업로드할 스토리지 찾아보기
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 7d0f2522117f4c5a5b85e99e2779d10cffcb7f22
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777403"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>스토리지로 이동하여 데이터 업로드 또는 모델 및 로그 다운로드

원격 머신 또는 Azure 파일 공유에서 모든 스토리지로 이동하여 데이터를 업로드하거나 모델 및 로그를 다운로드할 수 있습니다. 또는 특정 작업에 대한 로그 및 작업 출력에 액세스하려는 경우 작업 브라우저에서도 수행할 수 있습니다.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>원격 컴퓨터 또는 파일 공유에서 모든 데이터에 액세스하려면

1. **서버 탐색기**를 엽니다.
2. 원격 머신 또는 Batch AI 컴퓨팅 컨텍스트를 확장합니다.
3. **스토리지**를 마우스 오른쪽 단추로 클릭한 다음, **찾아보기**를 클릭합니다.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>원격 머신 또는 파일 공유에서 작업 관련 데이터에 액세스하려면

1. [작업 기록](job-details.md)을 엽니다.
2. 작업을 선택합니다.
3. 이러한 중요 로그 파일에 빠르게 액세스하기 위해 **작업 폴더**를 클릭하거나 **StdOut/Stderr**을 클릭합니다.

    ![storage](media/manage-storage/job-workingfolder.png)
