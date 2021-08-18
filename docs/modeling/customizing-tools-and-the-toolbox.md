---
title: Araçları ve Araç Kutusunu Özelleştirme
description: Kullanıcıların modellerine eklemesini istediğiniz öğeler için araç kutusu öğelerini nasıl tanımlamanız gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cb444f1f3378f62061e4116967e4fc0f525860e92e44234e571c8fb3f2e51275
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411151"
---
# <a name="customizing-tools-and-the-toolbox"></a>Araçları ve Araç Kutusunu Özelleştirme

Kullanıcıların modellerine eklemesini istediğiniz öğeler için araç kutusu öğeleri tanımlamanız gerekir. İki tür araç vardır: öğe araçları ve bağlantı araçları. Oluşturulan tasarımcıda, kullanıcı şekilleri diyagrama sürüklemek için bir öğe aracı ve şekiller arasında bağlantı çizmek için bir bağlantı aracı da seçerek bir öğe aracından seçim yapabilirsiniz. Genel olarak, öğe araçları kullanıcıların modellerine etki alanı sınıflarının örneklerini eklemesine, bağlantı araçları ise etki alanı ilişkilerinin örneklerini eklemesine izin verilmektedir.

## <a name="how-the-toolbox-is-defined"></a><a name="ToolboxDef"></a> Araç kutusu nasıl tanımlanır?
 DSL Gezgini'nde Düzenleyici düğümünü ve altındaki düğümleri genişletin. Genellikle aşağıdakine benzer bir hiyerarşi görünür:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

DSL Gezgini'nin bu bölümünde şunları sekleyebilirsiniz:

- Yeni sekmeler oluşturun. Sekmeler, araç kutusunda bölüm başlıklarını tanımlar.

- Yeni araçlar oluşturun.

- Araçları kopyalayıp yapıştırın.

- Araçları listede yukarı veya aşağı taşıma.

- Sekmeleri ve araçları silin.

> [!IMPORTANT]
> DSL Gezgini'ne öğe eklemek veya yapıştırmak için yeni düğümün yer alan öğesini sağ tıklatın. Örneğin, bir araç eklemek için Araçlar düğümüne değil sekmeye **sağ** tıklayın. Sekme eklemek için Düzenleyici düğümüne **sağ** tıklayın.

Her **aracın Araç** Kutusu Simgesi özelliği 16x16 bit eşlem dosyasına başvurur. Bu dosyalar genellikle **Dsl\Resources klasöründe** tutulur.

Bir öğe aracının **Class** özelliği somut bir etki alanı sınıfına başvurur. Varsayılan olarak, araç bu sınıfın örneklerini oluşturacak. Ancak, aracın öğe grupları veya farklı türlerde öğeler oluşturması için kod yazabilirsiniz.

Bir **bağlantı aracının Connection Builder** özelliği, aracın bağlanabilirsiniz öğe türlerini ve aralarında hangi ilişkileri oluşturduğu tanımlayan bir bağlantı oluşturucuya başvurur. Bağlantı oluşturucuları DSL Gezgini'nde düğüm olarak tanımlanır. Etki alanı ilişkilerini tanımladığınız zaman bağlantı oluşturucuları otomatik olarak oluşturulur, ancak bunları özelleştirmek için kod yazabilirsiniz.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Araç kutusuna araç eklemek için

1. Bir şekil sınıfı oluşturduktan ve bir etki alanı sınıfına eşledikten sonra genellikle bir öğe aracı oluşturmanız gerekir.

     Bağlayıcı sınıfını oluşturduktan ve bir başvuru ilişkisiyle eşledikten sonra genellikle bir bağlayıcı aracı oluşturmanız gerekir.

2. DSL Gezgini'nde Düzenleyici **düğümünü ve** Araç Kutusu **Sekmeleri düğümünü** genişletin.

     Araç kutusu sekme düğümüne sağ tıklayın ve ardından Yeni Öğe Aracı **Ekle veya Yeni** Bağlantı Aracı **Ekle'ye tıklayın.**

