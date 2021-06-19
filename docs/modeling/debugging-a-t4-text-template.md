---
title: Bir T4 Metin Şablonuna İlişkin Hata Ayıklama
description: Tasarım zamanı metin şablonunda hata ayıklamak için metin şablonu dosyasını kaydedin ve ardından Çözüm Gezgini dosyanın kısayol menüsünde T4 şablonunda Hata Ayıkla ' yı seçin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c9e4454071002e3bce8478bc825ecfddc17620f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385779"
---
# <a name="debugging-a-t4-text-template"></a>Bir T4 Metin Şablonuna İlişkin Hata Ayıklama
Kesme noktaları metin şablonlarında ayarlayabilirsiniz. Tasarım zamanı metin şablonunda hata ayıklamak için metin şablonu dosyasını kaydedin ve ardından Çözüm Gezgini dosyanın kısayol menüsünde **T4 şablonunda hata ayıkla** ' yı seçin. Çalışma zamanı metin şablonunda hata ayıklamak için, ait olduğu uygulamada hata ayıklaması yapmanız yeterlidir.

 Bir metin şablonunda hata ayıklamak için, şablon dönüştürme işleminin adımlarını anlamanız gerekir. Her adımda farklı hata türleri meydana gelebilir. Adımlar aşağıdaki gibidir.

|Adım|Tasarım zamanı şablonu: oluştuğunda|Çalışma zamanı şablonu: oluştuğunda|
|-|-|-|
|Kod, metin şablonundan oluşturulur.<br /><br /> Yönergelerden veya eşleşmeyen veya sıralanmış `<#...#>` etiketlerin hataları.|Şablonu kaydettiğinizde veya metin dönüşümünü çağırdığınızda.|Şablonu kaydettiğinizde veya metin dönüşümünü çağırdığınızda.|
|Oluşturulan kod derlenir.<br /><br /> Şablon kodunuzda derleme hataları.|Önceki adımdan hemen sonra.|Uygulama kodunuzla birlikte.|
|Kod çalışır.<br /><br /> Şablon kodunuzda çalışma zamanı hataları.|Önceki adımdan hemen sonra.|Uygulamanız çalışır ve şablon kodunu çağırır.|

 Çoğu durumda, şablon kodundaki satır numaraları hata raporunda verilir. Hata raporu, geçici bir dosya adına başvurduğunda, genellikle metin şablonunun kodunda eşleşmeyen bir köşeli ayraç olur.

 Metin şablonlarında kesme noktaları ve hata ayıklama işlemlerini olağan şekilde ayarlayabilirsiniz.

## <a name="common-errors-and-fixes"></a>Sık karşılaşılan hatalar ve düzeltmeler
 Aşağıdaki tabloda en yaygın hatalar ve bunların düzeltmeleri listelenmektedir.

