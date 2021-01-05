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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b84f638876270658be2f08a7e375540f0329a1d6
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729346"
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

    1. Çözümü yeniden derlemek için **F5** tuşuna basın. Visual Studio 'nun deneysel örneği açıldığında DSL 'nin bir örneğini açın.

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

6. Yeni bir kod dosyasında, alıcı sınıf için kısmi bir sınıf yazın ve yöntemi geçersiz kılın `MergeRelate` . Temel yöntemi çağırmayı unutmayın. Örneğin:

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

10. Çözümü derleyin ve çalıştırın. Visual Studio 'nun yeni bir örneği belirir.

11. **Çözüm Gezgini**' de Sample. mydsl ' yi açın. Diyagram ve **ComponentLanguage araç kutusu** görünür.

12. **Araç kutusundan** bir **giriş bağlantı noktasını** başka bir **giriş bağlantı noktasına sürükleyin.** Ardından, bir **outputport** değerini bir **ınputport** 'a ve sonra başka bir **outputport**'a sürükleyin.

     Kullanılamayan işaretçiyi görmemelisiniz ve yeni **giriş bağlantı noktasını** var olan bir üzerine bırakabilirsiniz. Yeni **giriş bağlantı noktasını** seçin ve **bileşen** üzerindeki başka bir noktaya sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Araçları ve Araç Kutusunu Özelleştirme](../modeling/customizing-tools-and-the-toolbox.md)
- [Devre şemaları örnek DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
