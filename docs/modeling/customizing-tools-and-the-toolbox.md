---
title: Araçları ve Araç Kutusunu Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e8e9fc3a9ecbadc47c3390d2d4a9b504a316658
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589727"
---
# <a name="customizing-tools-and-the-toolbox"></a>Araçları ve Araç Kutusunu Özelleştirme

Kullanıcıların modellerine eklemesini sağlamak istediğiniz öğeler için araç kutusu öğelerini tanımlamanız gerekir. İki tür araç vardır: öğe araçları ve bağlantı araçları. Oluşturulan tasarımcıda, Kullanıcı şekilleri diyagrama sürüklemek için bir öğe aracı seçebilir ve şekiller arasında bağlantı çizmek için bir bağlantı aracı seçebilir. Genel olarak, öğe araçları kullanıcıların, modellerine etki alanı sınıfı örnekleri eklemesine izin verir ve bağlantı araçları, etki alanı ilişkilerinin örneklerini eklemesini sağlar.

## <a name="ToolboxDef"></a>Araç kutusu nasıl tanımlanır
 DSL Gezgini 'nde, düzenleyici düğümünü ve altındaki düğümleri genişletin. Genellikle şuna benzer bir hiyerarşi görürsünüz:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

DSL Gezgini 'nin bu bölümünde şunları yapabilirsiniz:

- Yeni sekmeler oluşturun. Sekmeler araç kutusunda bölüm başlıklarını tanımlar.

- Yeni araçlar oluşturun.

- Araç Kopyala ve Yapıştır.

- Araçları listede yukarı veya aşağı taşıyın.

- Sekmeleri ve araçları silin.

> [!IMPORTANT]
> DSL Gezgininde öğe eklemek veya yapıştırmak için, yeni düğümün alt öğesine sağ tıklayın. Örneğin, bir araç eklemek için **Araçlar** düğümünü değil, sekmesine sağ tıklayın. Sekme eklemek için **Düzenleyici** düğümüne sağ tıklayın.

Her aracın **araç kutusu simgesi** özelliği bir 16x16 bit eşlem dosyasına başvurur. Bu dosyalar genellikle **Dsl\resources** klasöründe tutulur.

Bir öğe aracının **Class** özelliği somut bir etki alanı sınıfına başvurur. Varsayılan olarak, araç bu sınıfın örneklerini oluşturur. Ancak, aracın öğe grupları veya farklı türlerde öğeler oluşturmasını sağlamak için kod yazabilirsiniz.

Bir bağlantı aracının **bağlantı Oluşturucu** özelliği, aracın ne tür öğeleri bağlayabileceğini ve bunlar arasında hangi ilişkilerin oluşturduğunu tanımlayan bir bağlantı Oluşturucusu anlamına gelir. Bağlantı oluşturucular DSL Gezgininde düğüm olarak tanımlanır. Bağlantı oluşturucular, etki alanı ilişkileri tanımladığınızda otomatik olarak oluşturulur, ancak bunları özelleştirmek için kod yazabilirsiniz.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Araç kutusuna araç eklemek için

1. Genellikle bir şekil sınıfı oluşturduktan ve onu bir etki alanı sınıfıyla eşleştirdikten sonra bir öğe aracı oluşturursunuz.

     Genellikle bir bağlayıcı sınıfı oluşturup bir başvuru ilişkisiyle eşleştirdikten sonra bir bağlayıcı aracı oluşturursunuz.

2. DSL Gezgini ' nde **Düzenleyici** düğümünü ve **araç kutusu sekmeleri** düğümünü genişletin.

     Bir araç kutusu sekme düğümüne sağ tıklayın ve ardından **Yeni öğe Ekle aracı** veya **Yeni bağlantı ekle**' ye tıklayın.

3. **Araç kutusu simgesi** özelliğini 16x16 bit eşlem 'e başvuracak şekilde ayarlayın.

     Yeni bir simge tanımlamak istiyorsanız, **Dsl\resources** klasöründe Çözüm Gezgini bir bit eşlem dosyası oluşturun. Dosya aşağıdaki özellik değerlerine sahip olmalıdır: **derleme eylemi** **içerik** = ; **Çıkış dizinine kopyala** = **kopyalamayın**.

4. **Bir öğe aracı için:** Bir şekle eşlenen somut bir etki alanı sınıfına başvuracak şekilde aracın **sınıf** özelliğini ayarlayın.

     **Bağlayıcı aracı için:** Aracının **bağlantı Oluşturucu** özelliğini, açılan listede sunulan öğelerden birine ayarlayın. Bağlantı oluşturucular, bir bağlayıcıyı bir etki alanı ilişkisiyle eşleştirdiğinizde otomatik olarak oluşturulur. Yakın zamanda bir bağlayıcı oluşturduysanız, normalde ilişkili bağlantı oluşturucuyu seçersiniz.

