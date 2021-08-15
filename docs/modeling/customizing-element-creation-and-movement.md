---
title: Öğe Oluşturma ve Hareketini Özelleştirme
description: Bir öğenin araç kutusundan veya yapıştırma ya da taşıma işlemiyle başka bir öğeye sürüklenmelerine nasıl izin verebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3ee0cfc7a87d8e035dfdd0f1337c1e440f710c93083dbbe4137e0469f0346d65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271504"
---
# <a name="customizing-element-creation-and-movement"></a>Öğe Oluşturma ve Hareketini Özelleştirme

Bir öğenin araç kutusundan veya yapıştırma ya da taşıma işlemiyle başka bir öğeye sürüklenmelerine izin veebilirsiniz. Belirttiğiniz ilişkileri kullanarak, taşınan öğelerin hedef öğelere bağlı olarak taşınmalarını s ilişkisini s ilişkisine sahip olabilirsiniz.

Öğe birleştirme yönergesi (EMD), bir model öğesi başka bir model öğesiyle *birleştir olduğunda* ne olacağını belirtir. Aşağıdaki durumlarda bu gerçekleşir:

- Kullanıcı araç kutusundan diyagrama veya şekle sürükler.

- Kullanıcı, gezgindeki Ekle menüsünü veya bölme şeklini kullanarak bir öğe oluşturur.

- Kullanıcı bir öğeyi bir kulandan diğerine taşır.

- Kullanıcı bir öğeyi yapıştırıyor.

- Program kodunuz öğe birleştirme yönergesine çağrır.

Oluşturma işlemleri kopyalama işlemlerinden farklı görünse de aslında aynı şekilde çalışır. Bir öğe ekleniyorsa, örneğin araç kutusundan bir prototipi çoğaltılır. Prototip, modelin başka bir parçasından kopyalanan öğelerle aynı şekilde modelle birleştirilir.

EMD'nin sorumluluğu, bir nesnenin veya nesne grubunun modeldeki belirli bir konumda nasıl birleştirileceklerine karar vermektir. Özellikle, birleştirilen grubu modele bağlamaya ilişkin olarak hangi ilişkilerin örneklendirilecek olduğuna karar verir. Ayrıca özellikleri ayarlamak ve ek nesneler oluşturmak için de özelleştirebilirsiniz.

![E M D yeni bir öğenin nasıl ekli olduğunu belirlerken öğe ağacına ve başvuru ilişkilerine bakmadan önce ve sonra bir gösteren diyagram.](../modeling/media/dsl-emd_merge.png)

Ekleme ilişkisi tanımladığınız zaman BIR EMD otomatik olarak oluşturulur. Bu varsayılan EMD, kullanıcılar üst öğeye yeni alt örnekler eklese de ilişkinin bir örneğini oluşturur. Bu varsayılan EMD'leri, örneğin özel kod ekleyerek değiştirebilirsiniz.

Ayrıca, kullanıcıların birleştirilen ve alan sınıfların farklı birleşimlerini sürüklemesine veya yapıştırmasına izin vermeleri için DSL tanımına kendi EMD'lerinizi ekebilirsiniz.

## <a name="defining-an-element-merge-directive"></a>Öğe Birleştirme Yönergesi Tanımlama

Etki alanı sınıfları, etki alanı ilişkileri, şekiller, bağlayıcılar ve diyagramlar için öğe birleştirme yönergeleri ekleme. Bunları DSL Gezgini'nde alan etki alanı sınıfının altında ekleyebilir veya bulabilirsiniz. Alan sınıf, modelde zaten bulunan ve yeni veya kopyalanan öğenin birleştirilecek olduğu öğenin etki alanı sınıfıdır.

