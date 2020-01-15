---
title: 코드 분석을 위한 샘플 C++ 프로젝트
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 84f6ddc2012617a5216c58fa0761dc100fb8942f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75402753"
---
# <a name="sample-c-project-for-code-analysis"></a>코드 분석을 위한 샘플 C++ 프로젝트

다음 절차에서는 [연습: 오류에 대한 C/C++ 코드 분석](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)의 예제를 만드는 방법을 보여줍니다. 이 절차에서는 다음을 생성합니다.

- CppDemo라는 이름의 [!INCLUDEvsprvs] 솔루션.

- CodeDefects라는 정적 라이브러리 프로젝트

- Annotations라는 정적 라이브러리 프로젝트

절차에서는 헤더에 대해 코드를 제공하고, 정적 라이브러리에 대해 *.cpp* 파일을 제공합니다.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo 솔루션 및 CodeDefects 프로젝트 만들기

1. [!INCLUDEvsprvs]를 열고 **새 프로젝트 만들기**를 선택합니다.

2. 언어 필터를 **C++** 로 변경합니다.

3. **빈 프로젝트**를 선택하고 **다음**을 클릭합니다.

4. **프로젝트 이름** 텍스트 상자에 **CodeDefects**를 입력합니다.

5. **솔루션 이름** 텍스트 상자에 **CppDemo**를 입력합니다.

6. **만들기**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>정적 라이브러리 형태로 CodeDefects 프로젝트 구성

1. 솔루션 탐색기에서 **CodeDefects**를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.

2. **구성 속성**을 확장한 다음, **일반**을 클릭합니다.

3. **일반** 목록에서 **구성 유형**을 **정적 라이브러리(.lib)** 로 변경합니다.

4. **고급** 목록에서 **대상 파일 확장명**을 **.lib**로 변경합니다.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>CodeDefects 프로젝트에 헤더 및 원본 파일 추가

1. 솔루션 탐색기에서 **CodeDefects**를 확장하고, **헤더 파일**을 마우스 오른쪽 단추로 클릭하고, **추가**를 클릭한 다음, **새 항목**을 클릭합니다.

2. **새 항목 추가** 대화 상자에서 **코드**를 클릭한 다음, **헤더 파일(.h)** 을 클릭합니다.

3. **이름** 상자에 **Bug.h**를 입력한 다음, **추가**를 클릭합니다.

4. 다음 코드를 복사하여 편집기에서 *Bug.h* 파일에 붙여넣습니다.

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. 솔루션 탐색기에서 **원본 파일**을 마우스 오른쪽 단추로 클릭하고, **새로 만들기**를 가리킨 다음, **새 항목**을 클릭합니다.

6. **새 항목 추가** 대화 상자에서 **C++ 파일(.cpp)** 을 클릭합니다.

7. **이름** 상자에 **Bug.cpp**를 입력한 다음, **추가**를 클릭합니다.

8. 다음 코드를 복사하여 편집기에서 *Bug.cpp* 파일에 붙여넣습니다.

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

        delete[] domain;
        return result;
    }
    return false;
}

int path_dependent(int n)
{
    int i;
    int j;
    if (n == 0)
        i = 1;
    else
        j = 1;
    return i + j;
}
```

9. **파일** 메뉴를 클릭한 다음, **모두 저장**을 클릭합니다.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>주석 프로젝트 추가 및 정적 라이브러리로 구성

1. 솔루션 탐색기에서 **CppDemo**를 클릭하고, **추가**를 가리킨 다음, **새 프로젝트**를 클릭합니다.

2. **새 프로젝트 추가** 대화 상자에서 언어 필터를 **C++** 로 변경하고 **빈 프로젝트**를 선택한 후 **다음**을 클릭합니다.

3. **프로젝트 이름** 텍스트 상자에 **주석**을 입력한 다음 **만들기**를 클릭합니다.

4. 솔루션 탐색기에서 **주석**을 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.

5. **구성 속성**을 확장한 다음, **일반**을 클릭합니다.

6. **일반** 목록에서 **구성 유형**을 **정적 라이브러리(.lib)** 로 변경하고 클릭합니다.

7. **고급** 목록의 **대상 파일 확장명** 옆에 있는 열에서 텍스트를 선택한 다음 **.lib**를 입력합니다.


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>주석 프로젝트에 헤더 파일 및 원본 파일 추가

1. 솔루션 탐색기에서 **주석**을 확장하고, **헤더 파일**을 마우스 오른쪽 단추로 클릭하고, **추가**를 클릭한 다음, **새 항목**을 클릭합니다.

2. **새 항목 추가** 대화 상자에서 **헤더 파일(.h)** 을 클릭합니다.

3. **이름** 상자에 **annotations.h**를 입력한 다음, **추가**를 클릭합니다.

4. 다음 코드를 복사하여 편집기에서 *annotations.h* 파일에 붙여넣습니다.

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. 솔루션 탐색기에서 **원본 파일**을 마우스 오른쪽 단추로 클릭하고, **새로 만들기**를 가리킨 다음, **새 항목**을 클릭합니다.

6. **새 항목 추가** 대화 상자에서 **코드**를 클릭한 다음, **C++ 파일(.cpp)** 을 클릭합니다.

7. **이름** 상자에 **annotations.cpp**를 입력한 다음, **추가**를 클릭합니다.

8. 다음 코드를 복사하여 편집기에서 *annotations.cpp* 파일에 붙여넣습니다.

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. **파일** 메뉴를 클릭한 다음, **모두 저장**을 클릭합니다.


이제 솔루션이 완성되고 오류 없이 빌드됩니다.
