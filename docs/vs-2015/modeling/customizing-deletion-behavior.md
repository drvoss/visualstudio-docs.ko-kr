---
title: 삭제 동작 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa7db2f55a89bd6c542bff0cf30ee058e339f15c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433284"
---
# <a name="customizing-deletion-behavior"></a>삭제 동작 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일반적으로 요소를 삭제하면 관련 요소도 삭제됩니다. 해당 요소에 연결된 모든 관계와 모든 자식 요소도 삭제됩니다. 이 동작은 라고 *삭제 전파*합니다. 예를 들어 삭제 전파를 사용자 지정하여 추가 관련 요소도 삭제되도록 지정할 수 있습니다. 프로그램 코드를 작성하면 모델 상태에 따라 삭제 전파가 수행되도록 지정할 수 있습니다. 또한 삭제에 응답하여 다른 변경도 수행되도록 할 수 있습니다.  
  
 이 항목에는 다음 단원이 포함되어 있습니다.  
  
- [기본 삭제 동작](#default)  
  
- [역할의 삭제 전파 옵션 설정](#property)  
  
- [Delete Closure 재정의](#closure) –이 기술을 사용 하 여 인접 요소도 삭제 삭제는 발생할 수 있습니다.  
  
- [OnDeleting 및 OnDeleted 사용](#ondeleting) – 응답 값을 내부 또는 외부 저장소를 업데이트 하는 등 다른 작업에 포함 될 수 있습니다는 이러한 메서드를 사용 합니다.  
  
- [삭제 규칙](#rules) – 하나의 변경 내용을 다른 사람에 게 발생할 수 있습니다 위치 저장소에서 모든 종류의 업데이트를 전파 하려면 규칙을 사용 합니다.  
  
- [Deletion 이벤트](#rules) – 다른 곳으로 예를 들어 store 외부로 업데이트를 전파 하는 데 사용 하 여 저장소 이벤트 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 문서.  
  
- [UnMerge](#unmerge) – 자식 요소를 부모에 연결 하는 병합 작업을 취소 하려면 UnMerge 작업을 사용 합니다.  
  
## <a name="default"></a> 기본 삭제 동작  
 기본적으로 삭제 전파를 규정하는 규칙은 다음과 같습니다.  
  
- 요소를 삭제하면 포함된 요소도 모두 삭제됩니다. 포함된 요소는 이 요소가 소스인 포함 관계의 대상인 요소입니다. 예를 들어에서 포함 관계가 **앨범** 에 **Song**, 특정 앨범 삭제 되 면 모든 노래도 삭제도 됩니다.  
  
     반면 노래 하나를 삭제하는 경우 앨범은 삭제되지 않습니다.  
  
- 기본적으로 참조 관계에서는 삭제가 전파되지 않습니다. 참조 관계가 없으면 **ArtistPlaysOnAlbum** 에서 **앨범** 하 **Artist**, 앨범을 삭제 해도 관련된 아티스트는 삭제 되지 않습니다 및 아티스트를 삭제 하지 않습니다 모든 album을 삭제 합니다.  
  
     그러나 일부 기본 제공 관계에서는 삭제가 전파됩니다. 예를 들어 모델 요소를 삭제하면 다이어그램에서 해당 모양도 삭제됩니다. 요소와 모양은 `PresentationViewsSubject` 참조 관계를 통해 서로 연결되어 있습니다.  
  
- 소스 또는 대상 역할에서 요소에 연결되는 모든 관계는 삭제됩니다. 그러면 반대쪽 역할의 요소 역할 속성은 더 이상 삭제된 요소를 포함하지 않습니다.  
  
## <a name="property"></a> 역할의 삭제 전파 옵션 설정  
 삭제가 참조 관계에서 또는 포함된 자식에서 부모에 전파되도록 지정할 수 있습니다.  
  
#### <a name="to-set-delete-propagation"></a>삭제 전파를 설정하려면  
  
1. DSL 정의 다이어그램에서 선택 합니다 *역할* 를 삭제를 전파 합니다. 역할은 도메인 관계 상자 왼쪽이나 오른쪽의 선으로 표시됩니다.  
  
    예를 들어 앨범을 삭제할 때마다 관련 아티스트도 삭제되도록 지정하려면 Artist 도메인 클래스에 연결된 역할을 선택합니다.  
  
2. 속성 창에서 설정 된 **Propagates Delete** 속성입니다.  
  
3. F5 키를 누르고 다음 사항을 확인합니다.  
  
   - 이 관계의 인스턴스를 삭제하면 선택한 역할의 요소도 삭제됩니다.  
  
   - 반대쪽 역할의 요소를 삭제하면 이 관계 인스턴스가 삭제되며 이 역할에서 관련된 요소도 삭제됩니다.  
  
   확인할 수도 있습니다는 **Propagates Delete** 옵션을 **DSL 정보** 창입니다. 도메인 클래스를 선택 하 고 DSL 세부 정보 창에서 엽니다는 **Delete Behavior** 옆쪽 창에 단추를 클릭 하 여 페이지입니다. 합니다 **전파** 각 관계의 반대 역할에 대 한 옵션이 표시 됩니다. **스타일 삭제** 열에 표시 여부를 합니다 **전파** 옵션 기본 설정 되어 있지만 별도 영향을 주지 없습니다.  
  
## <a name="delete-propagation-by-using-program-code"></a>프로그램 코드를 사용하여 삭제 전파  
 DSL 정의 파일의 옵션을 사용하는 경우 삭제가 바로 인접한 항목으로 전파되는지 여부만을 선택할 수 있습니다. 더 복잡한 삭제 전파 체계를 구현하려는 경우에는 프로그램 코드를 작성하면 됩니다.  
  
> [!NOTE]
> DSL 정의 프로그램 코드를 추가 하려면 별도 코드 파일을 만들 합니다 **Dsl** 프로젝트 및 Generated Code 폴더의 클래스를 보완 하는 partial 정의 작성 합니다. 자세한 내용은 [도메인별 도메인별 언어 사용자 지정 하려면 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)합니다.  
  
## <a name="closure"></a> Delete Closure 정의  
 삭제 작업 클래스를 사용 _YourModel_**DeleteClosure** 초기 선택을 삭제 하려면 요소 결정 합니다. 이 클래스는 `ShouldVisitRelationship()` 및 `ShouldVisitRolePlayer()`를 반복적으로 호출하여 관계 그래프를 단계별로 이동합니다. 이러한 메서드를 재정의할 수 있습니다. ShouldVisitRolePlayer는 링크 역할 중 하나의 요소 및 링크의 ID와 함께 제공되며 다음 값 중 하나를 반환해야 합니다.  
  
- **VisitorFilterResult.Yes**– 요소를 삭제 해야 하며 워커를 계속할지 요소의 다른 링크 합니다.  
  
- **VisitorFilterResult.DoNotCare** – 다른 쿼리를 삭제 해야 응답 하지 않는 한 요소를 삭제 해서는 안 됩니다.  
  
- **VisitorFilterResult.Never** -요소 삭제 해서는 안, 다른 쿼리 대답을 제공 하는 경우에 **예**, 워커 하지 않아야 하 고 요소의 다른 링크 합니다.  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don’t delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we’re interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 Closure 기술을 사용하면 삭제가 시작되기 전에 삭제할 요소 및 링크 집합을 확인할 수 있습니다. 또한 워커는 Closure의 결과와 모델의 다른 부분 결과를 결합합니다.  
  
 그러나 이 기술은 삭제가 관계 그래프의 인접 항목에만 적용된다고 가정합니다. 따라서 이 메서드를 사용해 모델의 다른 부분에 있는 요소를 삭제할 수는 없습니다. 요소를 추가하거나 삭제에 대한 응답으로 다른 변경을 수행하려는 경우에는 이 메서드를 사용할 수 없습니다.  
  
## <a name="ondeleting"></a> OnDeleting 및 OnDeleted 사용  
 도메인 클래스나 도메인 관계에서 `OnDeleting()` 또는 `OnDeleted()`를 재정의할 수 있습니다.  
  
1. 요소를 삭제하려고 하면 해당 관계가 끊기기 전에 <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A>이 호출됩니다. 이 시점에서는 해당 요소와 다른 요소 간에 계속 이동할 수 있으며 해당 요소는 아직 `store.ElementDirectory`에 있습니다.  
  
    여러 요소를 동시에 삭제하는 경우에는 삭제를 수행하기 전에 모든 요소에 대해 OnDeleting이 호출됩니다.  
  
    `IsDeleting`이 true가 됩니다.  
  
2. 요소가 삭제되면 <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A>가 호출됩니다. 삭제된 요소는 필요 시 Undo를 수행할 수 있도록 CLR 힙에 남아 있지만 다른 요소에서 연결이 해제되며 `store.ElementDirectory`에서 제거됩니다. 관계에 대 한 역할은 이전 역할 수행자를 계속 참조 합니다.`IsDeleted` 그렇습니다.  
  
3. 사용자가 요소를 만든 후 Undo를 호출할 때와 Redo에서 이전 삭제를 반복할 때 OnDeleting 및 OnDeleted가 호출됩니다. 이러한 경우 store 요소를 업데이트하지 않으려면 `this.Store.InUndoRedoOrRollback`을 사용합니다. 자세한 내용은 [방법: 트랜잭션을 사용 모델을 업데이트 하 여](../modeling/how-to-use-transactions-to-update-the-model.md)입니다.  
  
   예를 들어 다음 코드는 마지막 자식 Song을 삭제하면 Album을 삭제합니다.  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 삭제는 역할 요소보다 관계 삭제에서 트리거하는 것이 더 유용한 경우가 많습니다. 이 방식은 요소를 삭제할 때와 관계 자체를 삭제할 때 모두 작동하기 때문입니다. 그러나 참조 관계의 경우 관련 요소가 삭제될 때 삭제를 전파하되 관계 자체를 삭제할 때는 전파되지 않도록 하는 것이 좋을 수 있습니다. 이 예에서는 마지막 참여 Artist를 삭제하면 Album을 삭제하되 관계를 삭제할 때는 전파가 응답하지 않도록 설정합니다.  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 요소에 대해 <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A>를 수행하면 OnDeleting 및 OnDeleted가 호출됩니다. 이러한 메서드는 항상 인라인으로, 즉 실제 삭제 직전과 직후에 수행됩니다. 코드가 둘 이상의 요소를 삭제하는 경우에는 모든 요소에 대해 OnDeleting 및 OnDeleted가 번갈아 가며 호출됩니다.  
  
## <a name="rules"></a> 삭제 규칙 및 이벤트  
 OnDelete 처리기를 사용하는 대신 삭제 규칙과 삭제 이벤트를 정의할 수 있습니다.  
  
1. **삭제** 하 고 **삭제** 규칙이 트리거되면만 트랜잭션이 아니라에 실행 취소 또는 다시 실행 합니다. 삭제를 수행하는 트랜잭션 종료 시 이러한 규칙이 실행 대기되도록 설정할 수 있습니다. Deleting 규칙은 항상 큐의 Deleted 규칙보다 먼저 실행됩니다.  
  
     규칙을 사용하면 관계, 다이어그램 요소 및 해당 속성을 포함한 Store의 요소에만 영향을 주는 변경을 전파할 수 있습니다. 일반적으로는 Deleting 규칙을 사용하여 삭제를 전파하고 Delete 규칙을 사용하여 대체 요소 및 관계를 만듭니다.  
  
     자세한 내용은 [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.  
  
2. **삭제** store 이벤트는 트랜잭션이 끝날 때 호출 되 고 실행 취소 또는 다시 실행 한 후 호출 됩니다. 따라서 이 이벤트는 파일, 데이터베이스 항목 또는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 기타 개체와 같은 Store 외부의 개체로 삭제를 전파하는 데 사용할 수 있습니다.  
  
     자세한 내용은 [이벤트 처리기 전파 변경 외부 모델](../modeling/event-handlers-propagate-changes-outside-the-model.md)합니다.  
  
    > [!WARNING]
    > 요소가 삭제된 경우 해당 도메인 속성 값에는 액세스할 수 있지만 관계 링크를 탐색할 수는 없습니다. 그러나 관계에 대해 Deleted 이벤트를 설정한 경우 역할 수행자였던 두 요소에도 액세스할 수 있습니다. 그러므로 모델 요소 삭제에 응답하는 동시에 해당 요소가 연결되어 있었던 요소에 액세스하려면 모델 요소의 도메인 클래스가 아닌 관계에 대해 Delete 이벤트를 설정합니다.  
  
### <a name="example-deletion-rules"></a>예제 삭제 규칙  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### <a name="example-deleted-event"></a>예제 Deleted 이벤트  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
## <a name="unmerge"></a> UnMerge  
 부모 자식 요소를 연결 하는 작업 이라고 *병합*입니다. 새 요소 또는 요소 그룹을 도구 상자에서 만들거나 모델의 다른 부분에서 이동하거나 클립보드에서 복사하면 병합이 수행됩니다. 병합 작업을 수행하면 부모와 새 자식 간에 포함 관계를 작성할 수 있을 뿐 아니라 추가 관계를 설정하고 보조 요소를 만들고 요소에서 속성 값을 설정할 수도 있습니다. 병합 작업은 EMD(Element Merge Directive)에서 캡슐화됩니다.  
  
 Emd는 추가 캡슐화 *unmerge* 또는 `MergeDisconnect` 작업 합니다. merge를 사용하여 생성된 요소 클러스터가 있는 경우 나머지 요소를 일관된 상태로 유지하려면 연결된 unmerge를 사용하여 해당 클러스터에서 요소를 제거하는 것이 좋습니다. unmerge 작업에서는 보통 이전 섹션에서 설명한 기술을 사용합니다.  
  
 자세한 내용은 [사용자 지정 요소 만들기 및 이동](../modeling/customizing-element-creation-and-movement.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)   
 [사용자 지정 요소 만들기 및 이동](../modeling/customizing-element-creation-and-movement.md)   
 [도메인별 언어를 사용자 지정하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