![Dizin oluşturma sınıfı olarak ExampleElement'in seçili olduğu ve Alt sınıflar için geçerlidir seçeneğinin işaretli olduğu bir E M D'nin eklendiğinde gösterilen DSL Gezgini'nin ekran görüntüsü.](../modeling/media/dsl-emd_details.png)

**Dizin Oluşturma Sınıfı,** alıcı sınıfın üyeleriyle birleştirilecek öğelerin etki alanı sınıfıdır. Alt sınıflara uygulanır'i False olarak ayarlamadıkça Dizin Oluşturma Sınıfının alt sınıf örnekleri de bu EMD **ile birleştirilir.**

İki tür birleştirme yönergesi vardır:

- İşlem **Birleştirme** yönergesi, yeni öğenin ağaçla bağlantılı olması gereken ilişkileri belirtir.

- **İleriYeni Birleştirme** yönergesi, yeni öğeyi genellikle üst öğe olan başka bir alıcı öğeye yeniden yönlendirmektedir.

Birleştirme yönergelerine özel kod eklemek için:

- Dizin **oluşturma öğesinin** belirli bir örneğinin hedef öğeyle birleştirilecek olup olmadığını belirlemek üzere kendi kodunuzu eklemek için Özel kabul kullanır'a ayarlayın. Kullanıcı araç kutusundan sürüklenerek "geçersiz" işaretçisi, kodunuzun birleştirmeye izin verip izin ve e-postaya izin verip ekleyemediklerini gösterir.

   Örneğin, birleştirmeye yalnızca alıcı öğe belirli bir durumda olduğunda izin veebilirsiniz.

- Birleştirme **gerçekleştirilirken** modelde yapılan değişiklikleri tanımlamak üzere kendi kodu sağlamak için özel birleştirme kullanır'ı ayarlayın.

   Örneğin, modeldeki yeni bir konumdan verileri kullanarak birleştirilmiş öğede özellikleri ayarlayın.

> [!NOTE]
> Özel birleştirme kodu yazarsanız, yalnızca bu EMD kullanılarak gerçekleştirilen birleştirmeleri etkiler. Aynı nesne türünü birleştiren başka EMD'ler varsa veya EMD'yi kullanmadan bu nesneleri oluşturan başka özel kod varsa, bunlar özel birleştirme kodunuz tarafından etkilenmez.
>
> Yeni bir öğenin veya yeni ilişkinin her zaman özel kodunuz tarafından işlendiğinden emin olmak için ekleme ilişkisinde ve öğesinin etki alanı sınıfında bir `AddRule` `DeleteRule` tanımlamayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

## <a name="example-defining-an-emd-without-custom-code"></a>Örnek: Özel kod olmadan EMD tanımlama

Aşağıdaki örnek, kullanıcıların aynı anda araç kutusundan mevcut bir şekle sürükleyerek bir öğe ve bağlayıcı oluşturmasına olanak sağlar. Örnek DSL Tanımına bir EMD ekler. Bu değişiklik öncesinde kullanıcılar araçları diyagrama sürükleyip var olan şekillere sürükleyemeyebilirsiniz.

Kullanıcılar ayrıca öğeleri diğer öğelere de yapıştırabilirsiniz.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Kullanıcıların aynı anda bir öğe ve bağlayıcı oluşturmasına izin verme

1. Minimal Language çözüm şablonunu kullanarak yeni **bir** DSL oluşturun.

    Bu DSL'i çalıştırarak şekiller arasında şekiller ve bağlayıcılar oluşturmanıza olanak sağlar. Araç kutusundan yeni **bir ExampleElement** şeklini mevcut bir şekle sürükleyebilirsiniz.

2. Kullanıcıların öğeleri şekiller üzerinde birleştirmesine `ExampleElement` izin için etki alanı sınıfında yeni bir EMD `ExampleElement` oluşturun:

   1. **DSL Gezgini'nde,** Etki Alanı **Sınıfları'ni genişletin.** öğesine sağ tıklayın `ExampleElement` ve ardından Add New Element Merge Directive **(Yeni Öğe Birleştirme Yönergesi Ekle) öğesine tıklayın.**

   2. Yeni **EMD'nin** ayrıntılarını görmek için DSL Ayrıntıları penceresinin açık olduğundan emin olun. (Menü: **Görünüm,** **Diğer Windows**, DSL **Ayrıntıları**.)

3. Hangi **öğe sınıflarının nesnelere** birleştirileceklerini tanımlamak için DSL Ayrıntıları penceresinde Dizin oluşturma sınıfını `ExampleElement` ayarlayın.

    Bu örnekte, kullanıcının yeni `ExampleElements` öğeleri mevcut öğelere sürüklemesi için öğesini seçin.

    Indexing sınıfının DSL Gezgini'nde EMD'nin adı haline geldi.

4. Bağlantıları **oluşturarak birleştirmeyi işleme altına** iki yol ekleyin:

   - Bir yol, yeni öğeyi üst modele bağlar. Girmeniz gereken yol ifadesi, mevcut öğeden üst modele ekleme ilişkisi aracılığıyla yukarı doğru ilerler. Son olarak, yeni öğenin atandığı yeni bağlantıda rolü belirtir. Yol aşağıdaki gibidir:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - Diğer yol, yeni öğeyi mevcut öğeye bağlar. Yol ifadesi, başvuru ilişkisini ve yeni öğenin atandığı rolü belirtir. Bu yol aşağıdaki gibidir:

      `ExampleElementReferencesTargets.Sources`

      Her yolu oluşturmak için yol gezinti aracını kullanabilirsiniz:

      1. Yollarda **bağlantılar oluşturarak birleştirmeyi işleme altında,**'ye **\<add path>** tıklayın.

      2. Liste öğesinin sağ tarafından açılan oka tıklayın. Bir ağaç görünümü görüntülenir.

      3. Belirtmek istediğiniz yolu oluşturmak için ağaçtaki düğümleri genişletin.

5. DSL'i test etmek için:

   1. Çözümü yeniden oluşturma ve çalıştırma için **F5** tuşuna basın.

        Oluşturulan kod, metin şablonlarından yeni DSL Tanımına uygun şekilde güncelleştirilecek olduğundan, yeniden oluşturma her zamankinden daha uzun sürer.

   2. Deneme örneği Visual Studio DSL'nizin model dosyasını açın. Bazı örnek öğeler oluşturun.

   3. Örnek Öğe **aracından** mevcut bir şekle sürükleyin.

        Yeni bir şekil görünür ve bir bağlayıcı ile mevcut şekle bağlanır.

   4. Mevcut bir şekli kopyalayın. Başka bir şekil seçip yapıştırın.

        İlk şeklin bir kopyası oluşturulur.  Yeni bir adı vardır ve bağlayıcı ile ikinci şekle bağlanır.

Bu yordamdan aşağıdaki noktalara dikkat edin:

- Öğe Birleştirme Yönergeleri oluşturarak, herhangi bir öğe sınıfının diğer tüm sınıflarını kabul etmelerine izin verilmiştir. EMD, alan etki alanı sınıfında oluşturulur ve kabul edilen etki alanı sınıfı Dizin sınıfı **alanında** belirtilir.

- Yolları tanımlayarak, yeni öğeyi mevcut modele bağlamak için hangi bağlantıların kullan gerektiğini belirtebilirsiniz.

     Belirttiğiniz bağlantılar bir ekleme ilişkisi içermeli.

- EMD hem araç kutusundan oluşturma hem de yapıştırma işlemlerini etkiler.

     Yeni öğeler oluşturan özel kod yazarsanız, yöntemini kullanarak EMD'i açıkça `ElementOperations.Merge` çağırabilirsiniz. Bu, kodunuzun yeni öğeleri diğer işlemlerle aynı şekilde modele bağlar. Daha fazla bilgi için [bkz. Kopyalama Davranışını Özelleştirme.](../modeling/customizing-copy-behavior.md)

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Örnek: EMD'ye Özel Kabul Kodu Ekleme

EMD'ye özel kod ekleyerek daha karmaşık birleştirme davranışı tanımlayabilirsiniz. Bu basit örnek, kullanıcının diyagrama sabit sayıdan fazla öğe eklemesini önler. Örnek, ekleme ilişkisine eşlik eden varsayılan EMD'leri değiştirebilir.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Kullanıcının eklerini kısıtlamak için Özel Kabul Kodu yazmak için

1. Minimum Dil çözümü şablonunu kullanarak **DSL** oluşturun. DSL Tanım diyagramını açın.

2. DSL Gezgini ' nde, **etki alanı sınıfları**, `ExampleModel` **öğe birleştirme yönergeleri**' ni genişletin. Adlı öğe birleştirme yönergesini seçin `ExampleElement` .

     Bu EMD, kullanıcının modelde yeni nesneler oluşturma şeklini denetler `ExampleElement` , örneğin araç kutusundan sürükleyin.

3. **DSL ayrıntıları** penceresinde, **özel kabul et kullanır**' ı seçin.

4. Çözümü yeniden derleyin. Oluşturulan kod modelden güncelleştirileceği için bu işlem normalden daha uzun sürer.

     Bir derleme hatası bildirilecek, şuna benzer: "Company. ElementMergeSample. ExampleElement CanMergeExampleElement için bir tanım içermiyor..."

     Yöntemini uygulamanız gerekir `CanMergeExampleElement` .

5. **DSL** projesinde yeni bir kod dosyası oluşturun. İçeriğini aşağıdaki kodla değiştirin ve ad alanını projenizin ad alanı olarak değiştirin.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    Bu basit örnek, üst modelle birleştirilebilen öğelerin sayısını kısıtlar. Daha ilgi çekici koşullar için, yöntemi, alıcı nesnesinin özelliklerinden ve bağlantılarından birini denetleyebilir. Ayrıca, bir içinde taşınan birleştirme öğelerinin özelliklerini de denetleyebilir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Hakkında daha fazla bilgi için `ElementGroupPrototypes` bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md). Bir modeli okuyan kodun nasıl yazılacağı hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

