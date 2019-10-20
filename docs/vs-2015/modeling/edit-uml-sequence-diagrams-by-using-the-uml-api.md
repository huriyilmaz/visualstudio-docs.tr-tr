---
title: UML API 'sini kullanarak UML sıralı diyagramlarını düzenleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbc7a6ce7edede6759c0562df1e524d932f62b91
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669707"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>UML API kullanarak sıralama diyagramlarını düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etkileşim, yaşam çizgileri kümesi arasındaki bir ileti dizisidir. Bir etkileşim, UML sıralı diyagramında görüntülenir.

 API 'nin tam ayrıntıları için bkz. [Microsoft. VisualStudio. Uml.](/previous-versions/dd493373(v=vs.140))Interactions.

 UML diyagramları için komut ve hareket işleyicileri yazma hakkında daha fazla genel bilgi için bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="basic-code"></a>Temel kod

### <a name="namespace-imports"></a>Ad alanı içeri aktarmaları
 Aşağıdaki `using` deyimlerini dahil etmeniz gerekir:

```
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types such as IPackage
using Microsoft.VisualStudio.Uml.Interactions;
   // for interaction types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // to create elements and use additional functions
```

 Menü komutları ve hareket işleyicileri oluşturuyorsanız şunları da yapmanız gerekir:

```
using System.ComponentModel.Composition;
   // for Import and Export
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   // for diagrams and context
```

 Daha fazla bilgi için bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="getting-the-context"></a>Bağlam alma
 Bir etkileşimi bir komut veya hareket işleyicisinin bir parçası olarak sıralı diyagramda düzenliyorsanız, bağlama bir başvuru elde edebilirsiniz. Örneğin:

```
[SequenceDesignerExtension]
[Export(typeof(ICommandExtension))]
public class MySequenceDiagramCommand : ICommandExtension
{
    [Import]
    public IDiagramContext Context { get; set; }
    public void QueryStatus (IMenuCommand command)
    {
      ISequenceDiagram sequenceDiagram =
          Context.CurrentDiagram as ISequenceDiagram;
         ...
```

### <a name="generated-and-uml-sequence-diagrams"></a>Oluşturulan ve UML sıralı diyagramlar
 İki tür sıralı diyagram vardır: bir UML modelleme projesinde el ile oluşturulan ve program kodundan oluşturulmuş olanlar. Sahip olduğunuz sıralı diyagramı saptamak için `UmlMode` özelliğini kullanın.

> [!NOTE]
> Bu özellik yalnızca Visual Studio 2013 ve önceki sürümleri kullanılarak koddan oluşturulan dizi diyagramları için false döndürür. Bu, 2013 ve öncesinden geçirilen kod tarafından oluşturulan sıralı diyagramlar içerir. Visual Studio 'nun bu sürümü, yeni sıralı diyagramlar oluşturmayı desteklemez.

 Örneğin, UML sıralı diyagramlarda yalnızca görünür olan bir menü komutu oluşturmak istiyorsanız `QueryStatus()` yöntemi aşağıdaki ifadeyi içerebilir:

```
command.Enabled = command.Visible =
      sequenceDiagram != null && sequenceDiagram.UmlMode;
```

 Oluşturulan bir sıralı diyagramda, yaşam çizgileri, iletiler ve diğer öğeler çoğunlukla UML sıralı diyagramı ile aynıdır. Bir UML modelinde model deposu, diğer tüm öğelerine sahip olan model olan bir köke sahiptir. Ancak oluşturulan bir etkileşim kendi model deposunda bulunur ve bu da null köke sahiptir:

```
IModel rootModel = sequenceDiagram.ModelStore.Root;
    // !sequenceDiagram.UmlMode == (rootModel == null)
```

## <a name="to-create-and-display-an-interaction"></a>Bir etkileşim oluşturmak ve göstermek için
 Etkileşimi bir paket veya modelin alt öğesi olarak oluşturun.

 Örneğin, boş bir sıralı diyagramda gerçekleştirilebilecek bir komut geliştiriyorsanız, etkileşimin mevcut olup olmadığını denetleyerek her zaman başlamanız gerekir.

