---
title: Etki Alanına Özgü Dili Özelleştirme ve Genişletme
description: Visual Studio modelleme ve görselleştirme SDK 'sının (VMSDK), modelleme araçlarını tanımlayabilmeniz için çeşitli düzeyler sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5c6a6572e8e26f6ab60a8af620d18642a3c35dbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055581"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Etki alanına özgü dili özelleştirme ve genişletme

Visual Studio Modelleme ve görselleştirme SDK 'Sı (VMSDK), modelleme araçlarını tanımlayabileceğiniz çeşitli düzeyler sağlar:

1. DSL tanımı diyagramını kullanarak etki alanına özgü dil (DSL) tanımlayın. Bir diagrammatik gösterimi, okunabilir bir XML formu ve kod ve diğer yapıtlar oluşturmak için gereken temel araçları kullanarak hızlı bir şekilde DSL oluşturabilirsiniz. Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

2. DSL tanımının daha gelişmiş özelliklerini kullanarak DSL 'yi hassas olarak ayarlayın. Örneğin, Kullanıcı bir öğe oluşturduğunda ek bağlantıların görüntülenmesini sağlayabilirsiniz. Bu teknikler genellikle DSL tanımında elde edilir ve bazıları bazı program kodu satırları gerektirir.

3. Program kodunu kullanarak modelleme araçlarınızı genişletin. VMSDK, uzantılarınızı DSL tanımından oluşturulan kodla tümleştirmeyi kolaylaştırmak için özel olarak tasarlanmıştır. Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> DSL tanımları dosyasını güncelleştirdiyseniz, çözümünüzü yeniden oluşturmadan önce **Çözüm Gezgini** araç çubuğundaki **Tüm Şablonları Dönüştür** ' e tıklamasını unutmayın.

## <a name="article-reference"></a>Makale başvurusu