6. DSL 'yi test etme:

    1. Çözümü yeniden derlemek için **F5** tuşuna basın. Visual Studio deneysel örneği açıldığında DSL 'nin bir örneğini açın.

    2. Çeşitli yollarla yeni öğeler oluşturun:

        - **Örnek öğe** aracından diyagram üzerine sürükleyin.

        - **Örnek Model Gezgini**' nde kök düğümüne sağ tıklayın ve ardından **Yeni örnek öğesi Ekle**' ye tıklayın.

        - Diyagramda bir öğe kopyalayıp yapıştırın.

    3. Modele dörtten fazla öğe eklemek için bu yolların hiçbirini kullanmediğinizi doğrulayın. Bunun nedeni, hepsi öğe birleştirme yönergesini Kullandır.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Örnek: bir EMD 'ye özel birleştirme kodu ekleme

Özel birleştirme kodunda, Kullanıcı bir araç sürüklediğinde veya bir öğenin üzerine yapıştırdığınızda ne olacağını belirleyebilirsiniz. Özel bir birleştirme tanımlamanın iki yolu vardır:

1. Ayarla **özel birleştirme kullanır** ve gerekli kodu sağlar. Kodunuz, oluşturulan birleştirme kodunun yerini almıştır. Birleştirmenin ne yaptığını tamamen yeniden tanımlamak istiyorsanız bu seçeneği kullanın.

