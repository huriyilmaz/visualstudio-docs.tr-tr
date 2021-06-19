---
title: Öğe Oluşturma ve Hareketini Özelleştirme
description: Bir öğenin, araç kutusundan veya bir yapıştırma ya da taşıma işleminde diğerine nasıl sürüklendiğini öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 42339c532db3442d5fb5c5da3b51d94801a0907d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389403"
---
# <a name="customizing-element-creation-and-movement"></a>Öğe Oluşturma ve Hareketini Özelleştirme

Bir öğenin, araç kutusundan veya bir yapıştırma ya da taşıma işleminde diğerine sürüklenmesi için izin verebilirsiniz. Taşınan öğelerin, belirttiğiniz ilişkileri kullanarak hedef öğelere bağlı olmasını sağlayabilirsiniz.

Bir öğe birleştirme yönergesi (EMD), bir model öğe başka bir model öğesiyle *birleştirildiğinde* ne olacağını belirtir. Aşağıdaki durumlarda bu gerçekleşir:

- Kullanıcı araç kutusundan diyagrama veya bir şekle sürükler.

- Kullanıcı gezgin veya bölme şeklindeki bir Ekle menüsünü kullanarak bir öğe oluşturur.

- Kullanıcı bir öğeyi bir kulvardan diğerine taşıdıkça.

- Kullanıcı bir öğe yapıştırır.

- Program kodunuz, öğe birleştirme yönergesini çağırır.

Oluşturma işlemleri kopyalama işlemlerinden farklı görünse de, bu işlemler aslında aynı şekilde çalışır. Bir öğe eklendiğinde (örneğin, araç kutusundan), bir prototipi çoğaltılır. Prototip, modelin başka bir bölümünden kopyalanmış öğelerle aynı şekilde modelde birleştirilir.

EMD 'nin sorumluluğu, bir nesne veya nesne grubunun modelde belirli bir konuma birleştirilmesi gerektiğine karar vermektedir. Özellikle, birleştirilmiş grubu modele bağlamak için hangi ilişkilerin oluşturulması gerektiğine karar verir. Ayrıca, özellikleri ayarlamak ve ek nesneler oluşturmak için özelleştirebilirsiniz.

![Bir E M D, yeni bir öğenin nasıl ekleneceğini belirleyen bir öğe ve bunların başvuru ilişkilerine göre daha önce ve sonra gösteren diyagram.](../modeling/media/dsl-emd_merge.png)

Bir katıştırma ilişkisi tanımladığınızda bir EMD otomatik olarak oluşturulur. Bu varsayılan EMD, kullanıcılar üst öğeye yeni alt örnekler eklerken ilişki örneği oluşturur. Bu varsayılan kullanıcıları, örneğin özel kod ekleyerek değiştirebilirsiniz.

Ayrıca, kullanıcıların birleştirilmiş ve alan sınıfların farklı kombinasyonlarını sürükleyebilmesine veya yapıştırmasına izin vermek için DSL tanımına kendi EMI 'leri ekleyebilirsiniz.

## <a name="defining-an-element-merge-directive"></a>Öğe birleştirme yönergesi tanımlama

Etki alanı sınıflarına, etki alanı ilişkilerine, şekillere, bağlayıcılara ve diyagramlara öğe birleştirme yönergeleri ekleyebilirsiniz. Bunları, alıcı etki alanı sınıfı altında DSL Gezgini 'ne ekleyebilir veya bulabilirsiniz. Alan sınıfı, zaten modelde olan ve yeni veya kopyalanmış öğenin birleştirileceği öğenin etki alanı sınıfıdır.

