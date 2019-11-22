---
title: Getting Started with Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 21e724e585f2a5bf0e1fe2a6b70f89c1bd5f5eec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298198"
---
# <a name="getting-started-with-python"></a>Python 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The Python Tools for Visual Studio (PTVS), is a free, [open-source](https://github.com/Microsoft/ptvs) plug-in for Visual Studio that a powerful Python development experience.  
  
## <a name="python-the-language"></a>Python 언어
  
Python is a popular programming language that is used by many universities, scientists, app scripters, casual developers, and professional developers, working on applications, web sites, and cloud services.

As a programming language, Python is:
  
- 신뢰할 수 있습니다.
- Generally useful for scripting quick programs, app scripting, desktop apps, web servers, web services, and scientific computing.
- 배우기 쉽고 효율적인 코딩을 유도하는 뛰어난 디자인을 가지고 있습니다(많은 대학에서 초급 프로그래밍 과정에 사용함).
- Flexible, supporting imperative, functional, and object-oriented programming styles.
- 무료 및 오픈 소스.
- Runs well on all major operating systems.  
- Supported by many free, useful, and well-designed libraries.  
- Supported by lots of documentation, samples, and a strong developer community.  

To learn more about the language, start with [Python for Beginners](https://www.python.org/about/gettingstarted/) on python.org.

To install Python itself, visit [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
The Python Tools for Visual Studio, which you can install from [visualstudio.com](https://www.visualstudio.com/explore/python-vs), provide the following features:  
  
- 여러 해석기 지원: 다양한 버전의 CPython, IronPython 및 IPython  
- Python 코드의 폴더 구조를 암시적으로 선택하고 앱 코드, 테스트 코드, 웹 페이지, JavaScript, 빌드 스크립트 등을 식별할 수 있도록 명시적으로 제어할 수 있는 프로젝트 시스템.  
- 콘솔, 웹, Azure, 데이터 과학 및 기타 형식의 프로젝트에 대한 프로젝트 템플릿    
- The Azure SDK for Python (see below)    
- 색 지정, 모든 코드 및 라이브러리에 대한 자동 완성, 시그니처 도움말, 클래스 뷰, 정의로 이동, 모든 참조 찾기, 리팩터링 등을 포함한 다양한 편집 및 코드 이해 기능    
- 대화형(REPL) 창
- 데이터 시각화를 사용한 IPython
- IronPython 및 .NET/WPF 지원    
- Visual Studio 프로젝트 없이 풍부한 디버깅, 기존 실행 파일에 대한 기능, 혼합 모드 디버깅, Mac/Windows/Linux로 원격 디버깅 및 대화형 창 내에서 디버깅   
- 프로파일링 도구  
- 테스트 도구  
  
다음 리소스는 시작하는 데 도움이 될 수 있습니다.

- [설치 가이드](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Getting started and deep dive short videos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)(PTVS 시작 및 자세히 알아보기 동영상)  
- Installation and features demo (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [문서](https://github.com/Microsoft/PTVS/wiki)  

Note that Visual Studio does not at present provide the means to create a stand-alone executable using Python, which essentially means a program with an embedded Python interpreter. 그러나 [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)에 설명된 것처럼 Python 커뮤니티 내에 이렇게 하는 다양한 방법이 있습니다. 또한 CPython은 블로그 게시물 [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)(CPython의 포함 가능한 Zip 파일 사용)에 설명된 것처럼 네이티브 애플리케이션 내에 포함되는 기능을 지원합니다.
  
## <a name="building-ui-with-python"></a>Building UI with Python  

The main offering for building a UI with Python is the [Qt Project](https://www.qt.io/qt-for-application-development/), with bindings for Python known as [PySide (the official binding)](https://wiki.qt.io/PySide) (also see [PySide downloads](https://download.qt.io/official_releases/pyside/.))and [PyQt](https://wiki.python.org/moin/PyQt). 현재는 Visual Studio의 Python 지원에 UI 개발용 특정 도구가 포함되지 않습니다.

## <a name="azure-sdk-for-python"></a>Python용 Azure SDK
  
Windows, Mac 및 Linux를 지원하는 Python용 Azure SDK을 통해 Microsoft Azure 서비스를 쉽게 이용하고 관리할 수 있습니다. 자세한 내용은 다음 리소스를 참조하세요. 

- SDK를 설치하려면 [Python Package Index](https://pypi.python.org/pypi/azure)(Python 패키지 인덱스)를 사용하거나 Azure 문서에서 [Python 및 SDK 설치](https://docs.microsoft.com/azure/python/python-sdk-azure-install)를 따르세요. 
- [Python 개발자 센터용 Azure SDK](https://azure.microsoft.com/develop/python/)에는 설치부터 자습서 포함 설명서에 이르기까지 많은 도움말이 있습니다.  중요 사항은 다음과 같습니다.  
- 방법 가이드:
  - [Storage Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Storage Queue](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Storage Table](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Service Bus 큐](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Service Bus 토픽/구독](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Python에서 서비스 관리를 사용하는 방법](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>과학적 컴퓨팅

모든 Python 데이터 과학자 라이브러리 외에도 Visual Studio용 Python 도구는 Azure에서 호스트할 수 있는 IPython 및 IPython Notebook을 지원합니다.

[University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)(캘리포니아 대학교 어바인 캠퍼스)에서 IPython 및 과학적 컴퓨팅 라이브러리(matplotlib, scipy, numpy 등)를 가져오는 것이 좋습니다.  
  
## <a name="see-also"></a>관련 항목:  

[PTVS 시작: Visual Studio 설정](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[PTVS 시작: 코딩 시작(프로젝트)](../python/getting-started-with-ptvs-start-coding-projects.md)
[PTVS 시작: 코드 편집](../python/getting-started-with-ptvs-editing-code.md)
[PTVS 시작: 디버깅](../python/getting-started-with-ptvs-debugging.md)
[PTVS 시작: 대화형 Python](../python/getting-started-with-ptvs-interactive-python.md)
[PTVS 시작: Azure에서 웹 사이트 빌드](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