2. `MergeRelate`Yöntemini ve isteğe bağlı olarak yöntemini geçersiz kılın `MergeDisconnect` . Bunu yapmak için, etki alanı sınıfının **Double türetilmiş** özelliğini oluştur ' u ayarlamanız gerekir. Kodunuz, temel sınıfta oluşturulan birleştirme kodunu çağırabilir. Birleştirme gerçekleştirildikten sonra ek işlemler gerçekleştirmek istiyorsanız bu seçeneği kullanın.

   Bu yaklaşımlar yalnızca bu EMD kullanılarak gerçekleştirilen birleştirmeleri etkiler. Birleştirilmiş öğenin oluşturulabileceği tüm yolları etkilemek istiyorsanız, `AddRule` ekleme ilişkisinde ve `DeleteRule` birleştirilmiş etki alanı sınıfında bir olan bir alternatif tanımlayın. Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Mergeregeç 'i geçersiz kılmak için

1. DSL tanımında, kod eklemek istediğiniz EMD 'yi tanımlamış olduğunuzdan emin olun. İsterseniz, yollar ekleyebilir ve önceki bölümlerde açıklandığı gibi özel kabul kodu tanımlayabilirsiniz.

2. DslDefinition diyagramında, birleştirmenin alma sınıfını seçin. Genellikle, bir katıştırma ilişkisinin kaynak sonundaki sınıftır.

     Örneğin, en düşük dil çözümünden oluşturulan bir DSL 'de öğesini seçin `ExampleModel` .

