---
title: Program kodundaki bir modeli gezinme ve güncelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb7c99e345b676576d51c97799cdc7b35f8279ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668517"
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Program Kodunda Modeli Gezinme ve Güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model öğeleri oluşturmak ve silmek, özelliklerini ayarlamak ve öğeler arasında bağlantı oluşturmak ve silmek için kod yazabilirsiniz. Tüm değişikliklerin bir işlem içinde yapılması gerekir. Öğeler bir diyagramda görüntülenirse, diyagram işlemin sonunda otomatik olarak "düzeltildi" olacaktır.

## <a name="in-this-topic"></a>Bu Konu kapsamında
 [Örnek DSL tanımı](#example)

 [Modelde gezinme](#navigation)

 [Sınıf bilgilerine erişme](#metadata)

 [Işlem içinde değişiklikler gerçekleştirme](#transaction)

 [Model öğeleri oluşturma](#elements)

 [Ilişki bağlantıları oluşturma](#links)

 [Öğeleri silme](#deleteelements)

 [Ilişki bağlantıları siliniyor](#deletelinks)

 [Ilişkinin bağlantılarını yeniden sıralama](#reorder)

 [Kaynaktaki](#locks)

 [Kopyala ve Yapıştır](#copy)

 [Diyagramları gezinme ve güncelleştirme](#diagrams)

 [Şekiller ve öğeler arasında gezinme](#views)

 [Şekillerin ve bağlayıcıların özellikleri](#shapeProperties)

 [DocView ve DocData](#docdata)

 Şekiller, bağlayıcılar ve diyagramlar ve model öğeleriyle ilişkileri ayrı bir konuda açıklanmıştır. Daha fazla bilgi için bkz. [nasıl yapılır: diyagramda gezinme ve güncelleştirme](../misc/how-to-navigate-and-update-a-diagram.md).

## <a name="example"></a>Örnek DSL tanımı
 Bu, bu konudaki örneklerde DslDefinition. dsl 'nin ana bölümüdür:

 ![DSL tanımı diyagramı &#45; aile ağacı modeli](../modeling/media/familyt-person.png "FamilyT_Person")

 Bu model, bu DSL 'nin bir örneğidir:

 ![Tuçi aile ağacı modeli](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

### <a name="references-and-namespaces"></a>Başvurular ve ad alanları
 Bu konudaki kodu çalıştırmak için şu başvuruya sahip olmalısınız:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Kodunuz bu ad alanını kullanacak:

 `using Microsoft.VisualStudio.Modeling;`

 Ayrıca, bir kodu DSL 'nin tanımlandığı bir projeden farklı bir projede yazıyorsanız DSL projesi tarafından oluşturulan derlemeyi içeri aktarmanız gerekir.

## <a name="navigation"></a>Modelde gezinme

### <a name="properties"></a>Özellikler
 DSL tanımında tanımladığınız etki alanı özellikleri, program kodunda erişebileceğiniz Özellikler olur:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Bir özellik ayarlamak isterseniz, bunu bir [işlemin](#transaction)içinde yapmanız gerekir:

 `henry.Name = "Henry VIII";`

 DSL tanımında bir özelliğin **türü** **hesaplanıyorsa**, ayarlanamaz. Daha fazla bilgi için bkz. [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>İlişkiler
 DSL tanımında tanımladığınız etki alanı ilişkileri, ilişkinin her ucunda bir sınıf olmak üzere özellik çiftleri haline gelir. Özelliklerin adları DslDefinition diyagramında ilişkinin her tarafındaki rollerin etiketleri olarak görünür. Rolün çoğuluna bağlı olarak, özelliğin türü ilişkinin diğer sonundaki sınıf veya bu sınıfın bir koleksiyonu olur.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Bir ilişkinin ters uçlarından özellikler her zaman karşılıklıdır. Bir bağlantı oluşturulduğunda veya silindiğinde, her iki öğe üzerindeki rol özellikleri güncelleştirilir. Aşağıdaki ifade (`System.Linq` uzantılarını kullanır) örnekteki ParentsHaveChildren ilişkisinde her zaman doğrudur:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. İlişki Ayrıca, etki alanı ilişki türünün bir örneği olan *bağlantı*adlı model öğesiyle temsil edilir. Bağlantının her zaman bir kaynak öğesi ve bir hedef öğesi vardır. Kaynak öğe ve hedef öğe aynı olabilir.

 Bir bağlantıya ve özelliklerine erişebilirsiniz:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Varsayılan olarak, bir ilişkinin birden fazla örneğinin herhangi bir çift model öğesi bağlantı yapmasına izin verilmez. Ancak DSL tanımında, ilişki için `Allow Duplicates` bayrağı true ise, birden fazla bağlantı olabilir ve `GetLinks` kullanmanız gerekir:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Bağlantılara erişim için de başka yöntemler de vardır. Örneğin:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Gizli roller.** DSL tanımında, **oluşturulan özellik** belirli bir rol için **false** ise, bu role karşılık gelen bir özellik oluşturulmaz. Ancak, bağlantılara erişmeye devam edebilir ve ilişkinin yöntemlerini kullanarak bağlantıları çapraz geçiş yapabilirsiniz:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 En sık kullanılan örnek, bir model öğesini diyagramda görüntüleyen şekle bağlayan <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> ilişkidir:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Öğe dizini
 Öğe dizinini kullanarak depodaki tüm öğelere erişebilirsiniz:

 `store.ElementDirectory.AllElements`

 Ayrıca, aşağıdaki gibi öğeleri bulmak için yöntemler de vardır:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="metadata"></a>Sınıf bilgilerine erişme
 Sınıflar, ilişkiler ve DSL tanımının diğer yönleri hakkında bilgi edinebilirsiniz. Örneğin:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Model öğelerinin üst sınıfları aşağıdaki gibidir:

- ModelElement-tüm öğeler ve ilişkiler ModelElements

- ElementLink-tüm ilişkiler ElementLinks

## <a name="transaction"></a>Işlem içinde değişiklikler gerçekleştirme
 Program kodunuz depodaki her şeyi değiştirdiğinde, bunun bir işlemin içinde olması gerekir. Bu, tüm model öğeleri, ilişkiler, şekiller, diyagramlar ve özellikleri için geçerlidir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Bir işlemi yönetmenin en kullanışlı yöntemi, `try...catch` bildiriminde yer aldığı `using` deyimidir:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Bir işlem içinde istediğiniz sayıda değişiklik yapabilirsiniz. Yeni işlemleri etkin bir işlem içinde açabilirsiniz.

 Değişikliklerinizi kalıcı hale getirmek için, işlem atılmadan önce işlemi `Commit` gerekir. İşlem içinde yakalanamayan bir özel durum oluşursa, depo, değişikliklerden önce durumuna sıfırlanır.

## <a name="elements"></a>Model öğeleri oluşturma
 Bu örnek, var olan bir modele bir öğesi ekler:

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Bu örnek, bir öğe oluşturma hakkında bu temel noktaları gösterir:

- Yeni öğeyi deponun belirli bir bölümünde oluşturun. Model öğeleri ve ilişkileri için, ancak şekillerin değil, bu genellikle varsayılan bölümdür.

- Bir katıştırma ilişkisinin hedefini yapın. Bu örneğin DslDefinition ' da, her birinin FamilyTreeHasPeople ilişki ekleme hedefi olması gerekir. Bunu başarmak için, kişi nesnesinin FamilyTreeModel rol özelliğini ayarlayabilir ya da kişiyi FamilyTreeModel nesnesinin kişiler rolü özelliğine ekleyebilirsiniz.

- Yeni bir öğenin özelliklerini, özellikle de `IsName`, DslDefinition içinde doğru olan özelliği ayarlayın. Bu bayrak, öğesini sahibi içinde benzersiz olarak tanımlamak için hizmet veren özelliği işaretler. Bu durumda, Name özelliği o bayrağa sahiptir.

- Bu DSL 'nin DSL tanımı depoya yüklenmiş olmalıdır. Bir menü komutu gibi bir uzantı yazıyorsanız, bu genellikle zaten doğru olur. Diğer durumlarda, modeli depoya açık bir şekilde yükleyebilir veya [ModelBus](/previous-versions/ee904639(v=vs.140)) 'ı kullanarak yükleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: program kodunda dosyadan model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Bu şekilde bir öğe oluşturduğunuzda, bir şekil otomatik olarak oluşturulur (DSL bir diyagramı varsa). Varsayılan şekil, renk ve diğer özelliklerle otomatik olarak atanmış bir konumda görüntülenir. İlişkili şeklin nerede ve nasıl göründüğünü denetlemek istiyorsanız, bkz. [bir öğe ve şekli oluşturma](#merge).

## <a name="links"></a>Ilişki bağlantıları oluşturma
 Örnek DSL tanımında tanımlanmış iki ilişki vardır. Her ilişki, ilişkinin her ucundaki sınıfta bir *rol özelliğini* tanımlar.

 Bir ilişkinin örneğini oluşturabileceğiniz üç yol vardır. Bu üç yöntemin her biri aynı etkiye sahiptir:

- Kaynak rol oyuncusunun özelliğini ayarlayın. Örneğin:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Hedef rol oyuncusunun özelliğini ayarlayın. Örneğin:

  - `edward.familyTreeModel = familyTree;`

       Bu rolün çoğulluğu `1..1`, bu nedenle değeri atadık.

  - `henry.Children.Add(edward);`

       Bu rolün çoğulluğu `0..*`, bu nedenle koleksiyona ekliyoruz.

- İlişkinin bir örneğini açıkça oluşturun. Örneğin:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Son yöntem, ilişkinin kendisi üzerinde özellikler ayarlamak istiyorsanız yararlıdır.

  Bu şekilde bir öğe oluşturduğunuzda, diyagramdaki bir bağlayıcı otomatik olarak oluşturulur, ancak varsayılan bir şekil, renk ve diğer özelliklere sahiptir. İlişkili bağlayıcının nasıl oluşturulduğunu denetlemek için, bkz. [bir öğe ve şekli oluşturma](#merge).

## <a name="deleteelements"></a>Öğeleri silme
 @No__t_0 çağırarak bir öğeyi silin:

 `henry.Delete();`

 Bu işlem de silinecek:

- Öğesinden ve öğeden bağlantı bağlantıları. Örneğin, `edward.Parents` artık `henry` içermez.

- Rollerdeki `PropagatesDelete` bayrak değeri true olan öğeler. Örneğin, öğesini görüntüleyen şekil silinir.

  Varsayılan olarak, her katıştırma ilişkisi hedef rolde doğru `PropagatesDelete`. @No__t_0 silmek `familyTree` silmez, ancak `familyTree.Delete()` tüm `Persons` silecektir. Daha fazla bilgi için bkz. [silme davranışını özelleştirme](../modeling/customizing-deletion-behavior.md).

  Varsayılan olarak, başvuru ilişkilerinin rolleri için `PropagatesDelete` true değildir.

  Bir nesneyi sildiğinizde silme kurallarının belirli yayılmaları yok saymasına neden olabilirsiniz. Bu, bir öğeyi başka bir öğe için değiştirirken yararlıdır. Silmenin yayılmaması gereken bir veya daha fazla rolün GUID 'sini sağlarsınız. GUID ilişki sınıfından elde edilebilir:

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  (Bu belirli örnekte hiçbir etkisi olmaz çünkü `PropagatesDelete`, `ParentsHaveChildren` ilişkisinin rolleri için `false`.)

  Bazı durumlarda, silme işlemi veya öğe üzerinde ya da yayma tarafından silinecek bir öğe üzerinde bir kilit var. Öğenin silinip silinemeyeceğini denetlemek için `element.CanDelete()` kullanabilirsiniz.

## <a name="deletelinks"></a>Ilişki bağlantıları siliniyor
 Rol özelliğinden bir öğe kaldırarak ilişki bağlantısını silebilirsiniz:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Bağlantıyı açıkça de silebilirsiniz:

 `edwardHenryLink.Delete();`

 Bu üç yöntemin hepsi aynı etkiye sahiptir. Yalnızca birini kullanmanız yeterlidir.

 Rolün 0.. 1 veya 1.. 1 çokluğu varsa, bunu `null` veya başka bir değere ayarlayabilirsiniz:

 `edward.FamilyTreeModel = null;`//veya:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="reorder"></a>Ilişkinin bağlantılarını yeniden sıralama
 Belirli bir model öğesinde kaynağı oluşturulan veya hedeflenen belirli bir ilişkinin bağlantılarının belirli bir sırası vardır. Bunlar eklendikleri sırada görünürler. Örneğin, bu ifade her zaman alt öğeleri aynı sırada verir:

 `foreach (Person child in henry.Children) ...`

 Bağlantıların sırasını değiştirebilirsiniz:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a>Kaynaktaki
 Değişiklikleriniz bir kilit ile engellenebilir. Kilitler tek tek öğeler üzerinde, bölümlerde ve depoda ayarlanabilir. Bu düzeylerin herhangi birinde, yapmak istediğiniz değişiklik türünü önleyen bir kilit varsa, bunu denediğinizde bir özel durum oluşturulabilir. Kilitleri öğesi kullanarak ayarlanmış olup olmadığını keşfedebilirsiniz. Ad alanında tanımlanan bir genişletme yöntemi olan Getkilitler () <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Daha fazla bilgi için bkz. [salt okuma kesimleri oluşturmak Için kilitleme Ilkesi tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy"></a>Kopyala ve Yapıştır
 Öğeleri veya öğe gruplarını bir <xref:System.Windows.Forms.IDataObject> kopyalayabilirsiniz:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Öğeler serileştirilmiş bir öğe grubu olarak depolanır.

 Bir IDataObject 'den öğeleri bir modele birleştirebilirsiniz:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()`, bir `PresentationElement` ya da `ModelElement` kabul edebilir. Buna bir `PresentationElement` verirseniz, hedef diyagramda bir konumu üçüncü parametre olarak da belirtebilirsiniz.

## <a name="diagrams"></a>Diyagramları gezinme ve güncelleştirme
 Bir DSL 'de, kişi veya şarkı gibi bir kavramı temsil eden etki alanı model öğesi, diyagramda gördüklerinizi temsil eden şekil öğesinden ayrıdır. Etki alanı model öğesi kavramların önemli özelliklerini ve ilişkilerini depolar. Shape öğesi, nesne görünümünün boyutunu, konumunu ve rengini diyagramda ve bileşen bölümlerinin düzenine depolar.

### <a name="presentation-elements"></a>Sunum öğeleri
 ![Taban şeklinin ve öğe türlerinin sınıf diyagramı](../modeling/media/dslshapesandelements.png "Dslşekillere Andelements")

 DSL tanımınızda, belirttiğiniz her öğe aşağıdaki standart sınıfların birinden türetilmiş bir sınıf oluşturur.

|Öğe türü|Temel sınıf|
|---------------------|----------------|
|Alan sınıfı|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Etki alanı ilişkisi|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Şekil|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Bağlayıcı|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diyagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Diyagramdaki bir öğe genellikle bir model öğesini temsil eder. Genellikle, bir <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> bir etki alanı sınıfı örneğini temsil eder ve bir <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> bir etki alanı ilişki örneğini temsil eder. @No__t_0 ilişkisi bir düğümü veya bağlantı şeklini temsil ettiği model öğesine bağlar.

 Her düğüm veya bağlantı şekli bir diyagrama aittir. İkili bağlantı şekli iki düğüm şeklini birbirine bağlar.

 Şekillerin iki küme içinde alt şekilleri olabilir. @No__t_0 kümesindeki bir şekil, üst öğesinin sınırlayıcı kutusuyla sınırlandırıyor. @No__t_0 listesindeki bir şekil, üst öğenin sınırları dışında veya kısmen dışında görünebilir (örneğin, bir etiket veya bağlantı noktası). Diyagramda `RelativeChildShapes` yok ve `Parent` yok.

### <a name="views"></a>Şekiller ve öğeler arasında gezinme
 Etki alanı modeli öğeleri ve Şekil öğeleri <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> ilişki ile ilgilidir.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Aynı ilişki, diyagramdaki bağlayıcılar ile ilişkilerini bağlar:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Bu ilişki Ayrıca modelin kökünü diyagrama bağlar:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Bir şekle göre temsil edilen model öğesini almak için şunu kullanın:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Diyagram çevresinde gezinme
 Genel olarak, diyagramdaki şekiller ve bağlayıcılar arasında gezinmek önerilmez. Modeldeki ilişkilerde gezinmek, yalnızca diyagramın görünümü üzerinde çalışmak gerektiğinde şekiller ve bağlayıcılar arasında hareket etmek daha iyidir. Bu yöntemler bağlayıcıları her uçtaki şekillere bağlar:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Birçok şekil Birleşik siteler; Bunlar bir üst şekilden ve alt öğelerin bir veya daha fazla katmanlarından oluşur. Başka bir şekle göre konumlandırılmış şekillerin *alt öğesi*olduğu söylenir. Üst Şekil taşındığında, alt öğeler onunla birlikte taşınır.

 *Göreli alt öğeler* , üst şeklin sınırlayıcı kutusunun dışında görünebilir. *Iç Içe yerleştirilmiş* alt öğeler tamamen üst öğenin sınırları içinde görünür.

 Diyagramdaki en üstteki şekil kümesini almak için şunu kullanın:

 `Diagram.NestedChildShapes`

 Şekillerin ve bağlayıcıların üst sınıfları şunlardır:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *şeklim*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *Bağlayıcısı*

### <a name="shapeProperties"></a>Şekillerin ve bağlayıcıların özellikleri
 Çoğu durumda, şekillere açık değişiklikler yapmak gerekli değildir. Model öğelerini değiştirdiğiniz zaman, "çözümü temizle" kuralları şekilleri ve bağlayıcıları güncelleştirir. Daha fazla bilgi için bkz. [değişiklikleri yanıtlama ve yayma](../modeling/responding-to-and-propagating-changes.md).

 Ancak, model öğelerinden bağımsız özelliklerde yer alan şekillerdeki bazı açık değişiklikler yapmak yararlı olur. Örneğin, bu özellikleri değiştirebilirsiniz:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-şeklin yüksekliğini ve genişliğini belirler.

- üst şekle veya diyagrama göre <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> konumu

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-şekil veya bağlayıcıyı çizmek için kullanılan kalemler ve fırçalar kümesi

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-şekli görünmez hale getirir

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-şekli bir `Hide()` sonra görünür hale getirir

### <a name="merge"></a>Öğe ve şeklini oluşturma
 Bir öğe oluşturup katıştırma ilişkisi ağacına bağladığınızda, bir şekil otomatik olarak oluşturulur ve onunla ilişkilendirilir. Bu işlem, işlemin sonunda yürütülen "Düzeltme" kuralları tarafından yapılır. Ancak, şekil otomatik olarak atanan bir konumda görünür ve şekli, rengi ve diğer özellikler varsayılan değerlere sahip olur. Şeklin nasıl oluşturulduğunu denetlemek için Merge işlevini kullanabilirsiniz. Önce eklemek istediğiniz öğeleri ElementGroup içine eklemeniz ve sonra grubu diyagram ile birleştirmeniz gerekir.

 Bu yöntem:

- Öğe adı olarak bir özellik atadıysanız, adı ayarlar.

- DSL tanımında belirttiğiniz herhangi bir öğe birleştirme yönergesi sunar.

  Bu örnek, kullanıcı diyagrama çift tıkladığında fare konumunda bir şekil oluşturur. Bu örneğe yönelik DSL tanımında `ExampleShape` `FillColor` özelliği kullanıma sunuldu.

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 Birden fazla şekil sağlarsanız, `AbsoluteBounds` kullanarak onun göreli konumlarını ayarlayın.

 Ayrıca, bu yöntemi kullanarak bağlayıcıların rengini ve diğer sunulma özelliklerini ayarlayabilirsiniz.

### <a name="use-transactions"></a>Işlemleri kullanma
 Şekiller, bağlayıcılar ve diyagramlar, <xref:Microsoft.VisualStudio.Modeling.ModelElement> ve depoda canlı olan alt türler. Bu nedenle, yalnızca bir işlemin içinde değişiklikler yapmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: modeli güncelleştirmek Için Işlemleri kullanma](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="docdata"></a>Belge görünümü ve belge verileri
 ![Standart diyagram türlerinin sınıf diyagramı](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")

## <a name="store-partitions"></a>Depolama bölümleri
 Bir model yüklendiğinde, eşlik eden diyagram aynı anda yüklenir. Genellikle, model Store. DefaultPartition içine yüklenir ve Diyagram içeriği başka bir bölüme yüklenir. Genellikle, her bölümün içeriği yüklenir ve ayrı bir dosyaya kaydedilir.

## <a name="see-also"></a>Ayrıca Bkz.
 etki alanına özgü [dilden kod oluşturan](../modeling/generating-code-from-a-domain-specific-language.md) , etki alanına [özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md) <xref:Microsoft.VisualStudio.Modeling.ModelElement> nasıl yapılır: [Visual Studio ModelBus yanıt verme kullanarak model tümleştirme modellerini](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [güncelleştirmek için işlemleri kullanma](../modeling/how-to-use-transactions-to-update-the-model.md) [ve Değişiklikler yayılıyor](../modeling/responding-to-and-propagating-changes.md)
