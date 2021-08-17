---
title: Bir T4 Metin Şablonuna İlişkin Hata Ayıklama
description: Tasarım zamanı metin şablonunda hata ayıklamak için metin şablonu dosyasını kaydedin ve ardından dosyanın kısayol menüsünden T4 Şablonunda Hata Ayıkla'yı Çözüm Gezgini.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 360c007363e8e5b559e3c95481a014c4c453093fa1ecac804b42f986ad2f8988
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398235"
---
# <a name="debugging-a-t4-text-template"></a>Bir T4 Metin Şablonuna İlişkin Hata Ayıklama
Metin şablonlarında kesme noktaları oluşturabilirsiniz. Tasarım zamanı metin şablonunda hata ayıklamak için, metin şablonu dosyasını kaydedin ve sonra dosyanın kısayol **menüsünden T4** Şablonunda Hata Ayıkla'yı Çözüm Gezgini. Çalışma zamanı metin şablonunda hata ayıklamak için, ait olduğu uygulamanın hata ayıklaması yapmanız gerekir.

 Bir metin şablonunda hata ayıklamak için şablon dönüştürme işleminin adımlarını anlamalısınız. Her adım içinde farklı türlerde hatalar oluşabilir. Adımlar aşağıdaki gibidir.

|Adım|Tasarım zamanı şablonu: bu olduğunda|Çalışma zamanı şablonu: bu olduğunda|
|-|-|-|
|Kod, metin şablonundan oluşturulur.<br /><br /> Yönergelerde hatalar, eşleşmeyen veya düzensiz `<#...#>` etiketler.|Şablonu kaydeden veya metin dönüştürmeyi çağıran.|Şablonu kaydeden veya metin dönüştürmeyi çağıran.|
|Oluşturulan kod derlenmiş.<br /><br /> Şablon kodundaki derleme hataları.|Önceki adımdan hemen sonra.|Uygulama kodunuzla birlikte.|
|Kod çalıştırmaları.<br /><br /> Şablon kodunda çalışma zamanı hataları.|Önceki adımdan hemen sonra.|Uygulama çalıştırarak şablon kodunu çağıran.|

 Çoğu durumda, şablon kodundaki satır numaraları hata raporunda verilir. Hata raporu geçici bir dosya adını ifade ederken, normal neden metin şablonunun kodunda eşleşmeyen köşeli ayraçtır.

 Metin şablonlarında kesme noktaları oluşturabilir ve her zamanki şekilde hata ayıkabilirsiniz.

## <a name="common-errors-and-fixes"></a>Yaygın Hatalar ve Düzeltmeler
 Aşağıdaki tabloda en sık karşılaşılan hatalar ve bunların düzeltmeleri listelene bir liste yer alır.

