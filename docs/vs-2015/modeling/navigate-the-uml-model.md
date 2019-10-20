---
title: UML modeline gidin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b90d8b532b004a7cbdaeed762300a0daf9ab45c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668540"
---
# <a name="navigate-the-uml-model"></a>UML modelinde gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu UML modelinin ana türlerini tanıtır.

## <a name="the-model-elements-model-and-model-store"></a>Model öğeleri, modeli ve model deposu
 **Microsoft. VisualStudio. Uml. Interfaces. dll** derlemesinde tanımlanan türler [UML belirtiminde, sürüm 2.1.2 'yi](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/)tanımlı türlere karşılık gelir.

 UML Belirtimindeki türler, Visual Studio 'da arabirimler olarak gerçekleştirilir. ' I ' harfi her türün adı ile sona erer. Örneğin: [IElement](/previous-versions/dd516035(v=vs.140)), [IClass](/previous-versions/dd523539%28v%3dvs.140%29), [ioperation](/previous-versions/dd481186(v=vs.140)).

 IElement dışındaki tüm türler, bir veya daha fazla üst türden özellikler devralınır.

- Model türlerinin bir özeti için bkz. [UML model öğe türleri](../modeling/uml-model-element-types.md).

- API 'nin tam ayrıntıları için bkz. [UML modelleme genişletilebilirliği Için API başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md).

### <a name="relationships"></a>İlişkiler
 UML belirtiminde tanımlanan özellikler ve ilişkiler .NET özellikleri olarak uygulanır.

 Çoğu ilişki her iki yönde de gezinilebilir. Bir ilişki, her uçtaki türde bir özellik ile bir çift özelliğe karşılık gelir. Örneğin, Özellikler `IElement.Owner` ve `IElement.OwnedElements` bir ilişkinin iki ucunu temsil eder. Bu nedenle, bu ifade her zaman true olarak değerlendirilir:

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 IAssociation gibi birçok ilişki Ayrıca kendi özelliklerine sahip olan bir nesne tarafından temsil edilir.

 Modelden bir öğe silerseniz, Bölüm aldığı herhangi bir ilişki otomatik olarak silinir ve diğer uçtaki özelliği güncellenir.

 UML belirtimi bir özelliğe 0.. 1 çeşitliliği atarsa, bu değer `null` olabilir. En büyük 1 ' den büyük bir çoğulluk, .NET özelliğinin*tür `>` türü* `IEnumerable<` olduğu anlamına gelir.

 Çapraz geçiş hakkında daha fazla bilgi için bkz. [UML API ile Ilişkilere gitme](../modeling/navigate-relationships-with-the-uml-api.md).

### <a name="the-ownership-tree"></a>Sahiplik ağacı
 Bir model [IElement](/previous-versions/dd516035(v=vs.140)) nesnelerinin ağacını içerir. Her öğe `OwnedElements` ve `Owner` özelliklere sahiptir.

 Çoğu durumda, `Owner` ve `OwnedElements` özelliklerinin hedefleri, daha belirli adlara sahip diğer özellikler tarafından da başvurulur. Örneğin, her UML işlemi bir UML sınıfına aittir. Bu nedenle [IOperation](/previous-versions/dd481186(v=vs.140)) , [IOperation. Class](/previous-versions/dd473473%28v%3dvs.140%29)adlı bir özelliğe sahiptir ve her [IOperation](/previous-versions/dd481186(v=vs.140)) nesnesinde `Class == Owner`.

 Ağacın, sahibi olmayan en üstteki öğesi bir `AuxiliaryConstructs.IModel`. IModel `IModelStore` içinde bulunur, burada [IModelStore. root](/previous-versions/ee789368(v=vs.140))olur.

 Her model öğesi bir sahibe göre oluşturulur. Daha fazla bilgi için bkz. [UML modellerinde öğe ve Ilişki oluşturma](../modeling/create-elements-and-relationships-in-uml-models.md).

 ![Sınıf diyagramı: model, diyagram, şekil ve öğe](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>Şekiller ve diyagramlar
 UML modelindeki öğeler, diyagramlarda görüntülenebilir. Farklı diyagram türleri IElement 'in farklı alt türlerini görüntüleyebilir.

 Bazı durumlarda, bir öğe birden fazla diyagramda görünebilir. Örneğin, bir IUseCase öğesi, bir diyagramda veya farklı diyagramlarda görünebilen birkaç IShapes içerebilir.

 Şekiller bir ağaçta düzenlenir. Ağacın kenarları ParentShape ve ChildShapes özellikleriyle temsil edilir. Diyagramlar, üst öğeleri olmayan tek şekillerdir. Bir diyagramın yüzeyindeki şekiller daha küçük parçalardan oluşur. Örneğin, bir sınıf şeklinin öznitelikler ve işlemler için bölmeleri vardır.

 Şekiller hakkında daha fazla bilgi için bkz. [DIYAGRAMLARDA UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="access-to-the-model-in-extensions"></a>Uzantılardaki modele erişim
 MEF Bileşenleri olarak tanımlanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantılarında, uzantının çalıştırıldığı bağlamdan bilgi içeri aktarılan özellikleri bildirebilirsiniz.

|Öznitelik türü|Bu, erişimi sağlar|Daha fazla bilgi|
|--------------------|----------------------------------|----------------------|
|Microsoft. VisualStudio. mimari Turetools. Extensibility. Presentation<br /><br /> . IDiagramContext<br /><br /> (Microsoft. VisualStudio. mimari Turetools. Extensibility. dll içinde)|Geçerli odak diyagramı.|[Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|
|Microsoft. VisualStudio. modellemesi. Extensionetkinleştirme<br /><br /> . Ilınkedundocontext<br /><br /> (Microsoft. VisualStudio. modellemesi. SDK 'da. [sürüm]. dll)|Değişiklikleri işlemlere gruplandırılmasına olanak sağlar.|[İşlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md)|
|Microsoft. VisualStudio. Shell. SVsServiceProvider<br /><br /> (Microsoft. VisualStudio. Shell. sabit içinde. [sürüm]. dll)|Ana bilgisayar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Buradan dosyalara, projelere ve diğer yönlere erişebilirsiniz.|[Visual Studio API kullanarak UML modeli açma](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|

### <a name="to-get-the-context"></a>Bağlamı almak için
 Uzantı sınıfınız içinde aşağıdaki arabirimlerin birini veya her ikisini birden bildirin:

```
[Import] public IDiagramContext DiagramContext { get; set; }

```

 Managed Extensibility Framework (MEF), bunları geçerli Diyagram, model deposu, kök nesne vb. elde ettiğiniz tanımlarla bağlayacaktır:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
IClassDiagram classDiagram = diagram as IClassDiagram;
       // or diagrams of other types
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

### <a name="to-get-the-current-selection"></a>Geçerli seçimi almak için

```
// All selected shapes and their elements
foreach (IShape shape in diagram.SelectedShapes)
{
   IDiagram selectedDiagram = shape as IDiagram;
   if (selectedDiagram != null)
   { // no shape selected - user right-clicked the diagram
     ... Context.CurrentDiagram ...
   }
   else
   {
     IElement selectedElement = shape.Element;
   ...}
// All selected shapes that display a specfic type of element
foreach (IShape<IInterface> in
   diagram.GetSelectedShapes<IInterface>())
{...}
```

## <a name="accessing-another-model-or-diagrams"></a>Başka bir modele veya diyagramlara erişme
 Şunları yapabilirsiniz:

- Farklı modellerdeki öğeler arasında bağlantılar oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model veri yolu kullanın. Daha fazla bilgi için bkz. [UML modellerini diğer modeller ve araçlarla tümleştirme](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Modelleme projesi ve diyagramlarını, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kullanıcı arabiriminde görünür yapmadan salt okunurdur modda yükleyin. Daha fazla bilgi için bkz. [program kodunda BIR UML modeli okuma](../modeling/read-a-uml-model-in-program-code.md).

- @No__t_0 bir modelleme projesi ve diyagramlarını açın ve ardından içeriğe erişin. Daha fazla bilgi için bkz. [Visual STUDIO API kullanarak BIR UML modeli açma](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="see-also"></a>Ayrıca bkz.

- [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)
- [UML API ile programlama](../modeling/programming-with-the-uml-api.md)