3. **Özellikler** penceresinde, **çift türetilmiş** öğesini **true** olarak ayarlayın.

4. Çözümü yeniden derleyin.

5. **Dsl\generated Files\DomainClasses.cs** içeriğini inceleyin. Adlı yöntemleri arayın `MergeRelate` ve içeriklerini inceleyin. Bu, kendi sürümlerinizi yazmanıza yardımcı olur.

6. Yeni bir kod dosyasında, alıcı sınıf için kısmi bir sınıf yazın ve yöntemi geçersiz kılın `MergeRelate` . Temel yöntemi çağırmayı unutmayın. Örnek:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>Özel birleştirme kodu yazmak için

1. **Dsl\generated Code\DomainClasses.cs** içinde adlı yöntemleri inceleyin `MergeRelate` . Bu yöntemler yeni bir öğe ve var olan model arasında bağlantılar oluşturur.

    Ayrıca, adlı yöntemleri inceleyin `MergeDisconnect` . Bu yöntemler, silinecek bir öğenin modelden bağlantısını kaldırın.

2. **DSL Gezgini**' nde özelleştirmek Istediğiniz öğe birleştirme yönergesini seçin veya oluşturun. **DSL ayrıntıları** penceresinde, ayarla **özel birleştirme kullanır**.

    Bu seçeneği belirlediğinizde, **Işlem birleştirme** ve **İleri birleştirme** seçenekleri yok sayılır. Bunun yerine kodunuz kullanılır.

3. Çözümü yeniden derleyin. Oluşturulan kod dosyaları modelden güncelleştirilemediğinden, bu işlem normalden daha uzun sürer.

    Hata iletileri görüntülenir. Oluşturulan koddaki yönergeleri görmek için hata iletilerine çift tıklayın. Bu yönergeler, `MergeRelate` *YourDomainClass* ve `MergeDisconnect` *YourDomainClass* olmak üzere iki yöntem vermenizi ister

4. Yöntemleri kısmi bir sınıf tanımına ayrı bir kod dosyasında yazın. Daha önce inceettiğiniz örneklerde ihtiyacınız olanları önermelisiniz.

   Özel birleştirme kodu doğrudan nesne ve ilişki oluşturan kodu etkilemez ve diğer kullanıcıları etkilemez. Ek değişikliklerinizin, öğenin oluşturulma şeklinden bağımsız olarak uygulandığından emin olmak için, `AddRule` bunun yerine bir ve yazmayı düşünün `DeleteRule` . Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Birleştirme Işlemini yeniden yönlendirme

İleri birleştirme yönergesi birleştirme işleminin hedefini yeniden yönlendirir. Genellikle, yeni hedef ilk hedefin gömme üst öğesidir.

