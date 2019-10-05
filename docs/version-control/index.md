---
layout: LandingPage
title: 버전 제어
description: Visual Studio에서 버전 제어 시작 가이드
keywords: VSTS, TFS, 버전 제어
author: steved0x
ms.manager: jillfra
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 805fe86fcbebdfeb3747dd593d9abbf0f641212d
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160018"
---
# <a name="version-control-in-visual-studio"></a>Visual Studio의 버전 제어

버전 제어 시스템을 사용하면 시간에 따른 코드 변경 내용을 추적하는 데 도움이 됩니다. 변경하면 버전 제어 시스템이 파일의 스냅샷을 작성합니다. 버전 제어 시스템에서는 이 스냅샷을 영구 저장하므로 필요할 때 불러올 수 있습니다. Visual Studio는 [Git](/azure/devops/repos/git/index?view=vsts) 및 [TFVC(Team Foundation 버전 제어)](/azure/devops/repos/tfvc/index?view=vsts)를 제공합니다. 두 시스템 중에서 결정하려면 [프로젝트에 대해 올바른 버전 제어 선택](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json)을 참조하세요.

## <a name="git"></a>Git

Git은 오늘날 가장 일반적으로 사용되는 버전 제어 시스템으로, 빠른 속도로 버전 제어 표준으로 자리잡고 있습니다. Git은 분산 버전 제어 시스템입니다. 즉, 코드의 로컬 사본은 완전한 버전 제어 리포지토리에 해당합니다. 이러한 모든 기능의 로컬 리포지토리 덕분에 오프라인으로 또는 원격으로 쉽게 작업할 수 있습니다. 작업을 로컬로 커밋한 다음 리포지토리 복사본을 서버의 사본과 동기화합니다. 이 패러다임은 클라이언트가 코드의 새 버전을 만들기 전에 서버와 코드를 동기화해야 하는 중앙 집중식 버전 제어와는 다릅니다.

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Git logo" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Git 알아보기</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Git logo" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Visual Studio에서 Git 시작</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Git logo" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>기존 Git 리포지토리 복제</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

TFVC(Team Foundation 버전 제어)는 중앙 집중식 버전 제어 시스템입니다. 일반적으로 팀 멤버는 자신의 고유 개발 컴퓨터에 각 파일 버전 하나만 보유합니다. 기록 데이터는 서버에만 보관됩니다. 분기는 경로에 기반을 두며 서버에서 만들어집니다.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Visual Studio logo" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>TFVC 알아보기</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Visual Studio logo" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Visual Studio에서 TFVC 시작</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Visual Studio logo" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>코드 검토</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="resources"></a>자료

- [Pro Git 책](https://git-scm.com/book/en/v2)
- [Git으로 마이그레이션 계획](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [TFVC에서 Git으로 마이그레이션](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [버전 제어(Mac용 Visual Studio)](/visualstudio/mac/version-control)