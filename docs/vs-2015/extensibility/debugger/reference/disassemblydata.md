---
title: DisassemblyData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea21b4ae9e6e852efcc3625dc3af24478bd88155
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198816"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

표시할 통합된 개발 환경 (IDE)에 대 한 하나의 디스어셈블리 명령을 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>멤버  
 `dwFields`  
 합니다 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 채워진 필드를 지정 하는 상수입니다.  
  
 `bstrAddress`  
 일부 시작 지점 (일반적으로 연결 된 함수의 시작)에서 오프셋으로 주소입니다.  
  
 `bstrCodeBytes`  
 이 명령에 대 한 코드 바이트입니다.  
  
 `bstrOpcode`  
 이 명령에 대 한 opcode입니다.  
  
 `bstrOperands`  
 이 명령에 대 한 피연산자입니다.  
  
 `bstrSymbol`  
 기호 이름을 있으면 주소 (공용 기호, 레이블 및 등)를 사용 하 여 연결 합니다.  
  
 `uCodeLocationId`  
 디스어셈블된이 줄의 코드 위치 식별자입니다. 한 줄의 코드 컨텍스트 주소를 다른 코드 컨텍스트 주소 보다 큰 다음 첫 번째 디스어셈블된 코드 위치 식별자를 두 번째 코드 위치 식별자를 초과할 수도 있습니다.  
  
 `posBeg`  
 합니다 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 디스어셈블리 데이터 시작 하는 문서에는 위치에 해당 하는 합니다.  
  
 `posEnd`  
 합니다 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 디스어셈블리 데이터 끝나는 문서의 위치에 해당 하는 합니다.  
  
 `bstrDocumentUrl`  
 파일 이름으로 나타낼 수 있는 텍스트 문서에 대 한 합니다 `bstrDocumentUrl` 소스를 찾을 수 있는, 파일 이름 필드는 채웁니다 형식을 사용 하 여 `file://file name`입니다.  
  
 파일 이름으로 표현할 수 없는 텍스트 문서에 대 한 `bstrDocumentUrl` 문서에 대 한 고유 식별자 이며 디버그 엔진 구현 해야 합니다 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) 메서드.  
  
 이 필드는 체크섬에 대 한 추가 정보를 포함할 수도 있습니다. 세부 정보에 대 한 설명을 참조 하세요.  
  
 `dwByteOffset`  
 명령 코드 줄의 시작 부분에서 바이트 수입니다.  
  
 `dwFlags`  
 합니다 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) 활성화 되어 있는 플래그를 지정 하는 상수입니다.  
  
## <a name="remarks"></a>설명  
 각 `DisassemblyData` 구조 디스어셈블리의 명령 하나에서 설명 합니다. 이러한 구조체의 배열에서 반환 되는 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드.  
  
 합니다 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 텍스트 기반 문서에만 구조를 사용 합니다. 예를 들어 문이나 줄에서 생성 된 첫 번째 명령에 대해서만이 명령에 대 한 소스 코드 범위를 채우는 경우 `dwByteOffset == 0`합니다.  
  
 텍스트가 아닌 된 문서에 대 한 코드에서 문서 컨텍스트를 가져오거나 및 `bstrDocumentUrl` 필드에 null 값 이어야 합니다. 경우는 `bstrDocumentUrl` 필드와 동일 합니다 `bstrDocumentUrl` 이전 필드 `DisassemblyData` 설정한 다음 요소를 배열를 `bstrDocumentUrl` null 값으로.  
  
 경우는 `dwFlags` 필드에는 `DF_DOCUMENT_CHECKSUM` 플래그가 설정 추가 체크섬 정보에서 가리키는 문자열 뒤에 나오는 다음는 `bstrDocumentUrl` 필드입니다. 특히, null 문자열 종결자가 오는, 후 있습니다 따릅니다 체크섬의 바이트 수를 나타내는 4 바이트 값 뒤에 그 다음에 다시 체크섬 바이트로 체크섬 알고리즘을 식별 하는 GUID입니다. 인코딩 및 디코딩이 필드에서 하는 방법은이 항목의 예제를 참조 하세요. [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]합니다.  
  
## <a name="example"></a>예제  
 합니다 `bstrDocumentUrl` 경우 필드를 문자열 이외의 추가 정보를 포함할 수 있습니다는 `DF_DOCUMENT_CHECKSUM` 플래그를 설정 합니다. 이 인코딩된 문자열을 읽고 만드는 과정은 만들었다면 [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]합니다. 그러나 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], 또 다른 문제는 것입니다. 사용자에 게 내용을 보려면, 다음 예제에서는에서 인코딩된 문자열을 만드는 한 가지 방법은 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 인코딩된 문자열을 디코드 하는 한 가지 방법은 및 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]합니다.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
