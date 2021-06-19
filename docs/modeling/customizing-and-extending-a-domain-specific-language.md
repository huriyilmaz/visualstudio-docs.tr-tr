---
title: Etki Alanına Özgü Dili Özelleştirme ve Genişletme
description: Visual Studio Ve Görselleştirme SDK'sı 'nın (VMSDK) modelleme araçlarını tanımladığınız çeşitli düzeyleri nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389390"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Etki alanına özgü bir dili özelleştirme ve genişletme

Visual Studio Modelleme ve Görselleştirme SDK'sı (VMSDK), modelleme araçlarını tanımladığınız çeşitli düzeyler sağlar:

1. DSL Tanımı diyagramını kullanarak etki alanına özgü bir dil (DSL) tanımlayın. Diyagramlı bir nota, okunabilir bir XML formuna ve kod ve diğer yapıtlar oluşturmak için gereken temel araçlara sahip bir DSL'yi hızlı bir şekilde oluşturabilirsiniz. Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

2. DSL Tanımının daha gelişmiş özelliklerini kullanarak DSL'de ince ayar. Örneğin, kullanıcı bir öğe oluşturduğunda ek bağlantıların görünmesini sebilirsiniz. Bu teknikler genellikle DSL Tanımında sağlanır ve bazıları için birkaç program kodu satırı gerekir.