|Hata İletisi|Açıklama|Çözüm|
|-|-|-|
|{0}Dönüştürme sınıfının devraldığı ' ' temel sınıfı yüklenemedi.|Bir şablon yönergesinde parametresinde belirtilen temel sınıfı bulamıyorsanız oluşur `inherits` . İleti, şablon yönergesinin satır numarasını sağlar.|Belirtilen sınıfın var olduğundan ve içinde bulunduğu derlemenin derleme yönergesinde belirtildiğinden emin olun.|
|Dosya için içerme metni çözümlenemedi:{0}|Dahil edilen bir şablon bulamıyorsanız oluşur. İleti, istenen içerme dosyasının adını sağlar.|Dosya yolunun özgün şablon yoluyla göreli olduğundan veya dosyanın konakla kaydedilmiş bir konumda olduğundan ya da dosyanın tam yolu olduğundan emin olun.|
|Dönüştürme nesnesi başlatılırken hatalar üretildi. Dönüşüm çalıştırılmayacak.|Dönüştürme sınıfının ' Initialize () ' değeri başarısız olduğunda veya false döndürüldüğünde gerçekleşir.|Initialize () işlevindeki kod, \<#@template#> yönergede ve yönerge işlemcilerinde belirtilen temel dönüşüm sınıfından gelir. Hata durumunda başlatmaya neden olan hata büyük olasılıkla hata listesinde. Neden başarısız olduğunu araştırın. Bir şablonda hata ayıklama yordamlarını izleyerek Initialize () için üretilen gerçek koda bakabilirsiniz.|
|' ' {0} Yönerge işlemcisi için ' ' derlemesine {1} FullTrust izin kümesi verilmedi. Yalnızca güvenilen derlemelerin yönerge işlemcileri sağlamasına izin verilir. Bu yönerge işlemcisi yüklenmeyecek.|Sistem, yönerge işlemcisi içeren bir derlemeye FullTrust izinleri vermediği zaman gerçekleşir. İleti, derleme adı ve yönerge işlemcisinin adı sağlar.|Yalnızca yerel makinede güvenilen derlemeler kullandığınızdan emin olun.|
|' ' Yolu {0} Bu bilgisayarda yerel olmalı veya güvenilen bölgenizin bir parçası olmalıdır.|Bir yönerge veya derleme yönergesi yerel makinenizde veya ağınızın güvenilen bölgesinde olmayan bir dosyaya başvurduğunda oluşur.|Yönergesinin veya derleme yönergelerinin bulunduğu dizinin Güvenilen bölgeniz olduğundan emin olun. Internet Explorer aracılığıyla güvenilir bölgenize bir ağ dizini ekleyebilirsiniz.|
|"Geçersiz belirteç ' catch '" veya "bir ad alanı doğrudan üye içeremez" gibi birden çok sözdizimi hatası|Şablon kodunuzda çok fazla kapanış ayracı var. Derleyici, standart oluşturma kodu ile kafa karıştırıcı.|Kod sınırlayıcıları içinde kapanış küme ayracı ve köşeli ayraçlar sayısını denetleyin.|
|Döngüler veya koşullar doğru derlenmez veya yürütülmedi. Örneğin: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Bu kod her zaman ı değerini verir. Yalnızca "sayı:" koşullu.|C# ' de, denetim ifadelerine gömülü metin bloklarını çevrelemek için her zaman ayraç kullanın.|Küme ayraçları ekle: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|Tasarım zamanı şablonu işlenirken veya bir çalışma zamanı (önceden işlenmiş) şablonu derlerken "ifade çok karmaşık".<br /><br /> Çalışma zamanı şablonu tarafından oluşturulan kodu incelemeye çalışırken Visual Studio çalışmayı durduruyor.|Metin bloğu çok uzun. T4, metin bloklarını her şablon satırı için bir dize sabit değeri olan dize birleştirme ifadesine dönüştürür. Çok uzun metin blokları derleyicinin boyut sınırlarını fazla sürebilir.|Uzun metin bloğunu, şöyle bir ifade bloğu ile bölün:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Uyarı açıklamaları ve düzeltmeler
 Aşağıdaki tabloda, varsa düzeltmelerle birlikte en sık kullanılan uyarılar listelenmektedir.

