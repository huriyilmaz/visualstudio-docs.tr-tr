---
title: İş öğesi bağlantı işleyicisini tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 380aaa5bed1e30c549334bc004ea38e3f0bdb762
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669931"
---
# <a name="define-a-work-item-link-handler"></a>İş öğesi bağlantı işleyicisi tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı bir UML model öğesi ve bir iş öğesi arasında bağlantı oluşturduğunda veya bu bağlantıyı sildiğinde yanıt veren bir Visual Studio Tümleştirme Uzantısı oluşturabilirsiniz. Örneğin, Kullanıcı yeni bir iş öğesini bir model öğesine bağlamayı seçtiğinde, kodunuz modeldeki değerlerden iş öğesi alanlarını başlatabilir.

## <a name="set-up-a-uml-extension-solution"></a>UML Uzantı çözümünü ayarlama
 Bu, işleyiciler geliştirmenize ve bunları diğer kullanıcılara dağıtmanıza imkan tanır. İki Visual Studio projesi ayarlamanız gerekir:

- Bağlantı işleyicisinin kodunu içeren bir sınıf kitaplığı projesi.

- Komutu yüklemek için kapsayıcı görevi gören bir VSıX projesi. İsterseniz, diğer bileşenleri aynı VSıX 'e ekleyebilirsiniz.

#### <a name="to-set-up-the-visual-studio-solution"></a>Visual Studio çözümünü ayarlamak için

1. Mevcut bir VSıX çözümüne ekleyerek veya yeni bir çözüm oluşturarak bir sınıf kitaplığı projesi oluşturun.

    1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

    2. **Yüklü şablonlar**altında **Visual C#** veya **Visual Basic**' i genişletin, ardından Orta sütundaki **sınıf kitaplığı**' na tıklayın.

    3. Yeni bir çözüm oluşturmak mı yoksa zaten açtığınız bir VSıX çözümüne bir bileşen eklemek mi istediğinizi belirtmek için **çözüm** ayarlayın.

    4. Proje adını ve konumunu ayarlayıp Tamam ' a tıklayın.

2. Çözümünüz bir tane içermiyorsa, bir VSıX projesi oluşturun.

    1. **Çözüm Gezgini**, çözümün kısayol menüsünde, **Ekle**, **Yeni proje**' yi seçin.

    2. **Yüklü şablonlar**altında **Visual C#** veya **Visual Basic**' i genişletin, ardından **genişletilebilirlik**' i seçin. Orta sütunda **VSIX projesi**' ni seçin.

3. VSıX projesini çözümün başlangıç projesi olarak ayarlayın.

    - Çözüm Gezgini, VSıX projesinin kısayol menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.

4. **Source. Extension. valtmanifest**dosyasında, **içerik**' in altında, sınıf kitaplığı projesini MEF bileşeni olarak ekleyin.

    1. **Meta veriler** sekmesinde VSIX için bir ad belirleyin.

    2. **Hedefleri yüklensin** sekmesinde, Visual Studio sürümlerini hedef olarak ayarlayın.

    3. **Varlıklar** sekmesinde **Yeni**' yi seçin ve iletişim kutusunda, şunu ayarlayın:

         **Tür**  =  **MEF bileşeni**

         **Kaynak**  =  **Geçerli çözümdeki bir proje**

         **Proje**  =  *Sınıf kitaplığı projeniz*

## <a name="defining-the-work-item-link-handler"></a>Iş öğesi bağlantı Işleyicisini tanımlama
 Sınıf kitaplığı projesinde aşağıdaki görevlerin tümünü gerçekleştirin.

### <a name="project-references"></a>Proje Başvuruları
 Aşağıdaki [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] derlemeleri projenizin başvurularına ekleyin:

 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`

 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

 `Microsoft.VisualStudio.Uml.Interfaces`

 `System.ComponentModel.Composition`

 `System.Drawing` -örnek kod tarafından kullanılır

 **Başvuru Ekle** iletişim kutusunun **.net** sekmesi altında bu başvurulardan birini bulamazsanız, \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies içinde bulmak için gözden geçirme sekmesini kullanın \\ .

### <a name="import-the-work-item-namespace"></a>Iş öğesi ad alanını içeri aktarma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Proje **başvurularında**, aşağıdaki derlemelere başvurular ekleyin:

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll

  Program kodunuzda aşağıdaki ad alanlarını içeri aktarın:

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;
```

