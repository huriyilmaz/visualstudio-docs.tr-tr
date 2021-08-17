---
title: Program Kodunda Modeli Gezinme ve Güncelleştirme
description: Model öğeleri oluşturmak ve silmek, özelliklerini ayarlamak ve öğeler arasında bağlantı oluşturmak ve silmek için nasıl kod yazabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cfe92dbaab0e952f6e46f3ca5fd6d877717dfa44d6eaa20a821275f338a17be4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398306"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Program Kodunda Modelde Gezinme ve Modeli Güncelleştirme

Model öğeleri oluşturmak ve silmek, özelliklerini ayarlamak ve öğeler arasında bağlantı oluşturmak ve silmek için kod yazabilirsiniz. Tüm değişikliklerin bir işlem içinde yapılması gerekir. Öğeler bir diyagramda görüntülenirse, diyagram işlemin sonunda otomatik olarak "düzeltildi" olacaktır.

## <a name="an-example-dsl-definition"></a><a name="example"></a> Örnek DSL tanımı
 Bu, bu konudaki örneklerde DslDefinition. dsl 'nin ana bölümüdür:

 ![DSL tanımı diyagramı &#45; aile ağacı modeli](../modeling/media/familyt_person.png)

 Bu model, bu DSL 'nin bir örneğidir:

 ![Tuçi aile ağacı modeli](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Başvurular ve ad alanları
 Bu konudaki kodu çalıştırmak için şu başvuruya sahip olmalısınız:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Kodunuz bu ad alanını kullanacak:

 `using Microsoft.VisualStudio.Modeling;`

 Ayrıca, bir kodu DSL 'nin tanımlandığı bir projeden farklı bir projede yazıyorsanız DSL projesi tarafından oluşturulan derlemeyi içeri aktarmanız gerekir.

## <a name="navigating-the-model"></a><a name="navigation"></a> Modelde gezinme

### <a name="properties"></a>Özellikler
 DSL tanımında tanımladığınız etki alanı özellikleri, program kodunda erişebileceğiniz Özellikler olur:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Bir özellik ayarlamak isterseniz, bunu bir [işlemin](#transaction)içinde yapmanız gerekir:

 `henry.Name = "Henry VIII";`

 DSL tanımında bir özelliğin **türü** **hesaplanıyorsa**, ayarlanamaz. daha fazla bilgi için bkz. [hesaplanan ve özel Depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>İlişkiler
 DSL tanımında tanımladığınız etki alanı ilişkileri, ilişkinin her ucunda bir sınıf olmak üzere özellik çiftleri haline gelir. Özelliklerin adları DslDefinition diyagramında ilişkinin her tarafındaki rollerin etiketleri olarak görünür. Rolün çoğuluna bağlı olarak, özelliğin türü ilişkinin diğer sonundaki sınıf veya bu sınıfın bir koleksiyonu olur.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Bir ilişkinin ters uçlarından özellikler her zaman karşılıklıdır. Bir bağlantı oluşturulduğunda veya silindiğinde, her iki öğe üzerindeki rol özellikleri güncelleştirilir. Aşağıdaki ifade (uzantısını kullanan `System.Linq` ), örnekteki ParentsHaveChildren ilişkisinde her zaman doğrudur:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. İlişki Ayrıca, etki alanı ilişki türünün bir örneği olan *bağlantı* adlı model öğesiyle temsil edilir. Bağlantının her zaman bir kaynak öğesi ve bir hedef öğesi vardır. Kaynak öğe ve hedef öğe aynı olabilir.

 Bir bağlantıya ve özelliklerine erişebilirsiniz:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Varsayılan olarak, bir ilişkinin birden fazla örneğinin herhangi bir çift model öğesi bağlantı yapmasına izin verilmez. Ancak DSL tanımında, bu, `Allow Duplicates` ilişki için true ise, birden fazla bağlantı olabilir ve şunları kullanmanız gerekir `GetLinks` :

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Bağlantılara erişim için de başka yöntemler de vardır. Örnek:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Gizli roller.** DSL tanımında, **oluşturulan özellik** belirli bir rol için **false** ise, bu role karşılık gelen bir özellik oluşturulmaz. Ancak, bağlantılara erişmeye devam edebilir ve ilişkinin yöntemlerini kullanarak bağlantıları çapraz geçiş yapabilirsiniz:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 En sık kullanılan örnek <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> , bir model öğesini diyagramda görüntüleyen şekle bağlayan ilişkidir:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Öğe dizini
 Öğe dizinini kullanarak depodaki tüm öğelere erişebilirsiniz:

 `store.ElementDirectory.AllElements`

 Ayrıca, aşağıdaki gibi öğeleri bulmak için yöntemler de vardır:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Sınıf bilgilerine erişme
 Sınıflar, ilişkiler ve DSL tanımının diğer yönleri hakkında bilgi edinebilirsiniz. Örnek:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Model öğelerinin üst sınıfları aşağıdaki gibidir:

- ModelElement-tüm öğeler ve ilişkiler ModelElements

- ElementLink-tüm ilişkiler ElementLinks

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> Işlem içinde değişiklikler gerçekleştirme
 Program kodunuz depodaki her şeyi değiştirdiğinde, bunun bir işlemin içinde olması gerekir. Bu, tüm model öğeleri, ilişkiler, şekiller, diyagramlar ve özellikleri için geçerlidir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Bir işlemi yönetmenin en kullanışlı yöntemi, `using` bir bildirimde yer aldığı deyimdir `try...catch` :

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

 Değişikliklerinizi kalıcı hale getirmek için, `Commit` işlem atılmadan önce işlemden önce yapmalısınız. İşlem içinde yakalanamayan bir özel durum oluşursa, depo, değişikliklerden önce durumuna sıfırlanır.

## <a name="creating-model-elements"></a><a name="elements"></a> Model öğeleri oluşturma
 Bu örnek, var olan bir modele bir öğesi ekler:

```csharp
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

- Yeni bir öğenin özelliklerini, özellikle de `IsName` DslDefinition içinde true olan özelliğini ayarlayın. Bu bayrak, öğesini sahibi içinde benzersiz olarak tanımlamak için hizmet veren özelliği işaretler. Bu durumda, Name özelliği o bayrağa sahiptir.

- Bu DSL 'nin DSL tanımı depoya yüklenmiş olmalıdır. Bir menü komutu gibi bir uzantı yazıyorsanız, bu genellikle zaten doğru olur. Diğer durumlarda, modeli depoya açık bir şekilde yükleyebilir veya [ModelBus](/previous-versions/ee904639(v=vs.140)) 'ı kullanarak yükleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: program kodunda dosyadan model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Bu şekilde bir öğe oluşturduğunuzda, bir şekil otomatik olarak oluşturulur (DSL bir diyagramı varsa). Varsayılan şekil, renk ve diğer özelliklerle otomatik olarak atanmış bir konumda görüntülenir. İlişkili şeklin nerede ve nasıl göründüğünü denetlemek istiyorsanız, bkz. [bir öğe ve şekli oluşturma](#merge).

## <a name="creating-relationship-links"></a><a name="links"></a> Ilişki bağlantıları oluşturma
 Örnek DSL tanımında tanımlanmış iki ilişki vardır. Her ilişki, ilişkinin her ucundaki sınıfta bir *rol özelliğini* tanımlar.

 Bir ilişkinin örneğini oluşturabileceğiniz üç yol vardır. Bu üç yöntemin her biri aynı etkiye sahiptir:

- Kaynak rol oyuncusunun özelliğini ayarlayın. Örnek:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Hedef rol oyuncusunun özelliğini ayarlayın. Örnek:

  - `edward.familyTreeModel = familyTree;`

       Bu rolün çoğulluğu olduğundan `1..1` , değeri atadık.

  - `henry.Children.Add(edward);`

       Bu rolün çoğulluğu olduğundan `0..*` , koleksiyona ekliyoruz.

- İlişkinin bir örneğini açıkça oluşturun. Örnek:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Son yöntem, ilişkinin kendisi üzerinde özellikler ayarlamak istiyorsanız yararlıdır.

  Bu şekilde bir öğe oluşturduğunuzda, diyagramdaki bir bağlayıcı otomatik olarak oluşturulur, ancak varsayılan bir şekil, renk ve diğer özelliklere sahiptir. İlişkili bağlayıcının nasıl oluşturulduğunu denetlemek için, bkz. [bir öğe ve şekli oluşturma](#merge).

## <a name="deleting-elements"></a><a name="deleteelements"></a> Öğeleri silme

Şunu çağırarak bir öğe silin `Delete()` :

`henry.Delete();`

Bu işlem de silinecek:

- Öğesinden ve öğeden bağlantı bağlantıları. Örneğin, `edward.Parents` artık içermeyecektir `henry` .

- Rollerdeki ve `PropagatesDelete` bayrağın doğru olduğu öğeler. Örneğin, öğesini görüntüleyen şekil silinir.

Varsayılan olarak, her ekleme ilişkisi `PropagatesDelete` hedef rolde true olur. Silme `henry` işlemi , 'i `familyTree` `familyTree.Delete()` silemez, ancak tüm 'leri `Persons` siler.

Varsayılan `PropagatesDelete` olarak, başvuru ilişkilerinin rolleri için doğru değildir.

Bir nesneyi silerken silme kurallarının belirli yayılmaları atlaymalarını silebilirsiniz. Bir öğeyi başka bir öğeye yazıyorsanız bu yararlı olur. Silme işleminin yayılmayacak bir veya daha fazla rolün GUID'ini sağlarsınız. GUID, ilişki sınıfından elde edilir:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(İlişkinin rolleri için olduğu için bu `PropagatesDelete` örnekte herhangi bir etkisi `false` `ParentsHaveChildren` olmaz.)

Bazı durumlarda silme işlemi, öğede veya yayma ile silinecek bir öğede kilit olmasıyla engellenir. öğesini kullanarak `element.CanDelete()` öğenin silinip siline olmadığını kontrol edin.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> İlişki Bağlantılarını Silme
 Rol özelliğinden bir öğeyi kaldırarak ilişki bağlantısını silebilirsiniz:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Bağlantıyı açıkça da silebilirsiniz:

 `edwardHenryLink.Delete();`

 Bu üç yöntemin hepsi aynı etkiye sahiptir. Bunlardan yalnızca birini kullana ihtiyacınız vardır.

 Rolün 0..1 veya 1..1 çokluğu varsa, rolü olarak veya başka bir `null` değere ayarlayın:

 `edward.FamilyTreeModel = null;` Veya:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> bir İlişkinin Bağlantılarını Yeniden Sıralama
 Belirli bir model öğesinin kaynağı olan veya hedeflenen belirli bir ilişkinin bağlantıları belirli bir diziye sahiptir. Eklenme sırasına göre görünürler. Örneğin, bu deyim her zaman aynı sırada çocukların verimini sağlar:

 `foreach (Person child in henry.Children) ...`

 Bağlantıların sıralamalarını değiştirebilirsiniz:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Kilit
 Değişiklikleriniz kilit tarafından engellenebilir. Kilitler tek tek öğelerde, bölümler üzerinde ve depoda ayar olabilir. Bu düzeylerden herhangi biri, yapmak istediğiniz değişikliği engelleyen bir kilite sahipse, bunu denerken bir özel durum atlenebilir. Öğesini kullanarak kilitlerin ayar olup olmadığını keşfedebilirsiniz. GetLocks()), ad alanı içinde tanımlanan bir uzantı <xref:Microsoft.VisualStudio.Modeling.Immutability> yöntemidir.

 Daha fazla bilgi için, [bkz. Create a Locking Policy to Create Read-Only Segmentleri](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Kopyala ve Yapıştır
 Öğeleri veya öğe gruplarını bir 'a <xref:System.Windows.Forms.IDataObject> kopyalayıp:

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Öğeler seri hale getirili Öğe Grubu olarak depolanır.

 IDataObject öğeleri bir modelde birleştirebilirsiniz:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` bir veya kabul `PresentationElement` `ModelElement` eder. Buna bir `PresentationElement` verirsiniz, hedef diyagramda üçüncü parametre olarak bir konum da belirtebilirsiniz.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Diyagramlarda gezinme ve diyagramları güncelleştirme
 DSL'de Person veya Song gibi bir kavramı temsil eden etki alanı modeli öğesi diyagramda gördüğünüz öğeyi temsil eden şekil öğesinden ayrıdır. Etki alanı modeli öğesi, kavramların önemli özelliklerini ve ilişkilerini depolar. Şekil öğesi, nesnenin görünümünün boyutunu, konumunu ve rengini diyagramda ve bileşen parçalarının düzenini depolar.

### <a name="presentation-elements"></a>Sunu Öğeleri
 ![Temel şekil ve öğe türlerinin sınıf diyagramı](../modeling/media/dslshapesandelements.png)

 DSL Tanımında, belirttiğiniz her öğe aşağıdaki standart sınıflardan biri türetilen bir sınıf oluşturur.

|Öğenin tür|Temel sınıf|
|-|-|
|Etki alanı sınıfı|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Etki alanı ilişkisi|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Şekil|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Bağlayıcı|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diyagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Diyagramda yer alan bir öğe genellikle bir model öğesini temsil eder. Genellikle (ama her zaman değil), <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> bir etki alanı sınıf örneğini temsil eder ve bir etki alanı ilişki örneğini temsil <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> eder. İlişki, <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> bir düğümü veya şekli temsil ettiği model öğesine bağlar.

 Her düğüm veya bağlantı şekli bir diyagrama aittir. İkili bağlantı şekli iki düğüm şeklini birbirine bağlar.

 Şekiller iki kümede alt şekillere sahip olabilir. Küme içindeki bir `NestedChildShapes` şekil, üst öğenin sınırlayıcı kutusuna sınırlandı. Listede yer alan bir şekil, etiketin veya bağlantı noktasının dışında veya kısmen üst öğenin `RelativeChildShapes` sınırları dışında görünebilir. Diyagramda hayır ve `RelativeChildShapes` `Parent` hayır.

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Şekiller ve öğeler arasında gezinme
 Etki alanı modeli öğeleri ve şekil öğeleri ilişkiyle <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> ilişkilidir.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Aynı ilişki, ilişkileri diyagramda bağlayıcılara bağlar:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Bu ilişki ayrıca modelin kökünü diyagrama bağlar:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Şekille temsil edilen model öğesini almak için şunları kullanın:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Diyagramda gezinme
 Genel olarak diyagramda şekiller ve bağlayıcılar arasında gezinmek tavsiye edilemez. Modelde ilişkilerde gezinmek, şekiller ve bağlayıcılar arasında geçiş yapmak, yalnızca diyagramın görünümü üzerinde çalışmak gerektiğinde gezinmek daha iyidir. Bu yöntemler bağlayıcıları her bir uçta yer alan şekillere bağlayın:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Birçok şekil bileşiktir; bunlar bir üst şekil ve bir veya daha fazla alt katmandan oluşur. Başka bir şekle göre konumlara sahip olan şekillerin, onun da kendi şekilleri olduğu *kabul edildi.* Üst şekil hareket ettiğinde alt öğe de bu şekille birlikte taşınır.

 *Göreli alt* öğe, üst şeklin sınırlayıcı kutusunun dışında görünebilir. *İç içe* geçmiş alt öğe, kesinlikle üst öğenin sınırları içinde görünür.

 Diyagramda üst şekil kümesi elde etmek için şunları kullanın:

 `Diagram.NestedChildShapes`

 Şekil ve bağlayıcıların üst sınıfları:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *Bağlantınız*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Şekillerin ve Bağlayıcıların Özellikleri
 Çoğu durumda, şekiller üzerinde açık değişiklikler yapmak gerekli değildir. Model öğelerini değiştir zaman, "düzeltme" kuralları şekilleri ve bağlayıcıları güncelleştirmesi. Daha fazla bilgi için [bkz. Değişiklikleri Yanıt verme ve Yayma.](../modeling/responding-to-and-propagating-changes.md)

 Ancak, model öğelerine bağımsız özelliklerde şekiller üzerinde bazı açık değişiklikler yapmak yararlıdır. Örneğin, şu özellikleri değiştirebilirsiniz:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> - şeklin yüksekliğini ve genişliğini belirler.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> - üst şekil veya diyagrama göre konum

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> - şekli veya bağlayıcıyı çizmek için kullanılan kalem ve fırça kümesi

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> - şekli görünmez yapar

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> - şekli bir sonra görünür hale `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Öğe ve Şekli Oluşturma

Bir öğe oluşturulduğunda ve bunu ekleme ilişkileri ağacına bağ her zaman otomatik olarak bir şekil oluşturulur ve bu öğeyle ilişkilendirililir. Bu işlem, işlem sonunda yürütülen "düzeltme" kuralları tarafından yapılır. Ancak, şekil otomatik olarak atanan bir konumda görünür ve şekli, rengi ve diğer özellikleri varsayılan değerlere sahip olur. Şeklin nasıl oluşturulacaklarını kontrol etmek için merge işlevini kullanabilirsiniz. Önce bir ElementGroup'a eklemek istediğiniz öğeleri eklemeniz ve ardından grubu diyagramda birleştirmelisiniz.

Bu yöntem:

- Öğe adı olarak bir özellik atadıysanız adı ayarlar.

- DSL Tanımında belirttiğiniz öğe birleştirme yönergelerini gözlemler.

Bu örnek, kullanıcı diyagrama çift tıkladığında fare konumunda bir şekil oluşturur. Bu örneğin DSL Tanımında, `FillColor` özelliği `ExampleShape` açığa çıkar.

```csharp
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

 Birden fazla şekil sağlarsanız, kullanarak bunların göreli konumlarını `AbsoluteBounds` ayarlayın.

 Bu yöntemi kullanarak bağlayıcıların rengini ve diğer açık özelliklerini de ayarlayabilirsiniz.

### <a name="use-transactions"></a>İşlemleri Kullanma
 Şekiller, bağlayıcılar ve diyagramlar depodaki alt türler <xref:Microsoft.VisualStudio.Modeling.ModelElement> ve canlı. Bu nedenle, yalnızca bir işlemin içinde değişiklikler yapmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: modeli güncelleştirmek Için Işlemleri kullanma](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Belge görünümü ve belge verileri
 ![Standart diyagram türlerinin sınıf diyagramı](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Depolama bölümleri
 Bir model yüklendiğinde, eşlik eden diyagram aynı anda yüklenir. Genellikle, model Store. DefaultPartition içine yüklenir ve Diyagram içeriği başka bir bölüme yüklenir. Genellikle, her bölümün içeriği yüklenir ve ayrı bir dosyaya kaydedilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Etki Alanına Özgü bir Dilde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)
- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
- [Nasıl yapılır: Modeli Güncelleştirmek için İşlemleri Kullanma](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
