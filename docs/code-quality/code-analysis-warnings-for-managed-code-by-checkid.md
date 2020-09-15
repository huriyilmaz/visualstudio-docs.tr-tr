---
title: Kod kalitesi kurallarına genel bakış
ms.date: 09/01/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1416
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 24f7dbcdd324620f2076f5fab8247c9ba99a72cb
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094232"
---
# <a name="code-quality-analysis-rules-by-rule-id"></a>Kural KIMLIĞINE göre kod kalitesi analiz kuralları

Aşağıdaki tabloda, kural tanımlayıcısına göre kod kalitesi analiz kuralları listelenmektedir.

| RuleId | Uyarı | Açıklama |
|---------| - | - |
| CA1000 | [CA1000: Genel türlerde statik üyeler belirtme](../code-quality/ca1000.md) | Genel türün statik üyesi çağrıldığında tür bağımsız değişkeni tür için belirlenmelidir. Destek çıkarımı desteklenmeyen genel örnek üyesi çağrıldığında tür bağımsız değişkeni üye için belirlenmelidir. Bu iki durumda tür bağımsız değişkenini belirleyen sözdizimi farklıdır ve kolaylıkla karıştırılır. |
| CA1001 | [CA1001: Atılabilen alanlara sahip türler atılabilir olmalıdır](../code-quality/ca1001.md) | Bir sınıf System.IDisposable tipi örnek alanını derler ve uygular ve sınıf IDisposable'ı uygulamaz. IDisposable alanını derleyen sınıf, yönetilmeyen kaynağı dolaylı yoldan sahiplenir ve IDisposable arayüzünü uygulamalıdır. |
| CA1002 | [CA1002: Genel listeleri gösterme](../code-quality/ca1002.md) | System. Collections. Generic. List< (/ \<(T> ) >), devralma değil, performans için tasarlanan genel bir koleksiyondur. Bu nedenle, Liste herhangi bir sanal üyeyi içermiyor. Bunun yerine devralma için tasarlanmış genel koleksiyonlar maruz kalmalıdır. |
| CA1003 | [CA1003: Genel olay işleyicisi örnekleri kullan](../code-quality/ca1003.md) |Bir tür, imzası iki parametre (ilk bir nesne ve ikinci olarak EventArgs 'a atanabilen bir tür) içeren void döndüren bir temsilci içerir ve kapsayan derleme Microsoft .NET Framework 2,0 ' i hedefler. |
| CA1005 | [CA1005: Genel türlerde aşırı parametre kullanmaktan kaçının](../code-quality/ca1005.md) | Daha çok tip parametresi, genel tip içerir, bilmek daha zordur ve hangi tip parametrelerinin temsil ettiğini anımsamak zordur. Genellikle bir tür parametresiyle ve bu, \<T> Sözlükte olduğu gibi iki tür parametresi olan belirli durumlarda belirgin bir şekilde açıktır \<TKey, TValue> . Ancak, iki parametreden fazla parametre varsa, birçok kullanıcı için zorluk derecesi artar. |
| CA1008 | [CA1008: Sabit listelerinin sıfır değeri olmalıdır](../code-quality/ca1008.md) | Tıpkı diğer türler gibi, başlatılmamış bir numaralandırmanın varsayılan değeri sıfırdır. İşaretlenmemiş bir geçerli numaralandırma, varsayılan değerin geçerli bir numaralandırma değeri olması için değeri sıfır olan bir üye tanımlaması gerekir. Numaralandırma FlagsAttribute özniteliği sıfır değerli üyeyi tanımlarsa, onun adı numaralandırmada hiçbir değerin ayarlanmadığı "Hiçbiri" olmalıdır. |
| CA1010 | [CA1010: Koleksiyonlar genel arabirimi uygulamalıdır](../code-quality/ca1010.md) | Bir koleksiyon kullanılabilirliğini genişletmek için genel koleksiyon arabirimlerinden birini uygulayın. Daha sonra koleksiyon genel koleksiyon türlerini doldurmak için kullanılabilir. |
| CA1012 | [CA1012: Soyut türlerin oluşturucuları olmamalıdır](../code-quality/ca1012.md) | Soyut türler üzerindeki kurucular yalnızca türetilen türler tarafından çağrılabilir. Ortak yapıcılar türün bir örneğini yaptığından ve siz bir soyut türün örneğini yapamayacağınızdan, soyut sınıf hatalı biçimde dizayn edilmiş ortak yapıcıya sahip olur. |
| CA1014 | [CA1014: Derlemeleri CLSCompliantAttribute ile işaretle](../code-quality/ca1014.md) | Ortak Dil Tanımlaması (CLS) ad kısıtlamalarını, veri türlerini ve karşıt programlama dillerini kullanırsa derlemelerin uyması zorunlu olan kuralları tanımlar. İyi tasarım, tüm derlemelerin kullanılarak açıkça CLS uyumluluğunu belirtmelerini belirler <xref:System.CLSCompliantAttribute> . Bu öznitelik bir derlemede yoksa, montaj uyumlu değildir. |
| CA1016 | [CA1016: Derlemeleri AssemblyVersionAttribute ile işaretleyin](../code-quality/ca1016.md) | .NET, bir derlemeyi benzersiz olarak tanımlamak ve kesin adlandırılmış derlemelerdeki türlere bağlamak için sürüm numarasını kullanır. Sürüm numarası, sürüm ve yayımcı ilkesi ile birlikte kullanılır. Varsayılan olarak uygulamalar yalnızca oluşturulmuş derleme sürümlerini çalıştırır. |
| CA1017 | [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017.md) |ComVisibleAttribute COM müşterilerinin yönetilen koda nasıl erişeceğini tanımlar. İyi tasarım derlemelerin açıkça COM görünürlüğünde gösterildiğini belirler. COM görünürlüğü tüm derleme için ayarlanabilir ve sonra bireysel tür ve tür üyeleri için geçersiz kılınabilir. Bu öznitelik yoksa, derleme içeriği COM istemcileri tarafından görülebilir. |
| CA1018 | [CA1018: Öznitelikleri AttributeUsageAttribute ile işaretle](../code-quality/ca1018.md) | Özel öznitelik tanımladığınızda, AttributeUsageAttribute kullanarak özel öznitelik kaynak kodunun nerede uygulanabilir olduğunu göstermek için işaretleyin. Bir özniteliğin anlamı ve amaçlanan kullanımı, kodun içinde onun varolan konumunu tanımlar. |
| CA1019 | [CA1019: Öznitelik bağımsız değişkenleri için erişimciler tanımlayın](../code-quality/ca1019.md) | Öznitelikler özniteliği işaretlediğinizde özelleştirilen zorunlu bağımsız değişkenleri tanımlayabilir. Ayrıca bunlar konum parametreleri olarak öznitelik yapıcısına verildiğinden duruma bağlı bağımsız değişkenler olarak da bilinirler. Zorunlu her bağımsız değişken için bağımsız değişkenin değeri yürütme zamanından alınması gerektiğinden öznitelik ilgili salt okunur özelliği de sağlamalıdır. Öznitelikler adlandırılmış bağımsız değişkenler olarak bilinen duruma bağlı bağımsız değişkenler olarak da tanımlanabilir. Bu bağımsız öznitelik oluşturucular ad tarafından sağlanır ve karşılık gelen bir okuma/yazma özelliğine sahip olmalıdır. |
| CA1021 | [CA1021: out parametrelerinden kaçının](../code-quality/ca1021.md) | Başvuruya ( out veya ref kullanarak ) göre türleri geçirmek işaretçi deneyimi gerektirir, değer türü ve referans türü arasındaki farkı ve işleme yöntemi ile birden çok değer döndürmeyi anlamak gerekir. Ayrıca, out ve ref parametreleri arasındaki fark açıkça anlaşılmadı. |
| CA1024 | [CA1024: Uygun yerlerde özellikleri kullanın](../code-quality/ca1024.md) | Ortak veya korumalı yöntem "Get" ile başlar, herhangi bir parametre almaz ve dizi olmayan bir değer döndüren adı vardır. Yöntem, özellik olmak için çok iyi bir aday olabilir. |
| CA1027 |[CA1027: Sabit listelerini FlagsAttribute ile işaretleyin](../code-quality/ca1027.md) | Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Anlamsız olarak birleştirildiğinde numaralandırmaya FlagsAttribute özelliğini uygulayın. |
| CA1028 | [CA1028: Sabit listesi depolaması Int32 olmalıdır](../code-quality/ca1028.md) | Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Varsayılan olarak, System.Int32 veri türü sabit değerleri depolamak için kullanılır. Bu temel türünü değiştirebilirsiniz, ancak bu önerilen bir senaryo değildir. |
| CA1030 | [CA1030: Uygun yerlerde olayları kullanın](../code-quality/ca1030.md) |Bu kural, normalde olaylar için kullanılan adlara sahip yöntemleri algılar. Yanıt olarak açıkça tanımlanmış bir durum değişikliği yöntemi çağrılırsa, olay işleyicisi tarafından yöntemin çağrılması gerekir. Yöntemi direkt olarak çağırmak yerine olayları yükselterek çağıran nesneler. |
| CA1031 | [CA1031: Genel özel durum türlerini yakalamayın](../code-quality/ca1031.md) | Genel özel durum yakalanmamalı. Daha özel istisnaları yakalayın ya da yakalama bloğundaki son durum olarak genel istisnaları yeniden fırlatın. |
| CA1032 |[CA1032: Standart özel durum oluşturucularını uygulayın](../code-quality/ca1032.md) | Yapıcıların tüm ayarlamasını sağlamaktaki başarısızlık, istisnalarla başa çıkmayı zorlaştırabilir. |
| CA1033 | [CA1033: Arabirim metotları alt türler tarafından çağrılabilmelidir](../code-quality/ca1033.md) | Ağzı açık dışarıdan görünen bir tür açık yöntem uygulaması ortak bir arabirim sağlar ve aynı ada sahip alternatif dışarıdan görünen bir yöntem sağlamaz. |
| CA1034 | [CA1034: İç içe türler görünür olmamalıdır](../code-quality/ca1034.md) | İç içe türü başka bir kapsamda bildirilen bir türdür. İç içe geçmiş türler, özel uygulama ayrıntılarını kapsayan türdeki kapsül oluşturma için kullanışlıdır. Bu amaçla kullanılan, iç içe türün dışarıdan görünür olmaması gerekir. |
| CA1036 | [CA1036: Karşılaştırılabilir türlerde metotları geçersiz kıl](../code-quality/ca1036.md) |Ortak veya korumalı tür System.IComparable arabirimini uygular. Object.Equals ne etkisiz kılınabilir ne de eşitlik için olan özel dil işleciyle aşırı yüklenebilir, eşitsizlik durumu olabilir, daha küçülebilir ya da büyüyebilir. |
| CA1040 |[CA1040: Boş arabirimlerden kaçının](../code-quality/ca1040.md) | Arayüzler bir davranış veya kullanım sözleşmesi sağlayan üyeleri tanımlar. Arabirim tarafından tanımlanan fonksiyonellik herhangi bir tür tarafından türün kalıtım hiyerarşisinde nerede belirdiği önemsenmeksizin devralınabilir. Tür arabirimin üyeleri için uygulamaları sağlayarak bir arayüz uygular. Boş bir arabirim herhangi bir üye tanımlamıyor; bu nedenle, uygulanabilir bir sözleşme tanımlamaz. |
| CA1041 | [CA1041: ObsoleteAttribute iletisi sağla](../code-quality/ca1041.md) | Tür veya üye belirtilen kendi ObsoleteAttribute.Message özelliğine sahip olmayan bir System.ObsoleteAttribute özniteliği kullanılarak işaretlendi. Özniteliğin ileti özelliği, türü veya ObsoleteAttribute kullanılarak işaretlenmiş tür veya üye derlendiğinde görüntülenir. Bu eski türü veya üye kullanıcı bilgilerini sağlar. |
| CA1043 | [CA1043: Dizin oluşturucular için tam sayı veya dize bağımsız değişken kullanın](../code-quality/ca1043.md) | Dizinle oluşturucular (dizinlenmiş özellikleri) dizin için integral veya dize türleri kullanılmalıdır. Bu türler, genellikle veri yapılarını dizinleme için kullanılır ve bunlar kitaplığın kullanılabilirliğini artırır. Nesne türünün kullanılması için belirli bir integral veya dize türü tasarım zamanında burada tarif edilemez, bu gibi durumlarda sınırlı tutulmalıdır. |
| CA1044 | [CA1044: Özellikler salt yazılır olmamalıdır](../code-quality/ca1044.md) | Salt okunur özelliğe sahip olmasına karşın kabul edilebilir ve genellikle gereklidir, tasarıma ilişkin yönergeler salt yazılır özellik kullanılmasını engeller. Bir kullanıcı değeri ayarlar ve sonra kullanıcı bu değeri görüntülemeyi engellerse bunun için herhangi bir güvenlik yoktur. Ayrıca, okuma erişimi olmadan, yararsız olduklarını sınırlayan paylaşılan nesnelerin durumu görüntülenemez. |
| CA1045 |[CA1045: Türleri başvuru olarak geçmeyin](../code-quality/ca1045.md) | Başvuruya ( out veya ref kullanarak ) göre türleri geçirmek işaretçi deneyimi gerektirir, değer türü ve referans türü arasındaki farkı ve işleme yöntemi ile birden çok değer döndürmeyi anlamak gerekir. Genel bir hedef kitle için tasarlayan kitaplık mimarları, kullanıcıların, veya parametreleriyle birlikte çalışmasını beklememelidir `out` `ref` . |
| CA1046 | [CA1046: Eşittir işlecini başvuru türlerinde aşırı yüklemeyin](../code-quality/ca1046.md) | Başvuru türleri için, varsayılan eşitlik işleci neredeyse her zaman doğrudur. Varsayılan olarak, yalnızca aynı nesneye gelirseniz iki başvuru eşit olur. |
| CA1047 |[CA1047: Sealed türlerde protected üyeler bildirmeyin](../code-quality/ca1047.md) | Türler, devralmasına erişebileceğiniz veya üyeyi geçersiz kılmak için korunan üyelerin türlerini bildirir. Tanım gereği, mühürlenmiş türler devralınamaz yani mühürlenmiş türler üzerindeki korunan yöntemler çağrılamaz. |
| CA1050 | [CA1050: Ad alanlarında türler bildirin](../code-quality/ca1050.md) | Türlerin ad çakışmalarını önlemek için ad alanlarını ve ilgili türü bir nesne sıradüzeni içinde düzenlemeniz için yöntem olarak bildirilir. |
| CA1051 | [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051.md) | Bir alanın birincil kullanım alanının uygulama ayrıntısı olması gerekir. Alanların özel veya iç olması gerekir ve özelliklerini kullanmaya maruz kalması gerekir. |
| CA1052 | [CA1052: Static tutucu türler sealed olmalıdır](../code-quality/ca1052.md) | Ortak veya korumalı tür yalnızca statik üyeleri içerir ve mühürlenmiş (C# Reference) (NotInheritable) değiştirici kullanarak bildirilmez. Devralınmayacak anlamına gelen tür mühürleme değiştirici kullanılarak basit tür gibi kullanılmak için işaretlenmelidir. |
| CA1053 |[CA1053: Static tutucu türlerin oluşturucuları olmamalıdır](../code-quality/ca1053.md) | Ortak veya iç içe geçmiş ortak tür yalnızca statik üyeleri bildirir ve ortak veya korumalı varsayılan bir oluşturucu vardır. Statik üyeleri çağırma bir tür örneği gerektirmediğinden kurucu gereksizdir. Dize aşırı yüklemesi, emniyet ve güvenlik için dize bağımsız değişkeni kullanılarak tekdüzen kaynak tanımlayıcısı (URI) çağırmalıdır. |
| CA1054 | [CA1054: URI parametreleri dize olmamalıdır](../code-quality/ca1054.md) | Bir yöntem URI'yı sunan bir dizeyi alırsa, bu hizmetleri sağlayan güvenli şekilde URI sınıfının bir örneğini alır, karşılık gelen aşırı olmalıdır. |
| CA1055 | [CA1055: URI dönüş değerleri dize olmamalıdır](../code-quality/ca1055.md) | Bu kural, yöntemin URI döndürdüğünü varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. System.Uri sınıfı bu hizmetleri güvenli bir şekilde sağlar. |
| CA1056 | [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056.md) | Bu kural, özelliğin Tekdüzen Kaynak Tanımlayıcısı (URI) tarafından temsil edildiğini varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. System.Uri sınıfı bu hizmetleri güvenli bir şekilde sağlar. |
| CA1058 | [CA1058: Türler belirli temel türleri aşmamalıdır](../code-quality/ca1058.md) | Dışarıdan görünen tür belirli temel türleri genişletir. Diğer seçenekleri kullanın. |
| CA1060 | [CA1060: NativeMethods sınıfına P/Invoke taşı](../code-quality/ca1060.md) | System.Runtime.InteropServices.DllImportAttribute özniteliği kullanılarak işaretlenenler veya ' de Declare anahtar sözcüğü kullanılarak tanımlanan Yöntemler gibi platform çağırma yöntemleri, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] yönetilmeyen koda erişim. Bu yöntemler, NativeMethods, SafeNativeMethods veya UnsafeNativeMethods sınıfının üyesi olmalıdır. |
| CA1061 |[CA1061: Temel sınıf metotlarını gizlemeyin](../code-quality/ca1061.md) | Basit türdeki bir yöntem türetilmiş türdeki adlandırılmış yöntem tarafından gizlenmiştir, türetilmiş yöntemin parametre imzası yalnızca türetilmiş türleri ve karşılık gelen temel yöntemin parametre imzası daha zayıf türlerine göre farklı olduğunda temel türde bir yöntemin türetilmiş türle aynı adlı yöntem olarak gizlidir. |
| CA1062 | [CA1062: Genel metotların bağımsız değişkenlerini doğrulayın](../code-quality/ca1062.md) | Dışarıdan görünen yöntemlerin null'a karşı denetlenmesi için geçirilen tüm başvuru bağımsız değişkenleri. |
| CA1063 | [CA1063: IDisposable'ı doğru uygulayın](../code-quality/ca1063.md) | Tüm IDisposable türleri Dispose kalıbını doğru uygulamalıdır. |
| CA1064 | [CA1064: Özel durumlar genel olmalıdır](../code-quality/ca1064.md) | Bir iç özel durum yalnızca kendi iç kapsamı içinde görülebilir. İç kapsam dışında kalan özel durumlardan sonra, sadece basit istisnalar istisna yakalamak için kullanılabilir. İç özel durum, veya öğesinden devralınmışsa, <xref:System.Exception> <xref:System.SystemException> <xref:System.ApplicationException> dış kod özel durumla ne yapılacağını belirlemek için yeterli bilgiye sahip olmayacaktır. |
| CA1065 | [CA1065: Beklenmeyen konumlarda özel durum harekete geçirmeyin](../code-quality/ca1065.md) | İstisna atılmasını beklemeyen yöntem bir istisna atar. |
| CA1066 | [CA1066: Equals’ı geçersiz kılarken IEquatable uygulayın](../code-quality/ca1066.md) | Değer türü yöntemi geçersiz kılar <xref:System.Object.Equals%2A> , ancak uygulamaz <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: IEquatable uygularken Equals’ı geçersiz kılın](../code-quality/ca1067.md) | Bir tür uygular <xref:System.IEquatable%601> , ancak metodunu geçersiz kılmaz <xref:System.Object.Equals%2A> . |
| CA1068 | [CA1068: CancellationToken parametreleri en sonda olmalıdır](../code-quality/ca1068.md) | Bir yöntem, son parametre olmayan CancellationToken parametresine sahiptir. |
| CA1069 | [CA1069: Sabit listeleri yinelenen değerlere sahip olmamalıdır](../code-quality/ca1069.md) | Bir numaralandırma, aynı sabit değere açıkça atanmış birden çok üyeye sahiptir. |
| CA1070 | [CA1070: Olay alanlarını sanal olarak bildirme](../code-quality/ca1070.md) | [Alan benzeri bir olay](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) sanal olarak bildirildi. |
| CA1200 | [CA1200: cref etiketlerini ön ek ile kullanmaktan kaçının](../code-quality/ca1200.md) | XML belgesi etiketindeki [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. `cref`Derleyicinin başvuruları doğrulamasını önlediği için ön ekleri olan etiketleri kullanmaktan kaçının. Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler. |
| CA1303 | [CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303.md) | Dışarıdan görülebilen bir yöntem, bir dize sabit değerini bir .NET oluşturucusuna veya yöntemine parametre olarak geçirir ve bu dize yerelleştirilebilir olmalıdır. |
| CA1304 | [CA1304: CultureInfo belirt](../code-quality/ca1304.md) | Yöntem veya Oluşturucu System.Globalization.CultureInfo parametre kabul eden aşırı yüklenmiş üye arar ve yöntem veya oluşturucu CultureInfo parametresi aşırı yükleme çağıramaz. Bir CultureInfo veya System.IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir. |
| CA1305 | [CA1305: IFormatProvider belirt](../code-quality/ca1305.md) | Yöntem veya oluşturucu System.IFormatProvider parametresini kabul eden aşırı yüklü bir veya daha fazla üye arar ve yöntem veya oluşturucu IFormatProvider parametre yüklemesini çağırmaz. Bir System.Globalization.CultureInfo veya IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir. |
| CA1307 | [CA1307: Daha anlaşılır olması için StringComparison belirtin](../code-quality/ca1307.md) | StringComparison parametresi ayarlanmamış bir yöntemi aşırı bir dize karşılaştırma işleminde kullanır. |
| CA1308 |[CA1308: Dizeleri büyük harfe normalleştirin](../code-quality/ca1308.md) | Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu küçük harfe dönüştürüldüğünde gidiş dönüş yapamaz. |
| CA1309 | [CA1309: Sıralı StringComparison kullanın](../code-quality/ca1309.md) | StringComparison parametresini Ordinal ya da OrdinalIgnoreCase'a ayarlayamayan dilbilimsel olmayan dize karşılaştırma işlemi. Açıkça StringComparison.Ordinal veya StringComparison.OrdinalIgnoreCase için parametre ayarıyla kodunuz genellikle hızlanır, daha doğru olur ve daha güvenilir hale gelir. |
| CA1310 | [CA1310: Doğruluk için StringComparison belirtin](../code-quality/ca1310.md) | Dize karşılaştırma işlemi, StringComparison parametresi ayarlanmamış ve varsayılan olarak kültüre özgü dize karşılaştırmayı kullanan bir yöntem aşırı yüklemesi kullanır. |
| CA1401 | [CA1401: P/Invoke görünür olmamalıdır](../code-quality/ca1401.md) | Ortak bir türdeki ortak veya korumalı yöntemin System.Runtime.InteropServices.DllImportAttribute özniteliği vardır (Ayrıca içindeki Declare anahtar sözcüğü tarafından uygulanır [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Bu tür yöntemler açıkta kalmamalıdır. |
| CA1416 | [CA1416: platform uyumluluğunu doğrulama](../code-quality/ca1416.md) | Bir bileşende platforma bağımlı API 'Lerin kullanılması, kodun artık tüm platformlarda çalışmamasına neden olur. |
| CA1417 | [CA1417: `OutAttribute` P/Invoke için dize parametrelerinde kullanmayın](../code-quality/ca1417.md) | Değeri ile geçirilen dize parametreleri, `OutAttribute` dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir. |
| CA1501 | [CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501.md) | Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. |
| CA1502 | [CA1502: Aşırı karmaşıklıktan kaçının](../code-quality/ca1502.md) | Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer. |
| CA1505 | [CA1505: Bakımı yapılamayan kodlardan kaçının](../code-quality/ca1505.md) | Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir. |
| CA1506 | [CA1506: Aşırı sınıf bağlantısından kaçının](../code-quality/ca1506.md) | Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer. |
| CA1507 | [CA1507: Dize yerine nameof kullanma](../code-quality/ca1507.md) | Bir dize sabit değeri, bir ifadenin kullanılabileceği bir bağımsız değişken olarak kullanılır `nameof` . |
| CA1508 | [CA1508: Ölü koşullu kodlardan kaçının](../code-quality/ca1508.md) | Bir yöntemde, her zaman çalışma zamanında olarak değerlendirilen koşullu kod bulunur `true` `false` . Bu `false` , koşulun dalındaki ölü koda yol açar. |
| CA1509 | [CA1509: Kod ölçümleri yapılandırma dosyasında geçersiz girdi](../code-quality/ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) ve [CA1506](ca1506.md)gibi kod ölçüm kuralları, geçersiz bir girişi olan adlı bir yapılandırma dosyası sağladı `CodeMetricsConfig.txt` . |
| CA1700 | [CA1700: Sabit listesi değerlerini 'Reserved' olarak adlandırmayın](../code-quality/ca1700.md) | Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır. |
| CA1707 | [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707.md) | Kural gereği, tanımlayıcı adlar alt çizgi (_) karakterini içermez. Bu kural ad alanlarını, türleri, üyeleri ve parametreleri denetler. |
| CA1708 | [CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708.md) | Ortak dil çalışma zamanı hedef dilleri büyük/küçük harf duyarlı olması gerekmediğinden ad alanları, türler, üyeler ve parametreler için tanımlayıcılar yalnızca büyük/küçük harfe göre farklılık göstermeyebilir. |
| CA1710 | [CA1710: Tanımlayıcılar doğru soneke sahip olmalıdır](../code-quality/ca1710.md) |Kural gereği, belli uzatılan türlerin adları ya da belli arayüzlerin uygulanması, ya da bu türlerden türetilen, basit tür veya arayüzden oluşturulan son eke sahiptir. |
| CA1711 | [CA1711: Tanımlayıcılar yanlış sonek içermemelidir](../code-quality/ca1711.md) | Kural gereği, yalnızca, belirli temel türleri genişleten veya bazı arabirimleri ya da bu türlerinden türetilmiş türleri uygulayan tür adları belirli ayrılmış öneklerle bitmelidir. Diğer tür adları aşağıdaki ayrılmış sonekleri kullanmamalı. |
| CA1712 | [CA1712: Sabit listesi değerlerine tür adını önek olarak eklemeyin](../code-quality/ca1712.md) | Numaralandırma üyelerinin adları, tür adı kullanılarak öneklenmemiştir, çünkü geliştirici araçlarının tür bilgisini sağlaması beklenmez. |
| CA1713 | [CA1713: Olaylar önce ya da sonra önekine sahip olmamalıdır](../code-quality/ca1713.md) | Olay adı "Önce" veya "Sonra" ile başlar. Belirli bir sırayla ilgili olayları adlandırmak için şimdiki veya geçmiş zamanı göreceli konumun sıralı eylemlerini belirtmek için kullanın. |
| CA1714 | [CA1714: Bayrak sabit listeleri çoğul adlara sahip olmalıdır](../code-quality/ca1714.md) | Ortak bir numaralandırma System.FlagsAttribute özniteliğine sahiptir ve adı "s" ile bitmez. Bileşik FlagsAttribute kullanarak işaretlenen öznitelik birden fazla değer belirtilebilir, çünkü çoğul adları vardır. |
| CA1715 | [CA1715: Tanımlayıcılar doğru ön eke sahip olmalıdır](../code-quality/ca1715.md) | Dışarıdan görünen bir arabirimin adı büyük "I" ile başlamıyor. Genel tür parametresi dışarıdan görünen tür veya yöntem adı büyük "T" ile başlamıyor. |
| CA1716 | [CA1716: Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir](../code-quality/ca1716.md) | Ad alanı adı veya tür adı ayrılmış anahtar sözcük bir programlama dili ile eşleşir. Tanımlayıcı adı ve türleri için ortak dil çalışma zamanı, hedef diller tarafından tanımlanan anahtar sözcüklerle aynı değildir. |
| CA1717 | [CA1717: Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır](../code-quality/ca1717.md) | Adlandırma kuralları numaralandırma için adlandırma aynı anda birden fazla numaralandırma değeri olduğunu gösterir. |
| CA1720 |[CA1720: Tanımlayıcılar tür adları içermemelidir](../code-quality/ca1720.md) | Parametre adı dışarıdan görünen üye, veri türü adını içerir ya da açıkça görünen üyenin adı dil özellikli veri türü adı içerir. |
| CA1721 | [CA1721: Özellik adları get metotları ile eşleşmemelidir](../code-quality/ca1721.md) |Ortak veya korumalı bir üye adı "Get" ile başlar ve aksi durumda ortak veya korumalı özellik adıyla eşleşir. "Get" yöntemlerinin ve özelliklerinin açıkça işlevlerinden ayırt edilebilen adları olması gerekir. |
| CA1724 | [CA1724: Tür adları ad alanları ile eşleşmemelidir](../code-quality/ca1724.md) | Tür adları .NET ad alanlarının adlarıyla eşleşmemelidir. Bu kuralın ihlali kitaplığın kullanılabilirliğini azaltabilir. |
| CA1725 | [CA1725: Parametre adları temel bildirimle eşleşmemelidir](../code-quality/ca1725.md) | Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir. |
| CA1801 | [CA1801: Kullanılmayan parametreleri gözden geçirin](../code-quality/ca1801.md) | Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. |
| CA1802 |[CA1802: Uygun yerlerde sabitleri kullanın](../code-quality/ca1802.md) |Bir alan statik ve salt okunur (paylaşılan ve salt okunur) olarak tanımlanır [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ve derleme zamanında oluşturulabilir bir değer kullanılarak başlatılır. Hedeflenen alana atanan değer derleme zamanında oluşturulabilir olduğundan, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] değerin çalışma zamanı yerine derleme zamanında hesaplanabilmesi için bildirimi const (const) alanı olarak değiştirin. |
| CA1805 | [CA1805: Gerekmediği durumlarda başlatmayın](../code-quality/ca1805.md) | .NET çalışma zamanı, oluşturucuyu çalıştırmadan önce, başvuru türlerindeki tüm alanları varsayılan değerlerine başlatır. Çoğu durumda, bir alanı varsayılan değerine açıkça başlatmak, bakım maliyetlerine eklenen ve performansı düşürebilir (örneğin, daha fazla derleme boyutuyla). |
| CA1806 | [CA1806: Metot sonuçlarını yoksaymayın](../code-quality/ca1806.md) | Yeni bir nesne oluşturulur, ancak hiç kullanılmaz veya çağrılan yeni dizeyi oluşturur ve döndürür ve yeni dize hiç kullanılmaz ya da COM veya P/Invoke yöntemi, bir HRESULT ya da hiç kullanılmayan hata kodu döndürür. |
| CA1810 | [CA1810: Başvuru türü statik alanları satır içinden başlatın](../code-quality/ca1810.md) | Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik oluşturucu denetimleri performansı düşürebilir. |
| CA1812 | [CA1812: Örneklenmemiş iç sınıflardan kaçının](../code-quality/ca1812.md) | Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz. |
| CA1813 | [CA1813: Mühürsüz özniteliklerden kaçının](../code-quality/ca1813.md) | .NET özel özniteliklerin alınması için yöntemler sağlar. Varsayılan olarak, bu yöntemleri öznitelik devralma hiyerarşisinde arar. Öznitelik mühürleme kalıtım hiyerarşisi aracılığıyla aramayı ortadan kaldırır ve performansı artırabilir. |
| CA1814 | [CA1814: Çok boyutlu diziler yerine basit dizileri tercih edin](../code-quality/ca1814.md) | Basit bir dizi, öğeleri dizi olan bir dizidir. Öğeleri olan diziler bazı veri kümeler için daha az harcanmış önde gelen farklı boyutlarda olabilir. |
| CA1815 | [CA1815: Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın](../code-quality/ca1815.md) | Değer türleri için, Equals'ın devralınmış uygulaması Reflection kitaplığını kullanır ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals'ı uygulamalıdır. |
| CA1816 | [CA1816: GC.SuppressFinalize'ı doğru çağırın](../code-quality/ca1816.md) | Dispose uygulamasının bir yöntemi GC çağrısını yapmaz. SuppressFinalize ya da Dispose çağrılarının uygulanması olmayan bir yöntem GC. SuppressFinalize ya da bir yöntemi GC çağırır. SuppressFinalize ve bu (Visual Basic) dışında bir şey geçirir. |
| CA1819 | [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819.md) | Özellik salt okunur olsa bile özellikleri tarafından döndürülen dizi yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Tipik olarak, kullanıcılar bu tür bir özellik aramanın performans üzerindeki olumsuz etkilerini anlamayacaktır. |
| CA1820 | [CA1820: Dize uzunluğunu kullanarak boş dizeleri test edin](../code-quality/ca1820.md) | String.Length özelliği veya String.IsNullOrEmpty yöntemi, Equals kullanılmasından önemli ölçüde daha hızlıdır. |
| CA1821 | [CA1821: Boş sonlandırıcıları kaldırın](../code-quality/ca1821.md) | Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Boş sonlandırıcı eklenen yükü çeker ve hiçbir avantaj sunmaz. |
| CA1822 |[CA1822: Üyeleri static olarak işaretleyin](../code-quality/ca1822.md) | Örnek verilerine erişmeyen Üyeler veya çağrı örnekleri metotları statik (içinde paylaşılan) olarak işaretlenebilir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için verebilir. |
| CA1823 | [CA1823: Kullanılmayan özel alanlardan kaçının](../code-quality/ca1823.md) | Derlemede erişimi görülmeyen özel alanlar algılandı. |
| CA1824 |[CA1824: Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin](../code-quality/ca1824.md) | NeutralResourcesLanguage özniteliği, bir derleme için nötr kültürün kaynaklarını göstermek için kullanılan dilin kaynak yöneticisini bilgilendirir. Bu ilk yüklediğiniz kaynak için arama performansını artırır ve çalışma kümenizi azaltabilir. |
| CA1825 |[CA1825: Sıfır uzunluklu dizi ayırmalarından kaçının](../code-quality/ca1825.md) | Sıfır uzunluklu bir diziyi başlatmak gereksiz bellek ayırmaya yol açar. Bunun yerine, çağırarak statik olarak ayrılan boş dizi örneğini kullanın <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Bellek ayırma, bu yöntemin tüm etkinleştirmeleri genelinde paylaşılır. |
| CA1826 |[CA1826: Linq Numaralandırma metodu yerine property kullan](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> LINQ yöntemi eşdeğer, daha verimli bir özelliği destekleyen bir tür üzerinde kullanıldı. |
| CA1827 |[CA1827: Any kullanılabiliyorsa Count/LongCount kullanma](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> ya da yöntemi <xref:System.Linq.Enumerable.LongCount%2A> , <xref:System.Linq.Enumerable.Any%2A> yöntemin daha verimli olacağı yerde kullanılmıştır. |
| CA1828 |[CA1828: AnyAsync kullanılabiliyorsa CountAsync/LongCountAsync kullanma](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> ya da yöntemi <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> , <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> yöntemin daha verimli olacağı yerde kullanılmıştır. |
| CA1829 |[CA1829: Enumerable.Count metodu yerine Length/Count özelliğini kullan](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> LINQ yöntemi eşdeğer, daha etkin veya özelliği destekleyen bir tür üzerinde kullanıldı `Length` `Count` . |
| CA1830 |[CA1830: StringBuilder'da kesin tür belirtilmiş Append ve Insert metodu aşırı yüklemelerini tercih et](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> ve <xref:System.Text.StringBuilder.Insert%2A> birden çok tür için aşırı yüklemeler sağlar <xref:System.String> .  Mümkün olduğunda, ToString () ve dize tabanlı aşırı yüklemeyi kullanarak türü kesin belirlenmiş aşırı yüklemeleri tercih edin. |
| CA1831 |[CA1831: Uygun olduğunda dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın](../code-quality/ca1831.md) | Bir dizede Aralık Dizin Oluşturucu kullanırken ve değeri örtük olarak ReadOnlySpan &lt; char türüne atamak için &gt; , yöntemi <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , dizenin istenen bölümünün bir kopyasını üreten yerine kullanılır. |
| CA1832 |[CA1832: Bir dizinin ReadOnlySpan veya ReadOnlyMemory kısmını almak için Aralık tabanlı dizin oluşturucular yerine AsSpan ya da AsMemory kullanın](../code-quality/ca1832.md) | Bir dizide Aralık Dizin Oluşturucu kullanırken ve değeri örtük olarak bir <xref:System.ReadOnlySpan%601> veya <xref:System.ReadOnlyMemory%601> türüne atandığında, yöntemi <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , dizinin istenen bölümünün bir kopyasını üreten yerine kullanılır. |
| CA1833 |[CA1833: Bir dizinin Span veya Memory kısmını almak için Aralık tabanlı dizin oluşturucular yerine AsSpan ya da AsMemory kullanın](../code-quality/ca1833.md) | Bir dizide Aralık Dizin Oluşturucu kullanırken ve değeri örtük olarak bir <xref:System.Span%601> veya <xref:System.Memory%601> türüne atandığında, yöntemi <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , dizinin istenen bölümünün bir kopyasını üreten yerine kullanılır. |
| CA1834 |[CA1834: Tek karakterli dizeler için StringBuilder.Append(char) kullanın](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> , `Append` bağımsız değişkeni olarak bir olan aşırı yüküne sahiptir `char` . `char`Performans nedenleriyle aşırı yüklemeyi çağırmayı tercih edin. |
| CA1835 |[CA1835: ' ReadAsync ' ve ' WriteAsync ' için ' Memory' tabanlı aşırı yüklemeleri tercih et](../code-quality/ca1835.md) | ' Stream ', &lt; &gt; ilk bağımsız değişken olarak ' bellek baytı ' ve &lt; &gt; ilk bağımsız değişken olarak ' readonlymemory byte ' olan bir ' WriteAsync ' aşırı yüklemesi olan ' ReadAsync ' aşırı yüklemesine sahip. Daha verimli olan bellek tabanlı aşırı yüklemeleri çağırmayı tercih edin. |
| CA1836 |[CA1836: `IsEmpty` `Count` kullanılabilir olduğunda tercih et](../code-quality/ca1836.md) | `IsEmpty` `Count` `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> Nesnenin bir öğe içerip içermediğini ya da olmadığını anlamak için, veya ' den daha verimli bir özellik tercih edin. |
| CA1837 | [CA1837: `Environment.ProcessId` yerine kullanın `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` daha basit ve daha hızlıdır `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: `StringBuilder` P/Invoke için parametrelerden kaçının](../code-quality/ca1838.md) | ' StringBuilder ' öğesinin sıralaması her zaman bir sıralama işlemi için birden çok ayırmaya neden olan bir yerel arabellek kopyası oluşturur. |
| CA2000 | [CA2000: Kapsamı kaybetmeden önce nesneleri bırakın](../code-quality/ca2000.md) | Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır. |
| CA2002 |[CA2002: Zayıf kimliği olan nesneleri kilitlemeyin](../code-quality/ca2002.md) |Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir. |
| CA2007 | [CA2007: Doğrudan bir Görevi beklemeyin](ca2007.md) | Zaman uyumsuz bir [awaits](/dotnet/csharp/language-reference/keywords/await) yöntem doğrudan bekler <xref:System.Threading.Tasks.Task> . Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task> doğrudan bekler, görevi oluşturan aynı iş parçacığında devamlılık oluşur. Bu davranış, performans açısından maliyetli olabilir ve Kullanıcı arabirimi iş parçacığında kilitlenmeye neden olabilir. <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType>Devamlılığını sağlamak için çağırmayı düşünün. |
| CA2008 | [CA2008: TaskScheduler geçirmeden görev oluşturmayın](ca2008.md) | Bir görev oluşturma veya devamlılık işlemi, bir parametre belirtmeyen bir yöntem aşırı yüklemesi kullanır <xref:System.Threading.Tasks.TaskScheduler> . |
| CA2009 | [CA2009: Bir ImmutableCollection değeri üzerinde ToImmutableCollection çağırma](ca2009.md) | `ToImmutable` Yöntem, ad alanından sabit bir koleksiyonda gereksiz şekilde çağrıldı <xref:System.Collections.Immutable> . |
| CA2011 | [CA2011: Özelliği, ayarlayıcısı içinde atama](ca2011.md) | Bir özelliğe yanlışlıkla kendi [set erişimcisi](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)içinde bir değer atandı. |
| CA2012 | [CA2012: ValueTask’leri doğru kullanın](ca2012.md) | Üye etkinleştirmeleri tarafından döndürülen ValueTasks, doğrudan beklenmek üzere tasarlanmıştır.  Bir ValueTask 'ı birden çok kez kullanmaya çalışır veya tamamlanması bilinmadan önce bir sonuca doğrudan erişmek için bir özel durumla veya bozulmaya neden olabilir.  Bu tür bir ValueTask, büyük olasılıkla işlevsel bir hatanın göstergesidir ve performansın düşmesine neden olabilir. |
| CA2013 | [CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın](ca2013.md) | Kullanılarak değerler karşılaştırılırken <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , objA ve objB değer türlerseler, yönteme geçirilmeden önce bunlar paketlenirler <xref:System.Object.ReferenceEquals%2A> . Bu, hem objA hem de objB bir değer türünün aynı örneğini temsil ediyorsa bile, <xref:System.Object.ReferenceEquals%2A> Yöntem false değerini döndürür. |
| CA2014 | [CA2014: Döngülerde stackalloc kullanmayın.](ca2014.md) | Bir stackalloc tarafından ayrılan yığın alanı yalnızca geçerli metodun çağrısının sonunda serbest bırakılır.  Bunu bir döngüde kullanmak, sınırsız yığın büyümesi ve nihai yığın taşması koşullarına yol açabilir. |
| CA2015 | [CA2015: MemoryManager T 'den türetilmiş türler için sonlandırıcılar tanımlama &lt;&gt;](ca2015.md) | ' Dan türetilmiş bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , bir tarafından kullanılmaya devam edilirken belleğin serbest olmasına izin verebilir <xref:System.Span%601> . |
| CA2016 | [CA2016: CancellationToken parametresini, parametre alan metotlara iletin](ca2016.md) | `CancellationToken`İşlem iptal bildirimlerinin düzgün şekilde yayıldığından emin olmak için parametreyi bir tane alan yöntemlere iletin veya `CancellationToken.None` açıkça belirteci yaymadığınızı belirtmek için açıkça geçiş yapın. |
| CA2100 | [CA2100: SQL sorgularını güvenlik açıkları için inceleyin](../code-quality/ca2100.md) | Bir yöntem, yönteme dize değişkeninden oluşturulmuş dize kullanarak System.Data.IDbCommand.CommandText özelliğini ayarlar. Bu kural, dize değişkeninin kullanıcı girişi içerdiğini varsayar. Kullanıcı girişi ile oluşturulan SQL komut dizesi, SQL enjeksiyon saldırılarına karşı savunmasız durumdadır. |
| CA2101 |[CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](../code-quality/ca2101.md) | Bir platform çağırma üyesi kısmen güvenilen arayanlara izin verir, bir dize parametresine sahiptir ve dize açıkça sıralanmaz. Bu, olası bir güvenlik açığına neden olabilir. |
| CA2109 | [CA2109: Görünen olay işleyicilerini gözden geçirin](../code-quality/ca2109.md) | Ortak veya korunan olay işleme yöntemi algılandı. Olay işleme yöntemleri kesinlikle gerekli olmadığı sürece maruz bırakılmamalıdır. |
| CA2119 | [CA2119: Özel arabirimleri karşılayan metotları mühürleyin](../code-quality/ca2119.md) | Devralınabilir bir ortak tür, bir iç (arkadaş) arabirimin geçersiz kılınabilir bir yöntem uygulamasını sağlar [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Bu kuralın ihlalini düzeltmek için yöntemin, derlemenin dışından geçersiz kılınmasını önleyin. |
| CA2153 |[CA2153: bozuk durum özel durumlarını işlemeyi önleyin](../code-quality/ca2153.md) | Bozulmuş durum özel durumları (CSEs), işlem sırasında bellek bozulmasının bulunduğunu gösterir. Bir saldırgan bozuk bellek bölgesine bir yararlanma işlemi gerçekleştirilebileceği takdirde, işlemin çökmesine izin vermek yerine bunları yakalama güvenlik açıklarına yol açabilir. |
| CA2200 | [CA2200: Yığın ayrıntılarını korumak için yeniden fırlatın](../code-quality/ca2200.md) | Tekrar fırlatılan bir özel durum ve fırlatma açıklamasında açıkça belirtilen özel durum. Bir özel durum throw deyiminde özel durum belirterek yeniden fırlatılırsa yöntem listesi özel durum döndüren özgün yöntem ile kaybolan geçerli yöntem arasında çağırır. |
| CA2201 | [CA2201: Ayrılmış özel durum türlerini harekete geçirmeyin](../code-quality/ca2201.md) | Bu özgün hata algılama ve hata ayıklamayı zorlaştırır. |
| CA2207 | [CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207.md) | Bir değer türü açık bir statik oluşturucu bildirir. Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın. |
| CA2208 |[CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin](../code-quality/ca2208.md) | Varsayılan (parametresiz) kurucu veya ArgumentException türeyen özel bir durum türü için çağrı yapılır veya hatalı dize bağımsız değişkeni parametreli bir kurucu veya ArgumentException türeyen bir özel durum türü iletilir. |
| CA2211 |[CA2211: Sabit olmayan alanlar görünür olmamalıdır](../code-quality/ca2211.md) | Ne sabitler, ne de salt okunur olan statik alanlar güvenli iş parçacığı değildir. Böyle bir alana erişim dikkatli bir şekilde denetlenebilir ve sınıf nesnesi erişimi eşitlemek için gelişmiş programlama tekniklerini gerektirir. |
| CA2213 | [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213.md) | IDisposable uygulayan türlerin alanları System.IDisposable uygulayan bir türle bildirilir. Bir Dispose yöntemi alanının tanıtıcısının bildirim türü Dispose yöntemi tarafından çağrılmaz. |
| CA2214 | [CA2214: Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın](../code-quality/ca2214.md) | Kurucu sanal bir yöntemi çağırdığında, yapıcı yöntemini çağıran örneği işletilmemiş olabilir. |
| CA2215 | [CA2215: Atma metotları taban sınıf atmayı çağırmalıdır](../code-quality/ca2215.md) | Tür atılabilen bir türden devralınırsa, kendi Dispose yönteminden basit tür olan Dispose yöntemini çağırmalıdır. |
| CA2216 |[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216.md) | System.IDisposable uygulayan yöntem ve yönetilmeyen kaynakların kullanımını öneren alanlar Object.Finalize'da açıklandığı gibi sonlandırıcıyı uygulamazlar. |
| CA2217 | [CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md) |Dışarıdan görünen FlagsAttribute ile işaretlenmiş numaralandırma ve ikinin katı olmayan ya da numaralandırma üzerinde tanımlanan diğer değerlerin kombinasyonu olmayan bir ya da daha fazla değer vardır. |
| CA2219 | [CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin](../code-quality/ca2219.md) | Bir istisna sonlandırıcı ya da arıza yan tümcesine neden olduğunda, yeni istisna aktif istisnayı saklar. Filtre yan tümcesinde bir özel durum ortaya çıktığında, çalışma zamanı özel durumu sessizce yakalar. Bu özgün hata algılama ve hata ayıklamayı zorlaştırır. |
| CA2225 | [CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225.md) |Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı. Adlandırılmış alternatif üye operatörün sağladığı gibi aynı fonksiyonlara erişmeyi sağlar ve aşırı yüklenmiş operatörlere destek olmayan dilleri programlayan programcılar için bunlar sağlanmıştır. |
| CA2226 | [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226.md) | Bir tür, eşitlik ya da eşitsizlik operatörünü uygular ve ters işleci uygulamaz. |
| CA2227 |[CA2227: Koleksiyon özellikleri salt okunur olmalıdır](../code-quality/ca2227.md) |Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamını farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir. |
| CA2229 | [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229.md) | Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. |
| CA2231 | [CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](../code-quality/ca2231.md) | Bir değer türü Object.Equals'ı geçersiz kılar, ama eşitlik işlecini uygulamaz. |
| CA2234 | [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234.md) | Adında "URI", "URI", "urn", "urn", "url" veya "url" içeren bir dize parametresi olan yöntem çağrısı yapıldı. Bildirim türü yöntemi, System.Uri parametresini aşırı yüklemeye uyan yöntemi içerir. |
| CA2235 | [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235.md) | Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. |
| CA2237 | [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237.md) | Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınması için, türler ISerializable arabirimini uygulaması aracılığıyla özel seri hale getirme yordamı kullanıldığında SerializableAttribute özniteliği kullanılarak işaretlenmelidir. |
| CA2241 | [CA2241: Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın](../code-quality/ca2241.md) | System.String.Format için geçirilen biçim, her bir nesne bağımsız değişkeninden sorumlu olan öğe biçimini içermez. |
| CA2242 |[CA2242: NaN için doğru test edin](../code-quality/ca2242.md) | Bu ifade, değeri Single.Nan veya Double.Nan'a karşı test eder. Single.IsNan(Single) ya da Double.IsNan(Double) değerini test etmek için kullanın. |
| CA2243 |[CA2243: Öznitelik dize harfleri doğru çözümlenmelidir](../code-quality/ca2243.md) | Bir öznitelik dize literal parametresi, URL, GUID ya da sürüm için doğru ayrıştırmaz. |
| CA2244 | [CA2244: Dizine eklenmiş öğe başlatmalarını yineleme](../code-quality/ca2244.md) | Bir nesne başlatıcısının aynı sabit dizine sahip birden fazla dizinli öğe başlatıcısı vardır. Son başlatıcı gereksizdir. |
| CA2245 | [CA2245: Bir özelliği kendisine atama](../code-quality/ca2245.md) | Bir özellik yanlışlıkla kendisine atandı. |
| CA2246 | [CA2246: Sembol ve üyesini aynı deyime atama](../code-quality/ca2246.md) | Bir sembol ve üyesini atama, diğer bir deyişle, bir alan veya özellik, aynı deyimde önerilmez. Üye erişiminin, bu deyimdeki atamadan önce simgenin eski değerini veya atamasından yeni değeri kullanması amaçlandıysa, bu, net değildir. |
| CA2247 | [CA2247: TaskCompletionSource oluşturucusuna geçirilen bağımsız değişken TaskContinuationOptions numaralandırması yerine TaskCreationOptions sabit listesi olmalıdır.](../code-quality/ca2247.md) | TaskCompletionSource, temel alınan görevi denetleyen TaskCreationOptions ve görevde saklanan nesne durumunu alan oluşturucuların bulunduğu oluşturuculara sahiptir.  TaskCreationOptions yerine bir TaskContinuationOptions 'ı yanlışlıkla geçirmek, çağrının durum olarak kabul edilmesine neden olur. |
| CA2248 | [CA2248: Enum.HasFlag için doğru sabit listesi bağımsız değişkenini belirtin](../code-quality/ca2248.md) | Yöntem çağrısına bir bağımsız değişken olarak geçirilen sabit listesi türü, `HasFlag` çağıran enum türünden farklı. |
| CA2249 | [CA2249: String.IndexOf yerine String.Contains kullanmayı düşünün](../code-quality/ca2249.md) | Bir alt `string.IndexOf` dizenin varlığını/yokluğunu denetlemek için sonucun kullanıldığı yere yapılan çağrılar ile değiştirilebilir `string.Contains` . |
| CA2300 | [CA2300: Güvenli olmayan seri durumdan çıkarıcı BinaryFormatter kullanmayın](../code-quality/ca2300.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2301 | [CA2301: İlk olarak BinaryFormatter.Binder öğesini ayarlamadan önce BinaryFormatter.Deserialize çağırmayın](../code-quality/ca2301.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2302 | [CA2302: BinaryFormatter.Deserialize çağırmadan önce BinaryFormatter.Binder öğesinin ayarlandığından emin olun](../code-quality/ca2302.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2305 | [CA2305: Güvenli olmayan seri kaldırıcı LosFormatter kullanmayın](../code-quality/ca2305.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2310 | [CA2310: Güvenli olmayan seri kaldırıcı NetDataContractSerializer kullanmayın](../code-quality/ca2310.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2311 | [CA2311: İlk olarak NetDataContractSerializer.Binder öğesini ayarlamadan seri durumdan çıkarmayın](../code-quality/ca2311.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2312 | [CA2312: Seri durumdan çıkarmadan önce NetDataContractSerializer.Binder öğesinin ayarlandığından emin olun](../code-quality/ca2312.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2315 | [CA2315: Güvenli olmayan seri kaldırıcı ObjectStateFormatter kullanmayın](../code-quality/ca2315.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2321 | [CA2321: SimpleTypeResolver kullanarak JavaScriptSerializer ile seri durumdan çıkarmayın](../code-quality/ca2321.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2322 | [CA2322: Seri durumdan çıkarmadan önce SimpleTypeResolver ile JavaScriptSerializer’ın başlatılmadığından emin olun](../code-quality/ca2322.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2326 | [CA2326: None dışında bir TypeNameHandling değeri kullanmayın](../code-quality/ca2326.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2327 | [CA2327: Güvenli olmayan JsonSerializerSettings kullanmayın](../code-quality/ca2327.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2328 | [CA2328: JsonSerializerSettings’in güvenli olduğundan emin olun](../code-quality/ca2328.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2329 | [CA2329: Güvenli olmayan bir yapılandırma kullanarak JsonSerializer ile seri durumdan çıkarma işlemi yapmayın](../code-quality/ca2329.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2330 | [CA2330: Seri durumdan çıkarılırken JsonSerializer’ın güvenli bir yapılandırmaya sahip olmasını sağlayın](../code-quality/ca2330.md) | Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır. Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir. |
| CA2350 | [CA2350: DataTable.ReadXml() girişinin güvenilir olduğundan emin olun](ca2350.md) | Bir saldırgan güvenilmeyen bir girişle seri durumdan çıkarılırken <xref:System.Data.DataTable> , bir hizmet reddi saldırısı gerçekleştirmek için kötü amaçlı giriş oluşturabilir. Bilinmeyen uzaktan kod yürütme güvenlik açıkları olabilir. |
| CA2351 | [CA2351: DataSet.ReadXml() girişinin güvenilir olduğundan emin olun](ca2351.md) | Bir saldırgan güvenilmeyen bir girişle seri durumdan çıkarılırken <xref:System.Data.DataSet> , bir hizmet reddi saldırısı gerçekleştirmek için kötü amaçlı giriş oluşturabilir. Bilinmeyen uzaktan kod yürütme güvenlik açıkları olabilir. |
| CA2352 | [CA2352: Seri duruma getirilebilir türdeki güvenli olmayan DataSet veya DataTable, uzaktan yapılan kod yürütme saldırılarına karşı savunmasız olabilir](ca2352.md) | İle işaretlenmiş bir sınıf veya yapı <xref:System.SerializableAttribute> <xref:System.Data.DataSet> , ya da <xref:System.Data.DataTable> alan ya da özellik içerir ve içermez <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: Seri duruma getirilebilir türdeki güvenli olmayan DataSet veya DataTable](ca2353.md) | XML serileştirme özniteliğiyle veya bir veri sözleşmesi özniteliğiyle işaretlenmiş bir sınıf veya yapı, bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> alanı veya özelliği içerir. |
| CA2354 | [CA2354: Seri durumdan çıkarılmış nesne grafındaki güvenli olmayan DataSet veya DataTable, uzaktan yapılan kod yürütme saldırılarına karşı savunmasız olabilir](ca2354.md) | Serileştirilmiş ile seri durumdan çıkarma ve, bulunan <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> türün nesne grafiği bir <xref:System.Data.DataSet> veya içerebilir <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: Seri durumdan çıkarılmış nesne grafındaki güvenli olmayan DataSet veya DataTable](ca2355.md) | Bulunan veya belirtilen türün nesne grafiğinde veya dahil edildiğinde seri durumdan çıkarma <xref:System.Data.DataSet> <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: web serisi kaldırılan nesne grafiğinde güvenli olmayan veri kümesi veya DataTable](ca2356.md) | Veya içeren bir yöntemi <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> , veya başvurusu olabilecek bir parametresine sahiptir <xref:System.Data.DataSet> <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: DataSet.ReadXml() içeren bir otomatik oluşturulmuş sınıfın güvenilmeyen verilerle kullanılmadığından emin olun](ca2361.md) | Bir saldırgan güvenilmeyen bir girişle seri durumdan çıkarılırken <xref:System.Data.DataSet> , bir hizmet reddi saldırısı gerçekleştirmek için kötü amaçlı giriş oluşturabilir. Bilinmeyen uzaktan kod yürütme güvenlik açıkları olabilir. |
| CA2362 | [CA2362: Otomatik oluşturulmuş, seri hale getirilebilir türdeki güvenli olmayan DataSet veya DataTable, uzaktan kod yürütme saldırılarına karşı savunmasız olabilir](ca2362.md) | Güvenilmeyen girdinin ile serisi kaldırılırken <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve serisi kaldırılan nesne grafı bir <xref:System.Data.DataSet> veya içerdiğinde <xref:System.Data.DataTable> , bir saldırgan uzaktan kod yürütme saldırısı gerçekleştirmek için kötü amaçlı bir yük oluşturabilir. |
| CA3001 | [CA3001: SQL ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3001.md) | Güvenilmeyen giriş ve SQL komutlarıyla çalışırken, SQL ekleme saldırılarına karşı en az bir yer vardır. SQL ekleme saldırısı, kötü amaçlı SQL komutları yürütebilir ve uygulamanızın güvenliğini ve bütünlüğünü tehlikeye atabilirler. |
| CA3002 | [CA3002: XSS güvenlik açıkları için inceleme kodu](../code-quality/ca3002.md) | Web isteklerinden güvenilmeyen giriş ile çalışırken, siteler arası komut dosyası (XSS) saldırıları olması gerekir. Bir XSS saldırısı, güvenilmeyen bir girişi ham HTML çıktısına çıkarır ve saldırganın kötü amaçlı betikler yürütmesine veya Web sayfanızda içeriği kötü amaçlı olarak değiştirmesine olanak tanır. |
| CA3003 | [CA3003: Dosya yolu ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3003.md) | Web isteklerinden güvenilmeyen giriş ile çalışırken, dosyalara yollar belirtirken Kullanıcı denetimli girişi kullanmanın en az olması gerekir. |
| CA3004 | [CA3004: Bilgilerin açığa çıkmasıyla ilgili güvenlik açıkları için inceleme kodu](../code-quality/ca3004.md) | Özel durum bilgilerini kapatma, saldırganlar uygulamanızın iç içgörüleri hakkında bilgi verir ve bu da saldırganların açıktan yararlanmaya yönelik diğer güvenlik açıklarını bulmasına yardımcı olabilir. |
| CA3006 | [CA3006: İşlem komutu ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3006.md) | Güvenilmeyen girişle çalışırken, komut ekleme saldırılarına karşı bir sorun yaşının. Bir komut ekleme saldırısı, temel işletim sisteminde kötü amaçlı komutlar yürütebilir ve sunucunuzun güvenliğini ve bütünlüğünü tehlikeye atabilirler. |
| CA3007 | [CA3007: Açık yeniden yönlendirme güvenlik açıkları için inceleme kodu](../code-quality/ca3007.md) | Güvenilmeyen girişle çalışırken, açık yeniden yönlendirme güvenlik açıklarına karşı bir sorun yaşının. Saldırgan, meşru bir URL 'nin görünümüne izin vermek için Web sitesini kullanmak üzere açık bir yeniden yönlendirme güvenlik açığıyla yararlanabilir, ancak şüphelenmeyecek bir ziyaretçi kimlik avına veya başka bir kötü amaçlı Web sayfasına yönlendirebilir. |
| CA3008 | [CA3008: XPath ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3008.md) | Güvenilmeyen girişle çalışırken, XPath ekleme saldırılarına karşı en az bir yer vardır. Güvenilmeyen giriş kullanarak XPath sorguları oluşturmak, bir saldırganın istenmeyen bir sonuç döndürmek için sorguyu kötü amaçlı olarak işlemesini ve sorgulanan XML 'in içeriğini açığa çıkarmasına izin verebilir. |
| CA3009 | [CA3009: XML ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3009.md) | Güvenilmeyen girişle çalışırken, XML ekleme saldırıları olması gerekir. |
| CA3010 | [CA3010: XAML ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3010.md) | Güvenilmeyen girişle çalışırken, XAML ekleme saldırılarına karşı daha az olun. XAML doğrudan nesne örneğini oluşturma ve yürütmeyi temsil eden bir biçimlendirme dilidir. Bu, XAML 'de oluşturulan öğelerin sistem kaynaklarıyla etkileşime girebileceği anlamına gelir (örneğin, ağ erişimi ve dosya sistemi GÇ). |
| CA3011 | [CA3011: DLL ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3011.md) | Güvenilmeyen girişle çalışırken güvenilmeyen kodun yüklenmesi gerekir. Web uygulamanız güvenilmeyen kod yüklerse, bir saldırgan işlem için kötü amaçlı dll 'Leri ekleyebilir ve kötü amaçlı kod yürütebilir. |
| CA3012 | [CA3012: Normal ifade ekleme güvenlik açıkları için inceleme kodu](../code-quality/ca3012.md) | Güvenilmeyen girişle çalışırken, en az sayıda Regex ekleme saldırısı olması gerekir. Saldırgan, normal ifadeyi kötü amaçlı olarak değiştirmek, Regex istenmeden sonuçlarla eşleştirmek için veya Regex aşırı CPU tüketmek için bir hizmet reddi saldırısından kaynaklanan Regex ekleme işlemini kullanabilir. |
| CA3061 | [CA3061: URL ile şema eklemeyin](../code-quality/ca3061.md) | Güvenilir olmayan dış başvurulara neden olabileceğinden Add yönteminin güvensiz aşırı yüklemesini kullanmayın. |
| CA3075 | [CA3075: Güvensiz DTD İşleme](../code-quality/ca3075.md) | Güvenli olmayan DTDProcessing örnekleri veya dış varlık kaynaklarına başvuru kullanırsanız, ayrıştırıcı güvenilmeyen girişi kabul edebilir ve duyarlı bilgileri saldırganlar 'e açıklayabilir. |
| CA3076 | [CA3076: Güvensiz XSLT Betiği Yürütme](../code-quality/ca3076.md) | .NET uygulamalarında Genişletilebilir Stil sayfası dil dönüşümleri (XSLT) çalıştırıyorsanız, işlemci güvenilir bilgileri saldırganlar 'e açığa çıkartabilir ve hizmet reddi ve siteler arası saldırılara maruz kalabilir. |
| CA3077 | [CA3077: API Tasarımı, XML Belgesi ve XML Metin Okuyucusunda Güvensiz İşleme](../code-quality/ca3077.md) | XMLDocument ve XMLTextReader 'dan türetilmiş bir API tasarlarken, DtdProcessing ' ın en az olması gerekir. Dış varlık kaynaklarının başvurulması veya çözümlenmesi veya XML 'deki güvenli olmayan değerlerin ayarlanması sırasında güvenli olmayan DTDProcessing örnekleri kullanmak bilgilerin açığa çıkmasına neden olabilir. |
| CA3147 | [CA3147: ValidateAntiForgeryToken ile fiil işleyicilerini işaretleme](../code-quality/ca3147.md) | Bir ASP.NET MVC denetleyicisi tasarlarken, siteler arası istek sahteciliği saldırılarına karşı daha fazla saldırı yapın. Siteler arası istek sahteciliği saldırısı, kimliği doğrulanmış bir kullanıcıdan ASP.NET MVC denetleyicinize kötü amaçlı istekler gönderebilir. |
| CA5350 | [CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5350.md) | Zayıf şifreleme algoritmaları ve karma işlevleri bugün çok sayıda nedenden dolayı kullanılır, ancak korudukları verilerin gizliliğini veya bütünlüğünü sağlamak için kullanılmamalıdır. Bu kural, koddaki TripleDES, SHA1 veya RIPEMD160 algoritmaları bulduğunda tetikler.|
| CA5351 | [CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5351.md) | Bozuk şifreleme algoritmaları güvenli olarak kabul edilmez ve kullanımları kesinlikle önerilmez. Bu kural, MD5 karma algoritmasını veya koddaki DES veya RC2 şifreleme algoritmalarından birini bulduğunda tetikler. |
| CA5358 | [CA5358: Güvenli Olmayan Şifreleme Modlarını Kullanmayın](../code-quality/ca5358.md) | Güvenli Olmayan Şifreleme Modlarını Kullanmayın |
| CA5359 | [CA5359 sertifika doğrulamayı devre dışı bırakma](../code-quality/ca5359.md) | Bir sertifika, sunucunun kimliğini doğrulamaya yardımcı olabilir. İsteklerin hedeflenen sunucuya gönderilmesini sağlamak için istemciler sunucu sertifikasını doğrulamalıdır. ServerCertificateValidationCallback her zaman döndürüyorsa `true` , tüm sertifikalar doğrulamayı geçer. |
| CA5360 | [CA5360, seri durumdan çıkarma sırasında tehlikeli yöntemleri çağırmayın](../code-quality/ca5360.md) | Güvenli olmayan seri kaldırma, güvenilir olmayan veriler bir uygulamanın mantığını kötüye kullanma, bir hizmet reddi (DoS) saldırısı veya hatta seri hale getirilmesi sırasında rastgele kod yürütme için kullanıldığında oluşan bir güvenlik açığıdır. Kötü amaçlı kullanıcıların, denetimi altında olan güvenilmeyen verileri seri durumdan çıkarılırken, bu, bu kaldırma özelliklerini kötüye kullanma olasılığı vardır. Özel olarak, seri durumdan çıkarma sürecinde tehlikeli Yöntemler çağırın. Güvenli olmayan güvenli seri kaldırma saldırıları, bir saldırganın DoS saldırıları, kimlik doğrulaması atlanır ve uzaktan kod yürütme gibi saldırıları çalıştırmasına izin verebilir. |
| CA5361 | [CA5361: Güçlü şifrelemenin Schannel kullanımını devre dışı bırakma](../code-quality/ca5361.md) | `Switch.System.Net.DontEnableSchUseStrongCrypto` `true` Giden Aktarım katmanı GÜVENLIĞI (TLS) bağlantılarında kullanılan şifrelemeyi zayıf olacak şekilde ayarlama. Daha zayıf şifreleme, uygulamanız ve sunucu arasındaki iletişimin gizliliğini tehlikeye atabilir ve saldırganlar hassas verileri daha fazla dinlemesine olanak sağlar. |
| CA5362 | [CA5362 olası başvuru döngüsünü seri durumdan çıkarılan nesne grafiğinde](../code-quality/ca5362.md) | Güvenilmeyen verilerin serisini kaldırıyorsa, serisi kaldırılan nesne grafiğinin herhangi bir kodu, sınırsız döngülere geçmeden başvuru döngülerini işlemeye ihtiyaç duyuyor. Bu, seri durumdan çıkarma geri çağrısının parçası olan kodu ve serisini kaldırma tamamlandıktan sonra nesne grafiğini işleyen kodu içerir. Aksi takdirde, bir saldırgan başvuru döngüsünü içeren kötü amaçlı verilerle bir hizmet reddi saldırısı gerçekleştirebilir. |
| CA5363 | [CA5363: İstek doğrulamayı devre dışı bırakmayın](../code-quality/ca5363.md) | İstek doğrulaması, HTTP isteklerini inceleyen ve siteler arası komut dosyası oluşturma da dahil olmak üzere ekleme saldırılarına yol açabilecek potansiyel olarak tehlikeli içerik içerip içermediğini belirleyen bir ASP.NET özelliğidir. |
| CA5364 | [CA5364: Kullanım Dışı Güvenlik Protokollerini Kullanmayın](../code-quality/ca5364.md) | Aktarım Katmanı Güvenliği (TLS), genellikle Köprü Metni Aktarım Protokolü güvenli (HTTPS) ile bilgisayarlar arasındaki iletişimin güvenliğini sağlar. TLS 'nin eski protokol sürümleri TLS 1,2 ve TLS 1,3 ' den daha az güvenlidir ve yeni güvenlik açıklarına sahip olma olasılığı yüksektir. Riski en aza indirmek için eski protokol sürümlerinden kaçının. |
| CA5365 | [CA5365 HTTP üst bilgisi denetimini devre dışı bırakma](../code-quality/ca5365.md) | HTTP üst bilgi denetimi, yanıt üstbilgilerinde bulunan satır başı ve yeni satır karakterlerinin, \r ve \n kodlamasının kodlanmasını sunar. Bu kodlama, üst bilgi tarafından içerilen güvenilmeyen verileri yansıtan bir uygulamadan yararlanan ekleme saldırılarına engel olmaya yardımcı olabilir. |
| CA5366 | [CA5366 veri kümesi okuma XML 'ı Için XmlReader kullanın](../code-quality/ca5366.md) | <xref:System.Data.DataSet>Güvenilmeyen VERILERLE XML okumak için bir kullanmak, <xref:System.Xml.XmlReader> Güvenli Çözümleyici Ile veya DTD işlemesi devre dışı olarak kullanılarak kısıtlanması gereken tehlikeli dış başvurular yükleyebilir. |
| CA5367 | [CA5367 Işaretçi alanları Ile türleri Serileştirmeyin](../code-quality/ca5367.md) | Bu kural, bir işaretçi alanı veya özelliği olan serileştirilebilir bir sınıf olup olmadığını denetler. Seri hale getirilemeyen Üyeler statik üyeler veya ile işaretlenmiş alanlar gibi bir işaretçi olabilir <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 bir sayfadan türetilmiş sınıflar Için ViewStateUserKey ayarla](../code-quality/ca5368.md) | Özelliği ayarlamak, <xref:System.Web.UI.Page.ViewStateUserKey> saldırganların bir saldırı oluşturmak için değişkeni kullanabilmesi adına, bireysel kullanıcılar için Görünüm durumu değişkenine bir tanımlayıcı atamanıza izin vererek uygulamanızdaki saldırıları önlemenize yardımcı olabilir. Aksi takdirde, siteler arası istek sahteciliği için güvenlik açıkları olacaktır. |
| CA5369 | [CA5369: Seri durumdan çıkarma için XmlReader kullanma](../code-quality/ca5369.md) | Güvenilmeyen DTD ve XML şemalarını işlemek, güvenli bir çözümleyici ile veya DTD ile XML satır içi şema işlemesi devre dışı bırakılmış bir XmlReader kullanılarak kısıtlanması gereken tehlikeli dış başvuruların yüklenmesini sağlayabilir. |
| CA5370 | [CA5370: Okuyucuyu doğrulamak için XmlReader kullanma](../code-quality/ca5370.md) | Güvenilmeyen DTD ve XML şemalarını işlemek, tehlikeli dış başvuruların yüklenmesini etkinleştirebilir. Bu tehlikeli yükleme, güvenli çözümleyici veya DTD ile XML satır içi şema işlemesi devre dışı bırakılmış bir XmlReader kullanılarak kısıtlanabilir. |
| CA5371 | [CA5371: Şema okuma için XmlReader kullanma](../code-quality/ca5371.md) | Güvenilmeyen DTD ve XML şemalarını işlemek, tehlikeli dış başvuruların yüklenmesini etkinleştirebilir. Bir XmlReader 'yi güvenli çözümleyici ile veya DTD ile XML satır içi şema işlemeyle kullanma devre dışı bırakılırsa bunu kısıtlar. |
| CA5372 | [CA5372: XPathDocument için XmlReader kullanma](../code-quality/ca5372.md) | Güvenilmeyen verilerden XML işleme, güvenli çözümleyici ile veya DTD işlemesi devre dışı bırakılmış bir XmlReader kullanılarak kısıtlanabilir. |
| CA5373 | [CA5373: Eski anahtar türetme işlevini kullanmayın](../code-quality/ca5373.md) | Bu kural, zayıf anahtar türetme yöntemlerinin ve ' nin çağrılmasını algılar <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> Zayıf algoritma PBKDF1 kullandı. |
| CA5374 | [CA5374 XslTransform kullanma](../code-quality/ca5374.md) | Bu kural <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> kodda örneği oluşturulmuş olup olmadığını denetler. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> artık kullanılmıyor ve kullanılmamalıdır. |
| CA5375 | [CA5375 hesap paylaşılan erişim imzasını kullanma](../code-quality/ca5375.md) | Hesap SAS, bir hizmet SAS 'si ile izin verilmeyen blob kapsayıcıları, tablolar, kuyruklar ve dosya paylaşımları üzerinde okuma, yazma ve silme işlemlerine erişim yetkisi verebilir. Ancak kapsayıcı düzeyindeki ilkeleri desteklemez ve verilen izinler üzerinde daha az esneklik ve denetim sağlar. Kötü amaçlı kullanıcılar bu uygulamayı aldıktan sonra, depolama hesabınızın güvenliği tehlikeye alınacaktır. |
| CA5376 | [CA5376 SharedAccessProtocol HttpsOnly kullanın](../code-quality/ca5376.md) | SAS, HTTP üzerinde düz metin olarak aktarılamaz gizli veriler. |
| CA5377 | [CA5377 kapsayıcı düzeyinde erişim ilkesi kullan](../code-quality/ca5377.md) | Kapsayıcı düzeyinde erişim ilkesi herhangi bir zamanda değiştirilebilir veya iptal edilebilir. Verilen izinler üzerinde daha fazla esneklik ve denetim sağlar. |
| CA5378 | [CA5378: ServicePointManagerSecurityProtocols'u Devre Dışı Bırakma](../code-quality/ca5378.md) | `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` `true` Windows Communication Framework 'ÜN (WCF) aktarım katmanı GÜVENLIĞI (TLS) bağlantılarını TLS 1,0 ile sınırlayan şekilde ayarlama. Bu TLS sürümü kullanım dışı olacaktır. |
| CA5379 | [CA5379 zayıf anahtar türetme işlevi algoritması kullanma](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>Sınıfı, algoritmayı kullanmak için varsayılan değer <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> . Ya da daha yüksek bir oluşturucunun bazı yüklerini kullanmak için karma algoritmasını belirtmeniz gerekir <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . , <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> Özelliği yalnızca bir `get` erişimciye sahiptir ve `overriden` değiştiriciye sahip değildir. |
| CA5380 | [CA5380: Kök depoya sertifika eklemeyin](../code-quality/ca5380.md) | Bu kural, güvenilen kök sertifika yetkilileri sertifika deposuna bir sertifika ekleyen kodu algılar. Varsayılan olarak, güvenilen kök sertifika yetkilileri sertifika deposu, Microsoft kök sertifika programı gereksinimlerini karşılayan bir dizi genel CA ile yapılandırılır. |
| CA5381 | [CA5381: Sertifikaların kök depoya eklenmemiş olduğundan emin olun](../code-quality/ca5381.md) | Bu kural, güvenilen kök sertifika yetkilileri sertifika deposuna potansiyel olarak bir sertifika ekleyen kodu algılar. Varsayılan olarak, güvenilen kök sertifika yetkilileri sertifika deposu, Microsoft kök sertifika programı gereksinimlerini karşılayan bir dizi ortak sertifika yetkilisi (CA) ile yapılandırılır. |
| CA5382 | [CA5382 ASP.NET Core güvenli tanımlama bilgileri kullan](../code-quality/ca5382.md) | HTTPS üzerinden kullanılabilir uygulamalar, tarayıcıda tanımlama bilgisinin yalnızca Güvenli Yuva Katmanı (SSL) kullanılarak iletilmesi gerektiğini belirten güvenli tanımlama bilgileri kullanmalıdır. |
| CA5383 | [CA5383 ASP.NET Core güvenli tanımlama bilgileri kullanmayı sağlama](../code-quality/ca5383.md) | HTTPS üzerinden kullanılabilir uygulamalar, tarayıcıda tanımlama bilgisinin yalnızca Güvenli Yuva Katmanı (SSL) kullanılarak iletilmesi gerektiğini belirten güvenli tanımlama bilgileri kullanmalıdır. |
| CA5384 | [CA5384 dijital imza algoritması (DSA) kullanma](../code-quality/ca5384.md) | DSA, zayıf bir asimetrik şifreleme algoritmasıdır. |
| CA5385 | [CA5385, yeterli anahtar boyutuna sahip Rivest – Shamir – Adtaman (RSA) algoritmasını kullan](../code-quality/ca5385.md) | 2048 bitten daha küçük bir RSA anahtarı, deneme yanılma saldırılarına karşı daha savunmasız olur. |
| CA5386 | [CA5386: SecurityProtocolType değerini sabit kodlamaktan kaçının](../code-quality/ca5386.md) | Aktarım Katmanı Güvenliği (TLS), genellikle Köprü Metni Aktarım Protokolü güvenli (HTTPS) ile bilgisayarlar arasındaki iletişimin güvenliğini sağlar. Protokol sürümleri TLS 1,0 ve TLS 1,1 kullanım dışıdır, ancak TLS 1,2 ve TLS 1,3 geçerli bir özelliktir. Daha sonra, TLS 1,2 ve TLS 1,3 kullanım dışı bırakılmış olabilir. Uygulamanızın güvenli kalmasını sağlamak için, bir protokol sürümünü ve en az .NET Framework v 4.7.1 hedefini kullanmaktan kaçının. |
| CA5387 | [CA5387 yetersiz yineleme sayısıyla zayıf anahtar türetme işlevi kullanmıyor](../code-quality/ca5387.md) | Bu kural, bir şifreleme anahtarının tarafından <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 100.000 'den daha az bir yineleme sayısıyla oluşturulup oluşturulmadığını denetler. Daha yüksek bir yineleme sayısı, oluşturulan şifreleme anahtarını tahmin etmeye çalışan sözlük saldırılarına karşı hafifletmek için yardımcı olabilir. |
| CA5388 | [CA5388 zayıf anahtar türetme işlevi kullanırken yeterli yineleme sayısı sağlayın](../code-quality/ca5388.md) | Bu kural, tarafından <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 100.000 ' den küçük olabilecek bir yineleme sayısıyla bir şifreleme anahtarının oluşturulup oluşturulmadığını denetler. Daha yüksek bir yineleme sayısı, oluşturulan şifreleme anahtarını tahmin etmeye çalışan sözlük saldırılarına karşı hafifletmek için yardımcı olabilir. |
| CA5389 | [CA5389: Hedef dosya sistemi yoluna arşiv öğesinin yolunu eklemeyin](../code-quality/ca5389.md) | Dosya yolu göreli olabilir ve dosya sistemi erişimine beklenen dosya sistemi hedef yolu dışında, kötü amaçlı yapılandırma değişikliklerine ve düzenleme ve bekleme tekniği aracılığıyla uzaktan kod yürütmeye yol açabilir. |
| CA5390 | [CA5390 sabit kod şifreleme anahtarı](../code-quality/ca5390.md) | Simetrik algoritmanın başarılı olması için, gizli anahtar yalnızca gönderici ve alıcı için bilinmelidir. Anahtar sabit kodluysa kolayca keşfedilir. Derlenmiş ikili dosyalar da dahil olmak üzere kötü amaçlı kullanıcıların bunu çıkartmasına çok kolay. Özel anahtar tehlikeden sonra şifre metninin şifresi doğrudan çözülür ve artık korunmaz. |
| CA5391 | [CA5391 ASP.NET Core MVC denetleyicilerindeki antiforgery belirteçlerini kullanma](../code-quality/ca5391.md) | Bir `POST` `PUT` `PATCH` `DELETE` antiforgery belirtecini doğrulamadan bir,, veya isteği işlemek, siteler arası istek sahteciliği saldırılarına karşı savunmasız olabilir. Siteler arası istek sahteciliği saldırısı, kimliği doğrulanmış bir kullanıcıdan ASP.NET Core MVC denetleyicinize kötü amaçlı istekler gönderebilir. |
| CA5392 | [CA5392 P/Invoke için Defaultdllımportsearchpaths özniteliğini kullanın](../code-quality/ca5392.md) | Varsayılan olarak, yoklama kullanan P/Invoke işlevleri <xref:System.Runtime.InteropServices.DllImportAttribute> , kitaplığa yüklenecek geçerli çalışma dizini de dahil olmak üzere bir dizi dizin sağlar. Bu, belirli uygulamalar için bir güvenlik sorunu olabilir ve bu, DLL ele geçirme için önde gelen. |
| CA5393 | [CA5393, güvenli olmayan bir Dllı-SearchPath değeri kullanmaz](../code-quality/ca5393.md) | Varsayılan DLL arama dizinleri ve derleme dizinlerinde kötü amaçlı bir DLL olabilir. Uygulamanızın nerede çalıştırıldığına bağlı olarak, uygulamanın dizininde kötü amaçlı bir DLL olabilir. |
| CA5394 | [CA5394, güvenli olmayan rasgelelik kullanma](../code-quality/ca5394.md) | Şifreli olarak zayıf sözde rastgele sayı oluşturucusunun kullanılması, bir saldırganın hangi güvenlik duyarlı değerin oluşturulacağını önlemelerine izin verebilir. |
| CA5395 | [Eylem yöntemleri için CA5395 Isabetsiz HttpVerb özniteliği](../code-quality/ca5395.md) | Verileri oluşturan, düzenleme, silme ya da başka bir şekilde değiştiren tüm eylem yöntemlerinin, siteler arası istek sahteciliği saldırılarına karşı antiforgery özniteliğiyle korunması gerekir. GET işleminin gerçekleştirilmesi, yan etkileri olmayan ve kalıcı verilerinizi değiştirmeyen bir güvenli işlem olmalıdır. |
| CA5396 | [HttpCookie için CA5396 set HttpOnly true olarak ayarlandı](../code-quality/ca5396.md) | Derinlemesine bir savunma ölçüsünde güvenlik duyarlı HTTP tanımlama bilgilerinin HttpOnly olarak işaretlendiğinden emin olun. Bu, Web tarayıcılarının betiklerin tanımlama bilgilerine erişmesine izin vermemelidir. Eklenen kötü amaçlı betikler, tanımlama bilgilerini çalmaya yönelik yaygın bir yoldur. |
| CA5397 | [CA5397: Kullanım dışı SslProtocols değerlerini kullanmayın](../code-quality/ca5397.md) | Aktarım Katmanı Güvenliği (TLS), genellikle Köprü Metni Aktarım Protokolü güvenli (HTTPS) ile bilgisayarlar arasındaki iletişimin güvenliğini sağlar. TLS 'nin eski protokol sürümleri TLS 1,2 ve TLS 1,3 ' den daha az güvenlidir ve yeni güvenlik açıklarına sahip olma olasılığı yüksektir. Riski en aza indirmek için eski protokol sürümlerinden kaçının. |
| CA5398 | [CA5398: Sabit kodlanmış SslProtocols değerlerini kullanmaktan kaçının](../code-quality/ca5398.md) | Aktarım Katmanı Güvenliği (TLS), genellikle Köprü Metni Aktarım Protokolü güvenli (HTTPS) ile bilgisayarlar arasındaki iletişimin güvenliğini sağlar. Protokol sürümleri TLS 1,0 ve TLS 1,1 kullanım dışıdır, ancak TLS 1,2 ve TLS 1,3 geçerli bir özelliktir. Daha sonra, TLS 1,2 ve TLS 1,3 kullanım dışı bırakılmış olabilir. Uygulamanızın güvenli kalmasını sağlamak için bir protokol sürümünü kodlamadan kaçının. |
| CA5399 | [CA5399 kesinlikle HttpClient sertifika iptal listesi denetimini devre dışı bırak](../code-quality/ca5399.md) | İptal edilen bir sertifika artık güvenilir değil. Saldırganlar, bazı kötü amaçlı verileri geçirerek veya HTTPS iletişiminden hassas verileri çalmaya yönelik olarak kullanılabilir. |
| CA5400 | [CA5400 HttpClient sertifika iptal listesi denetiminin devre dışı olmadığından emin olun](../code-quality/ca5400.md) | İptal edilen bir sertifika artık güvenilir değil. Saldırganlar, bazı kötü amaçlı verileri geçirerek veya HTTPS iletişiminden hassas verileri çalmaya yönelik olarak kullanılabilir. |
| CA5401 | [CA5401 varsayılan olmayan IV ile CreateEncryptor kullanma](../code-quality/ca5401.md) | Simetrik şifrelemenin sözlük saldırılarını engellemek için her zaman yinelenebilir olmayan bir başlatma vektörü kullanması gerekir. |
| CA5402 | [CA5402 varsayılan IV ile CreateEncryptor kullanın](../code-quality/ca5402.md) | Simetrik şifrelemenin sözlük saldırılarını engellemek için her zaman yinelenebilir olmayan bir başlatma vektörü kullanması gerekir. |
| CA5403 | [CA5403: Sertifikayı sabit olarak kodlamayın](../code-quality/ca5403.md) | `data` `rawData` <xref:System.Security.Cryptography.X509Certificates.X509Certificate> Veya oluşturucusunun veya parametresi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sabit kodlanmış. |
| IL3000 | [IL3000 tek bir dosya olarak yayımlarken derleme dosya yoluna erişmeyi önleyin](../code-quality/il3000.md) | Tek bir dosya olarak yayımlarken derleme dosya yoluna erişim kullanmaktan kaçının |
| IL3001 | [IL3001 tek dosya olarak yayımlarken derleme dosya yoluna erişmeyi önleyin](../code-quality/il3001.md) | Tek dosya olarak yayımlarken derleme dosya yoluna erişmemeye özen gösterin |