### <a name="define-the-linked-work-item-event-handler"></a>Bağlantılı Iş öğesi olay Işleyicisini tanımlama
 Sınıf kitaplığı projesine bir sınıf dosyası ekleyin ve içeriğini aşağıdaki şekilde ayarlayın. Ad alanı ve sınıf adlarını tercih ettiğiniz her şey ile değiştirin.

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;

namespace WorkItems
{
  [Export(typeof(ILinkedWorkItemExtension))]
  public class MyWorkItemExtension : ILinkedWorkItemExtension
  {
    // Called before a new work item is edited by the user.
    // Use this to initialize work item fields from the model element.
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)
    {
      INamedElement namedElement =
            elementsToBeLinked.First() as INamedElement;
      if (namedElement != null)
        workItemDocument.Item.Title = namedElement.Name;

    }

    // Called when any work item is linked to a model element.
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)
    {
      foreach (IElement element in elements)
        foreach (IShape shape in element.Shapes())
          shape.Color = System.Drawing.Color.Red;
    }

    // Called when a work item is unlinked from a model element.
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)
    {
      foreach (IShape shape in element.Shapes())
        shape.Color = System.Drawing.Color.White;
    }
  }
}
```

## <a name="testing-the-link-handler"></a>Bağlantı Işleyicisini test etme
 Test amaçları için bağlantı işleyicinizi hata ayıklama modunda yürütün.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlanmak için TFS kaynak kodu denetimine (SCC) zaten bağlanmış olmanız gerekir. Farklı bir TFS SCC bağlantısını açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmayı veya bir iş öğesini bağlamayı denemeden önce uygun SCC 'e zaten bağlı olduğunuzdan emin olun. Visual Studio 'nun sonraki sürümlerinde, bir SCC 'e bağlı değilseniz menü komutları kullanılamaz.

#### <a name="to-test-the-link-handler"></a>Bağlantı işleyicisini test etmek için

1. **F5**tuşuna basın veya **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' ı seçin.

     Deneysel bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar.

     **Sorun giderme**: yeni bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlamazsa, VSIX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.

2. Deneysel içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir modelleme projesi açın veya oluşturun ve bir modelleme diyagramı açın veya oluşturun.

3. UML sınıfı gibi bir model öğesi oluşturun ve adını ayarlayın.

4. Öğeye sağ tıklayın ve sonra **Iş öğesi oluştur**' a tıklayın.

    - Alt menü **açık Team Foundation Server bağlantıyı**gösteriyorsa projeyi kapatmanız, uygun TFS 'ye bağlanmanız ve bu yordamı yeniden başlatmanız gerekecektir.

    - Alt menü, iş öğesi türlerinin bir listesini gösteriyorsa, bir tane tıklatın.

         Yeni bir iş öğesi formu açılır.

5. Önceki bölümde örnek kodu kullandıysanız, çalışma öğesi başlığının model öğesiyle aynı olduğunu doğrulayın. Bu `OnWorkItemCreated()` , çalıştığını gösterir.

6. Formu doldurun, iş öğesini kaydedin ve kapatın.

7. İş öğesinin artık kırmızı renkte olduğunu doğrulayın. Bu `OnWorkItemLinked()` örnek kodda gösterilmektedir.

     **Sorun giderme**: işleyici yöntemleri çalıştırılmadığından aşağıdakileri doğrulayın:

    - Sınıf kitaplığı projesi, VSıX projesindeki **kaynak. Extensions. manifest** içindeki **IÇERIK** listesinde bir MEF bileşeni olarak listelenir.

    - Doğru `Export` öznitelik işleyici sınıfına iliştirilir ve sınıfı uygular `ILinkedWorkItemExtension` .

    - Tüm `Import` ve `Export` özniteliklerinin parametreleri geçerlidir.

## <a name="about-the-work-item-handler-code"></a>Iş öğesi Işleyici kodu hakkında

### <a name="listening-for-new-work-items"></a>Yeni Iş öğeleri için dinleme
 `OnWorkItemCreated` Kullanıcı model öğelerine bağlanacak yeni bir iş öğesi oluşturmayı seçtiğinde çağrılır. Kodunuz iş öğesi alanlarını başlatabilir. Daha sonra iş öğesi kullanıcıya sunulur, alanları güncelleştirebilir ve iş öğesini kaydedebilir. Bir model öğesine bağlantı, iş öğesi başarılı bir şekilde kaydedilene kadar oluşturulmaz.

```
public void OnWorkItemCreated(
    IEnumerable<IElement> elementsToBeLinked,
    IWorkItemDocument workItem)
{
  INamedElement namedElement =
         elementsToBeLinked.First() as INamedElement;
  if (namedElement != null)
      workItem.Item.Title = namedElement.Name;
}
```

### <a name="listening-for-link-creation"></a>Bağlantı oluşturma için dinleme
 `OnWorkItemLinked` bir bağlantı oluşturulduktan hemen sonra çağrılır. Bağlantının yeni bir iş öğesine mi yoksa varolan bir öğeye mi ait olduğu çağrılır. Her iş öğesi için bir kez çağrılır.

```
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  foreach (IElement element in elements)
    foreach (IShape shape in element.Shapes())
         shape.Color = System.Drawing.Color.Red;
}
```

> [!NOTE]
> Bu örneği yapmak için, ' a bir proje başvurusu eklemeniz `System.Drawing.dll` ve ad alanını içeri aktarmanız gerekir `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation` . Ancak, bu eklemeler diğer uygulamaları için gerekli değildir `OnWorkItemLinked` .

### <a name="listening-for-link-removal"></a>Bağlantı kaldırma için dinleme
 `OnWorkItemRemoved` , silinen her iş öğesi bağlantısından hemen önce çağrılır. Bir model öğesi silinirse tüm bağlantıları kaldırılır.

```
public void OnWorkItemRemoved
         (IElement element, string serverUri, int workItemId)
{...}
```

## <a name="updating-a-work-item"></a>İş öğesini güncelleştirme
 Team Foundation ad alanlarını kullanarak bir iş öğesini yönetebilirsiniz.

 Aşağıdaki örneği kullanmak için, bu .NET derlemelerini projenizin başvurularına ekleyin:

- Microsoft.TeamFoundation.Client.dll

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

```

