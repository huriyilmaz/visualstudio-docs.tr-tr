---
title: Program Kodunda Modeli Gezinme ve Güncelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 521ad703b92133f56d38e061123bf13db13d6375
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75566182"
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

 DSL tanımında bir özelliğin **türü** **hesaplanıyorsa**, ayarlanamaz. Daha fazla bilgi için bkz. [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>İlişkiler
 DSL tanımında tanımladığınız etki alanı ilişkileri, ilişkinin her ucunda bir sınıf olmak üzere özellik çiftleri haline gelir. Özelliklerin adları DslDefinition diyagramında ilişkinin her tarafındaki rollerin etiketleri olarak görünür. Rolün çoğuluna bağlı olarak, özelliğin türü ilişkinin diğer sonundaki sınıf veya bu sınıfın bir koleksiyonu olur.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Bir ilişkinin ters uçlarından özellikler her zaman karşılıklıdır. Bir bağlantı oluşturulduğunda veya silindiğinde, her iki öğe üzerindeki rol özellikleri güncelleştirilir. Aşağıdaki ifade (uzantısını kullanan `System.Linq` ), örnekteki ParentsHaveChildren ilişkisinde her zaman doğrudur:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. İlişki Ayrıca, etki alanı ilişki türünün bir örneği olan *bağlantı*adlı model öğesiyle temsil edilir. Bağlantının her zaman bir kaynak öğesi ve bir hedef öğesi vardır. Kaynak öğe ve hedef öğe aynı olabilir.

 Bir bağlantıya ve özelliklerine erişebilirsiniz:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Varsayılan olarak, bir ilişkinin birden fazla örneğinin herhangi bir çift model öğesi bağlantı yapmasına izin verilmez. Ancak DSL tanımında, bu, `Allow Duplicates` ilişki için true ise, birden fazla bağlantı olabilir ve şunları kullanmanız gerekir `GetLinks` :

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Bağlantılara erişim için de başka yöntemler de vardır. Örneğin:

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

- Kaynak rol oyuncusunun özelliğini ayarlayın. Örneğin:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Hedef rol oyuncusunun özelliğini ayarlayın. Örneğin:

  - `edward.familyTreeModel = familyTree;`

       Bu rolün çoğulluğu olduğundan `1..1` , değeri atadık.

  - `henry.Children.Add(edward);`

       Bu rolün çoğulluğu olduğundan `0..*` , koleksiyona ekliyoruz.

- İlişkinin bir örneğini açıkça oluşturun. Örneğin:

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

Varsayılan olarak, her katıştırma ilişkisi `PropagatesDelete` hedef rolde true 'dur. Silme, `henry` öğesini silmez, `familyTree` ancak `familyTree.Delete()` Tümünü siler `Persons` .

Varsayılan olarak, `PropagatesDelete` başvuru ilişkilerinin rolleri için doğru değildir.

Bir nesneyi sildiğinizde silme kurallarının belirli yayılmaları yok saymasına neden olabilirsiniz. Bu, bir öğeyi başka bir öğe için değiştirirken yararlıdır. Silmenin yayılmaması gereken bir veya daha fazla rolün GUID 'sini sağlarsınız. GUID ilişki sınıfından elde edilebilir:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Bu belirli örnekte hiçbir etkisi olmaz, çünkü `PropagatesDelete` `false` ilişkinin rollerine yöneliktir `ParentsHaveChildren` .)

Bazı durumlarda, silme işlemi veya öğe üzerinde ya da yayma tarafından silinecek bir öğe üzerinde bir kilit var. `element.CanDelete()`Öğesinin silinip silinemeyeceğini denetlemek için ' i kullanabilirsiniz.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> Ilişki bağlantıları siliniyor
 Rol özelliğinden bir öğe kaldırarak ilişki bağlantısını silebilirsiniz:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Bağlantıyı açıkça de silebilirsiniz:

 `edwardHenryLink.Delete();`

 Bu üç yöntemin hepsi aynı etkiye sahiptir. Yalnızca birini kullanmanız yeterlidir.

 Rolün 0.. 1 veya 1.. 1 çokluğu varsa, `null` ya da başka bir değere ayarlayabilirsiniz:

 `edward.FamilyTreeModel = null;` veya

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> Ilişkinin bağlantılarını yeniden sıralama
 Belirli bir model öğesinde kaynağı oluşturulan veya hedeflenen belirli bir ilişkinin bağlantılarının belirli bir sırası vardır. Bunlar eklendikleri sırada görünürler. Örneğin, bu ifade her zaman alt öğeleri aynı sırada verir:

 `foreach (Person child in henry.Children) ...`

 Bağlantıların sırasını değiştirebilirsiniz:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Kaynaktaki
 Değişiklikleriniz bir kilit ile engellenebilir. Kilitler tek tek öğeler üzerinde, bölümlerde ve depoda ayarlanabilir. Bu düzeylerin herhangi birinde, yapmak istediğiniz değişiklik türünü önleyen bir kilit varsa, bunu denediğinizde bir özel durum oluşturulabilir. Kilitleri öğesi kullanarak ayarlanmış olup olmadığını keşfedebilirsiniz. Ad alanında tanımlanan genişletme yöntemi olan Getkilitler () <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 Daha fazla bilgi için bkz. [salt okuma kesimleri oluşturmak Için kilitleme Ilkesi tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Kopyala ve Yapıştır
 Öğeleri veya öğe gruplarını bir öğesine kopyalayabilirsiniz <xref:System.Windows.Forms.IDataObject> :

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Öğeler serileştirilmiş bir öğe grubu olarak depolanır.

 Bir IDataObject 'den öğeleri bir modele birleştirebilirsiniz:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` ya da olarak kabul edebilir `PresentationElement` `ModelElement` . A verirseniz `PresentationElement` , hedef diyagramda bir konumu üçüncü parametre olarak da belirtebilirsiniz.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Diyagramları gezinme ve güncelleştirme
 Bir DSL 'de, kişi veya şarkı gibi bir kavramı temsil eden etki alanı model öğesi, diyagramda gördüklerinizi temsil eden şekil öğesinden ayrıdır. Etki alanı model öğesi kavramların önemli özelliklerini ve ilişkilerini depolar. Shape öğesi, nesne görünümünün boyutunu, konumunu ve rengini diyagramda ve bileşen bölümlerinin düzenine depolar.

### <a name="presentation-elements"></a>Sunum öğeleri
 ![Taban şeklinin ve öğe türlerinin sınıf diyagramı](../modeling/media/dslshapesandelements.png)

 DSL tanımınızda, belirttiğiniz her öğe aşağıdaki standart sınıfların birinden türetilmiş bir sınıf oluşturur.

|Öğe türü|Temel sınıf|
|-|-|
|Alan sınıfı|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Etki alanı ilişkisi|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Şekil|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Bağlayıcı|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diyagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Diyagramdaki bir öğe genellikle bir model öğesini temsil eder. Genellikle (her zaman değil), bir <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> etki alanı sınıfı örneğini temsil eder ve bir <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> etki alanı ilişki örneğini temsil eder. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>İlişki bir düğümü veya bağlantı şeklini temsil ettiği model öğesine bağlar.

 Her düğüm veya bağlantı şekli bir diyagrama aittir. İkili bağlantı şekli iki düğüm şeklini birbirine bağlar.

 Şekillerin iki küme içinde alt şekilleri olabilir. Küme içindeki bir şekil, `NestedChildShapes` üst öğesinin sınırlayıcı kutusuyla sınırlandırıyor. Listedeki bir şekil, `RelativeChildShapes` üst öğenin sınırları dışında veya kısmen dışında, örneğin bir etiket veya bağlantı noktası olabilir. Diyagramda Hayır `RelativeChildShapes` ve Hayır `Parent` .

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Şekiller ve öğeler arasında gezinme
 Etki alanı modeli öğeleri ve Şekil öğeleri ilişki ile ilgilidir <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> .

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

 ------- *Şeklim*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Şekillerin ve bağlayıcıların özellikleri
 Çoğu durumda, şekillere açık değişiklikler yapmak gerekli değildir. Model öğelerini değiştirdiğiniz zaman, "çözümü temizle" kuralları şekilleri ve bağlayıcıları güncelleştirir. Daha fazla bilgi için bkz. [değişiklikleri yanıtlama ve yayma](../modeling/responding-to-and-propagating-changes.md).

 Ancak, model öğelerinden bağımsız özelliklerde yer alan şekillerdeki bazı açık değişiklikler yapmak yararlı olur. Örneğin, bu özellikleri değiştirebilirsiniz:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -şeklin yüksekliğini ve genişliğini belirler.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -üst şekle veya diyagrama göre konum

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -Şekil veya bağlayıcıyı çizmek için kullanılan kalemler ve fırçalar kümesi

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -şekli görünmez yapar

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -şekli bir işlem sonrasında görünür hale getirir `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Öğe ve şeklini oluşturma

Bir öğe oluşturup katıştırma ilişkisi ağacına bağladığınızda, bir şekil otomatik olarak oluşturulur ve onunla ilişkilendirilir. Bu işlem, işlemin sonunda yürütülen "Düzeltme" kuralları tarafından yapılır. Ancak, şekil otomatik olarak atanan bir konumda görünür ve şekli, rengi ve diğer özellikler varsayılan değerlere sahip olur. Şeklin nasıl oluşturulduğunu denetlemek için Merge işlevini kullanabilirsiniz. Önce eklemek istediğiniz öğeleri ElementGroup içine eklemeniz ve sonra grubu diyagram ile birleştirmeniz gerekir.

Bu yöntem:

- Öğe adı olarak bir özellik atadıysanız, adı ayarlar.

- DSL tanımında belirttiğiniz herhangi bir öğe birleştirme yönergesi sunar.

Bu örnek, kullanıcı diyagrama çift tıkladığında fare konumunda bir şekil oluşturur. Bu örnek için DSL tanımında, `FillColor` özelliği `ExampleShape` kullanıma sunuldu.

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

 Birden fazla şekil sağlarsanız, kullanarak onun göreli konumlarını ayarlayın `AbsoluteBounds` .

 Ayrıca, bu yöntemi kullanarak bağlayıcıların rengini ve diğer sunulma özelliklerini ayarlayabilirsiniz.

### <a name="use-transactions"></a>Işlemleri kullanma
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