3. Program kodunu kullanarak modelleme araçlarınızı genişletme. VMSDK, uzantılarınızı DSL Tanımından oluşturulan kodla tümleştirin. Daha fazla bilgi için, [bkz. Writing Code to Customize a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> DSL Tanımları dosyasını güncelleştirildiğinde, çözümlerinizi yeniden  oluşturmadan önce Çözüm Gezgini araç çubuğunda Tüm Şablonları **Dönüştür'e** tıklamayı unutmayın.

## <a name="article-reference"></a>Makale başvurusu

|Bu etkiyi elde etmek için|Bu konuya bakın|
|-|-|
|Kullanıcının şeklin renk ve stil özelliklerini ayarlamasına izin verme.|Şekil veya bağlayıcı sınıfına sağ tıklayın, Ortaya Konan **Ekle'nin üzerine gelin** ve bir öğeye tıklayın.|
|Diyagramda, ilk yükseklik ve genişlik, renk, araç ipucu gibi özellikleri paylaşan farklı model öğesi sınıfları benzer görünür.|Şekiller veya bağlayıcı sınıfları arasında devralmayı kullanın. Türetilmiş şekiller ve türetilmiş etki alanı sınıfları arasındaki eşlemeler, üstlerin eşleme ayrıntılarını devralın.<br /><br /> Veya farklı etki alanı sınıflarını aynı şekil sınıfına eşler.|
|Model öğesinin sınıfı farklı şekiller bağlamları tarafından görüntülenir.|Birden fazla şekil sınıfını aynı etki alanı sınıfına eşler. Çözümü derleme sırasında, hata raporunu izleyin ve hangi şeklin kullanıca karar vermek için istenen kodu girin.|
|Şekil rengi veya yazı tipi gibi diğer özellikler geçerli durumu gösterir.|Bkz. [Modeli Yansıtmak için Şekilleri ve Bağlayıcıları Güncelleştirme.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> Açığa çıkarnan özellikleri güncelleştirmeye sahip bir kural oluşturun. Bkz. [Model içindeki Değişiklikleri Yayma Kuralları.](../modeling/rules-propagate-changes-within-the-model.md)<br /><br /> Veya bağlantı okları veya yazı tipi gibi açığa çıkarilmeyen özellikleri güncelleştirmek için OnAssociatedPropertyChanged() kullanabilirsiniz.|
|Durumu göstermek için şekil değişikliklerinin simgesi.|DSL Ayrıntıları penceresinde dekoratör eşlemesi görünürlüğünü ayarlayın. Aynı konumda birkaç görüntü dekoratör bulun. Bkz. [Modeli Yansıtmak için Şekilleri ve Bağlayıcıları Güncelleştirme.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> Veya geçersiz `ImageField.GetDisplayImage()` kılın. bkz. içinde <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> örnek.|
|Herhangi bir şekilde arka plan görüntüsü ayarlama|Sabit bir ImageField eklemek için InitializeInstanceResources() işlevini geçersiz kılın.|
|Şekilleri herhangi bir derinliğe iç içe yerleştirme|Recursive embedding ağacı ayarlayın. Şekilleri içermesi için BoundsRules'i tanımlayın.|
|Bağlayıcıları bir öğenin sınırındaki sabit noktalara iliştirin.|Diyagramda küçük bağlantı noktalarıyla temsil edilen katıştırılmış terminal öğelerini tanımlayın. Bağlantı noktalarını yerinde düzeltmek için BoundsRules kullanın. Görselleştirme ve Modelleme SDK'sı konusunda [Devre Diyagramı örneğine bakın.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|
|Metin alanında diğer değerlerden türetilen bir değer görüntülenir.|Metin dekoratörü bir Hesaplanan veya Özel Depolama etki alanı özelliğiyle eşler. Daha fazla bilgi için [bkz. Hesaplanan ve Özel Depolama Özellikleri.](../modeling/calculated-and-custom-storage-properties.md)|
|Değişiklikleri model öğeleri arasında veya şekiller arasında yayma|Bkz. [Domain-Specific Dilinde Doğrulama.](../modeling/validation-in-a-domain-specific-language.md)|
|Değişiklikleri depo dışındaki diğer Visual Studio kaynaklara yayma.|Bkz. [Olay İşleyicileri Değişiklikleri Modelin Dışına Yayma.](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Özellik penceresinde ilgili bir öğenin özellikleri görüntülenir.|Özellik iletmeyi ayarlayın. Bkz. [Özellikler Penceresini Özelleştirme.](../modeling/customizing-the-properties-window.md)|
|Özellik kategorileri|Özellikler penceresi kategoriler adlı bölümlere ayrılır. Etki alanı **özelliklerinizin** Kategorisini ayarlayın. Aynı kategori adına sahip özellikler aynı bölümde görünür. Ayrıca bir ilişki **rolünün Kategorisini** de ayarlayabilirsiniz.|
|Etki alanı özelliklerine kullanıcı erişimini denetleme|Çalışma **zamanında bir etki** alanı özelliğinin çalışma zamanında Özellikler penceresi için Gözatılabilir false olarak ayarlayın. Yine de metin dekoratörlerine eşlersiniz.<br /><br /> **Kullanıcı Arabirimi Salt Okunur** ise, kullanıcıların bir etki alanı özelliğini değiştirmesini önler.<br /><br /> Etki alanı özelliğine program erişimi etkilenmez.|
|DSL'nizin model gezgininde düğümlerin adını, simgesini ve görünürlüğünü değiştirme.|Bkz. [Model Gezgini'ni Özelleştirme.](../modeling/customizing-the-model-explorer.md)|
|Kopyalama, kesme ve yapıştırmayı etkinleştirme|DSL **Gezgini'nde Düzenleyici düğümünün** **Kopya Yapıştırmayı** Etkinleştir özelliğini ayarlayın.|
|Bir öğe her kopyalansa başvuru bağlantılarını ve hedeflerini kopyalayın. Örneğin, bir öğeye eklenmiş Olan Açıklamalar'a kopyalayın.|Kaynak **rolün Yayma Kopyalama** özelliğini ayarlayın (DSL Tanımı diyagramında etki alanı ilişkisinin bir tarafındaki satırla temsil edilmiştir).<br /><br /> Daha karmaşık etkiler elde etmek için ProcessOnCopy'i geçersiz kılmak için kod yazın.<br /><br /> Bkz. [Kopyalama Davranışını Özelleştirme.](../modeling/customizing-copy-behavior.md)|
|Bir öğe silindiğinde ilgili öğeleri silin, yeniden ya da yeniden bağlantılandırın.|İlişki **rolünün Yayma Silme** değerini ayarlayın. Daha karmaşık etkiler için, `ShouldVisitRelationship` `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel.cs** içinde tanımlanan sınıfında geçersiz kılma ve yöntemler.|
|Kopyalama ve sürükle bırak ile şekil düzenini ve görünümünü koruma.|Kopyalanan öğeye şekilleri ve bağlayıcıları `ElementGroupPrototype` ekleyin. Geçersiz kılmanın en kullanışlı yöntemi şu şekildedir: `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Bkz. [Kopyalama Davranışını Özelleştirme.](../modeling/customizing-copy-behavior.md)|
|Şekilleri, geçerli imleç konumu gibi seçili bir konuma yapıştırın.|Konuma `ClipboardCommandSet.ProcessOnCopy()` özgü sürümünü kullanmak için geçersiz kılın. `ElementOperations.Merge().` [Bkz. Kopyalama Davranışını Özelleştirme.](../modeling/customizing-copy-behavior.md)|
|Yapıştırma işlemiyle ilgili ek bağlantılar oluşturma|ClipboardCommandSet.ProcessOnPasteCommand() geçersiz kılın|
|Bu diyagramdan, diğer DSL'ler ve Windows öğelerinden sürükleyip bırakmayı etkinleştirin|Bkz. [Nasıl? Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Bir şeklin veya aracın üst öğeye sürüklenmiş gibi bir bağlantı noktası gibi bir alt şekle sürüklenmelerine izin verme.|Bırakılan nesneyi üst öğeye iletmesi için hedef nesne sınıfında bir Öğe Birleştirme Yönergesi tanımlayın. Bkz. [Öğe Oluşturma ve Taşımayı Özelleştirme.](../modeling/customizing-element-creation-and-movement.md)|
|Bir şeklin veya aracın bir şekle sürüklenip ek bağlantılar veya nesneler oluşturmasına izin verir. Örneğin, bir açıklamanın bağlantılı olduğu bir öğeye bırakıldıklarına izin vermek için.|Hedef etki alanı sınıfında bir Öğe Birleştirme Yönergesi tanımlayın ve üretilecek bağlantıları tanımlayın. Karmaşık durumlarda özel kod ekebilirsiniz. Bkz. [Öğe Oluşturma ve Taşımayı Özelleştirme.](../modeling/customizing-element-creation-and-movement.md)|
|Tek bir araçla bir öğe grubu oluşturun. Örneğin, sabit bağlantı noktası kümesine sahip bir bileşen.|ToolboxHelper.cs içinde araç kutusu başlatma yöntemini geçersiz kılın. Öğeleri ve onların ilişki bağlantılarını içeren bir Öğe Grubu Prototipi (EGP) oluşturun. Bkz. [Araçları özelleştirme ve Araç Kutusu.](../modeling/customizing-tools-and-the-toolbox.md)<br /><br /> EGP'ye sorumlu ve bağlantı noktası şekillerini dahil et veya EGP örneği esndirken bağlantı noktası şekillerini konumlandırmak için BoundsRules'i tanımlayın.|
|Birkaç ilişki türü örneği için bir bağlantı aracı kullanın.|Araç tarafından çağrılan Bağlantı Oluşturucusu'na Bağlantı Bağlantısı Yönergeleri 'ne (VERI BAĞLANTıSı Yönergeleri) ekleyin. LCD'ler, iki öğenin türlerinden ilişkinin türünü belirler. Bunu öğelerin durumlarını bağlı hale yapmak için özel kod ekebilirsiniz. Bkz. [Araçları özelleştirme ve Araç Kutusu.](../modeling/customizing-tools-and-the-toolbox.md)|
|Yapışkan araçlar - kullanıcı herhangi bir araçta çift tıklar ve ardından birçok şekil veya bağlayıcı oluşturabilir.|DSL Gezgini'nde düğümü `Editor` seçin. Uygulamanın Özellikler penceresi, Yapışkan **Araç Kutusu Öğelerini Kullanır'a tıklayın.**|
|Menü komutlarını tanımlama|Bkz. [Nasıl yapabilirsiniz: Standart Menü Komutunu Değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Modeli doğrulama kurallarıyla sınırlama|Bkz. [Domain-Specific Dilinde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)|
|DSL'den kod, yapılandırma dosyaları veya belgeler oluşturma.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Modellerin dosyaya nasıl kaydedildiklerini özelleştirin.|Bkz. [Dosya Depolama ve XML Serileştirmesini Özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Modelleri veritabanlarına veya diğer medyalara kaydedin.|*YourLanguage DocData'nızı* Geçersiz Kılma<br /><br /> Bkz. [Dosya Depolama ve XML Serileştirmesini Özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Birden çok DSL'nin tek bir uygulamanın parçası olarak çalışması için tümleştirin.|Bkz. [Visual Studio Modelbus kullanarak Modelleri Tümleştirme.](../modeling/integrating-models-by-using-visual-studio-modelbus.md)|
|DSL'nizin üçüncü taraflar tarafından genişlet olmasına izin verme ve uzantıyı denetleme.|[MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