5. DSL 'yi test etmek için F5 veya CTRL + F5 tuşlarına basın ve Visual Studio 'nun deneysel örneğinde örnek bir model dosyası açın. Yeni araç araç kutusunda görünmelidir. Yeni bir öğe oluşturduğunu doğrulamak için onu diyagrama sürükleyin.

     Araç görünmezse, deneysel Visual Studio 'Yu durdurun. Windows **Başlat** menüsünde **Microsoft Visual Studio 2010 Deneysel örneğini Sıfırla**' yı çalıştırın. Üzerinde **derleme** menüsünde tıklatın **çözümü yeniden derle**. Ardından DSL 'yi yeniden test edin.

## <a name="customizing"></a>Öğe araçlarını özelleştirme
 Varsayılan olarak, araç belirtilen sınıfın tek bir örneğini oluşturur, ancak bunu iki şekilde değiştirebilirsiniz:

- Diğer sınıflarda öğe birleştirme yönergeleri tanımlayın, bu sınıfın yeni örneklerini kabul etmelerini ve yeni öğe oluşturulduğunda ek bağlantılar oluşturmalarına olanak tanır. Örneğin, kullanıcının başka bir öğeye açıklama bırakmaya izin verebilir ve bu nedenle ikisi arasında bir başvuru bağlantısı oluşturabilirsiniz.

     Bu özelleştirmeler Ayrıca Kullanıcı bir öğeyi yapıştırdığınızda veya sürüklediğinde ne olacağını da etkiler.

     Daha fazla bilgi için bkz. [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).

