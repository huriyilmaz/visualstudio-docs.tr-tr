---
title: Program Kodunda Modeli Gezinme ve Güncelleştirme
description: Model öğelerini oluşturmak ve silmek, özelliklerini ayarlamak ve öğeler arasında bağlantı oluşturmak ve silmek için kod yazmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b34c51744c6bab1c6021a006f7ec9b4da0f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390977"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Program Kodunda Modelde Gezinme ve Modeli Güncelleştirme

Model öğelerini oluşturmak ve silmek, özelliklerini ayarlamak ve öğeler arasındaki bağlantıları oluşturmak ve silmek için kod yazabilirsiniz. Tüm değişikliklerin bir işlem içinde yapılmış olması gerekir. Öğeler diyagramda görüntülenirse, diyagram işlem sonunda otomatik olarak "düzeltilir".

## <a name="an-example-dsl-definition"></a><a name="example"></a> Örnek DSL Tanımı
 Bu, bu konudaki örnekler için DslDefinition.dsl'nin ana bölümüdir:

 ![DSL Tanımı diyagramı &#45; ağaç modeli](../modeling/media/familyt_person.png)

 Bu model bu DSL'nin bir örneğidir:

 ![Tudor Aile Ağacı Modeli](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Başvurular ve Ad Alanları
 Bu konu başlığındaki kodu çalıştırmak için şu kaynaklara başvurabilirsiniz:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Kodunuz şu ad alanını kullanır:

 `using Microsoft.VisualStudio.Modeling;`

 Ayrıca, DSL'nizin tanımlandığı projeden farklı bir projede kod yazıyorsanız, Dsl projesi tarafından inşa edilen derlemeyi içeri aktarmanız gerekir.

## <a name="navigating-the-model"></a><a name="navigation"></a> Modelde Gezinme

### <a name="properties"></a>Özellikler
 DSL tanımında tanımladığınız etki alanı özellikleri, program kodunda erişebilirsiniz özelliklere dönüşer:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Bir özellik ayarlamak için bir işlem içinde bunu yapmak [gerekir:](#transaction)

 `henry.Name = "Henry VIII";`

 DSL tanımında bir özelliğin **Kind** değeri **Hesaplandı** ise, ayarlanmaz. Daha fazla bilgi için [bkz. Hesaplanan ve Özel Depolama Özellikleri.](../modeling/calculated-and-custom-storage-properties.md)

### <a name="relationships"></a>İlişkiler
 DSL tanımında tanımladığınız etki alanı ilişkileri, ilişkinin her sonunda sınıfta bir tane olmak üzere özellik çiftleri haline gelir. Özelliklerin adları DslDefinition diyagramında, ilişkinin her bir tarafındaki rollerde etiketler olarak görünür. Rolün çokluğuna bağlı olarak, özelliğin türü ilişkinin diğer ucundaki sınıf veya bu sınıfın bir koleksiyonudur.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 bir ilişkinin ters uçlarının özellikleri her zaman karşılıklıdır. Bir bağlantı oluşturulduğunda veya silindiğinde, her iki öğede de rol özellikleri güncelleştirilir. Aşağıdaki ifade (uzantılarını `System.Linq` kullanır) örnekteki ParentsChildren ilişkisi için her zaman doğrudur:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. İlişki, etki alanı ilişki türünün bir örneği olan *bağlantı* adlı bir model öğesiyle de temsil edilen bir ilişkidir. Bağlantının her zaman bir kaynak öğesi ve bir hedef öğesi vardır. Kaynak öğe ve hedef öğe aynı olabilir.

 Bağlantıya ve özelliklerine erişebilirsiniz:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Varsayılan olarak, bir ilişki örneğinin herhangi bir model öğe çiftini bağlamasına izin verilmez. Ancak DSL tanımında ilişki için bayrağı true ise, birden fazla bağlantı olabilir ve `Allow Duplicates` bunu kullansanız `GetLinks` gerekir:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Bağlantılara erişmek için başka yöntemler de vardır. Örneğin:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Gizli roller.** DSL tanımında, **Belirli** bir rol için Oluşturulan Özellik **false** ise, o role karşılık gelen bir özellik oluşturulmaz. Ancak, yine de bağlantılara erişebilirsiniz ve ilişkinin yöntemlerini kullanarak bağlantıları çapraz geçirebilirsiniz:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 En sık kullanılan örnek, model öğesini diyagramda görüntüleyen şekle <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> bağlar ilişkidir:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Öğe Dizini
 Öğe dizinini kullanarak depoda yer alan tüm öğelere erişebilirsiniz:

 `store.ElementDirectory.AllElements`

 Ayrıca, aşağıdakiler gibi öğeleri bulma yöntemleri de vardır:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Sınıf Bilgilerine Erişme
 DSL tanımının sınıfları, ilişkileri ve diğer yönleri hakkında bilgi edinebilirsiniz. Örneğin:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Model öğelerinin üst sınıfları aşağıdaki gibidir:

- ModelElement - tüm öğeler ve ilişkiler ModelElements'tir

- ElementLink - tüm ilişkiler ElementLinks'tir

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> İşlem İçinde Değişiklik Gerçekleştirme
 Program kodunuz Store'daki herhangi bir şeyi her değiştirirse, bunu bir işlem içinde yapmaları gerekir. Bu tüm model öğeleri, ilişkiler, şekiller, diyagramlar ve bunların özellikleri için geçerlidir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Bir işlemi yönetmenin en kullanışlı yöntemi, deyiminin içine `using` alınmış bir `try...catch` deyimdir:

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

 Bir işlem içinde herhangi bir sayıda değişiklik yapabilirsiniz. Etkin bir işlem içinde yeni işlemler açtırarak.

 Değişikliklerinizi kalıcı hale yapmak için, `Commit` işlemi atmadan önce sizin de olması gerekir. İşlem içinde yakalanmaz bir özel durum oluşursa, Store değişiklik öncesinde durumuna sıfırlanır.

## <a name="creating-model-elements"></a><a name="elements"></a> Model Öğeleri Oluşturma
 Bu örnek, mevcut modele bir öğe ekler:

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

 Bu örnek, öğe oluşturmayla ilgili şu temel noktaları göstermektedir:

- Yeni öğeyi Mağaza'nın belirli bir bölümü içinde oluşturun. Model öğeleri ve ilişkiler için ancak şekiller için bu genellikle varsayılan bölümdür.

- Bunu ekleme ilişkisinin hedefi yapma. Bu örneğin DslDefinition'sinde her Kişi, FamilyTreeHasPeople ilişkisi eklemenin hedefi olması gerekir. Bunu başarmak için Person nesnesinin FamilyTreeModel rol özelliğini ayar ekleyebilir veya Person'i FamilyTreeModel nesnesinin People rol özelliğine ekleyebiliriz.

- Özellikle DslDefinition içinde true olan özelliği olmak `IsName` üzere yeni bir öğenin özelliklerini ayarlayın. Bu bayrak, öğesini sahibi içinde benzersiz olarak tanımlamaya hizmet eden özelliği işaretler. Bu durumda Name özelliği bu bayrağına sahip olur.

- Bu DSL'nin DSL tanımının Depoya yüklenmiş olması gerekir. Menü komutu gibi bir uzantı yazıyorsanız, bu genellikle zaten doğrudur. Diğer durumlarda, modeli açıkça Store'a yük olabilir veya [ModelBus'i](/previous-versions/ee904639(v=vs.140)) kullanarak yükleysiniz. Daha fazla bilgi için, [bkz. How to: Open a Model from File in Program Code](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Bu şekilde bir öğe oluşturulduğunda otomatik olarak bir şekil oluşturulur (DSL'de diyagram varsa). Varsayılan şekil, renk ve diğer özelliklerle otomatik olarak atanan bir konumda görünür. İlişkili şeklin nerede ve nasıl görüntülendiğinden kontrol etmek için bkz. [Öğe oluşturma ve şekli.](#merge)

## <a name="creating-relationship-links"></a><a name="links"></a> İlişki Bağlantıları Oluşturma
 Örnek DSL tanımında tanımlanmış iki ilişki vardır. Her ilişki, *ilişkinin her* sonundaki sınıfında bir rol özelliği tanımlar.

 Bir ilişkinin örneğini oluşturmanın üç yolu vardır. Bu üç yöntemin her biri aynı etkiye sahiptir:

- Kaynak rol oynatıcının özelliğini ayarlayın. Örneğin:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Hedef rol oynatıcının özelliğini ayarlayın. Örneğin:

  - `edward.familyTreeModel = familyTree;`

       Bu rolün çokluğu olduğu için `1..1` değeri ataruz.

  - `henry.Children.Add(edward);`

       Bu rolün çokluğudur, `0..*` bu nedenle koleksiyonuna ekleriz.

- İlişkinin bir örneğini açıkça oluşturun. Örneğin:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  İlişkinin kendi özellikleri ayarlamak için son yöntem yararlıdır.

  Bu şekilde bir öğe oluşturulduğunda, diyagramda bir bağlayıcı otomatik olarak oluşturulur, ancak bu öğenin varsayılan şekli, rengi ve diğer özellikleri vardır. İlişkili bağlayıcının nasıl oluşturulacaklarını kontrol etmek için [bkz. Öğe Oluşturma ve Şekli.](#merge)

## <a name="deleting-elements"></a><a name="deleteelements"></a> Öğeleri Silme

öğesini çağırarak bir öğeyi `Delete()` silin:

`henry.Delete();`

Bu işlem şunları da siler:

- öğeye ve öğesinden ilişki bağlantıları. Örneğin, `edward.Parents` artık `henry` içermez.

- Bayrağın true olduğu `PropagatesDelete` rollerdeki öğeler. Örneğin, öğesini görüntüleyen şekil silinir.

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

 Daha fazla bilgi için bkz. [Read-Only segmentleri oluşturmak Için kilitleme Ilkesi tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

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

 Birçok şekil Birleşik siteler; Bunlar bir üst şekilden ve alt öğelerin bir veya daha fazla katmanlarından oluşur. Başka bir şekle göre konumlandırılmış şekillerin *alt öğesi* olduğu söylenir. Üst Şekil taşındığında, alt öğeler onunla birlikte taşınır.

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
 Şekiller, bağlayıcılar ve diyagramlar, Store'da bulunan <xref:Microsoft.VisualStudio.Modeling.ModelElement> ve bu öğenin alt türleridir. Bu nedenle yalnızca bir işlem içinde değişiklik yapabilirsiniz. Daha fazla bilgi için, [bkz. How to: Use Transactions to Update the Model](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Belge Görünümü ve Belge Verileri
 ![Standart diyagram türlerinin sınıf diyagramı](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Bölümleri Depolama
 Bir model yüklendiğinde, eşlik eden diyagram aynı anda yüklenir. Model genellikle Store.DefaultPartition içine yüklenir ve diyagram içeriği başka bir Bölüme yüklenir. Genellikle her bölümün içeriği yüklenir ve ayrı bir dosyaya kaydedilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Etki Alanına Özgü bir Dilde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)
- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
- [Nasıl yapılır: Modeli Güncelleştirmek için İşlemleri Kullanma](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