|Hata İletisi|Açıklama|Çözüm|
|-|-|-|
|Dönüştürme sınıfının devralınan {0} '' temel sınıfı yüklenemedi.|Bir şablon yönergesinde parametresinde belirtilen temel sınıfı `inherits` bulamazsanız oluşur. İleti, şablon yönergesi için satır numarasını sağlar.|Belirtilen sınıfın mevcut olduğundan ve içinde yer alan derlemenin bir derleme yönergesinde belirtilmiş olduğundan emin olun.|
|Dosya için ekleme metni çözümlanamadı:{0}|Dahil edilen bir şablonu bulamasanız gerçekleşir. İleti, istenen include dosyasının adını sağlar.|Dosya yolunun özgün şablon yoluyla göreli olduğundan veya dosyanın ana bilgisayarla kayıtlı bir konumda olduğundan veya dosyanın tam bir yolu olduğundan emin olun.|
|Dönüştürme nesnesi başlatıldıken hatalar oluşturulmuş. Dönüştürme çalıştırmayacak.|Dönüştürme sınıfının 'Initialize()' başarısız olduğunda veya false döndürürken gerçekleşir.|Initialize() işlevinde kod, yönergesinde belirtilen temel dönüştürme sınıfından ve \<#@template#> yönerge işlemcilerinden gelir. Başlatmanın başarısız olmasıyla ilgili hata büyük olasılıkla hata listesindedir. Neden başarısız olduğunu araştır. Bir şablonda hata ayıklama yordamlarını takip etmek için Initialize() için gerçek oluşturulan koda bakabilirsiniz.|
|Yönerge {0} işlemcisi ' için {1} '' derlemesine FullTrust izin kümesi verilmedi. Yönerge işlemcileri sağlamak için yalnızca güvenilen derlemelere izin verilir. Bu yönerge işlemcisi yüklenmez.|Sistem, yönerge işlemcisi içeren bir derlemeye FullTrust izinleri verilmeyen bir durum oluşur. İleti derlemenin adını ve yönerge işlemcisinin adını sağlar.|Yalnızca yerel makinede güvenilen derlemeleri kullanmaya emin olun.|
|'' {0} yolu bu bilgisayarda yerel veya güvenilen bölgenizin bir parçası olmalıdır.|Bir yönerge veya derleme yönergesi, yerel makineniz veya ağ ın güvenilen bölgesinde yer alan bir dosyaya başvuracaksa gerçekleşir.|Yönergenin veya derleme yönergelerinin bulunduğu dizinin güvenilen bölgeniz içinde olduğundan emin olun. Ağ dizininizi kullanarak güvenilen bölgenize bir ağ Internet Explorer.|
|"Geçersiz belirteç 'catch' veya "Bir ad alanı doğrudan üye içeremedi" gibi birden çok söz dizimi hatası|Şablon kodunda çok fazla kapatma ayracı var. Derleyici bunu standart oluşturma koduyla karıştırır.|Kod sınırlayıcılarının içindeki kapatma ayraçlarının ve köşeli ayraçların sayısını kontrol edin.|
|Döngüler veya koşullular derlenmiş veya doğru yürütülmlü değil. Örneğin: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Bu kod her zaman i değerini verir. Yalnızca "Sayı: " koşullu.|C# içinde, denetim deyimlerine eklenmiş metin bloklarının çevresini her zaman ayraçlar kullanın.|Küme ayraçları ekleyin: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|Tasarım zamanı şablonunu işlerken veya bir çalışma zamanı (önceden işlenmemiş) şablonu derleme sırasında "İfade çok karmaşık".<br /><br /> Visual Studio çalışma zamanı şablonu tarafından oluşturulan kodu incelemeye çalışırken uygulama çalışmayı durdurıyor.|Metin bloğu çok uzun. T4, her şablon satırı için bir dize değişmez değeri ile metin bloklarını dize bir concatenation ifadesine dönüştürür. Çok uzun metin blokları derleyicinin boyut sınırlarını aşebilir.|Uzun metin bloğuna aşağıdaki gibi bir ifade bloğuyla ayrıl:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Uyarı Açıklamaları ve Düzeltmeleri
 Aşağıdaki tabloda, varsa düzeltmelerle birlikte en yaygın uyarılar listeleyecektir.