- Araç, öğe grupları oluşturabilmesi için özelleştirmek üzere kod yazın. Araç, geçersiz kılabileceğiniz ToolboxHelper.cs içindeki yöntemlerle başlatılır. Daha fazla bilgi için, bkz. [bir araçtan öğe grupları oluşturma](#groups).

## <a name="groups"></a>Bir araçtan öğe grupları oluşturma
 Her öğe aracında oluşturulması gereken öğelerin bir prototipi bulunur. Varsayılan olarak, her öğe aracı tek bir öğe oluşturur, ancak aynı zamanda bir araçla ilişkili nesneler grubu oluşturmak da mümkündür. Bunu yapmak için, aracı ilgili öğeleri içeren bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> başlatın.

 Aşağıdaki örnek, bir tür dönüştürme işlemi olan bir DSL 'den alınmıştır. Her bir Transislatör üç adlı terminalde sahiptir. Transtemciler için öğe Aracı, dört model öğesi ve üç ilişki bağlantısı içeren bir prototipi depolar. Kullanıcı, aracı diyagram üzerine sürüklediğinde, prototip oluşturulur ve model köküne bağlanır.

 Bu kod, **Dsl\GeneratedCode\ToolboxHelper.cs**içinde tanımlanan bir yöntemi geçersiz kılar.

 Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

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

## <a name="connections"></a>Bağlantı araçlarını özelleştirme
 Genellikle, yeni bir bağlayıcı sınıfı oluşturduğunuzda bir öğe aracı oluşturursunuz. Alternatif olarak, iki ucunun türlerin ilişki türünü belirlemesine izin vererek bir aracı aşırı yükleyebilirsiniz. Örneğin, hem kişi-kişi ilişkileri hem de kişi-şehir ilişkileri oluşturabileceğiniz bir bağlantı aracı tanımlayabilirsiniz.

 Bağlantı araçları bağlantı oluşturucularını çağırır. Kullanıcıların oluşturulan tasarımcıda öğeleri nasıl bağlayabilirler belirtmek için bağlantı oluşturucuları kullanın. Bağlantı oluşturucular, bağlanoluşturulabilecek öğeleri ve aralarında oluşturulan bağlantı türünü belirtir.

 Etki alanı sınıfları arasında bir başvuru ilişkisi oluşturduğunuzda, bağlantı Oluşturucu otomatik olarak oluşturulur. Bağlantı aracını eşlediğinizde Bu bağlantı oluşturucusunu kullanabilirsiniz. Bağlantı araçları oluşturma hakkında daha fazla bilgi için bkz. [araç kutusunu yapılandırma](../modeling/customizing-tools-and-the-toolbox.md).

 Varsayılan bağlantı oluşturucuyu, farklı bir kaynak ve hedef türleri aralığıyla uğraşabilmesi ve farklı türde ilişkiler oluşturabilmeniz için değiştirebilirsiniz.

 Bağlantı oluşturuculara yönelik kaynak ve hedef sınıfları belirtmek için Ayrıca bağlantı oluşturucuları için özel kod yazabilir, yapılacak bağlantı türünü tanımlayabilir ve bir bağlantının oluşturulmasıyla ilişkili diğer işlemleri gerçekleştirebilirsiniz.

### <a name="the-structure-of-connection-builders"></a>Bağlantı oluşturucuların yapısı
 Bağlantı oluşturucular, etki alanı ilişkisini ve kaynak ve hedef öğeleri belirten bir veya daha fazla bağlantı bağlama yönergesi içerir. Örneğin, görev akışı çözüm şablonunda, **DSL Gezgini**'Nde **CommentReferencesSubjectsBuilder** ' ı görebilirsiniz. Bu bağlantı Oluşturucusu, **commentreferencesilgilileri**adlı bir bağlantı bağlama yönergesi içerir ve bu ad alanı Ilişkisi **commentreferenceskonularıyla**eşlenir. Bu bağlantı bağlama yönergesi, `Comment` etki alanı sınıfına işaret eden bir kaynak rol yönergesi ve `FlowElement` etki alanı sınıfına işaret eden bir hedef rol yönergesi içerir.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Kaynak ve hedef rolleri kısıtlamak için bağlantı oluşturucuları kullanma
 Kaynak roldeki veya belirli bir etki alanı ilişkisinin hedef rolündeki belirli sınıfların oluşumunu kısıtlamak için bağlantı oluşturucularını kullanabilirsiniz. Örneğin, başka bir etki alanı sınıfıyla bir etki alanı ilişkisine sahip olan bir temel etki alanı sınıfınız olabilir, ancak taban sınıfın tüm türetilmiş sınıflarının bu ilişkide aynı rollere sahip olmasını istemeyebilirsiniz. Görev akışı çözümünde, doğrudan soyut etki alanı sınıfından (StartPoint, **uç nokta**, MergeBranch ve eşitleme **), bundan**dolaylı olarak miras alan iki somut etki alanı sınıfı**vardır (** **StartPoint**, Endpoint, **MergeBranch**ve **Synchronization**) **.** Ayrıca, hem kaynak rolünde hem de hedef rolde **aynı etki alanı** sınıflarını alan bir **akış** başvurusu ilişkisi vardır. Ancak, bir **uç nokta** etki alanı sınıfının bir örneği bir **akış** ilişkisi örneğinin kaynağı olmamalıdır, ya da bir **StartPoint** sınıfının örneği bir **akış** ilişkisi örneğinin hedefi olmalıdır. **FlowBuilder** bağlantı oluşturucusunun, kaynak rolünü (**görev**, **MergeBranch**, **StartPoint**ve **Synchronization**) çalabildiğini ve hedef rolünü (**MergeBranch**, **uç nokta**ve **eşitleme**) çalabildiğini belirten **Flow** adlı bir bağlantı bağlama yönergesi vardır.

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Birden çok bağlantı bağlama yönergesi olan bağlantı oluşturucular
 Bir bağlantı oluşturucusuna birden fazla bağlantı bağlama yönergesi ekleyebilirsiniz. Bu, etki alanı modelinin bazı karmaşıklıklarını gizlemenize ve **araç kutusunun** çok karışık olmasını sağlamanıza yardımcı olabilir. Tek bir bağlantı oluşturucusuna birkaç farklı etki alanı ilişkisi için bağlantı bağlama yönergeleri ekleyebilirsiniz. Ancak, etki alanı ilişkilerini yaklaşık olarak aynı işlevi gerçekleştirirken birleştirmeniz gerekir.

 Görev akışı çözümünde **akış** bağlantısı aracı hem **Flow** hem de **objectflow** etki alanı ilişkilerinin örneklerini çizmek için kullanılır. **FlowBuilder** bağlantı Oluşturucu, daha önce açıklanan **Flow** bağlantı bağlama yönergesinin yanı sıra **objectflow**adlı iki bağlantı bağlama yönergesi içerir. Bu yönergeler, **objectinstate** etki alanı sınıfının örnekleri arasında ya **da bir** **ObjectInState** örneğinden bir görevin örneğine veya **bir görevin bir** örneğinden bir **Objectinstate**örneğine **değil, bir** **objectflow** ilişkisinin bir örneğinin çizildiğini belirtir. Ancak, bir **akış** ilişkisinin bir örneği bir **görevin**iki örneği arasında çizilebilir. Görev akışı çözümünü derleyip çalıştırırsanız, bir **Objectinstate** örneğinden bir **görevin** örneğine **akış** çizimi için bir **objectflow**örneği oluşturur, ancak bir **görevin** iki örneği arasında bir **akış** çizmek bir **akış**örneği oluşturur.

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

 Bileşenler diyagramı örneğinde bağlantı etki alanı ilişkisine yönelik bağlantı Oluşturucu, bağlantı noktaları arasında yapılabilecek bağlantıları kısıtlamak için özelleştirilir. Aşağıdaki çizimde yalnızca `OutPort` öğelerinden `InPort` öğelerine bağlantı yapabileceğiniz gösterilmektedir, ancak bileşenleri birbirine iç içe geçirebilirsiniz.

 **Iç Içe geçmiş bir bileşenden giden bağlantı noktasına gelen bağlantı**

 ![Bağlantı Oluşturucu](../modeling/media/connectionbuilder_3.png)

 Bu nedenle, bir bağlantının iç içe geçmiş bir bileşenden giden bağlantı noktasına gelebileceğini belirtmek isteyebilirsiniz. Böyle bir bağlantı belirtmek için, Aşağıdaki çizimlerde gösterildiği **gibi,** **InPort** türü Için kaynak rol ve **çıkış noktası** türü ' nde hedef rol olarak **özel kabul et** ' i ayarlayın:

 **DSL Gezgininde bağlantı bağlama yönergesi**

 ![Bağlantı Oluşturucu görüntüsü](../modeling/media/connectionbuilder_4a.png)

 **DSL ayrıntıları penceresinde bağlantı bağlama yönergesi**

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
