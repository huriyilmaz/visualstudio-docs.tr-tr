---
title: Bir T4 Metin Şablonuna İlişkin Hata Ayıklama
description: Tasarım zamanı metin şablonunda hata ayıklamak için metin şablonu dosyasını kaydedin ve ardından Çözüm Gezgini dosyanın kısayol menüsünde T4 şablonunda Hata Ayıkla ' yı seçin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b197fd52972162acbc6e7d6882507f943b2a560c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935358"
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

|Hata İletisi|Description|Çözüm|
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

|Uyarı Iletisi|Description|Çözüm|
|-|-|-|
|İçerme dosyasını yükleme ' {0} ', null veya boş bir dize döndürdü.|Eklenen bir metin şablonu dosyası boşsa gerçekleşir. İleti, eklenen dosyanın dosya adını sağlar.|Include yönergesini kaldırın ya da dosyanın bazı içeriklere sahip olduğundan emin olun.|
|Dönüştürme derleniyor:|Bu dizeyi, dönüştürmeyi derlediğinde derleyicinin kaynaklandığı tüm hatalara veya uyarılara ekleyin. Bu dize, derleyicinin bir hata veya uyarı oluşturduğu anlamına gelir.|DLL 'yi bulmakta bir sorun yaşıyorsanız, DLL GAC 'deyse tam yolu veya tam nitelikli bir ad belirtmeniz gerekebilir.|
|' ' Parametresi {0} yönergesinde zaten var. Yinelenen parametre yok sayılacak.|Bir parametre bir yönergede birden çok kez belirtildiğinde oluşur. İleti, parametrenin adını ve yönergesinin satır numarasını sağlar.|Yinelenen parametre belirtimini kaldırın.|
|İçerme dosyası ' ' yüklenirken bir hata oluştu {0} . İçerme yönergesi yok sayılacak.|Bir yönergede belirtilen bir dosyayı bulamıyorsanız oluşur `include` . İleti, dosyanın adını ve yönergesinin satır numarasını sağlar.|Dahil etme dosyasının özgün metin şablonu dosyasıyla aynı dizinde veya ana bilgisayara kayıtlı olan içerme dizinlerinden birinde bulunduğundan emin olun.|
|Dönüştürme sınıfı için geçersiz bir temel sınıf belirtildi. Temel sınıfın Microsoft. VisualStudio. Textşablon. TextTransformation öğesinden türetilmesi gerekir.|`inherits`Bir şablon yönergesinin parametresi öğesinden devraldığı bir sınıfı belirttiğinde gerçekleşir `TextTransformation` . İleti, şablon yönergesinin satır numarasını sağlar.|Öğesinden türetilen bir sınıf belirtin `TextTransformation` .|
|' Şablon ' yönergesinde geçersiz bir kültür belirtildi. Kültür "XX-XX" biçiminde olmalıdır. Sabit kültür kullanılacaktır.|Bir şablon yönergesinin Kültür parametresi hatalı belirtildiğinde gerçekleşir. İleti, şablon yönergesinin satır numarasını sağlar.|Kültür parametresini "XX-XX" biçimindeki geçerli bir kültür olarak değiştirin.|
|Şablon yönergesinde geçersiz bir ' ' hata ayıklama değeri {0} belirtildi. Hata ayıklama değeri "true" veya "false" olmalıdır. Varsayılan "false" değeri kullanılacaktır.|`debug`Bir şablon yönergesinin parametresi hatalı belirtildiğinde gerçekleşir. İleti, şablon yönergesinin satır numarasını sağlar.|Hata ayıklama parametresini "true" veya "false" olarak ayarlayın.|
|Şablon yönergesinde geçersiz bir HostSpecific değeri ' {0} ' belirtildi. HostSpecific değeri "true" ya da "false" olmalıdır. Varsayılan "false" değeri kullanılacaktır.|Yönergedeki konağa özgü parametre `template` yanlış belirtildiğinde gerçekleşir. İleti, şablon yönergesinin satır numarasını sağlar.|Konağa özgü parametreyi "true" veya "false" olarak ayarlayın.|
|{0}' Şablon ' yönergesinde geçersiz bir dil ' ' belirtildi. Dil "C#" ya da "VB" olmalıdır. Varsayılan "C#" değeri kullanılacaktır.|Yönergede desteklenmeyen bir dil belirtildiğinde gerçekleşir `template` . Yalnızca "C#" veya "VB" değerlerine izin verilir (büyük/küçük harfe duyarsız). İleti, şablon yönergesinin satır numarasını sağlar.|`language`Şablon yönergesinin parametresini "C#" veya "vb" olarak ayarlayın.|
|Şablonda birden çok çıkış yönergesi bulundu. İlki hariç sayılır.|`output`Şablon dosyasında birden çok yönergeler belirtildiğinde gerçekleşir. İleti, yinelenen çıkış yönergesinin satır numarasını sağlar.|Yinelenen `output` yönergeleri kaldırın.|
|Şablonda birden çok şablon yönergesi bulundu. İlki hariç sayılır. Şablon yönergesinin birden çok parametresi, bir şablon yönergesi içinde belirtilmelidir.|`template`Bir metin şablonu dosyası içinde birden çok yönergesi belirtirseniz (dahil edilen dosyalar dahil) oluşur. İleti, Yinelenen şablon yönergesinin satır numarasını sağlar.|Farklı `template` yönergeleri tek bir yönergede toplayın `template` .|
|' ' Adlı yönerge için hiçbir işlemci belirtilmedi {0} . Yönerge yoksayılacak.|Bir `custom` yönerge belirtirseniz ancak bir öznitelik sağlamadıysanız gerçekleşir `processor` . İleti, yönergenin adını ve satır numarasını sağlar.|`processor`Yönergeyle ilgili işlemcinin adına sahip bir öznitelik sağlayın `directive` .|
|' ' {0} Adlı yönerge için ' ' adlı bir işlemci bulunamadı {1} . Yönerge yoksayılacak.|Sistem `directive` bir yönerge içinde belirttiğiniz işlemciyi bulamadığında oluşur `custom` . İleti yönerge adı, işlemci adı ve yönergenin satır numarasını sağlar.|`processor`Yönergedeki özniteliğini yönerge işlemcisinin adına ayarlayın.|
|{0}' ' Yönergesi için gerekli bir ' ' parametresi {1} bulunamadı. Yönerge yoksayılacak.|Sistem gerekli yönerge parametresini sağlamıyorsa oluşur. İleti, eksik parametrenin adı, yönerge adı ve satır numarası sağlar.|Eksik parametre sağlayın.|
|' ' Adlı işlemci {0} ' ' adlı yönergeyi desteklemiyor {1} . Yönerge yoksayılacak.|Yönerge işlemcisi bir yönergeyi desteklemediği zaman gerçekleşir. İleti, yönerge işlemcisinin adı ile birlikte sorunlu yönergenin adını ve satır numarasını sağlar.|Yönergenin adını düzeltin.|
|' ' Dosyası için içerme yönergesi {0} sonsuz bir döngüye neden oluyor.|Döngüsel içerme yönergeleri belirtilmişse görüntülenir (örneğin, A dosyası, dosya A içeren B dosyasını içerir).|Dairesel içerme yönergeleri belirtmeyin.|
|Dönüştürme çalıştırılıyor:|Bu dizeyi, dönüşüm çalıştırılırken oluşturulan tüm hatalara veya uyarılara ekleyin.|Geçerli değildir.|
|Bir blok içinde beklenmeyen bir başlangıç veya bitiş etiketi bulundu. Bir başlangıç veya bitiş etiketi yazdığınızdan ve şablonda iç içe taşmayın olmadığından emin olun.|Beklenmedik bir şekilde kullandığınızda gösterilir \<# or #> . Diğer bir deyişle, \<# after another open tag that has not been closed, or you have a #> bundan önce kapatılmamış açık etiket olmadığında. İleti, eşleşmeyen etiketin satır numarasını sağlar.|Eşleşmeyen başlangıç veya bitiş etiketini kaldırın ya da bir kaçış karakteri kullanın.|
|Yanlış biçimde bir yönerge belirtildi. Yönerge yoksayılacak. Lütfen yönergeyi biçimde belirtin `<#@ name [parametername="parametervalue"]*  #>`|Doğru biçimde bir yönerge belirtilmemişse ayrıştırıcı tarafından görüntülenir. İleti yanlış yönergenin satır numarasını sağlar.|Tüm yönergelerin biçimde olduğundan emin olun `<#@ name [parametername="parametervalue"]*  #>` . Daha fazla bilgi için bkz. [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).|
|' ' {0} Kayıtlı yönerge işlemcisi için ' ' derlemesi yüklenemedi {1}<br /><br /> {2}|Bir yönerge işlemcisi ana bilgisayar tarafından yüklenemediğinde gerçekleşir. İleti, yönerge işlemcisi ve yönerge işlemcisinin adı için belirtilen derlemeyi tanımlar.|Yönerge işlemcisinin doğru kaydedildiğinden ve derlemenin var olduğundan emin olun.|
|' ' {0} {1} Kayıtlı yönerge işlemcisi için ' ' derlemesinde ' ' türü bulunamadı {2}<br /><br /> {3}|Bir yönerge işlemcisi türü derlemeden yüklenemediğinde gerçekleşir. İleti, tür, derleme ve yönerge işlemcisinin adını sağlar.|VSHost, kayıt defterinde yönerge işlemcisi bilgilerini (ad, derleme ve tür) bulur. Yönerge işlemcisinin doğru şekilde kaydedildiğinden ve türün derlemede bulunduğundan emin olun.|
|' ' Derlemesi yüklenirken bir sorun oluştu {0}|Derleme yüklenirken bir sorun olduğunda gerçekleşir. İleti, derlemenin adını sağlar.|\<@#assembly#>Yönergeler ve yönerge işlemcilere göre yüklenecek derlemeleri belirtebilirsiniz. Bu dizeyi izleyen hata iletisi, derleme yükünün neden başarısız olduğuna ilişkin daha fazla veri sağlamalıdır.|
|' ' Adlı bir yönerge için işlemci oluşturulurken ve başlatılırken bir sorun oluştu {1} . İşlemcinin türü {0} . Yönerge yoksayılacak.|Sistem bir yönerge işlemcisi oluşturmayabilir veya başlatılamadığından oluşur. İleti, yönergenin adını ve satır numarasını ve işlemcinin türünü sağlar.|Doğru yönerge işlemcisini kullandığınızdan ve yönerge işlemcisinin ortak bir varsayılan oluşturucuya sahip olduğundan emin olun. Aksi takdirde, yönerge işlemcisinin Initialize () yönteminin neden başarısız olduğunu bulmak için hata ayıklama seçeneklerini kullanın. Daha fazla bilgi için bkz. [sorun giderme metin şablonları](../modeling/debugging-a-t4-text-template.md).|
|' ' Adlı yönerge işlenirken bir özel durum oluştu {0} .|Yönerge işlemcisi bir yönergeyi işlerken bir özel durum oluşturduğunda gerçekleşir.|Yönerge işlemcisi parametrelerinin doğru olduğundan emin olun.|
|Konak, ' ' derleme başvurusunu çözümlemeye çalışırken bir özel durum oluşturdu {0} .|Ana bilgisayar bir derleme başvurusunu çözümlemeye çalıştığında bir özel durum oluşturduğunda gerçekleşir. İleti, derleme başvuru dizesi sağlar.|Derleme başvuruları \<@#assembly#> yönergelerden ve yönerge işlemcilerinde gelir. Derleme parametresinde belirtilen ' name ' parametresinin doğru olduğundan emin olun.|
|{1}Yönergesi için desteklenmeyen ' ' değerini belirtme girişimi {0}{2}|RequiresProvidesDirectiveProcessor tarafından gerçekleşir (tüm oluşturulan yönerge işlemcileri bundan türetilir), ancak, desteklenmeyen bir gerektirir veya bağımsız değişken sağlar.|Ad = ' Value ' çiftindeki adların, gerektirdiğinden ve parametrelerinin sağlanması doğru olduğundan emin olun.|