![Dizin oluşturma sınıfı ve alt sınıflar için geçerlidir seçeneği belirlenmiş olan ExampleElement ile eklenmekte olan bir E M D 'yi gösteren DSL Gezgini ekran görüntüsü.](../modeling/media/dsl-emd_details.png)

**Dizin oluşturma sınıfı** , alıcı sınıfının üyeleriyle birleştirilebilen öğelerin alan sınıfıdır. Alt **sınıflar Için geçerli** olarak ayarlanmadığınız müddetçe, dizin oluşturma sınıfının alt sınıflarının örnekleri de bu EMD tarafından birleştirilir.

İki tür birleştirme yönergesi vardır:

- **Işlem birleştirme** yönergesi, yeni öğenin ağaca bağlanması gereken ilişkiyi belirtir.

- **Ileri birleştirme** yönergesi, yeni öğeyi, genellikle bir üst öğe olan başka bir alma öğesine yeniden yönlendirir.

Birleştirme yönergeleri için özel kod ekleyebilirsiniz:

- Küme, belirli bir dizin oluşturma öğesinin belirli bir örneğinin hedef öğeyle birleştirilmesi gerekip gerekmediğini anlamak için kendi kodunuzu eklemek için **özel kabul et kullanır** . Kullanıcı araç kutusundan sürüklendiğinde "geçersiz" işaretçisi, kodunuzun birleştirmeye izin vermez olduğunu gösterir.

   Örneğin, birleştirmeye yalnızca alma öğesi belirli bir durumda olduğunda izin verebilirsiniz.

- Küme, birleştirme gerçekleştirildiğinde modelde yapılan değişiklikleri tanımlamak için kendi kodunu sağlamak üzere **özel birleştirme kullanır** .

   Örneğin, modeldeki yeni konumundaki verileri kullanarak birleştirilmiş öğedeki özellikleri ayarlayabilirsiniz.

> [!NOTE]
> Özel birleştirme kodu yazarsanız, bu, yalnızca bu EMD kullanılarak gerçekleştirilen birleştirmeleri etkiler. Aynı nesne türünü birleştirmek için veya EMD 'yi kullanmadan bu nesneleri oluşturan başka özel kod varsa, özel birleştirme kodunuzun etkilenmemesi gerekir.
>
> Yeni bir öğenin veya yeni ilişkinin her zaman özel kodunuz tarafından işlendiğinden emin olmak istiyorsanız, `AddRule` katıştırma ilişkisi üzerinde bir oluşturma ve `DeleteRule` öğenin etki alanı sınıfı üzerinde bir öğesi tanımlamayı düşünün. Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Örnek: özel kod olmadan EMD tanımlama

Aşağıdaki örnek, kullanıcıların araç kutusundan varolan bir şekle sürükleyerek bir öğe ve bağlayıcıyı aynı anda oluşturmalarına olanak sağlar. Örnek DSL tanımına bir EMD ekler. Bu değişiklikten önce, kullanıcılar, araçları diyagrama sürükleyebilir, ancak mevcut şekillerin üzerine sürükleyebilirler.

Kullanıcılar ayrıca öğeleri diğer öğelere de yapıştırabilirsiniz.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Kullanıcıların aynı anda bir öğe ve bağlayıcı oluşturmasına izin vermek için

1. **En küçük dil** çözümü şablonunu kullanarak yenı bir DSL oluşturun.

    Bu DSL 'yi çalıştırdığınızda, şekiller arasında şekil ve bağlayıcı oluşturmanıza olanak sağlar. Yeni bir **ExampleElement** şeklini araç kutusundan varolan bir şekle sürükleyemezsiniz.

2. Kullanıcıların öğeleri şekillere birleştirmelerine izin vermek için `ExampleElement` , `ExampleElement` etki alanı sınıfında yeni bir emd oluşturun:

   1. **DSL Gezgini**' nde, **etki alanı sınıfları**' nı genişletin. Sağ tıklayın `ExampleElement` ve ardından **Yeni öğe birleştirme yönergesi Ekle**' ye tıklayın.

   2. Yeni EMTıD 'nin ayrıntılarını görmek için **DSL ayrıntıları** penceresinin açık olduğundan emin olun. (Menü: **Görünüm**, **diğer pencereler**, **DSL ayrıntıları**.)

3. Nesneler üzerinde neleri birleştirilebilen öğelerin sınıfını tanımlamak için DSL ayrıntıları penceresinde **Dizin oluşturma sınıfını** ayarlayın `ExampleElement` .

    Bu örnek için, `ExampleElements` kullanıcının yeni öğeleri varolan öğelere sürükleyebilmesi için öğesini seçin.

    Dizin oluşturma sınıfının DSL Gezgini 'nde EMTıD 'nin adı olduğuna dikkat edin.

4. **Bağlantılar oluşturarak işlem birleştirme** altında iki yol ekleyin:

   - Bir yol, yeni öğeyi üst modele bağlar. Girmeniz gereken yol ifadesi, ana modele eklenen ilişki aracılığıyla varolan öğeden gider. Son olarak, yeni öğenin atanacağı yeni bağlantıda rolü belirtir. Yol aşağıdaki gibidir:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - Diğer yol, yeni öğeyi var olan öğesine bağlar. Yol ifadesi, başvuru ilişkisini ve yeni öğenin atanacağı rolü belirtir. Bu yol aşağıdaki gibidir:

      `ExampleElementReferencesTargets.Sources`

      Yol gezintisi aracını her bir yolu oluşturmak için kullanabilirsiniz:

      1. **Yollarda bağlantılar oluşturarak işlem birleştirme** altında öğesine tıklayın **\<add path>** .

      2. Liste öğesinin sağ tarafındaki aşağı açılan oka tıklayın. Ağaç görünümü görüntülenir.

      3. Belirtmek istediğiniz yolu oluşturmak için ağaçtaki düğümleri genişletin.

5. DSL 'yi test etme:

   1. Çözümü yeniden derlemek ve çalıştırmak için **F5** tuşuna basın.

        Oluşturulan kod, yeni DSL tanımına uymak üzere metin şablonlarından güncelleştirildiğinden, yeniden oluşturma normalden daha uzun sürer.

   2. Visual Studio 'nun deneysel örneği başlatıldığında, DSL 'nizin bir model dosyasını açın. Örnek öğeleri oluşturun.

   3. **Örnek öğe** aracından varolan bir şekle sürükleyin.

        Yeni bir şekil görüntülenir ve bağlayıcı ile var olan şekle bağlanır.

   4. Varolan bir şekli kopyalayın. Başka bir şekil seçin ve yapıştırın.

        İlk şeklin bir kopyası oluşturulur.  Yeni bir ada sahiptir ve bağlayıcı ile ikinci şekle bağlanır.

Bu yordamdan aşağıdaki noktalara dikkat edin:

- Öğe birleştirme yönergeleri oluşturarak herhangi bir öğe sınıfının diğerini kabul etmesine izin verebilirsiniz. ALD, alan etki alanı sınıfında oluşturulur ve kabul edilen etki alanı sınıfı **Dizin sınıfı** alanında belirtilir.

- Yollar tanımlayarak, yeni öğeyi mevcut modele bağlamak için hangi bağlantıların kullanılması gerektiğini belirtebilirsiniz.

     Belirttiğiniz bağlantılar tek bir katıştırma ilişkisi içermelidir.

- EMD, araç kutusundan oluşturmayı ve ayrıca yapıştırma işlemlerini etkiler.

     Yeni öğeler oluşturan özel kod yazarsanız, yöntemini kullanarak EMD 'yi açık bir şekilde çağırabilirsiniz `ElementOperations.Merge` . Bu, kodunuzun yeni öğeleri diğer işlemlerle aynı şekilde modele bağlacağından emin olur. Daha fazla bilgi için bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Örnek: bir EMD 'ye özel kabul kodu ekleme

EMD 'ye özel kod ekleyerek, daha karmaşık birleştirme davranışı tanımlayabilirsiniz. Bu basit örnek, kullanıcının diyagrama sabit sayıda öğe eklemesini önler. Örnek, bir katıştırma ilişkisine eşlik eden varsayılan EMD 'yi değiştirir.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Kullanıcının neleri ekleyebileceğini kısıtlamak için özel kabul kodu yazmak için

1. **Minimal dil** çözümü şablonunu kullanarak bir DSL oluşturun. DSL tanımı diyagramını açın.

2. DSL Gezgini'nde, Etki **Alanı Sınıfları ,**, Öğe Birleştirme `ExampleModel` **Yönergeleri'ni genişletin.** adlı öğe birleştirme yönergesi `ExampleElement` seçin.

     Bu EMD, örneğin araç kutusundan `ExampleElement` sürükleyerek kullanıcının modelde yeni nesneler oluşturmasına izin verir.

3. DSL Ayrıntıları **penceresinde Özel** kabul **kullanır'ı seçin.**

4. Çözümü yeniden derleyin. Oluşturulan kod modelden güncelleştirilecek olduğundan bu durum her zamankinden daha uzun sürer.

     Şöyle bir derleme hatası bildiriliyor: "Company.ElementMergeSample.ExampleElement, CanMergeExampleElement için bir tanım içeriyor..."

     yöntemini `CanMergeExampleElement` uygulamalısiniz.

5. Dsl projesinde yeni bir kod **dosyası** oluşturun. İçeriğini aşağıdaki kodla değiştirin ve ad alanını projenizin ad alanı olarak değiştirin.

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

    Bu basit örnek, üst modelle birleştirilecek öğelerin sayısını kısıtlar. Daha ilginç koşullar için yöntemi, alıcı nesnenin özelliklerinin ve bağlantılarının herhangi birini inceler. Ayrıca, bir içinde yürütülen birleştirme öğelerinin özelliklerini de <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> inceler. hakkında daha fazla bilgi `ElementGroupPrototypes` için [bkz. Kopyalama Davranışını Özelleştirme.](../modeling/customizing-copy-behavior.md) Bir modeli okumak için kod yazma hakkında daha fazla bilgi için bkz. Program Kodunda [Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

6. DSL'i test etmek için:

    1. Çözümü yeniden inşa etmek için **F5** tuşuna basın. Deneysel Visual Studio, DSL örneğinizi açın.

    2. Yeni öğeleri çeşitli yollarla oluşturun:

        - Örnek Öğe **aracından** diyagrama sürükleyin.

        - Örnek Model **Gezgini'nde** kök düğüme sağ tıklayın ve ardından Yeni Örnek **Öğesi Ekle'ye tıklayın.**

        - Diyagramda bir öğeyi kopyalayıp yapıştırın.

    3. Modele dörtten fazla öğe eklemek için bu yöntemlerden herhangi birini kullanamayabilirsiniz. Bunun nedeni, hepsinin Öğe Birleştirme Yönergesi'nin kullanımıdır.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Örnek: EMD'ye Özel Birleştirme kodu ekleme

Özel birleştirme kodunda, kullanıcı bir aracı sürükler veya öğeye yapıştırsa ne olacağını tanımlayabilirsiniz. Özel birleştirmeyi tanımlamanın iki yolu vardır:

1. Özel **Birleştirme kullanır'ı** ayarlayın ve gerekli kodu girin. Kodunuz, oluşturulan birleştirme kodunun yerini almaktadır. Birleştirmenin ne yaptığını tamamen yeniden tanımlamak için bu seçeneği kullanın.

2. yöntemini `MergeRelate` ve isteğe bağlı olarak yöntemini geçersiz `MergeDisconnect` kılın. Bunu yapmak için etki alanı sınıfının **Generates Double Derived** özelliğini ayarlayabilirsiniz. Kodunuz, temel sınıfta oluşturulan birleştirme kodunu çağırabilir. Birleştirme gerçekleştirildikten sonra ek işlemler gerçekleştirmek için bu seçeneği kullanın.

   Bu yaklaşımlar yalnızca bu EMD kullanılarak gerçekleştirilen birleştirmeleri etkiler. Birleştirilen öğenin oluşturula tüm yollarını etkilerse, alternatif olarak ekleme ilişkisi ve birleştirilmiş etki alanı sınıfı üzerinde bir `AddRule` `DeleteRule` tanımlamaktır. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

### <a name="to-override-mergerelate"></a>MergeRelate'ı geçersiz kılmak için

1. DSL tanımında, kod eklemek istediğiniz EMD'yi tanımlandığından emin olun. 2. 2. bölümde açıklandığı gibi yollar ekleyebilir ve özel kabul kodu tanımlayabilirsiniz.

2. DslDefinition diyagramında birleştirmenin alıcı sınıfını seçin. Genellikle ekleme ilişkisinin kaynak ucundaki sınıfıdır.

     Örneğin, En Düşük Dil çözümünden oluşturulan bir DSL'de öğesini `ExampleModel` seçin.

3. Özellikler penceresinde **Çift** **Türetilen Oluştur'a true** **olarak ayarlayın.**

4. Çözümü yeniden derleyin.

5. **Dsl\Generated Files\DomainClasses.cs içeriğini inceleme.** adlı yöntemleri ara ve `MergeRelate` içeriklerini incele. Bu, kendi sürümlerinizi yazmanıza yardımcı olur.

6. Yeni bir kod dosyasında, alıcı sınıfı için kısmi bir sınıf yazın ve yöntemini geçersiz `MergeRelate` kılın. Temel yöntemi çağırmayı unutmayın. Örneğin:

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

### <a name="to-write-custom-merge-code"></a>Özel Birleştirme kodu yazmak için

1. **Dsl\Generated Code\DomainClasses.cs içinde** adlı yöntemleri `MergeRelate` inceler. Bu yöntemler, yeni bir öğe ile mevcut model arasında bağlantılar oluşturma.

    Ayrıca adlı yöntemleri de `MergeDisconnect` incele. Bu yöntemler, silinecek öğenin bağlantısını modelden kaldırıyor.

2. **DSL Gezgini'nde,** özelleştirmek istediğiniz Öğe Birleştirme Yönergesi'ni seçin veya oluşturun. DSL Ayrıntıları **penceresinde Özel** Birleştirme **Kullanır'ı ayarlayın.**

    Bu seçeneği ayarsanız İşlem Birleştirme **ve Birleştirmeyi** **İleriye Doğru seçenekleri** yoksayılır. Bunun yerine kodunuz kullanılır.

3. Çözümü yeniden derleyin. Oluşturulan kod dosyaları modelden güncelleştirilecek olduğundan, bu her zamankinden daha uzun sürer.

    Hata iletileri görüntülenir. Oluşturulan kodda yönergeleri görmek için hata iletilerine çift tıklayın. Bu yönergeler sizden `MergeRelate` *YourDomainClass* ve `MergeDisconnect` *YourDomainClass* olmak iki yöntem sağlar

4. Yöntemleri ayrı bir kod dosyasında kısmi sınıf tanımına yazın. Daha önce incelediğiniz örnekler, ihtiyacınız olan şeyi önermeli.

   Özel birleştirme kodu doğrudan nesne ve ilişki oluşturan kodu etkilemez ve diğer EMD'leri etkilemez. Öğenin nasıl oluşturulduktan bağımsız olarak ek değişikliklerinizin gerçekleştiril olduğundan emin olmak için bir ve yazmayı `AddRule` göz önünde `DeleteRule` bulundurarak. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

## <a name="redirecting-a-merge-operation"></a>Birleştirme İşlemlerini Yeniden Yönlendirme

Bir ileri birleştirme yönergesi, birleştirme işlemi hedefini yeniden yönlendirmektedir. Genellikle yeni hedef, ilk hedefin ekleme üst öğesidir.

Örneğin, bileşen diyagramı şablonuyla oluşturulmuş bir DSL'de Bağlantı noktaları Bileşenler'e katıştırılabilir. Bağlantı noktaları, bileşen şeklinin kenarında küçük şekiller olarak görüntülenir. Kullanıcı, Bağlantı Noktası aracını bileşen şekline sürükleyerek bağlantı noktaları oluşturur. Ancak bazen kullanıcı bileşen yerine bağlantı noktası aracını yanlışlıkla mevcut bir bağlantı noktasına sürükler ve işlem başarısız olur. Mevcut birkaç bağlantı noktası olduğunda bu kolay bir hatadır. Kullanıcının bu sorunu önlemesine yardımcı olmak için, bağlantı noktalarının mevcut bir bağlantı noktasına sürüklenmelerine izin ve ardından eylemin ana bileşene yönlendirilmesine izin veebilirsiniz. İşlem, hedef öğe bileşen gibi çalışır.

Bileşen Modeli çözümünde bir iletme birleştirme yönergesi oluşturabilirsiniz. Özgün çözümü derler ve çalıştırsanız, kullanıcıların herhangi bir  sayıda Giriş  Bağlantı Noktası veya Çıkış Bağlantı Noktası öğesini **Araç** Kutusundan Bileşen öğesine sürükleyeblerini **görüyorsanız.** Ancak, bir bağlantı noktasını mevcut bir bağlantı noktasına sürükleyip sürükleyemezler. Kullanılamıyor işaretçisi, bu taşımanın etkinleştirilmemiş olduğunu belirtir. Ancak, var olan bir Giriş Bağlantı Noktasına istenemeyen bir bağlantı noktasının Bileşen öğesine iletilecek şekilde bir iletme birleştirme **yönergesi oluşturabilirsiniz.** 

### <a name="to-create-a-forward-merge-directive"></a>İleriye doğru birleştirme yönergesi oluşturmak için

1. Bileşen [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Modeli şablonunu kullanarak bir çözüm oluşturun.

2. DslDefinition.dsl'i açarak **DSL** Gezgini'ni görüntüleyin.

3. DSL **Gezgini'nde Etki** Alanı **Sınıfları'ni genişletin.**

4. **ComponentPort** soyut etki alanı sınıfı, hem InPort hem de **OutPort'un** **temel sınıfıdır.** **ComponentPort'a sağ tıklayın** ve ardından Add **New Element Merge Directive (Yeni Öğe Birleştirme Yönergesi Ekle) öğesine tıklayın.**

    Öğe Birleştirme **Yönergeleri düğümü** altında yeni bir Öğe **Birleştirme Yönergesi düğümü** görünür.

5. Öğe Birleştirme **Yönergesi düğümünü** seçin ve **DSL Ayrıntıları penceresini** açın.

6. Dizin oluşturma sınıfı listesinde **ComponentPort öğesini seçin.**

7. Birleştirmeyi **farklı bir etki alanı sınıfına ilet'i seçin.**

8. Yol seçim listesinde **ComponentPort** öğesini genişletin, **ComponentHasPorts öğesini genişletin** ve bileşen'i **seçin.**

    Yeni yol aşağıdakine benzer:

    **ComponentHasPorts.Component/!Component**

9. Çözümü kaydedin ve ardından araç çubuğundaki en sağdaki düğmeye tıklayarak **Çözüm Gezgini** dönüştürebilirsiniz.

10. Çözümü derleyin ve çalıştırın. Yeni bir örnek Visual Studio görüntülenir.

11. Bu **Çözüm Gezgini** Sample.mydsl'i açın. Diyagram ve **ComponentLanguage Araç Kutusu** görüntülenir.

12. Bir Giriş **Bağlantı Noktasını Araç** **Kutusundan başka bir** Giriş Bağlantı Noktasına **sürükleyin.** Ardından bir **OutputPort'ı** **bir InputPort'a ve** ardından başka bir **OutputPort'a sürükleyin.**

     Kullanılamıyor işaretçisini görmeli ve yeni Giriş Bağlantı Noktasını mevcut **işaretçiye** bırakabilirsiniz. Yeni Giriş Bağlantı **Noktasını seçin** ve Bileşeni'nin başka bir noktasına **sürükleyin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Araçları ve Araç Kutusunu Özelleştirme](../modeling/customizing-tools-and-the-toolbox.md)
- [Bağlantı Hattı Diyagramları örnek DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
