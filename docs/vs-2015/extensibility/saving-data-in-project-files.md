---
title: 프로젝트 파일에 데이터 저장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc671963854e4fa0c2af763de5000fac82a839b8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432526"
---
# <a name="saving-data-in-project-files"></a>프로젝트 파일에 데이터 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 하위 형식 저장 하 고 프로젝트 파일에서 하위 형식의 특정 데이터를 검색할 수 있습니다. 관리 패키지 프레임 워크 (MPF)는이 작업을 수행 하는 두 가지 인터페이스를 제공 합니다.  
  
- 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 인터페이스의 액세스 속성 값을 허용 합니다 **MSBuild** 프로젝트 파일의 섹션입니다. 제공 하는 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 로드 하거나 저장 된 사용자가 관련된 데이터를 빌드할 때마다 사용자가 호출할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 자유 형식 xml에서 비 빌드 관련된 데이터를 유지 하는 데 사용 됩니다. 제공 하는 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 이 호출한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 때마다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 아닌 빌드 프로젝트 파일의 관련된 데이터를 유지 해야 합니다.  
  
  빌드 및 비 빌드 관련된 데이터를 유지 하는 방법에 대 한 자세한 내용은 참조 하세요. [MSBuild 프로젝트 파일의 데이터 유지](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)합니다.  
  
## <a name="saving-and-retrieving-build-related-data"></a>관련 데이터를 저장 하 고 빌드를 검색 합니다.  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>프로젝트 파일에서 데이터 관련 빌드를 저장 하려면  
  
- 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 프로젝트 파일의 전체 경로 저장 하는 방법입니다.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>빌드를 검색할 프로젝트 파일에서 데이터를 관련  
  
- 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> 프로젝트 파일의 전체 경로 검색 하는 방법입니다.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="saving-and-retrieving-non-build-related-data"></a>저장 및 검색 되지 않은 빌드 관련된 데이터  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>저장 되지 않은 빌드 관련 프로젝트 파일의 데이터  
  
1. 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> XML 조각을 마지막으로 변경 되었는지 여부를 결정 하는 메서드는 현재 파일에 저장 합니다.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2. 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> 프로젝트 파일에 XML 데이터를 저장 하는 방법입니다.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>프로젝트 파일에서 비 빌드 관련된 데이터를 검색 하려면  
  
1. 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> 프로젝트 확장 속성 및 기타 빌드에 관계 없이 데이터를 초기화 하는 방법입니다. 이 메서드는 프로젝트 파일에 있는 XML 구성 데이터가 없는 경우에 호출 됩니다.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2. 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> 프로젝트 파일에서 XML 데이터를 로드 하는 방법입니다.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
> 이 항목에서 제공 하는 모든 코드 예제는 보다 큰 예의 일부 [VSSDK 샘플](../misc/vssdk-samples.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [MSBuild 프로젝트 파일의 데이터 유지](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
