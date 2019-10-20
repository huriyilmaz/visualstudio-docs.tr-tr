---
title: Silme davranışını özelleştirme | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d0dcfc5724e87d57d2803b9b64a6eb121314b99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655039"
---
# <a name="customizing-deletion-behavior"></a>Silme Davranışını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir öğeyi silmek genellikle ilgili öğelerin de silinmesine neden olur. Kendisine bağlı tüm ilişkiler ve tüm alt öğeler silinir. Bu davranış, *Delete yayma*olarak adlandırılır. Ek ilgili öğelerin silindiğini düzenlemek için, silme yaymayı özelleştirebilirsiniz. Program kodunu yazarak, silme yayılımını modelin durumuna bağlı hale getirebilirsiniz. Ayrıca, silmeye yanıt olarak başka değişikliklerin oluşmasına de neden olabilirsiniz.

 Bu konu aşağıdaki bölümleri içermektedir:

- [Varsayılan silme davranışı](#default)

- [Bir rolün silmeyi yay seçeneğini ayarlama](#property)

- [Silme kapanışını geçersiz kılma](#closure) – silmenin komşu öğelerin silinmesine neden olabileceği bu tekniği kullanın.

- [Onsilinmeye ve OnDeleted kullanarak](#ondeleting) , yanıtın içinde veya dışında bir değeri güncelleştirmek gibi diğer eylemleri içerebilen bu yöntemleri kullanın.

- [Silme kuralları](#rules) – mağaza içindeki her türlü güncelleştirmeyi yayan bir değişikliğin başkalarına neden olabileceği, kuralları kullanın.

- [Olayları silme](#rules) : mağaza dışındaki güncelleştirmeleri, örneğin diğer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belgelerine yaymak için mağaza olaylarını kullanın.

- [Ayır](#unmerge) – bir alt öğe üst öğesine eklenen birleştirme işlemini geri almak için bölme işlemini kullanın.

## <a name="default"></a>Varsayılan silme davranışı
 Varsayılan olarak, aşağıdaki kurallar silme yayılmasını yönetir:

- Bir öğe silinirse, tüm katıştırılmış öğeler de silinir. Katıştırılmış öğeler, bu öğe için kaynak olan ilişki katıştırma hedefleri olan olanlardır. Örneğin, **albüme** **şarkının**bulunduğu bir katıştırma ilişkisi varsa, belirli bir albüm silindiğinde, tüm şarkıları de silinir.

     Bunun aksine, bir şarkıyı silmek albümü silmez.

- Varsayılan olarak, silme işlemi başvuru ilişkileri üzerinde yayılmaz. **Albümünden** **sanatçıya**bir **başvuru ilişkisi varsa** , albümün silinmesi ilgili sanatçının hiçbirini silmez ve bir sanatçının silinmesi herhangi bir albümü silmez.

     Ancak, silme bazı yerleşik ilişkiler için de yayılır. Örneğin, bir model öğesi silindiğinde, diyagramdaki şekli de silinir. Öğe ve şekil `PresentationViewsSubject` başvuru ilişkisi ile ilgilidir.

- Kaynak veya hedef rolde, öğesine bağlı her ilişki silinir. Ters roldeki öğenin rol özelliği artık silinmiş öğeyi içermiyor.

## <a name="property"></a>Bir rolün silmeyi yay seçeneğini ayarlama
 Silmeye bir başvuru ilişkisi veya gömülü bir alt öğe üzerinden yaymasına neden olabilirsiniz.

#### <a name="to-set-delete-propagation"></a>Silme yayılmasını ayarlamak için

1. DSL tanımı diyagramında, yayma işlemini silmek istediğiniz *rolü* seçin. Rol, bir etki alanı ilişkisi kutusunun sol veya sağ tarafındaki satırla temsil edilir.

    Örneğin, bir albümün her silindiğinde, ilgili sanatçıların da silindiği, ardından etki alanı sınıfı sanatçıya bağlı rolü seçmektir.

2. Özellikler penceresi, **yayar Delete** özelliğini ayarlayın.

3. F5 tuşuna basın ve şunları doğrulayın:

   - Bu ilişkinin bir örneği silindiğinde, seçilen roldeki öğe de silinir.

   - Ters roldeki bir öğe silindiğinde, bu ilişkinin örnekleri silinir ve bu roldeki ilgili öğeler silinir.

   Ayrıca **DSL ayrıntıları** penceresinde, **silme seçeneğini yayar** ' i de görebilirsiniz. Bir etki alanı sınıfı seçin ve DSL ayrıntıları penceresinde pencerenin yanındaki düğmeye tıklayarak **davranış silme** sayfasını açın. **Yay** seçeneği, her ilişkinin karşıt rolü için gösterilir. **Stil Sil** sütunu, **yayma** seçeneğinin varsayılan ayarında olup olmadığını gösterir, ancak herhangi bir ayrı etkiye sahip değildir.

## <a name="delete-propagation-by-using-program-code"></a>Program kodunu kullanarak yayılmayı Sil
 DSL tanımı dosyasındaki seçenekler yalnızca silme işleminin hemen bir komşuyla yayıp yaymayacağını seçmenizi sağlar. Daha karmaşık bir Delete yayma şeması uygulamak için program kodu yazabilirsiniz.

> [!NOTE]
> DSL tanımınıza program kodu eklemek için **DSL** projesinde ayrı bir kod dosyası oluşturun ve oluşturulan kod klasöründeki sınıfları genişletmek için kısmi tanımlar yazın. Daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="closure"></a>Silme kapanışı tanımlama
 Silme işlemi, bir başlangıç seçimi verildiğinde hangi öğelerin silineceğini belirleyen, kendi _modelli_**deletekapanış** sınıfını kullanır. @No__t_0 çağırır ve sürekli `ShouldVisitRolePlayer()` ilişkilerin grafiğini yürütir. Bu yöntemleri geçersiz kılabilirsiniz. ShouldVisitRolePlayer bir bağlantının kimliği ve bağlantının rollerinin birindeki öğe ile birlikte verilir. Aşağıdaki değerlerden birini döndürmelidir:

- **VisitorFilterResult. Yes**– öğenin diğer bağlantılarını denemek için, öğe silinmeli ve denetçisi devam etmelidir.

- **VisitorFilterResult. Donotcde** : başka bir sorgu silinmemelidir, bu öğe silinmemelidir.

- **VisitorFilterResult. asla** – başka bir sorgu **Evet**yanıt olsa bile öğe silinmemelidir ve denetçisi öğenin diğer bağlantılarını denememelidir.

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

 Kapanış tekniği, silme işlemi başlamadan önce, silinecek öğe ve bağlantıların kümesinin belirlendiğini sağlar. Bu denetçisi, kapasitenizin sonuçlarını modelin diğer bölümlerinden de birleştirir.

 Ancak, yöntem, silmenin yalnızca ilişkilerin grafiğinde bulunan komşuları etkilediğini kabul eder: modelin başka bir bölümündeki bir öğeyi silmek için bu yöntemi kullanamazsınız. Bir silmeye yanıt olarak öğe eklemek veya başka değişiklikler yapmak istiyorsanız bunu kullanamazsınız.

## <a name="ondeleting"></a>Onsilinmeye ve OnDeleted kullanma
 @No__t_0 veya `OnDeleted()` bir etki alanı sınıfında ya da bir etki alanı ilişkisinde geçersiz kılabilirsiniz.

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A>, bir öğe silinmek üzereyken çağrılır, ancak ilişkilerin bağlantısı kesilmeyecektir. Hala diğer öğelere ve bu öğeden gezinilebilir ve hala `store.ElementDirectory`.

    Aynı anda birkaç öğe silinirse, silme işlemleri yapılmadan önce bunların hepsi için OnDeleted çağırılır.

    `IsDeleting` true.

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A>, öğe silindiğinde çağrılır. Gerektiğinde geri alma işlemi gerçekleştirilebileceği, ancak diğer öğelerden bağlantısı kesildiğinde ve `store.ElementDirectory` kaldırıldıktan sonra, CLR yığınında kalır. İlişkiler için roller hala eski rol oynatıcılara başvurur. `IsDeleted` doğru.

3. Kullanıcı bir öğe oluşturduktan sonra geri al çağrıldığında ve önceki bir silme tekrarlandığında yinelendiğinde Onsilinmeye ve OnDeleted çağrılır. Bu durumlarda mağaza öğelerinin güncelleştirilmesini önlemek için `this.Store.InUndoRedoOrRollback` kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: modeli güncelleştirmek Için Işlemleri kullanma](../modeling/how-to-use-transactions-to-update-the-model.md).

   Örneğin, aşağıdaki kod, son alt şarkının silindiği zaman bir albümü siler:

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

 Bu, hem öğe silindiğinde hem de ilişkinin kendisi silindiği zaman çalıştığı için rol öğesinden farklı olan ilişkinin silinmesinden tetiklenmesi genellikle daha yararlıdır. Bununla birlikte, bir başvuru ilişkisi için, ilgili bir öğe silindiğinde, ilişkinin kendisi silinmediği zaman, silme işlemini yaymak isteyebilirsiniz. Bu örnek, son katkıda bulunan sanatçı silindiğinde bir albümü siler, ancak ilişkiler silinirse yanıt vermez:

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

 Bir öğe üzerinde <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> gerçekleştirdiğinizde OnDeleted ve OnDeleted çağrılır. Bu yöntemler her zaman satır içi yapılır – bu, gerçek silme işleminden hemen önce ve sonra yapılır. Kodunuz iki veya daha fazla öğeyi silerse, OnDelete ve OnDeleted öğelerinin tümünde sırayla çağrılabilir.

## <a name="rules"></a>Silme kuralları ve olayları
 OnDelete işleyicilerine alternatif olarak, silme kurallarını ve silme olaylarını tanımlayabilirsiniz.

1. Kuralları **silme** ve **silme** işlemleri yalnızca bir Işlemde tetiklenir, geri alma veya yineleme içinde değildir. Bu, silmenin gerçekleştirildiği işlemin sonunda yürütülecek şekilde kuyruğa alınmış olarak ayarlayabilirsiniz. Kuralların silinmesi, kuyruktaki tüm silinen kuralların önüne her zaman yürütülür.

     İlişkiler, diyagram öğeleri ve özellikleri dahil olmak üzere yalnızca depodaki öğeleri etkileyen değişiklikleri yaymak için kuralları kullanın. Genellikle, silme işleminin yayılması için bir silme kuralı kullanılır ve değiştirme öğelerini ve ilişkileri oluşturmak için bir silme kuralı kullanılır.

     Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

2. **Silinen** depo olayı bir işlemin sonunda çağrılır ve geri alma veya yineleme sonrasında çağırılır. Bu nedenle, silme işlemleri dosyalar, veritabanı girişleri veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diğer nesneler gibi mağaza dışındaki nesnelere yayılır.

     Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    > Bir öğe silindiğinde, kendi etki alanı özellik değerlerine erişebilirsiniz ancak ilişki bağlantılarında gezinmezsiniz. Ancak, bir ilişkide silinen bir olay ayarlarsanız, rol oyuncuları olan iki öğeye de erişebilirsiniz. Bu nedenle, bir model öğesinin silinmesine yanıt vermek, ancak bağlandığı bir öğeye erişmek istiyorsanız, model öğesinin etki alanı sınıfı yerine ilişkisinde bir Delete olayı ayarlayın.

### <a name="example-deletion-rules"></a>Örnek silme kuralları

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

### <a name="example-deleted-event"></a>Örnek silinen olay

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

## <a name="unmerge"></a>Hücreleri ayır
 Bir alt öğeyi üst öğesine ekleyen işlem *merge*olarak adlandırılır. Araç kutusundan yeni bir öğe veya öğe grubu oluşturulduğunda ya da modelin başka bir kısmından taşındığında veya Panodan kopyalandığında gerçekleşir. Ayrıca, üst ve yeni alt öğesi arasında bir katıştırma ilişkisi oluştururken, birleştirme işlemi ek ilişkiler de ayarlayabilir, yardımcı öğeler oluşturabilir ve öğelerinde özellik değerlerini ayarlayabilir. Birleştirme işlemi bir öğe birleştirme yönergesinde (EMD) kapsüllenir.

 Bir EMD, tamamlayıcı *bölme* veya `MergeDisconnect` işlemini de kapsar. Birleştirme kullanılarak oluşturulmuş bir öğe kümeniz varsa, geri kalan öğeleri tutarlı bir durumda bırakmak isterseniz, ilişkili ayrıldığınızda bir öğeyi kaldırmak için kullanılması önerilir. Bölme işlemi genellikle önceki bölümlerde açıklanan teknikleri kullanır.

 Daha fazla bilgi için bkz. [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md) [öğe oluşturma ve](../modeling/customizing-element-creation-and-movement.md) [bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