```
public void Execute (IMenuCommand command)
{
    ISequenceDiagram sequenceDiagram =
         Context.CurrentDiagram as ISequenceDiagram;
    if (sequenceDiagram == null) return;
    // Get the diagram's interaction:
    IInteraction interaction = sequenceDiagram.Interaction;
    // A new sequence diagram might have no interaction:
    if (interaction == null)
    {
       // Get the home package or model of the diagram:
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();
       interaction = parentPackage.CreateInteraction();
       // Display the interaction on the sequence diagram:
       sequenceDiagram.Bind(interaction);
    }
```

## <a name="updating-an-interaction-and-its-layout"></a>Bir etkileşimi ve onun yerleşimini güncelleştirme
 Bir etkileşimi güncelleştirdiğinizde, aşağıdaki yöntemlerden birini kullanarak kendi yerleşimini güncelleştirerek işleminizi her zaman sonlandırın:

- `ISequenceDiagram.UpdateShapePositions()`, yakın zamanda eklenen veya taşınan şekillerin ve onların komşu şekillerinin konumlarını ayarlar.

- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` tüm diyagramı yeniden çizer. Yaşam çizgilerini, iletileri veya her ikisini de yeniden konumlandırmayı belirtmek için parametresini kullanabilirsiniz.

  Yeni öğeler eklediğinizde veya varolan öğeleri taşırken bu özellikle önemlidir. Bu işlemlerden birini gerçekleştirene kadar diyagramda doğru konumlarda yer olmayacaktır. Bir dizi değişikliğin sonunda bu işlemlerden birini yalnızca bir kez çağırmanız gerekir.

  Komutunuz sonrasında geri alma gerçekleştiren kullanıcıyı kullanmaktan kaçınmak için, değişikliklerinizi ve son `Layout()` veya `UpdateShapePositions()` işlemlerini kapsamak üzere bir `ILinkedUndoTransaction` kullanın. Örneğin:

```
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))
{
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);
  Diagram.UpdateShapePositions();
  transaction.Commit();
}
```

 @No__t_0 kullanmak için bu bildirimi sınıfınıza yapmanız gerekir:

```
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }
```

 Daha fazla bilgi için bkz. [işlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md).

## <a name="building-an-interaction"></a>Etkileşim oluşturma

### <a name="to-create-lifelines"></a>Yaşam çizgileri oluşturmak için

```
ILifeline lifeline = interaction.CreateLifeline();
```

 Bir yaşam çizgisi, bir tür örneği olan bağlanılabilir bir öğeyi temsil eder. Örneğin, bir bileşenin iç bölümlerine gelen iletileri nasıl temsil ettiğini göstermek için etkileşim kullanılıyorsa, yaşam çizgileri bileşenin bağlantı noktalarını ve parçalarını temsil edebilir:

```
foreach (IConnectableElement part in
            component.Parts
           .Concat<IConnectableElement>(component.OwnedPorts))
{
   ILifeline lifeline = interaction.CreateLifeline();
   lifeline.Represents = part;
}
```

 Alternatif olarak, etkileşim rastgele bir nesne kümesini gösteriyorsa, etkileşim içinde bir özellik veya başka `IConnectableElement` oluşturabilirsiniz:

```
ILifeline lifeline = interaction.CreateLifeline();
IProperty property1 = interaction.CreateProperty();
property1.Type = model.CreateInterface();
property1.Type.Name = "Type 1";
lifeline.Represents = property1;
```

 Başka bir alternatif olarak, bir yaşam çizgisinin adını ve türünü bağlanılabilir bir öğeye bağlamadan ayarlayabilirsiniz:

```
ILifeline lifeline = interaction.CreateLifeline();
lifeline.Name = "c1";
lifeline.SetInstanceType("Customer");
System.Diagnostics.Debug.Assert(
           lifeline.GetDisplayName() == "c1:Customer"  );