|Bu etkiyi elde etmek için|Bu konuya başvurun|
|-|-|
|Kullanıcının bir şeklin renk ve stil özelliklerini ayarlamaya izin verin.|Şekle veya bağlayıcı sınıfına sağ tıklayın, **gösterilen Ekle**' nin üzerine gelin ve bir öğeye tıklayın.|
|Farklı model öğesi sınıfları diyagram üzerinde benzerdir, ilk yükseklik ve genişlik, renk ve araç ipuçları gibi özellikleri paylaşıyor.|Şekiller veya bağlayıcı sınıfları arasında devralmayı kullanın. Türetilmiş şekiller ve türetilmiş etki alanı sınıfları arasındaki eşlemeler üst öğelerinin eşleme ayrıntılarını alırlar.<br /><br /> Ya da, farklı etki alanı sınıflarını aynı şekil sınıfına eşleyin.|
|Model öğesi sınıfı farklı şekil bağlamları tarafından görüntülenir.|Birden fazla şekil sınıfını aynı etki alanı sınıfına eşleyin. Çözümü oluştururken, hata raporunu izleyin ve hangi şekle kullanılacağına karar vermek için istenen kodu sağlayın.|
|Şekil rengi veya yazı tipi gibi diğer özellikler geçerli durumu gösterir.|Bkz. [modeli yansıtmak Için şekilleri ve bağlayıcıları güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Gösterilen özellikleri güncelleştiren bir kural oluşturun. Bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Ya da bağlantı okları veya yazı tipi gibi görünmeyen özellikleri güncelleştirmek için Onilişkilendirilmemiş PropertyChanged () kullanın.|
|Durumu göstermek için şekildeki simge değişiklikleri.|DSL ayrıntıları penceresinde dekoratör eşlemesinin görünürlüğünü ayarlayın. Birçok görüntü dekoratlarını aynı konumda bulun. Bkz.  [modeli yansıtmak Için şekilleri ve bağlayıcıları güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Veya geçersiz kılın `ImageField.GetDisplayImage()` . Örneğe bakın <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Herhangi bir şekil üzerinde arka plan resmi ayarlama|Sabitlenmiş bir ImageField eklemek için ınitializeınstancereso, () öğesini geçersiz kılın.|
|Şekilleri herhangi bir derinliğe iç içe geçme|Özyinelemeli bir ekleme ağacı ayarlayın. Şekilleri içerecek BoundsRules tanımlayın.|
|Bir öğenin sınırında sabit noktalara bağlayıcılar ekleyin.|Diyagramda küçük bağlantı noktalarıyla temsil edilen gömülü Terminal öğelerini tanımlayın. Bağlantı noktalarını yerinde onarmak için BoundsRules kullanın. [Görselleştirme ve modelleme SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)'Sindeki devre diyagramı örneğine bakın.|
|Metin alanı diğer değerlerden türetilmiş bir değeri görüntüler.|metin dekoratörü hesaplanan veya özel bir Depolama etki alanı özelliği ile eşleyin. daha fazla bilgi için bkz. [hesaplanan ve özel Depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|
|Değişiklikleri model öğeleri veya şekiller arasında yayma|[Domain-Specific dilde doğrulamaya](../modeling/validation-in-a-domain-specific-language.md)bakın.|
|değişiklikleri mağaza dışındaki diğer Visual Studio uzantıları gibi kaynaklara yayın.|Bkz. [olay Işleyicileriyle değişiklikleri model dışına yayın](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Özellik penceresi, ilgili bir öğenin özelliklerini görüntüler.|Özellik Iletmeyi ayarlayın. Bkz. [Özellikler penceresini özelleştirme](../modeling/customizing-the-properties-window.md).|
|Özellik kategorileri|Özellikler penceresi Kategoriler adlı bölümlere ayrılmıştır. Etki alanı özelliklerinin **kategorisini** ayarlayın. Aynı kategori adına sahip özellikler aynı bölümde görüntülenir. Bir ilişki rolü **kategorisini** de ayarlayabilirsiniz.|
|Etki alanı özelliklerine Kullanıcı erişimini denetleme|Bir etki alanı özelliğinin çalışma zamanında Özellikler penceresi görünmesini engellemek için, bu ayarı göz **atılamaz** false. Yine de metin Dekoratörleri ile eşleme yapabilirsiniz.<br /><br /> **UI Read yalnızca** kullanıcıların bir etki alanı özelliğini değiştirmesini engeller.<br /><br /> Alan özelliğine program erişimi etkilenmez.|
|DSL model Gezgininde düğümlerin adını, simgesini ve görünürlüğünü değiştirin.|Bkz. [model Gezginini özelleştirme](../modeling/customizing-the-model-explorer.md).|
|Kopyalama, kesme ve yapıştırmayı etkinleştir|DSL Gezgini 'ndeki **Düzenleyici** düğümünün **kopyalama Yapıştır özelliğini etkinleştir** ' i ayarlayın.|
|Her öğe kopyalanırken başvuru bağlantılarını ve bunların hedeflerini kopyalayın. Örneğin, bir öğeye ekli açıklamaları kopyalayın.|Kaynak rolün **yayar kopyalama** özelliğini AYARLAYıN (DSL tanım diyagramında etki alanı ilişkisinin bir tarafındaki satırla temsil edilir).<br /><br /> Daha karmaşık etkileri elde etmek için ProcessOnCopy 'i geçersiz kılmak üzere kod yazın.<br /><br /> Bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|
|Bir öğe silindiğinde, ilgili öğeleri silin, yeniden üst üste veya yeniden bağlayın.|Bir ilişki rolünün **yayar silme** değerini ayarlayın. Daha karmaşık efektler için, `ShouldVisitRelationship` `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel. cs** içinde tanımlanan, sınıfında geçersiz kılın ve yöntemleri.|
|Kopyalama ve sürükleme bırakma üzerinde şekil mizanpajını ve görünümünü koruyun.|Kopyalanacak şekilleri ve bağlayıcıları ekleyin `ElementGroupPrototype` . Geçersiz kılınacak en kullanışlı Yöntem `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|
|Şekilleri seçili bir konuma (örneğin, geçerli imleç konumu) yapıştırın.|`ClipboardCommandSet.ProcessOnCopy()`Konuma özgü sürümü kullanmak için geçersiz kılma `ElementOperations.Merge().` [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).|
|Yapıştırma sırasında ek bağlantılar oluştur|ClipboardCommandSet. ProcessOnPasteCommand () öğesini geçersiz kıl|
|bu diyagramdan sürükleyip bırakmayı etkinleştir, diğer dsls ve Windows öğeleri|Bkz [. nasıl yapılır: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Bir şeklin veya aracın, üst öğeye sürüklenmiş gibi bir alt şekle (bağlantı noktası gibi) sürüklenmesi için izin verin.|Bırakılan nesneyi üst öğeye iletmek için, hedef nesne sınıfında bir öğe birleştirme yönergesi tanımlayın. Bkz. [öğe oluşturma ve taşımayı özelleştirme](../modeling/customizing-element-creation-and-movement.md).|
|Şekil veya aracın bir şekle sürüklenmesi ve ek bağlantılara ya da nesnelerin oluşturulmasını sağlar. Örneğin, bir yorumun bağlanacağı bir öğeye bırakılmasına izin vermek için.|Hedef etki alanı sınıfında bir öğe birleştirme yönergesi tanımlayın ve oluşturulacak bağlantıları tanımlayın. Karmaşık durumlarda özel kod ekleyebilirsiniz. Bkz. [öğe oluşturma ve taşımayı özelleştirme](../modeling/customizing-element-creation-and-movement.md).|
|Bir araçla bir öğe grubu oluşturun. Örneğin, sabit bir bağlantı noktası kümesine sahip bir bileşen.|ToolboxHelper. cs dosyasındaki araç kutusu başlatma yöntemini geçersiz kılın. Öğeleri ve bunların ilişki bağlantılarını içeren bir öğe grubu prototipi (EGP) oluşturun. Bkz. [Araçları özelleştirme ve Araç Kutusu.](../modeling/customizing-tools-and-the-toolbox.md)<br /><br /> EGP'ye sorumlu ve bağlantı noktası şekillerini dahil et veya EGP örneği esndirken bağlantı noktası şekillerini konumlandırmak için BoundsRules'i tanımlayın.|
|Birkaç ilişki türü örneği için bir bağlantı aracı kullanın.|Araç Bağlan Çağrılan Bağlantı Oluşturucusu'nu Bağlantı Oluşturucusu'nu bağlama yönergelerini (veri bağlama yönergeleri) ekleyin. LCD'ler, iki öğenin türlerinden ilişkinin türünü belirler. Bunu öğelerin durumlarını bağlı hale eklemek için özel kod ekebilirsiniz. Bkz. [Araçları özelleştirme ve Araç Kutusu.](../modeling/customizing-tools-and-the-toolbox.md)|
|Yapışkan araçlar - kullanıcı herhangi bir araçta çift tıklar ve ardından birçok şekil veya bağlayıcı oluşturabilir.|DSL Gezgini'nde düğümü `Editor` seçin. Uygulamanın Özellikler penceresi, **Yapışkan Araç Kutusu Öğelerini Kullanır'a tıklayın.**|
|Menü komutlarını tanımlama|Bkz. [Nasıl yapabilirsiniz: Standart Menü Komutunu Değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Modeli doğrulama kurallarıyla sınırlama|Bkz. [Domain-Specific Dilinde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)|
|DSL'den kod, yapılandırma dosyaları veya belgeler oluşturma.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Modellerin dosyaya nasıl kaydedildiklerini özelleştirin.|Bkz. [Dosya Depolama VE XML Serileştirmesini Özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Modelleri veritabanlarına veya diğer medyalara kaydedin.|*YourLanguage DocData'nızı* Geçersiz Kılma<br /><br /> Bkz. [Dosya Depolama VE XML Serileştirmesini Özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Birden çok DSL'nin tek bir uygulamanın parçası olarak çalışması için tümleştirin.|Bkz. [Visual Studio Modelbus kullanarak Modelleri Tümleştirme.](../modeling/integrating-models-by-using-visual-studio-modelbus.md)|
|DSL'nizin üçüncü taraflar tarafından genişlet olmasına izin verme ve uzantıyı denetleme.|[MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