|Uyarı İletisi|Açıklama|Çözüm|
|-|-|-|
|'' include dosyası {0} yükleniyor, null veya boş bir dize döndürdü.|Dahil edilen bir metin şablonu dosyası boşsa gerçekleşir. İleti, dahil edilen dosyanın dosya adını sağlar.|Include yönergesi kaldır veya dosyada bazı içerikler olduğundan emin olun.|
|Dönüştürmeyi derleme:|Bu dizeyi, dönüştürmeyi derlerken derleyiciden kaynaklanan tüm hatalara veya uyarılara hazırlar. Bu dize, derleyicinin bir hata veya uyarı attığı anlamına gelir.|DLL'yi bulma konusunda bir sorun varsa, DLL GAC'de ise tam yolu veya tam bir güçlü adı sağlamanız gerekir.|
|'' {0} parametresi yönergesinde zaten var. Yinelenen parametre yoksayılır.|Bir parametre bir yönergede birden çok kez belirtiliyorsa gerçekleşir. İleti parametrenin adını ve yönergenin satır numarasını sağlar.|Yinelenen parametre belirtimlerini kaldırın.|
|'' dahil dosyası yüklenirken bir hata {0} oluştu. Include yönergesi yoksayılır.|Bir yönergede belirtilen bir dosyayı bulamasanız `include` gerçekleşir. İleti, dosyanın adını ve yönergenin satır numarasını sağlar.|Ekleme dosyasının özgün metin şablonu dosyasıyla aynı dizinde veya konakla kayıtlı ekleme dizinlerinden biri içinde mevcut olduğundan emin olun.|
|Dönüşüm sınıfı için geçersiz bir temel sınıf belirtildi. Temel sınıf Microsoft.VisualStudio.TextTemplating.TextTransformation'dan türetildi.|Şablon `inherits` yönergesinde parametresi, 'den devralmaz bir sınıf belirtirken `TextTransformation` gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|sınıfından türeten bir sınıf `TextTransformation` belirtin.|
|'Template' yönergesinde geçersiz bir kültür belirtildi. Kültürün "xx-XX" biçiminde olması gerekir. Sabit kültür kullanılır.|Şablon yönergesinde kültür parametresi yanlış belirtiliyorsa gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|Culture parametresini "xx-XX" biçiminde geçerli bir kültür olarak değiştirme.|
|Şablon yönergesinde geçersiz bir {0} hata ayıklama değeri ' ' belirtildi. Hata ayıklama değeri "true" veya "false" olabilir. Varsayılan "false" kullanılır.|Şablon `debug` yönergesinde parametresi yanlış belirtiliyorsa gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|Hata ayıklama parametresini "true" veya "false" olarak ayarlayın.|
|Şablon yönergesinde geçersiz bir HostSpecific {0} değeri ' ' belirtildi. HostSpecific değeri "true" veya "false" olabilir. Varsayılan "false" kullanılır.|Bir yönergede ana bilgisayar özel parametresi yanlış `template` belirtiliyorsa gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|Ana bilgisayar için özel parametreyi "true" veya "false" olarak ayarlayın.|
|'template' {0} yönergesinde geçersiz bir dil ' ' belirtildi. Dil "C#" veya "VB" olabilir. Varsayılan "C#" değeri kullanılır.|yönergesinde desteklenmeyen bir dil belirtilirse `template` gerçekleşir. Yalnızca "C#" veya "VB"ye izin verilir (büyük/büyük/büyük harfe duyarlı değildir). İleti, şablon yönergesi için satır numarasını sağlar.|Şablon `language` yönergesinde parametresini "C#" veya "VB" olarak ayarlayın.|
|Şablonda birden çok çıkış yönergesi bulundu. İlki değil, hepsi yoksayılır.|Bir şablon dosyasında `output` birden çok yönerge belirtilirse gerçekleşir. İleti, yinelenen çıkış yönergesi için satır numarasını sağlar.|Yinelenen yönergeleri `output` kaldırın.|
|Şablonda birden çok şablon yönergesi bulundu. İlki değil, hepsi yoksayılır. Şablon yönergesine birden çok parametre, bir şablon yönergesi içinde belirtilmelidir.|Bir metin şablonu dosyasında `template` (dahil edilen dosyalar dahil) birden çok yönerge belirtirsiniz. İleti, yinelenen şablon yönergesi için satır numarasını sağlar.|Farklı yönergeleri `template` tek bir yönergede `template` toplama.|
|'' adlı yönerge için işlemci {0} belirtilmedi. Yönerge yoksayılır.|Bir yönerge belirtir, `custom` ancak öznitelik sağlamazsanız `processor` oluşur. İleti yönergenin adını ve satır numarasını sağlar.|yönergesi `processor` için işlemcinin adıyla bir `directive` öznitelik girin.|
|' ' adlı yönerge için ' {0} adlı bir işlemci {1} bulunamadı. Yönerge yoksayılır.|Sistem, bir yönerge içinde belirttiğiniz `directive` işlemciyi bulamazsa `custom` gerçekleşir. İleti yönerge adını, işlemci adını ve yönergenin satır numarasını sağlar.|yönergesinde `processor` özniteliğini yönerge işlemcisinin adıyla ayarlayın.|
|' ' {0} yönergesi için gerekli ' {1} ' parametresi bulunamadı. Yönerge yoksayılır.|Sistem gerekli bir yönerge parametresi sağlamazsa gerçekleşir. İleti eksik parametrenin adını, yönerge adını ve satır numarasını sağlar.|Eksik parametreyi girin.|
|' adlı işlemci {0} ' ' adlı yönergeyi {1} desteklemez. Yönerge yoksayılır.|Bir yönerge işlemcisi bir yönergeyi desteklemez. İleti, yönerge işlemcisinin adıyla birlikte soruna neden olan yönergenin adını ve satır numarasını sağlar.|Yönergenin adını düzeltin.|
|' dosyası için include {0} yönergesi sonsuz döngüye neden olur.|Döngüsel include yönergeleri belirtilirse görüntülenir (örneğin, A dosyası A dosyasını içeren B dosyasını içerir).|Döngüsel dahil etmek yönergelerini belirtme.|
|Dönüştürmeyi çalıştırma:|Bu dizeyi, dönüştürme çalışırken oluşturulan tüm hatalara veya uyarılara hazırlar.|Geçerli değildir.|
|Blok içinde beklenmeyen bir başlangıç veya bitiş etiketi bulundu. Bir başlangıç veya bitiş etiketini yanlış yazmamış ve şablonda iç içe geçmiş bloklar olmadığınızdan emin olun.|Beklenmeyen bir olduğunda \<# or #> görüntülenir. Başka bir ifadeyle, daha önce açık etiketi olmayan bir \<# after another open tag that has not been closed, or you have a #> etiketine sahipsiniz. İleti, eşleşmeyen etiketin satır numarasını sağlar.|Eşleşmeyen başlangıç veya bitiş etiketini kaldırın veya bir kaçış karakteri kullanın.|
|Yönerge yanlış biçimde belirtildi. Yönerge yoksayılır. Yönergeyi biçiminde belirtin `<#@ name [parametername="parametervalue"]*  #>`|Bir yönerge doğru biçimde belirtilmemişse ayrıştırıcı tarafından görüntülenir. İleti yanlış yönergenin satır numarasını sağlar.|Tüm yönergelerin şeklinde olduğundan emin `<#@ name [parametername="parametervalue"]*  #>` olun. Daha fazla bilgi için [bkz. T4 Metin Şablonu Yönergeleri.](../modeling/t4-text-template-directives.md)|
|Kayıtlı yönerge işlemcisi ' {0} için '' Derlemesi yüklenemedi {1}<br /><br /> {2}|Bir yönerge işlemcisi konak tarafından yüklenemedi. İleti, yönerge işlemcisi için sağlanan derlemeyi ve yönerge işlemcisinin adını tanımlar.|Yönerge işlemcisinin doğru şekilde kaydedildiklerini ve derlemenin mevcut olduğundan emin olun.|
|Kayıtlı yönerge işlemcisi {0} ' için Derleme ' içinde ' türü {1} {2} bulunamadı<br /><br /> {3}|Yönerge işlemcisi türü derlemeden yüklenemediklerinde oluşur. İleti türü, derleme ve yönerge işlemcisinin adını sağlar.|vshost, kayıt defterinde yönerge işlemci bilgilerini (ad, derleme ve tür) bulur. Yönerge işlemcisinin doğru şekilde kaydedildiklerini ve türün derlemede mevcut olduğundan emin olun.|
|'' derlemesi yüklenirken bir sorun {0} oldu|Derleme yüklenirken sorun oluştuğunda oluşur. İleti derlemenin adını sağlar.|Yönergelerde yüklenecek derlemeleri ve yönerge \<@#assembly#> işlemcileri tarafından belirtsiniz. Bu dizeyi izleyen hata iletisi, derleme yükünün neden başarısız olduğuyla ilgili daha fazla veri sağla olmalıdır.|
|'' adlı yönerge için işlemci oluşturma ve başlatma sırasında bir sorun {1} vardı. İşlemcinin türü {0} olur. Yönerge yoksayılır.|Sistem bir yönerge işlemcisi oluşturamadığında veya başlatamadığında gerçekleşir. İleti, yönergenin adını ve satır numarasını ve işlemci türünü sağlar.|Doğru yönerge işlemcisini kullanmaya ve yönerge işlemcisinin genel bir varsayılan oluşturucuya sahip olduğundan emin olun. Aksi takdirde, yönerge işlemcisinin Initialize() yönteminin neden başarısız olduğunu bulmak için hata ayıklama seçeneklerini kullanın. Daha fazla bilgi için [bkz. Metin Şablonları sorunlarını giderme.](../modeling/debugging-a-t4-text-template.md)|
|'' adlı yönerge işlenmiştir. {0}|Yönerge işlemcisi bir yönergeyi işlerken özel durum oluştuğunda gerçekleşir.|Yönerge işlemcisi parametrelerinin doğru olduğundan emin olun.|
|Konak, ' ' derleme başvurusunu çözümlemeye çalışırken bir özel durum oluşturdu {0} .|Ana bilgisayar bir derleme başvurusunu çözümlemeye çalıştığında bir özel durum oluşturduğunda gerçekleşir. İleti, derleme başvuru dizesi sağlar.|Derleme başvuruları \<@#assembly#> yönergelerden ve yönerge işlemcilerinde gelir. Derleme parametresinde belirtilen ' name ' parametresinin doğru olduğundan emin olun.|
|{1}Yönergesi için desteklenmeyen ' ' değerini belirtme girişimi {0}{2}|RequiresProvidesDirectiveProcessor tarafından gerçekleşir (tüm oluşturulan yönerge işlemcileri bundan türetilir), ancak, desteklenmeyen bir gerektirir veya bağımsız değişken sağlar.|Ad = ' Value ' çiftindeki adların, gerektirdiğinden ve parametrelerinin sağlanması doğru olduğundan emin olun.|