3. Araç Kutusu Simgesi özelliğini 16x16 bit eşlem değerine başvurmak için ayarlayın. 

     Yeni bir simge tanımlamak için **Dsl\Resources** klasöründeki Çözüm Gezgini bit eşlem dosyası oluşturun. Dosyanın şu özellik değerlerine sahip olması gerekir: **Derleme Eylemi**  =  **İçeriği**; **Çıkış Dizinine Kopyalama**  =  **kopyalamayın.**

4. **Bir öğe aracı için:** Bir şekle eşlenmiş somut bir etki alanı sınıfına başvurmak için aracın **Class** özelliğini ayarlayın.

     **Bağlayıcı aracı için:** Aracın **Connection Builder** özelliğini açılan listede sunulan öğelerden biri olarak ayarlayın. Bir bağlayıcıyı bir etki alanı ilişkisiyle eşleyenin bağlantı oluşturucuları otomatik olarak oluşturulur. Yakın zamanda bir bağlayıcı oluşturduysanız normalde ilişkili bağlantı oluşturucusu'nu seçersiniz.

5. DSL'yi test etmek için F5 veya CTRL+F5 tuşlarına basın ve Visual Studio örnek model dosyasını açın. Yeni aracın araç kutusunda görünmesi gerekir. Yeni bir öğe oluşturduğundan emin olmak için diyagrama sürükleyin.

     Araç görünmüyorsa deneysel aracı Visual Studio. Başlat menüsünde Windows  **2010 Deneysel Örneği'Microsoft Visual Studio sıfırla'yı çalıştırın.** Derleme menüsünde **Çözümü Yeniden** **Oluştur'a tıklayın.** Ardından DSL'i yeniden test etmek.

## <a name="customizing-element-tools"></a><a name="customizing"></a> Öğe Araçlarını Özelleştirme
 Varsayılan olarak, araç belirtilen sınıfın tek bir örneğini oluşturacak, ancak bunu iki şekilde değiştirebilirsiniz:

- Diğer sınıflarda Öğe Birleştirme Yönergelerini tanımlayın, bu sınıfların yeni örneklerini kabul etmelerini ve yeni öğe oluşturulduğunda ek bağlantılar oluşturmalarını sağlar. Örneğin, kullanıcının bir Açıklamayı başka bir öğeye bırakmasına ve böylece ikisi arasında bir başvuru bağlantısı oluşturmasına izin veebilirsiniz.

     Bu özelleştirmeler, kullanıcı bir öğeyi yapıştırarak veya sürükler ve bıraksa ne olacağını da etkiler.

     Daha fazla bilgi için [bkz. Öğe Oluşturma ve Taşımayı Özelleştirme.](../modeling/customizing-element-creation-and-movement.md)

- Araç, öğe grupları oluşturacak şekilde özelleştirmek için kod yazın. Araç, Geçersiz kılabilirsiniz ToolboxHelper.cs'de yöntemlerle başlatılır. Daha fazla bilgi için [bkz. Bir Araçtan Öğe Grupları Oluşturma.](#groups)