```

### <a name="to-create-messages"></a>İleti oluşturmak için
 Bir ileti oluşturmak için, kaynak ve hedef yaşam çizgilerine ekleme noktaları tanımlamalısınız. Örneğin:

```
interaction.CreateMessage( sourceInsertionPoint,
                           targetInsertionPoint,
                           MessageKind.Complete,
                           MessageSort.ASynchCall)
```

 Tanımsız bir kaynağa veya tanımsız hedefe sahip bir ileti oluşturmak için:

```
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);
```

 Bir yaşam çizgisinde tüm anahtar noktalarında ekleme noktalarını belirlemek için kullanabileceğiniz birkaç ileti vardır:

|ILifeline 'daki Yöntem|Bu noktada eklemek için kullanın|
|-------------------------|------------------------------------|
|`FindInsertionPointAtTop()`|Yaşam çizgisinin en üstü.|
|`FindInsertionPointAtBottom()`|Yaşam çizgisinin altı.|
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Belirtilen iletiden hemen sonra gelen bir nokta.|
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Nokta, yaşam çizgisinde ya da bir üst yürütme belirtim bloğunda olabilir.|
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Etkileşim kullanımını izleyen bir nokta.|
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Birleşik parçayı izleyen bir nokta.|
|`FindInsertionPoint(IExecutionSpecification block)`|Yürütme bloğunun en üstü.|
|`FindInsertionPoint(IInteractionOperand fragment)`|Birleşik parçanın bir işleneninin en üstü.|

 İleti oluştururken, başka bir ileti üzerinde geçiş yapan bir ileti tanımlamaktan kaçının.

### <a name="to-create-combined-fragments-and-interaction-uses"></a>Birleşik parçalar ve etkileşim kullanımları oluşturmak için
 Öğe kapsamında olması gereken her bir yaşam çizgisinde bir ekleme noktası belirterek birleştirilmiş parçalar ve etkileşim kullanımları oluşturabilirsiniz. Mevcut bir ileti veya parçanın üzerinde geçiş yapan bir işaret kümesi belirtmekten kaçının.

```
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
Interaction.CreateInteractionUse(
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
```

 Ayrıca, varolan bir ileti kümesini içeren Birleşik bir parça oluşturabilirsiniz. İletilerin tümü aynı yaşam çizgisi veya yürütme bloğunda kaynaklıdır olmalıdır.

```
ICombinedFragment cf = Interaction.CreateCombinedFragment(
  InteractionOperatorKind.Loop,
  Interaction.Lifelines.First().GetAllOutgoingMessages());
```

 Birleşik parça her zaman tek bir işlenen ile oluşturulur. Yeni bir işlenen oluşturmak için, daha önce veya sonrasında eklemek istediğiniz mevcut işleneni ve öğesinden sonra mı yoksa önüne mi eklemek istediğinizi belirtmeniz gerekir:

```
// Create an additional operand before the first
cf.CreateInteractionOperand(cf.Operands.First(), false);
// Create an additional operand after the last:
cf.CreateInteractionOperand(cf.Operands.Last(), true);
```

## <a name="troubleshooting"></a>Sorun giderme
 Değişiklikler bir `UpdateShapePositions()` veya `Layout()` işlemiyle tamamlanmazsa, şekiller yanlış konumlarda görüntülenir.

 Birçok diğer sorun, ekleme noktalarının yanlış hizalanmış olmasından kaynaklanır, böylece yeni iletiler veya parçalar diğerlerinden daha fazla çapraz olmalıdır. Belirtiler hiçbir değişikliğin gerçekleştirilmeyeceğini veya bir özel durum atılır. @No__t_0 veya `Layout()` işlemi gerçekleştirilene kadar özel durum oluşmayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft. VisualStudio. Uml. Interactions](/previous-versions/dd493373(v=vs.140))
- [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)
- [Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
- [Özel bir modelleme araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md)
- [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)
- [UML API ile programlama](../modeling/programming-with-the-uml-api.md)
