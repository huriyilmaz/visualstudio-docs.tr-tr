---
title: Etki Alanına Özgü Dili Özelleştirme ve Genişletme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e6346f960efe1cd3af6ad9cbd070227d9171f01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654027"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Etki alanına özgü dili özelleştirme ve genişletme

Visual Studio modelleme ve görselleştirme SDK 'Sı (VMSDK), modelleme araçlarını tanımlayabilmeniz için çeşitli düzeyler sağlar:

1. DSL tanımı diyagramını kullanarak etki alanına özgü dil (DSL) tanımlayın. Bir diagrammatik gösterimi, okunabilir bir XML formu ve kod ve diğer yapıtlar oluşturmak için gereken temel araçları kullanarak hızlı bir şekilde DSL oluşturabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

2. DSL tanımının daha gelişmiş özelliklerini kullanarak DSL 'yi hassas olarak ayarlayın. Örneğin, Kullanıcı bir öğe oluşturduğunda ek bağlantıların görüntülenmesini sağlayabilirsiniz. Bu teknikler genellikle DSL tanımında elde edilir ve bazıları bazı program kodu satırları gerektirir.

3. Program kodunu kullanarak modelleme araçlarınızı genişletin. VMSDK, uzantılarınızı DSL tanımından oluşturulan kodla tümleştirmeyi kolaylaştırmak için özel olarak tasarlanmıştır. Daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> DSL tanımları dosyasını güncelleştirdiyseniz, çözümünüzü yeniden oluşturmadan önce **Çözüm Gezgini** araç çubuğundaki **Tüm Şablonları Dönüştür** ' e tıklamasını unutmayın.

## <a name="article-reference"></a>Makale başvurusu