## <a name="creating-groups-of-elements-from-a-tool"></a><a name="groups"></a> Araçtan Öğe Grupları Oluşturma
 Her öğe aracı, oluşturması gereken öğelerin bir prototipini içerir. Varsayılan olarak, her öğe aracı tek bir öğe oluşturur, ancak tek bir araçla bir grup ilgili nesne oluşturmak da mümkündür. Bunu yapmak için, aracı ilgili öğeleri içeren <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> bir ile başlatabilirsiniz.

 Aşağıdaki örnek, transistor türünün olduğu bir DSL'den alınarak alınır. Her Transistor üç adlandırılmış Terminale sahip olur. Transistors için öğe aracı dört model öğesi ve üç ilişki bağlantısı içeren bir prototip depolar. Kullanıcı aracı diyagrama sürüklerse prototip örneği ve model köküne bağlıdır.

 Bu kod **Dsl\GeneratedCode\ToolboxHelper.cs içinde tanımlanan bir yöntemi geçersiz kılar.**

 Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. Program Kodunda [Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="customizing-connection-tools"></a><a name="connections"></a> Bağlantı Araçlarını Özelleştirme
 Genellikle, yeni bir bağlayıcı sınıfı oluşturmak için bir öğe aracı oluşturmanız gerekir. Alternatif olarak, iki uç türünün ilişkinin türünü belirlemesi için bir aracı aşırı yük devredebilirsiniz. Örneğin, hem ilişki oluşturma hem de ilişki oluşturma Person-Person bir bağlantı Person-Town tanımlayabilirsiniz.

 Bağlantı araçları bağlantı oluşturucularını çağırır. Kullanıcıların oluşturulan tasarımcıda öğeleri nasıl bağlaylarını belirtmek için bağlantı oluşturucuları kullanın. Bağlantı oluşturucuları bağlanacak öğeleri ve aralarında oluşturulan bağlantının türlerini belirtir.

 Etki alanı sınıfları arasında bir başvuru ilişkisi oluşturulduğunda, otomatik olarak bir bağlantı oluşturucu oluşturulur. Bir bağlantı aracını eşlerken bu bağlantı oluşturucusu'nu kullanabilirsiniz. Bağlantı araçları oluşturma hakkında daha fazla bilgi için [bkz. Araç Kutusunu Yapılandırma.](../modeling/customizing-tools-and-the-toolbox.md)

 Varsayılan bağlantı oluşturucusu'nu farklı bir kaynak ve hedef türü aralığıyla ilgilenerek farklı ilişki türleri oluşturarak değiştirebilirsiniz.

 Ayrıca bağlantının kaynak ve hedef sınıflarını belirtmek, yapılacak bağlantı türünü tanımlamak ve bağlantının oluşturulmasıyla ilişkili diğer eylemleri yapmak için bağlantı oluşturucuları için özel kod da yazabilirsiniz.

### <a name="the-structure-of-connection-builders"></a>Bağlantı Oluşturucularının Yapısı
 Bağlantı oluşturucuları, etki alanı ilişkisini, kaynak ve hedef öğeleri belirten bir veya daha fazla bağlantı bağlantısı yönergesi içerir. Örneğin, Görev Yöneticisi Flow şablonunda DSL Gezgini'nde **CommentReferencesSubjectsBuilder'ı** **görebilir.** Bu bağlantı oluşturucu, **CommentReferencesSubjects** etki alanı ilişkisiyle eşlenen **CommentReferencesSubjects** adlı bir bağlantı bağlantı yönergesi içerir. Bu bağlantı bağlantısı yönergesi, etki alanı sınıfını ve etki alanı sınıfına yönelik bir hedef rol yönergesi ile birlikte bir `Comment` kaynak rol `FlowElement` yönergesi içerir.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Kaynak ve Hedef Rolleri Kısıtlamak için Bağlantı Oluşturucularını Kullanma
 Belirli sınıfların kaynak rolde veya belirli bir etki alanı ilişkisinin hedef rolünde oluşumunu kısıtlamak için bağlantı oluşturucuları kullanabilirsiniz. Örneğin, başka bir etki alanı sınıfıyla etki alanı ilişkisi olan bir temel etki alanı sınıfına sahip olabilir, ancak temel sınıfın türetilmiş tüm sınıflarının bu ilişkide aynı rollere sahip olması istemeyebilirsiniz. Görev Flow çözümünde, doğrudan **FlowElement** soyut etki alanı sınıfından devralan dört somut etki alanı sınıfı **(StartPoint**, **EndPoint**, **MergeBranch** ve **Eşitleme)** ve bundan dolaylı olarak devralınan iki somut etki alanı sınıfı **(Task** **ve ObjectInState)** vardır. Ayrıca, hem **kaynak Flow** hem de hedef rolünde **FlowElement** etki alanı sınıflarını alan bir başvuru ilişkisi vardır. Ancak, **bir EndPoint** etki alanı sınıfının örneği **bir Flow** ilişkisinin örneğinin kaynağı veya **StartPoint** sınıfının örneği, bir Flow ilişkisinin **örneğinin hedefi** olmalıdır. **FlowBuilder** bağlantı oluşturucusu, **hangi** etki alanı sınıflarının kaynak rolü (**Görev**, **MergeBranch**, **StartPoint** ve **Eşitleme**) oynata ve hedef rolü (**MergeBranch,** **Uç** Nokta ve Eşitleme ) oynatanı belirten Flow adlı bir bağlantı bağlantısı yönergesine **sahip.**

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Birden Çok Bağlantı Bağlama Yönergesi Bağlan Oluşturucular
 Bir bağlantı oluşturucuya birden fazla bağlantı bağlantısı yönergesi ekleme. Bu, etki alanı modelinin bazı karmaşıklıklarını kullanıcılardan gizlemeye ve **Toolbox'ın** çok dağınık hale gelen durumlarını ortadan kaldırır. Tek bir bağlantı oluşturucuya birkaç farklı etki alanı ilişkisi için bağlantı bağlantısı yönergeleri ebilirsiniz. Ancak, yaklaşık olarak aynı işlevi gerçekleştirecekleri zaman etki alanı ilişkilerini birleştirmeniz gerekir.

 Task Flow çözümünde, **Flow** bağlantı aracı hem Flow hem de **ObjectFlow** **etki alanı** ilişkilerinin örneklerini çizmek için kullanılır. **FlowBuilder bağlantı** oluşturucusu, daha önce **açıklanan Flow** bağlantı bağlantısı yönergesine ek olarak ObjectFlow adlı iki bağlantı bağlantısı **yönergesine de sahip.** Bu **yönergeler, objectFlow** ilişkisinin bir örneğinin ObjectInState etki alanı sınıfının örnekleri arasında veya **bir ObjectInState** örneğinden bir Görevin örneğine çekilene, ancak bir  Görevin iki örneği arasında ya da bir Görev örneğinden **bir ObjectInState** örneğine çekilene kadar belirtmektedir.   Ancak, bir görev **Flow** bir görevin iki örneği arasında **çizilir.** Task Flow çözümünü derler ve çalıştırırsanız, **bir ObjectInState** örneğinden bir Görev örneğine **Flow** çiziminin  **ObjectFlow** örneği oluşturduğuna ancak bir Görevin iki örneği arasında bir  **Flow** çiziminin bir **Flow** örneği oluşturduğuna dikkat edersiniz.

### <a name="custom-code-for-connection-builders"></a>Bağlantı oluşturucuları için özel kod
 Kullanıcı arabiriminde, bağlantı oluşturucuların farklı tür özelleştirmesini tanımlayan dört onay kutusu vardır:

- Kaynak veya hedef rol yönergesinde **özel kabul etme** onay kutusu

- Kaynak veya hedef rol yönergesinde **özel Bağlan** onay kutusu

- Connect yönergesinde **özel Bağlan** onay kutusu kullanılır

- bağlantı oluşturucusunun **özel** özelliği

  Bu özelleştirmeleri yapmak için bazı program kodları sağlamanız gerekir. Sağlamanız gereken kodu öğrenmek için, bu kutulardan birini işaretleyin, tüm Şablonları Dönüştür ' e tıklayın ve çözümünüzü oluşturun. Bir hata raporu neden olur. Hangi kodun ekleneceğini açıklayan bir açıklama görmek için hata raporuna çift tıklayın.

> [!NOTE]
> Özel kod eklemek için, GeneratedCode klasörlerindeki kod dosyalarından ayrı bir kod dosyasında kısmi bir sınıf tanımı oluşturun. Çalışmanızı kaybetmemek için, oluşturulan kod dosyalarını düzenlememelisiniz. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Özel bağlantı kodu oluşturma
 Her bağlantı bağlama yönergesinde **kaynak rol yönergeleri** sekmesi, sürüklediğiniz türlerden tanımlar. Benzer şekilde, **hedef rol yönergeleri** sekmesi de sürüklediğiniz türleri tanımlar. Her tür için, **özel kabul** bayrağını ayarlayıp daha sonra ek kod sağlayarak bağlantıya izin verip vermeyeceğinizi (Bu bağlantı bağlama yönergesi için) belirtebilirsiniz.

 Bağlantı yapıldığında ne olduğunu da özelleştirebilirsiniz. Örneğin, yalnızca sürükleme işleminin belirli bir sınıfa veya belirli bir sınıftan olduğu, bir bağlantı bağlantı yönergesinin bir bağlantı bağlantı yönergesinin veya tüm FlowBuilder bağlantı oluşturucusunun olduğu durumu özelleştirebilirsiniz. Bu seçeneklerin her biri için uygun düzeyde özel bayraklar ayarlayabilirsiniz. Tüm şablonları dönüştürdüğünüzde ve çözümü oluşturmaya çalıştığınızda, hata iletileri oluşturulan koddaki açıklamalara doğrudan yönlendirir. Bu açıklamalar ne sağlamanız gerektiğini belirler.

 Bileşenler diyagramı örneğinde bağlantı etki alanı ilişkisine yönelik bağlantı Oluşturucu, bağlantı noktaları arasında yapılabilecek bağlantıları kısıtlamak için özelleştirilir. Aşağıdaki çizimde yalnızca öğelerden öğelere bağlantı yapabileceğiniz gösterilmektedir `OutPort` `InPort` , ancak bileşenleri birbirlerine iç içe yerleştirebilirsiniz.

 **Iç Içe geçmiş bir bileşenden giden bağlantı noktasına gelen bağlantı**

 ![Bağlantı Oluşturucu](../modeling/media/connectionbuilder_3.png)

 Bu nedenle, bir bağlantının iç içe geçmiş bir bileşenden giden bağlantı noktasına gelebileceğini belirtmek isteyebilirsiniz. Böyle bir bağlantı belirtmek için, Aşağıdaki çizimlerde gösterildiği **gibi,** **InPort** türü Için kaynak rol ve **çıkış noktası** türü ' nde hedef rol olarak **özel kabul et** ' i ayarlayın:

 **DSL gezgininde bağlantı Bağlan yönergesi**

 ![Bağlantı Oluşturucu görüntüsü](../modeling/media/connectionbuilder_4a.png)

 **DSL ayrıntıları penceresinde bağlantı Bağlan yönergesi**

 ![DSL ayrıntıları penceresinde bağlantı bağlama yönergesi](../modeling/media/connectionbuilder_4b.png)

 Daha sonra, ConnectionBuilder sınıfında Yöntemler sağlamanız gerekir:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Örneğin, kullanıcıların üst-alt bağlantılarla döngüler oluşturmasını engellemek için benzer kodu kullanabilirsiniz. Bu kısıtlamalar ' Hard ' kısıtlamaları olarak değerlendirilir, çünkü kullanıcılar bunları dilediğiniz zaman ihlal edemez. Ayrıca, kullanıcıların kaydedebilecekleri geçersiz konfigürasyonlar oluşturarak geçici olarak atlayabilecekleri ' geçici ' doğrulama denetimleri de oluşturabilirsiniz.

### <a name="good-practice-in-defining-connection-builders"></a>Bağlantı oluşturucularını tanımlamaya yönelik iyi bir uygulama
 Yalnızca kavramsal olarak ilişkili olmaları durumunda farklı türlerde ilişkiler oluşturmak için bir bağlantı oluşturucuyu tanımlamanız gerekir. Görev akışı örneğinde, görevler arasında ve ayrıca görevler ve nesneler arasında akış oluşturmak için aynı oluşturucuyu kullanırsınız. Ancak, açıklamalar ve görevler arasında ilişkiler oluşturmak için aynı oluşturucunun kullanılması kafa karıştırıcı olur.

 Birden çok ilişki türü için bir bağlantı Oluşturucu tanımlarsanız, aynı kaynak ve hedef nesne çiftinden birden fazla türle eşleşmemesini güvence altına almalısınız. Aksi takdirde, sonuçlar tahmin edilemez olur.

 ' Hard ' kısıtlamalarını uygulamak için özel kod kullanın, ancak kullanıcıların geçici olarak geçersiz bağlantılar yapıp yapamayacağını göz önünde bulundurmanız gerekir. Olmaları gerekiyorsa, kullanıcılar değişiklikleri kaydetmeye çalıştıklarında bağlantıların doğrulanması için kısıtlamaları değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğe Oluşturma ve Hareketini Özelleştirme](../modeling/customizing-element-creation-and-movement.md)
- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Devre şemaları örnek DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