Örneğin, bileşen diyagramı şablonuyla oluşturulmuş bir DSL 'de, bağlantı noktaları bileşenlere katıştırılır. Bağlantı noktaları, bileşen şeklinin kenarında küçük şekiller olarak görüntülenir. Kullanıcı, bağlantı noktası aracını bir bileşen şeklinin üzerine sürükleyerek bağlantı noktaları oluşturur. Ancak bazen Kullanıcı, bağlantı noktası aracını, bileşen yerine mevcut bir bağlantı noktasına yanlışlıkla sürükleymekte ve işlem başarısız olur. Bu, birkaç mevcut bağlantı noktası olduğunda kolay bir hata olur. Kullanıcının bu nuktans önlemek için, bağlantı noktalarının mevcut bir bağlantı noktası üzerine sürüklenip olmasını sağlayabilir, ancak eylemin üst bileşene yönlendirilmesini sağlayabilirsiniz. İşlem, hedef öğe bileşen gibi olarak da kullanılır.

Bileşen modeli çözümünde bir ileriye doğru birleştirme yönergesi oluşturabilirsiniz. Özgün çözümü derleyip çalıştırırsanız, kullanıcıların **araç kutusundan** herhangi bir sayıda **giriş bağlantı noktasını** veya **çıkış bağlantı noktası** öğesini bir **bileşen** öğesine sürükleyemeyeceğini görmeniz gerekir. Ancak, bir bağlantı noktasını mevcut bir bağlantı noktasına sürükleyeamazlar. Kullanılamayan işaretçi Bu taşımanın etkin olmadığı uyarıları uyarır. Ancak, bir ileriye doğru birleştirme yönergesi oluşturarak, yanlışlıkla varolan bir **giriş bağlantı noktasında** bırakılan bir bağlantı noktasının **bileşen** öğesine iletilmesini sağlayabilirsiniz.

### <a name="to-create-a-forward-merge-directive"></a>İleri birleştirme yönergesi oluşturmak için

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]Bileşen modeli şablonunu kullanarak bir çözüm oluşturun.

2. DslDefinition. dsl dosyasını açarak **DSL Gezginini** görüntüleyin.

3. **DSL Gezgini**' nde, **etki alanı sınıfları**' nı genişletin.

4. **ComponentPort** soyut etki alanı sınıfı, hem **InPort** hem de **OutPort** temel sınıfıdır. **ComponentPort** öğesine sağ tıklayın ve ardından **Yeni öğe birleştirme yönergesi Ekle**' ye tıklayın.

    **Öğe birleştirme yönergeleri** düğümünün altında yeni bir **öğe birleştirme yönergesi** düğümü görüntülenir.

5. **Öğe birleştirme yönergesi** düğümünü seçin ve **DSL ayrıntıları** penceresini açın.

6. Dizin oluşturma sınıfı listesinde, **ComponentPort**' ı seçin.

7. **Farklı bir etki alanı sınıfına ileri birleştirme** seçeneğini belirleyin.

8. Yol seçimi listesinde, **ComponentPort**' ı genişletin, **ComponentHasPorts**' yi genişletin ve **bileşen**' i seçin.

    Yeni yol şuna benzemelidir:

    **ComponentHasPorts. Component/! bileşeni**

9. Çözümü kaydedin ve sonra **Çözüm Gezgini** araç çubuğunda en sağdaki düğmeye tıklayarak şablonları dönüştürün.

10. Çözümü derleyin ve çalıştırın. Yeni bir örnek Visual Studio görüntülenir.

11. Bu **Çözüm Gezgini** Sample.mydsl'i açın. Diyagram ve **ComponentLanguage Araç Kutusu** görüntülenir.

12. Bir Giriş **Bağlantı Noktasını Araç** **Kutusundan başka bir** Giriş Bağlantı Noktasına **sürükleyin.** Ardından, bir **OutputPort'ı** **bir InputPort'a ve** ardından başka bir **OutputPort'a sürükleyin.**

     Kullanılamıyor işaretçisini görmeli ve yeni Giriş Bağlantı Noktasını mevcut **işaretçiye** bırakabilirsiniz. Yeni Giriş Bağlantı **Noktasını seçin** ve Bileşeni'nin başka bir noktasına **sürükleyin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Araçları ve Araç Kutusunu Özelleştirme](../modeling/customizing-tools-and-the-toolbox.md)
- [Bağlantı Hattı Diyagramları örnek DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