|Bu etkiyi elde etmek için|Bu konuya başvurun|
|-|-|
|Kullanıcının bir şeklin renk ve stil özelliklerini ayarlamaya izin verin.|Şekle veya bağlayıcı sınıfına sağ tıklayın, **gösterilen Ekle**' nin üzerine gelin ve bir öğeye tıklayın.|
|Farklı model öğesi sınıfları diyagram üzerinde benzerdir, ilk yükseklik ve genişlik, renk ve araç ipuçları gibi özellikleri paylaşıyor.|Şekiller veya bağlayıcı sınıfları arasında devralmayı kullanın. Türetilmiş şekiller ve türetilmiş etki alanı sınıfları arasındaki eşlemeler üst öğelerinin eşleme ayrıntılarını alırlar.<br /><br /> Ya da, farklı etki alanı sınıflarını aynı şekil sınıfına eşleyin.|
|Model öğesi sınıfı farklı şekil bağlamları tarafından görüntülenir.|Birden fazla şekil sınıfını aynı etki alanı sınıfına eşleyin. Çözümü oluştururken, hata raporunu izleyin ve hangi şekle kullanılacağına karar vermek için istenen kodu sağlayın.|
|Şekil rengi veya yazı tipi gibi diğer özellikler geçerli durumu gösterir.|Bkz. [modeli yansıtmak Için şekilleri ve bağlayıcıları güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Gösterilen özellikleri güncelleştiren bir kural oluşturun. Bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Ya da bağlantı okları veya yazı tipi gibi görünmeyen özellikleri güncelleştirmek için Onilişkilendirilmemiş PropertyChanged () kullanın.|
|Durumu göstermek için şekildeki simge değişiklikleri.|DSL ayrıntıları penceresinde dekoratör eşlemesinin görünürlüğünü ayarlayın. Birçok görüntü dekoratlarını aynı konumda bulun. Bkz. [modeli yansıtmak Için şekilleri ve bağlayıcıları güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Veya `ImageField.GetDisplayImage()` geçersiz kılın. @No__t_0 örneğe bakın.|
|Herhangi bir şekil üzerinde arka plan resmi ayarlama|Sabitlenmiş bir ImageField eklemek için ınitializeınstancereso, () öğesini geçersiz kılın.|
|Şekilleri herhangi bir derinliğe iç içe geçme|Özyinelemeli bir ekleme ağacı ayarlayın. Şekilleri içerecek BoundsRules tanımlayın.|
|Bir öğenin sınırında sabit noktalara bağlayıcılar ekleyin.|Diyagramda küçük bağlantı noktalarıyla temsil edilen gömülü Terminal öğelerini tanımlayın. Bağlantı noktalarını yerinde onarmak için BoundsRules kullanın. [Görselleştirme ve modelleme SDK](http://go.microsoft.com/fwlink/?LinkID=186128)'Sindeki devre diyagramı örneğine bakın.|
|Metin alanı diğer değerlerden türetilmiş bir değeri görüntüler.|Metin dekoratörü hesaplanan veya özel bir depolama alanı özelliği ile eşleyin. Daha fazla bilgi için bkz. [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|
|Değişiklikleri model öğeleri veya şekiller arasında yayma|Bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).|
|Mağaza dışındaki diğer Visual Studio uzantıları gibi kaynaklardaki değişiklikleri yayın.|Bkz. [olay Işleyicileriyle değişiklikleri model dışına yayın](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Özellik penceresi, ilgili bir öğenin özelliklerini görüntüler.|Özellik Iletmeyi ayarlayın. Bkz. [Özellikler penceresini özelleştirme](../modeling/customizing-the-properties-window.md).|
|Özellik kategorileri|Özellikler penceresi Kategoriler adlı bölümlere ayrılmıştır. Etki alanı özelliklerinin **kategorisini** ayarlayın. Aynı kategori adına sahip özellikler aynı bölümde görüntülenir. Bir ilişki rolü **kategorisini** de ayarlayabilirsiniz.|
|Etki alanı özelliklerine Kullanıcı erişimini denetleme|Bir etki alanı özelliğinin çalışma zamanında Özellikler penceresi görünmesini engellemek için, bu ayarı göz **atılamaz** false. Yine de metin Dekoratörleri ile eşleme yapabilirsiniz.<br /><br /> **UI Read yalnızca** kullanıcıların bir etki alanı özelliğini değiştirmesini engeller.<br /><br /> Alan özelliğine program erişimi etkilenmez.|
|DSL model Gezgininde düğümlerin adını, simgesini ve görünürlüğünü değiştirin.|Bkz. [model Gezginini özelleştirme](../modeling/customizing-the-model-explorer.md).|
|Kopyalama, kesme ve yapıştırmayı etkinleştir|DSL Gezgini 'ndeki **Düzenleyici** düğümünün **kopyalama Yapıştır özelliğini etkinleştir** ' i ayarlayın.|
|Her öğe kopyalanırken başvuru bağlantılarını ve bunların hedeflerini kopyalayın. Örneğin, bir öğeye ekli açıklamaları kopyalayın.|Kaynak rolün **yayar kopyalama** özelliğini AYARLAYıN (DSL tanım diyagramında etki alanı ilişkisinin bir tarafındaki satırla temsil edilir).<br /><br /> Daha karmaşık etkileri elde etmek için ProcessOnCopy 'i geçersiz kılmak üzere kod yazın.<br /><br /> Bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|
|Bir öğe silindiğinde, ilgili öğeleri silin, yeniden üst üste veya yeniden bağlayın.|Bir ilişki rolünün **yayar silme** değerini ayarlayın. Daha karmaşık efektler için, **DomainModel.cs**içinde tanımlanan `MyDslDeleteClosure` sınıfında `ShouldVisitRelationship` ve `ShouldVisitRolePlayer` yöntemleri geçersiz kılın.|
|Kopyalama ve sürükleme bırakma üzerinde şekil mizanpajını ve görünümünü koruyun.|Şekilleri ve bağlayıcıları kopyalanmış `ElementGroupPrototype` ekleyin. Geçersiz kılınacak en kullanışlı Yöntem `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|
|Şekilleri seçili bir konuma (örneğin, geçerli imleç konumu) yapıştırın.|@No__t_1 konuma özgü sürümü kullanmak için `ClipboardCommandSet.ProcessOnCopy()` geçersiz kılın bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|
|Yapıştırma sırasında ek bağlantılar oluştur|ClipboardCommandSet. ProcessOnPasteCommand () öğesini geçersiz kıl|
|Bu diyagramdan ve diğer DSLs ve Windows öğelerinden sürükleyip bırakmayı etkinleştir|Bkz [. nasıl yapılır: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Bir şeklin veya aracın, üst öğeye sürüklenmiş gibi bir alt şekle (bağlantı noktası gibi) sürüklenmesi için izin verin.|Bırakılan nesneyi üst öğeye iletmek için, hedef nesne sınıfında bir öğe birleştirme yönergesi tanımlayın. Bkz. [öğe oluşturma ve taşımayı özelleştirme](../modeling/customizing-element-creation-and-movement.md).|
|Şekil veya aracın bir şekle sürüklenmesi ve ek bağlantılara ya da nesnelerin oluşturulmasını sağlar. Örneğin, bir yorumun bağlanacağı bir öğeye bırakılmasına izin vermek için.|Hedef etki alanı sınıfında bir öğe birleştirme yönergesi tanımlayın ve oluşturulacak bağlantıları tanımlayın. Karmaşık durumlarda özel kod ekleyebilirsiniz. Bkz. [öğe oluşturma ve taşımayı özelleştirme](../modeling/customizing-element-creation-and-movement.md).|
|Bir araçla bir öğe grubu oluşturun. Örneğin, sabit bir bağlantı noktası kümesine sahip bir bileşen.|ToolboxHelper.cs içinde araç kutusu başlatma yöntemini geçersiz kılın. Öğeleri ve bunların ilişki bağlantılarını içeren bir öğe grubu prototipi (EGP) oluşturun. Bkz. [araçları ve araç kutusunu özelleştirme](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> EGP 'ye asıl ve bağlantı noktası şekillerini ekleyin ya da EGP örneği oluşturulduğunda bağlantı noktası şekillerini konumlandırmak için BoundsRules tanımlayın.|
|Çeşitli ilişki türlerini örneklemek için bir bağlantı aracı kullanın.|Araç tarafından çağrılan bağlantı oluşturucusuna bağlantı bağlama yönergeleri (LCD) ekleyin. LCD 'Ler, iki öğenin türünden ilişki türünü tespit. Bunu, öğelerin durumlarına bağlı yapmak için özel kod ekleyebilirsiniz. Bkz. [araçları ve araç kutusunu özelleştirme](../modeling/customizing-tools-and-the-toolbox.md).|
|Yapışkan araçlar-Kullanıcı, art arda birçok şekil veya bağlayıcı oluşturmak için herhangi bir araca çift tıklaedebilir.|DSL Gezgini ' nde `Editor` düğümünü seçin. Özellikler penceresi, kümesi **yapışkan araç kutusu öğelerini kullanır**.|
|Menü komutlarını tanımlama|Bkz [. nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Modeli doğrulama kurallarıyla kısıtlama|Bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md)|
|DSL 'den kod, yapılandırma dosyaları veya belgeler oluşturun.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Modellerin dosyaya nasıl kaydedildiğini özelleştirin.|Bkz. [Dosya depolamayı ve XML Serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Modelleri veritabanlarına veya diğer ortamlara kaydedin.|DocData *dilini*geçersiz kılın<br /><br /> Bkz. [Dosya depolamayı ve XML Serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Birden çok DSLs 'yi bir uygulamanın parçası olarak çalışacak şekilde tümleştirin.|Bkz. [Visual Studio ModelBus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|DSL 'nizin üçüncü taraflarca uzatılarak ve uzantıyı denetlemesine izin verin.|[MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