|Uyarı Iletisi|Açıklama|Çözüm|
|-|-|-|
|İçerme dosyasını yükleme ' {0} ', null veya boş bir dize döndürdü.|Eklenen bir metin şablonu dosyası boşsa gerçekleşir. İleti, eklenen dosyanın dosya adını sağlar.|Include yönergesini kaldırın ya da dosyanın bazı içeriklere sahip olduğundan emin olun.|
|Dönüştürme derleniyor:|Bu dizeyi, dönüştürmeyi derlediğinde derleyicinin kaynaklandığı tüm hatalara veya uyarılara ekleyin. Bu dize, derleyicinin bir hata veya uyarı oluşturduğu anlamına gelir.|DLL 'yi bulmakta bir sorun yaşıyorsanız, DLL GAC 'deyse tam yolu veya tam nitelikli bir ad belirtmeniz gerekebilir.|
|' ' Parametresi {0} yönergesinde zaten var. Yinelenen parametre yok sayılacak.|Bir parametre bir yönergede birden çok kez belirtildiğinde oluşur. İleti, parametrenin adını ve yönergesinin satır numarasını sağlar.|Yinelenen parametre belirtimini kaldırın.|
|İçerme dosyası ' ' yüklenirken bir hata oluştu {0} . İçerme yönergesi yok sayılacak.|Bir yönergede belirtilen bir dosyayı bulamıyorsanız oluşur `include` . İleti, dosyanın adını ve yönergesinin satır numarasını sağlar.|Dahil etme dosyasının özgün metin şablonu dosyasıyla aynı dizinde veya ana bilgisayara kayıtlı olan içerme dizinlerinden birinde bulunduğundan emin olun.|
|Dönüştürme sınıfı için geçersiz bir temel sınıf belirtildi. Temel sınıfın Microsoft. VisualStudio. Textşablon. TextTransformation öğesinden türetilmesi gerekir.|`inherits`Bir şablon yönergesinin parametresi öğesinden devraldığı bir sınıfı belirttiğinde gerçekleşir `TextTransformation` . İleti, şablon yönergesinin satır numarasını sağlar.|sınıfından türeten bir sınıf `TextTransformation` belirtin.|
|'Template' yönergesinde geçersiz bir kültür belirtildi. Kültürün "xx-XX" biçiminde olması gerekir. Sabit kültür kullanılır.|Şablon yönergesinde kültür parametresi yanlış belirtiliyorsa gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|Culture parametresini "xx-XX" biçiminde geçerli bir kültür olarak değiştirme.|
|Şablon yönergesinde geçersiz bir {0} hata ayıklama değeri ' ' belirtildi. Hata ayıklama değeri "true" veya "false" olabilir. Varsayılan "false" kullanılır.|Şablon `debug` yönergesinde parametresi yanlış belirtiliyorsa gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|Hata ayıklama parametresini "true" veya "false" olarak ayarlayın.|
|Şablon yönergesinde geçersiz bir HostSpecific {0} değeri ' ' belirtildi. HostSpecific değeri "true" veya "false" olabilir. Varsayılan "false" kullanılır.|Bir yönergede ana bilgisayar özel parametresi yanlış `template` belirtiliyorsa gerçekleşir. İleti, şablon yönergesi için satır numarasını sağlar.|Ana bilgisayar için özel parametreyi "true" veya "false" olarak ayarlayın.|
|'template' {0} yönergesinde geçersiz bir dil ' ' belirtildi. Dil "C#" veya "VB" olabilir. Varsayılan "C#" değeri kullanılır.|yönergesinde desteklenmeyen bir dil belirtilirse `template` gerçekleşir. Yalnızca "C#" veya "VB"ye izin verilir (büyük/büyük/büyük harfe duyarlı değildir). İleti, şablon yönergesi için satır numarasını sağlar.|Şablon `language` yönergesinde parametresini "C#" veya "VB" olarak ayarlayın.|
|Şablonda birden çok çıkış yönergesi bulundu. İlki değil, hepsi yoksayılır.|Bir şablon dosyasında `output` birden çok yönerge belirtilirse gerçekleşir. İleti, yinelenen çıkış yönergesi için satır numarasını sağlar.|Yinelenen yönergeleri `output` kaldırın.|
|Şablonda birden çok şablon yönergesi bulundu. İlki değil, hepsi yoksayılır. Şablon yönergesine birden çok parametre, bir şablon yönergesi içinde belirtilmelidir.|Bir metin şablonu dosyasında `template` (dahil edilen dosyalar dahil) birden çok yönerge belirtirsiniz. İleti, yinelenen şablon yönergesi için satır numarasını sağlar.|Farklı yönergeleri `template` tek bir yönergede `template` toplama.|
|'' adlı yönerge için işlemci {0} belirtilmedi. Yönerge yoksayılır.|Bir yönerge belirtir, `custom` ancak öznitelik sağlamazsanız `processor` oluşur. İleti yönergenin adını ve satır numarasını sağlar.|yönergesi `processor` için işlemcinin adıyla bir `directive` öznitelik girin.|
|' ' adlı yönerge için ' {0} adlı bir işlemci {1} bulunamadı. Yönerge yoksayılır.|Sistem, bir yönerge içinde belirttiğiniz `directive` işlemciyi bulamazsa `custom` gerçekleşir. İleti yönerge adını, işlemci adını ve yönergenin satır numarasını sağlar.|yönergesinde `processor` özniteliğini yönerge işlemcisinin adıyla ayarlayın.|
|' ' {0} yönergesi için gerekli ' {1} ' parametresi bulunamadı. Yönerge yoksayılır.|Sistem gerekli bir yönerge parametresi sağlamazsa gerçekleşir. İleti eksik parametrenin adını, yönerge adını ve satır numarasını sağlar.|Eksik parametreyi girin.|
|' adlı işlemci {0} ' ' adlı yönergeyi {1} desteklemez. Yönerge yoksayılır.|Yönerge işlemcisi bir yönergeyi desteklemezken gerçekleşir. İleti, yönerge işlemcisinin adıyla birlikte soruna neden olan yönergenin adını ve satır numarasını sağlar.|Yönergenin adını düzeltin.|
|' dosyası için include {0} yönergesi sonsuz döngüye neden olur.|Döngüsel include yönergeleri belirtilirse görüntülenir (örneğin, A dosyası A dosyasını içeren B dosyasını içerir).|Döngüsel dahil etmek yönergelerini belirtme.|
|Dönüştürmeyi çalıştırma:|Bu dizeyi, dönüştürme çalışırken oluşturulan tüm hatalara veya uyarılara hazırlar.|Geçerli değildir.|
|Blok içinde beklenmeyen bir başlangıç veya bitiş etiketi bulundu. Bir başlangıç veya bitiş etiketini yanlış yazmamış ve şablonda iç içe geçmiş bloklar olmadığınızdan emin olun.|Beklenmeyen bir olduğunda \<# or #> görüntülenir. Başka bir ifadeyle, daha önce açık etiketi olmayan bir \<# after another open tag that has not been closed, or you have a #> etiketine sahipsinizdir. İleti, eşleşmeyen etiketin satır numarasını sağlar.|Eşleşmeyen başlangıç veya bitiş etiketini kaldırın veya bir kaçış karakteri kullanın.|
|Yönerge yanlış biçimde belirtildi. Yönerge yoksayılır. Yönergeyi biçiminde belirtin `<#@ name [parametername="parametervalue"]*  #>`|Bir yönerge doğru biçimde belirtilmemişse ayrıştırıcı tarafından görüntülenir. İleti yanlış yönergenin satır numarasını sağlar.|Tüm yönergelerin şeklinde olduğundan emin `<#@ name [parametername="parametervalue"]*  #>` olun. Daha fazla bilgi için [bkz. T4 Metin Şablonu Yönergeleri.](../modeling/t4-text-template-directives.md)|
|Kayıtlı yönerge işlemcisi ' {0} için '' Derlemesi yüklenemedi {1}<br /><br /> {2}|Bir yönerge işlemcisi konak tarafından yüklenemedi. İleti, yönerge işlemcisi için sağlanan derlemeyi ve yönerge işlemcisinin adını tanımlar.|Yönerge işlemcisinin doğru şekilde kaydedildiklerini ve derlemenin mevcut olduğundan emin olun.|
|Kayıtlı yönerge işlemcisi {0} ' için Derleme ' içinde ' türü {1} {2} bulunamadı<br /><br /> {3}|Yönerge işlemcisi türü derlemeden yüklenemediklerinde oluşur. İleti türü, derleme ve yönerge işlemcisinin adını sağlar.|vshost, kayıt defterinde yönerge işlemci bilgilerini (ad, derleme ve tür) bulur. Yönerge işlemcisinin doğru şekilde kaydedildiklerini ve türün derlemede mevcut olduğundan emin olun.|
|'' derlemesi yüklenirken bir sorun {0} oldu|Bir derleme yüklenirken sorun oluştuğunda oluşur. İleti derlemenin adını sağlar.|Yönergelerde yüklenecek derlemeleri ve yönerge \<@#assembly#> işlemcileri tarafından belirtsiniz. Bu dizeyi izleyen hata iletisi, derleme yükünün neden başarısız olduğuyla ilgili daha fazla veri sağla olmalıdır.|
|'' adlı yönerge için işlemci oluşturma ve başlatma sırasında bir sorun {1} vardı. İşlemcinin türü {0} olur. Yönerge yoksayılır.|Sistem bir yönerge işlemcisi oluşturamadığında veya başlatamadığında gerçekleşir. İleti, yönergenin adını ve satır numarasını ve işlemci türünü sağlar.|Doğru yönerge işlemcisini kullanmaya ve yönerge işlemcisinin genel bir varsayılan oluşturucuya sahip olduğundan emin olun. Aksi takdirde, yönerge işlemcisinin Initialize() yönteminin neden başarısız olduğunu bulmak için hata ayıklama seçeneklerini kullanın. Daha fazla bilgi için [bkz. Metin Şablonları sorunlarını giderme.](../modeling/debugging-a-t4-text-template.md)|
|'' adlı yönerge işlenmiştir. {0}|Yönerge işlemcisi bir yönergeyi işlerken özel durum oluştuğunda gerçekleşir.|Yönerge işlemcisinin parametrelerinin doğru olduğundan emin olun.|
|Konak, '' derleme başvurusunuzu çözümlemeye çalışırken bir özel durum {0} oluşturdu.|Konak, derleme başvurularını çözümlemeye çalıştığında bir özel durum oluştuğunda gerçekleşir. İleti, derleme başvuru dizesini sağlar.|Derleme başvuruları yönergelerinden \<@#assembly#> ve yönerge işlemcilerinden gelir. Derleme parametresinde sağlanan 'name' parametresinin doğru olduğundan emin olun.|
|yönergesi için desteklenmeyen {1} ' ' değerini {0} belirtmeye çalışma {2}|Desteklenmeyen bir gerektirir veya bağımsız değişken sağladığında RequiresProvidesDirectiveProcessor tarafından gerçekleşir (tüm oluşturulan yönerge işlemcilerimiz bundan türetmektedir).|requires ve provides parametrelerinde sağlanan name='value' çiftlerinin adlarının doğru olduğundan emin olun.|
