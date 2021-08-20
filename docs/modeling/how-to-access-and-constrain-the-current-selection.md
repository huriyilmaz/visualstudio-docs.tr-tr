---
title: 'Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama'
description: Etki alanına özgü diliniz için bir komut veya hareket işleyicisi yazarak kullanıcının hangi öğeye sağ tık yaptığını nasıl belirleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 692e730135bd1f62ef98c83669d133da552d6b3e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150566"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama

Etki alanına özgü diliniz için bir komut veya hareket işleyicisi yazarken, kullanıcının sağ tıklamış olduğu öğeyi anabilirsiniz. Ayrıca bazı şekillerin veya alanların seçilmesini de önleyebilirsiniz. Örneğin, kullanıcı bir simge dekoratörüne tıkladığında, bunu içeren şeklin seçili olduğunu ayarlayabilirsiniz. Seçimi bu şekilde sınırlamak, yazmanız gereken işleyici sayısını azaltır. Ayrıca, dekoratörden kaçınmak zorunda kalmadan şeklin herhangi bir yerine tıklandıran kullanıcı için de daha kolay hale getirir.

## <a name="access-the-current-selection-from-a-command-handler"></a>Bir Komut İşleyiciden Geçerli Seçime Erişme

Etki alanına özgü bir dil için komut kümesi sınıfı, özel komutlarınız için komut işleyicilerini içerir. Etki alanına özgü bir dil için komut kümesi sınıfının türetilir <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> sınıfı, geçerli seçime erişmek için birkaç üye sağlar.

Komuta bağlı olarak, komut işleyicisi model tasarımcısında, model gezgininde veya etkin pencerede seçimine ihtiyaç olabilir.

### <a name="to-access-selection-information"></a>Seçim bilgilerine erişmek için

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>sınıfı, geçerli seçime erişmek için kullanılan aşağıdaki üyeleri tanımlar.

    |Üye|Açıklama|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> yöntemi|Model tasarımcısında seçilen öğelerden herhangi biri bölme şekliyse , değilse `true` `false` döndürür.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> yöntemi|Diyagram `true` model tasarımcısında seçiliyse döndürür; aksi takdirde `false` döndürür.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> yöntemi|Model `true` tasarımcısında tam olarak bir öğe seçilirse döndürür; aksi takdirde `false` döndürür.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> yöntemi|Etkin `true` pencerede tam olarak bir öğe seçilirse döndürür; aksi takdirde `false` döndürür.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Özellik|Model tasarımcısında seçilen öğelerin salt okunur koleksiyonunu alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Özellik|Etkin pencerede seçilen öğelerin salt okunur koleksiyonunu alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Özellik|Model tasarımcısında seçimin birincil öğesini alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Özellik|Etkin pencerede seçimin birincil öğesini alır.|

2. sınıfının özelliği, model tasarımcısı penceresini temsil eden nesneye erişim sağlar ve model tasarımcısında <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> seçili <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> öğelere ek erişim sağlar.

3. Ayrıca, oluşturulan kod, etki alanına özgü dil için komut kümesi sınıfında bir gezgin araç penceresi özelliği ve gezgin seçim özelliği tanımlar.

    - Gezgin araç penceresi özelliği, etki alanına özgü dil için gezgin araç penceresi sınıfının bir örneğini döndürür. Gezgin araç penceresi sınıfı sınıfından <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> türetildi ve etki alanına özgü dil için model gezginini temsil eder.

    - özelliği, `ExplorerSelection` etki alanına özgü dil için model gezgini penceresinde seçili öğeyi döndürür.

## <a name="determine-which-window-is-active"></a>Hangi pencerenin etkin olduğunu belirleme

Arabirimi, <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> kabukta geçerli seçim durumuna erişim sağlayan üyeleri tanımlar. Paket sınıfından veya etki alanına özgü dil için komut kümesi sınıfından her biri temel sınıfında tanımlanan özelliği aracılığıyla bir <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> `MonitorSelection` nesnesi elde edersiniz. Paket sınıfı sınıfından <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> türetildi ve komut kümesi sınıfı sınıfından <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> türetildi.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Bir komut işleyiciden etkin olan pencere türünü belirlemek için

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>sınıfının <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> özelliği, <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> kabukta geçerli seçim durumuna erişim sağlayan bir nesnesi döndürür.

2. Arabirimin <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> özelliği <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> etkin seçim kapsayıcısı alır ve bu kapsayıcı etkin pencereden farklı olabilir.

3. Hangi pencere türünün etkin olduğunu belirlemek için etki alanına özgü diliniz için komut kümesi sınıfına aşağıdaki özellikleri ekleyin.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Seçimi Kısıtla

Seçim kuralları ekleyerek, kullanıcı modeldeki bir öğeyi seçerken hangi öğelerin seçileceklerini kontrol etmek için kullanılabilirsiniz. Örneğin, kullanıcının birkaç öğeye tek bir birim olarak davranmasına izin vermek için bir seçim kuralı kullanabilirsiniz.

### <a name="to-create-a-selection-rule"></a>Seçim kuralı oluşturmak için

1. DSL projesinde özel kod dosyası oluşturma

2. sınıfından türetilen bir seçim kuralı sınıfı <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> tanımlayın.

3. Seçim <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> ölçütlerini uygulamak için seçim kuralı sınıfının yöntemini geçersiz kılın.

4. Özel kod dosyanıza ClassDiagram sınıfı için kısmi bir sınıf tanımı ekleyin.

     sınıfı `ClassDiagram` sınıfından türetildi ve DSL projesinde <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> oluşturulan diagram.cs kod dosyasında tanımlanır.

5. Özel <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> seçim kuralını geri `ClassDiagram` dönmek için sınıfının özelliğini geçersiz kılın.

     Özelliğin varsayılan <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> uygulaması, seçimi değiştirmeyen bir seçim kuralı nesnesi alır.

### <a name="example"></a>Örnek

Aşağıdaki kod dosyası, seçimi başlangıçta seçilen etki alanı şekillerinin tüm örneklerini içerecek şekilde genişleten bir seçim kuralı oluşturur.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>