using Microsoft.TeamFoundation.Client;
using Microsoft.TeamFoundation.WorkItemTracking.Client;
...
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  TfsTeamProjectCollection tfs =
        TfsTeamProjectCollectionFactory
            .GetTeamProjectCollection(new Uri(serverUri));
  WorkItemStore workItemStore = new WorkItemStore(tfs);
  WorkItem item = workItemStore.GetWorkItem(workItemId);
  item.Open();
  item.Title = "something";
  item.Save();
} 
```

## <a name="accessing-the-work-item-reference-links"></a>Iş öğesi başvuru bağlantılarına erişme
 Bağlantılara aşağıdaki gibi erişebilirsiniz:

```
//Get:
string linkString = element.GetReference(ReferenceConstants.WorkItem);
// Set:
element.AddReference(ReferenceConstants.WorkItem, linkString, true);

```

 Biçimi `linkString` :

 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`

 burada:

- Sunucunuzun URI 'SI şöyle olacaktır:

   `http://tfServer:8080/tfs/projectCollection`

   Büyük/küçük harf önemlidir `projectCollection` .

- `RepositoryGuid` TFS bağlantınızdan elde edilebilir:

  ```csharp
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;
  RepositoryGuid= tpc.InstanceId;

  ```

  Başvurular hakkında daha fazla bilgi için bkz. [UML model öğelerine başvuru dizeleri iliştirme](../modeling/attach-reference-strings-to-uml-model-elements.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft. TeamFoundation. WorkItemTracking. Client. WorkItemStore](/previous-versions/visualstudio/visual-studio-2013/bb179850(v=vs.120))
- [Model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md)
- [Model öğelerine başvuru dizeleri ekleme](../modeling/attach-reference-strings-to-uml-model-elements.md)
- [Modelleme uzantısı tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)
- [UML API ile programlama](../modeling/programming-with-the-uml-api.md)
