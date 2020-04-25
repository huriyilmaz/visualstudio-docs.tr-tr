---
title: CheckId Tarafından Yönetilen Kod için Kod Analizi Uyarıları
ms.date: 04/18/2019
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1200
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1508
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
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
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d4f532baf1434ea318a86ce2cb2fc717fff98623
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82153017"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>CheckId tarafından yönetilen kod için kod analizi uyarıları

Aşağıdaki tablo uyarının CheckId tanımlayıcısı tarafından yönetilen kodu için Kod Çözümleyicisi uyarılarını listeler.

| CheckId | Uyarı | Açıklama |
|---------| - | - |
| CA2007 | [CA2007: bir görevi doğrudan bekleme](ca2007.md) | Zaman uyumsuz bir [awaits](/dotnet/csharp/language-reference/keywords/await) Yöntem <xref:System.Threading.Tasks.Task> doğrudan bekler. Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task> doğrudan bekler, görevi oluşturan aynı iş parçacığında devamlılık oluşur. Bu davranış, performans açısından maliyetli olabilir ve Kullanıcı arabirimi iş parçacığında kilitlenmeye neden olabilir. Devamlılığını <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> sağlamak için çağırmayı düşünün. |
| CA1000 | [CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000.md) | Genel türün statik üyesi çağrıldığında tür bağımsız değişkeni tür için belirlenmelidir. Destek çıkarımı desteklenmeyen genel örnek üyesi çağrıldığında tür bağımsız değişkeni üye için belirlenmelidir. Bu iki durumda tür bağımsız değişkenini belirleyen sözdizimi farklıdır ve kolaylıkla karıştırılır. |
| CA1001 | [CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır](../code-quality/ca1001.md) | Bir sınıf System.IDisposable tipi örnek alanını derler ve uygular ve sınıf IDisposable'ı uygulamaz. IDisposable alanını derleyen sınıf, yönetilmeyen kaynağı dolaylı yoldan sahiplenir ve IDisposable arayüzünü uygulamalıdır. |
| CA1002 | [CA1002: Genel listeleri gösterme](../code-quality/ca1002.md) | System. Collections. Generic. List< (/ \<(T>) >), devralma değil, performans için tasarlanan genel bir koleksiyondur. Bu nedenle, Liste herhangi bir sanal üyeyi içermiyor. Bunun yerine devralma için tasarlanmış genel koleksiyonlar maruz kalmalıdır. |
| CA1003 | [CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003.md) |Bir tür, imzası iki parametre (ilk bir nesne ve ikinci olarak EventArgs 'a atanabilen bir tür) içeren void döndüren bir temsilci içerir ve kapsayan derleme Microsoft .NET Framework 2,0 ' i hedefler. |
| CA1004 | [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004.md) | Tip argümanının açıkça özelleştirilmesi yerine yöntemi geçen argüman tipiyle tanımlanan genel yöntemin nasıl tip argümanı olduğunun sonucudur. Çıkarımı etkinleştirmek için bir genel yöntem parametre imzası yöntem türü parametresi gibi aynı türde bir parametre içermelidir. Bu durumda, tip bağımsız değişkeninin belirtilmesine gerek yoktur. Tüm tip parametreleri için çıkarım kullanılırken, genel ve genel olmayan örnek yöntemleri için sözdüzümü benzerdir; bu genel yöntemlerin kullanımını kolaylaştırır. |
| CA1005 | [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005.md) | Daha çok tip parametresi, genel tip içerir, bilmek daha zordur ve hangi tip parametrelerinin temsil ettiğini anımsamak zordur. Genellikle, liste\<T> gibi tek bir tür parametresiyle ve sözlük\<TKey, TValue> olarak iki tür parametresi olan belirli durumlarda belirgin olur. Ancak, iki parametreden fazla parametre varsa, birçok kullanıcı için zorluk derecesi artar. |
| CA1006 | [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006.md) | Bir yuvalanmış bağımsız değişken aynı zamanda genel tip olan bir tip bağımsız değişkendir. Yuvalanmış tip bağımsız değişkeni içeren imzası olan bir üye çağırmak için, kullanıcı bir genel tipi örneklemeli ve bu tipi ikinci bir genel tipin yapıcısına geçirmelidir. Gerekli yordam ve sözdizimi karmaşıktır ve kaçınılmalıdır. |
| CA1007 |[CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007.md) | System.Object türünde bir başvuru parametresi dışarıdan görünen bir yöntem içerir. Bir genel yöntem kullanımı başvuru parametresi türünü ilk tür olarak atmadan yönteme aktarılan kısıtlamalar için tüm türleri ve konuları etkinleştirir. |
| CA1008 | [CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır](../code-quality/ca1008.md) | Tıpkı diğer türler gibi, başlatılmamış bir numaralandırmanın varsayılan değeri sıfırdır. İşaretlenmemiş bir geçerli numaralandırma, varsayılan değerin geçerli bir numaralandırma değeri olması için değeri sıfır olan bir üye tanımlaması gerekir. Numaralandırma FlagsAttribute özniteliği sıfır değerli üyeyi tanımlarsa, onun adı numaralandırmada hiçbir değerin ayarlanmadığı "Hiçbiri" olmalıdır. |
| CA1009 | [CA1009: Olay işleyicilerini doğru bildirin](../code-quality/ca1009.md) | Olay işleyicisi yöntemleri iki parametre alır. İlk System.Object türündedir ve "gönderen" olarak adlandırılır. Bu olayda oluşan nesnedir. İkinci parametre System.EventArgs türüdür ve "e" olarak adlandırılır. Bu olay ile ilişkilendirilmiş olan verilerdir. Olay işleyici yöntemlerine bir değer döndürmemelidir; C# programlama diliyle, dönüş türü boşluk tarafından belirtilir. |
| CA1010 | [CA1010: Koleksiyonlar genel arabirim uygulamalıdır](../code-quality/ca1010.md) | Bir koleksiyon kullanılabilirliğini genişletmek için genel koleksiyon arabirimlerinden birini uygulayın. Daha sonra koleksiyon genel koleksiyon türlerini doldurmak için kullanılabilir. |
| CA1011 |[CA1011: Temel türleri parametre olarak geçirmeyi düşünün](../code-quality/ca1011.md) | Temel tür yöntem bildiriminde parametre olarak belirtildiğinde temel türünden türetilen herhangi bir tür yöntemine karşılık gelen bağımsız değişken olarak geçirilebilir. Türetilmiş parametre türü tarafından sağlanan ek işlevler gerekmiyorsa, temel tür kullanımı yöntemi daha geniş kullanımını etkinleştirir. |
| CA1012 | [CA1012: Soyut türlerde oluşturucular bulunmamalıdır](../code-quality/ca1012.md) | Soyut türler üzerindeki kurucular yalnızca türetilen türler tarafından çağrılabilir. Ortak yapıcılar türün bir örneğini yaptığından ve siz bir soyut türün örneğini yapamayacağınızdan, soyut sınıf hatalı biçimde dizayn edilmiş ortak yapıcıya sahip olur. |
| CA1013 | [CA1013: Eşittir işlecini ekleme ve çıkarmayı aşırı yükleyerek aşırı yükleyin](../code-quality/ca1013.md) | Bir genel ya da korumalı tür eşitlik imlecini uygulamadan ekleme ya da çıkarma işleçlerini uygular. |
| CA1014 | [CA1014: Derlemeleri CLSCompliantAttribute ile işaretleyin](../code-quality/ca1014.md) | Ortak Dil Tanımlaması (CLS) ad kısıtlamalarını, veri türlerini ve karşıt programlama dillerini kullanırsa derlemelerin uyması zorunlu olan kuralları tanımlar. İyi tasarım, tüm derlemelerin kullanılarak <xref:System.CLSCompliantAttribute> açıkça CLS uyumluluğunu belirtmelerini belirler. Bu öznitelik bir derlemede yoksa, montaj uyumlu değildir. |
| CA1016 | [CA1016: Derlemeleri AssemblyVersionAttribute ile işaretleyin](../code-quality/ca1016.md) | .NET, bir derlemeyi benzersiz olarak tanımlamak ve kesin adlandırılmış derlemelerdeki türlere bağlamak için sürüm numarasını kullanır. Sürüm numarası, sürüm ve yayımcı ilkesi ile birlikte kullanılır. Varsayılan olarak uygulamalar yalnızca oluşturulmuş derleme sürümlerini çalıştırır. |
| CA1017 | [CA1017: Derlemeleri ComVisibleAttribute ile işaretleme](../code-quality/ca1017.md) |ComVisibleAttribute COM müşterilerinin yönetilen koda nasıl erişeceğini tanımlar. İyi tasarım derlemelerin açıkça COM görünürlüğünde gösterildiğini belirler. COM görünürlüğü tüm derleme için ayarlanabilir ve sonra bireysel tür ve tür üyeleri için geçersiz kılınabilir. Bu öznitelik yoksa, derleme içeriği COM istemcileri tarafından görülebilir. |
| CA1018 | [CA1018: Öznitelikleri AttributeUsageAttribute ile işaretleyin](../code-quality/ca1018.md) | Özel öznitelik tanımladığınızda, AttributeUsageAttribute kullanarak özel öznitelik kaynak kodunun nerede uygulanabilir olduğunu göstermek için işaretleyin. Bir özniteliğin anlamı ve amaçlanan kullanımı, kodun içinde onun varolan konumunu tanımlar. |
| CA1019 | [CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın](../code-quality/ca1019.md) | Öznitelikler özniteliği işaretlediğinizde özelleştirilen zorunlu bağımsız değişkenleri tanımlayabilir. Ayrıca bunlar konum parametreleri olarak öznitelik yapıcısına verildiğinden duruma bağlı bağımsız değişkenler olarak da bilinirler. Zorunlu her bağımsız değişken için bağımsız değişkenin değeri yürütme zamanından alınması gerektiğinden öznitelik ilgili salt okunur özelliği de sağlamalıdır. Öznitelikler adlandırılmış bağımsız değişkenler olarak bilinen duruma bağlı bağımsız değişkenler olarak da tanımlanabilir. Bu bağımsız öznitelik oluşturucular ad tarafından sağlanır ve karşılık gelen bir okuma/yazma özelliğine sahip olmalıdır. |
| CA1020 | [CA1020: Birkaç türü olan ad alanlarından kaçının](../code-quality/ca1020.md) | Her bir ad alanının kendi mantıksal düzenlemesi vardır ve seyrek doldurulmuş bir ad alanına türleri koymak için geçerli bir nedeni olduğundan emin olun. |
| CA1021 | [CA1021: Out parametrelerinden kaçının](../code-quality/ca1021.md) | Başvuruya ( out veya ref kullanarak ) göre türleri geçirmek işaretçi deneyimi gerektirir, değer türü ve referans türü arasındaki farkı ve işleme yöntemi ile birden çok değer döndürmeyi anlamak gerekir. Ayrıca, out ve ref parametreleri arasındaki fark açıkça anlaşılmadı. |
| CA1023 | [CA1023: Dizin oluşturucular çok boyutlu olmamalıdır](../code-quality/ca1023.md) | Dizin oluşturucular (dizinlenmiş özellikleri) tek bir dizin kullanmalı. Çok boyutlu dizin oluşturucular kitaplığın kullanılabilirliğini önemli ölçüde azaltabilir. |
| CA1024 | [CA1024: Uygun yerlerde özellikler kullan](../code-quality/ca1024.md) | Ortak veya korumalı yöntem "Get" ile başlar, herhangi bir parametre almaz ve dizi olmayan bir değer döndüren adı vardır. Yöntem, özellik olmak için çok iyi bir aday olabilir. |
| CA1025 | [CA1025: Tekrarlanan bağımsız değişkenleri params dizisi ile değiştirin](../code-quality/ca1025.md) | Parametre dizisini bağımsız değişkenin gerçek sayısı bilinmediğinde ve bağımsız değişkenler aynı türde olduğunda ya da aynı tür olarak geçirilebileceğinde bağımsız değişkenleri tekrarlamak için kullanın. |
| CA1026 | [CA1026: Varsayılan parametreler kullanılmamalıdır](../code-quality/ca1026.md) | Varsayılan parametreleri kullanma yöntemleri CLS altında izin verilir; ancak, CLS derleyicileri bu parametreler için atanmış değerleri gözardı etmeye olanak sağlar. Programlama dilleri arasında istediğiniz davranışı korumak için varsayılan parametreleri kullanan yöntemler varsayılan parametreleri sağlayan tekrar yüklenen yöntem tarafından değiştirilmelidir. |
| CA1027 |[CA1027: Numaralandırmaları FlagsAttribute ile işaretle](../code-quality/ca1027.md) | Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Anlamsız olarak birleştirildiğinde numaralandırmaya FlagsAttribute özelliğini uygulayın. |
| CA1028 | [CA1028: Numaralandırma depolaması Int32 olmalıdır](../code-quality/ca1028.md) | Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Varsayılan olarak, System.Int32 veri türü sabit değerleri depolamak için kullanılır. Bu temel türünü değiştirebilirsiniz, ancak bu önerilen bir senaryo değildir. |
| CA1030 | [CA1030: Uygun yerlerde olaylar kullanın](../code-quality/ca1030.md) |Bu kural, normalde olaylar için kullanılan adlara sahip yöntemleri algılar. Yanıt olarak açıkça tanımlanmış bir durum değişikliği yöntemi çağrılırsa, olay işleyicisi tarafından yöntemin çağrılması gerekir. Yöntemi direkt olarak çağırmak yerine olayları yükselterek çağıran nesneler. |
| CA1031 | [CA1031: Genel özel durum türlerini yakalamayın](../code-quality/ca1031.md) | Genel özel durum yakalanmamalı. Daha özel istisnaları yakalayın ya da yakalama bloğundaki son durum olarak genel istisnaları yeniden fırlatın. |
| CA1032 |[CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032.md) | Yapıcıların tüm ayarlamasını sağlamaktaki başarısızlık, istisnalarla başa çıkmayı zorlaştırabilir. |
| CA1033 | [CA1033: Arabirim yöntemleri alt türler tarafından çağırılabilir olmalıdır](../code-quality/ca1033.md) | Ağzı açık dışarıdan görünen bir tür açık yöntem uygulaması ortak bir arabirim sağlar ve aynı ada sahip alternatif dışarıdan görünen bir yöntem sağlamaz. |
| CA1034 | [CA1034: İç içe türler görünebilir olmamalıdır](../code-quality/ca1034.md) | İç içe türü başka bir kapsamda bildirilen bir türdür. İç içe geçmiş türler, özel uygulama ayrıntılarını kapsayan türdeki kapsül oluşturma için kullanışlıdır. Bu amaçla kullanılan, iç içe türün dışarıdan görünür olmaması gerekir. |
| CA1035 | [CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035.md) | Bu kural ICollection uygulamalarına türü kesin belirlenmiş üyeler sağlamak için gereklidir, böylece kullanıcıların arabirim tarafından sağlanan işlevselliği kullandığı zaman, bağımsız değişkenleri Nesne türüne atamaları gerekli değildir. Bu kural, Nesneden daha güçlü tür örnekleri topluluğunu yöneteceğinden türün ICollection uyguladığını varsayar. |
| CA1036 | [CA1036: Karşılaştırılabilir türlerde geçersiz kılma yöntemleri](../code-quality/ca1036.md) |Ortak veya korumalı tür System.IComparable arabirimini uygular. Object.Equals ne etkisiz kılınabilir ne de eşitlik için olan özel dil işleciyle aşırı yüklenebilir, eşitsizlik durumu olabilir, daha küçülebilir ya da büyüyebilir. |
| CA1038 | [CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038.md) | Bu kural, kullanıcı arabirimi tarafından sağlanan işlevselliği kullandığınızda güçlü tür için dönen değer atama yapmak için gerekli değildir, ayrıca süregelen özelliğinin türü kesin belirlenmiş bir sürümünü sağlamak için IEnumerator uygulamaları gereklidir. |
| CA1039 | [CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039.md) | Bu kural türü kesin belirlenmiş üyeler sağlamak için IList uygulamaları gerektirir böylece kullanıcıların arabirim tarafından sağlanan işlevselliği kullandığı zaman, bağımsız değişkenleri System.Object türüne atamaları gerekli değildir. |
| CA1040 |[CA1040: Boş arabirimlerden kaçının](../code-quality/ca1040.md) | Arayüzler bir davranış veya kullanım sözleşmesi sağlayan üyeleri tanımlar. Arabirim tarafından tanımlanan fonksiyonellik herhangi bir tür tarafından türün kalıtım hiyerarşisinde nerede belirdiği önemsenmeksizin devralınabilir. Tür arabirimin üyeleri için uygulamaları sağlayarak bir arayüz uygular. Boş bir arabirim herhangi bir üye tanımlamıyor; bu nedenle, uygulanabilir bir sözleşme tanımlamaz. |
| CA1041 | [CA1041: ObsoleteAttribute iletisi sağlayın](../code-quality/ca1041.md) | Tür veya üye belirtilen kendi ObsoleteAttribute.Message özelliğine sahip olmayan bir System.ObsoleteAttribute özniteliği kullanılarak işaretlendi. Özniteliğin ileti özelliği, türü veya ObsoleteAttribute kullanılarak işaretlenmiş tür veya üye derlendiğinde görüntülenir. Bu eski türü veya üye kullanıcı bilgilerini sağlar. |
| CA1043 | [CA1043: Dizin oluşturucular için tamsayı veya dize bağımsız değişkeni kullanın](../code-quality/ca1043.md) | Dizinle oluşturucular (dizinlenmiş özellikleri) dizin için integral veya dize türleri kullanılmalıdır. Bu türler, genellikle veri yapılarını dizinleme için kullanılır ve bunlar kitaplığın kullanılabilirliğini artırır. Nesne türünün kullanılması için belirli bir integral veya dize türü tasarım zamanında burada tarif edilemez, bu gibi durumlarda sınırlı tutulmalıdır. |
| CA1044 | [CA1044: Özellikler salt yazılır olmamalıdır](../code-quality/ca1044.md) | Salt okunur özelliğe sahip olmasına karşın kabul edilebilir ve genellikle gereklidir, tasarıma ilişkin yönergeler salt yazılır özellik kullanılmasını engeller. Bir kullanıcı değeri ayarlar ve sonra kullanıcı bu değeri görüntülemeyi engellerse bunun için herhangi bir güvenlik yoktur. Ayrıca, okuma erişimi olmadan, yararsız olduklarını sınırlayan paylaşılan nesnelerin durumu görüntülenemez. |
| CA1045 |[CA1045: Türleri başvuruya göre geçirmeyin](../code-quality/ca1045.md) | Başvuruya ( out veya ref kullanarak ) göre türleri geçirmek işaretçi deneyimi gerektirir, değer türü ve referans türü arasındaki farkı ve işleme yöntemi ile birden çok değer döndürmeyi anlamak gerekir. Genel bir hedef kitle için tasarlayan kitaplık mimarları, kullanıcıların, veya `out` `ref` parametreleriyle birlikte çalışmasını beklememelidir. |
| CA1046 | [CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin](../code-quality/ca1046.md) | Başvuru türleri için, varsayılan eşitlik işleci neredeyse her zaman doğrudur. Varsayılan olarak, yalnızca aynı nesneye gelirseniz iki başvuru eşit olur. |
| CA1047 |[CA1047: Korumalı türlerde korunan üyeleri bildirmeyin](../code-quality/ca1047.md) | Türler, devralmasına erişebileceğiniz veya üyeyi geçersiz kılmak için korunan üyelerin türlerini bildirir. Tanım gereği, mühürlenmiş türler devralınamaz yani mühürlenmiş türler üzerindeki korunan yöntemler çağrılamaz. |
| CA1048 | [CA1048: Korumalı türlerde sanal üyeleri bildirme](../code-quality/ca1048.md) | Türler yöntemi sanal olarak bildirir, böylece devralan türler sanal yöntemin uygulanmasını geçersiz kılabilir. Tanım gereği, mühürlenmiş bir tür devralınamaz. Bu, sanal yöntemi mühürlenmiş bir türde anlamsız hale getirir. |
| CA1049 | [CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır](../code-quality/ca1049.md) | Yönetilmeyen kaynakların tahsis türlerini arayanların isteğine bağlı kaynakları serbest bırakmak ve kaynakları tutan nesnelerin yaşam sürelerini kısaltmak için etkinleştirmek üzere IDisposable gerçekleştirmelisiniz. |
| CA1050 | [CA1050: Ad alanlarında türleri bildirin](../code-quality/ca1050.md) | Türlerin ad çakışmalarını önlemek için ad alanlarını ve ilgili türü bir nesne sıradüzeni içinde düzenlemeniz için yöntem olarak bildirilir. |
| CA1051 | [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051.md) | Bir alanın birincil kullanım alanının uygulama ayrıntısı olması gerekir. Alanların özel veya iç olması gerekir ve özelliklerini kullanmaya maruz kalması gerekir. |
| CA1052 | [CA1052: Statik tutucu türleri mühürlenmelidir](../code-quality/ca1052.md) | Ortak veya korumalı tür yalnızca statik üyeleri içerir ve mühürlenmiş (C# Reference) (NotInheritable) değiştirici kullanarak bildirilmez. Devralınmayacak anlamına gelen tür mühürleme değiştirici kullanılarak basit tür gibi kullanılmak için işaretlenmelidir. |
| CA1053 |[CA1053: Statik tutucu türlerinde oluşturucular bulunmamalıdır](../code-quality/ca1053.md) | Ortak veya iç içe geçmiş ortak tür yalnızca statik üyeleri bildirir ve ortak veya korumalı varsayılan bir oluşturucu vardır. Statik üyeleri çağırma bir tür örneği gerektirmediğinden kurucu gereksizdir. Dize aşırı yüklemesi, emniyet ve güvenlik için dize bağımsız değişkeni kullanılarak tekdüzen kaynak tanımlayıcısı (URI) çağırmalıdır. |
| CA1054 | [CA1054: URI parametreleri dizeler olmamalıdır](../code-quality/ca1054.md) | Bir yöntem URI'yı sunan bir dizeyi alırsa, bu hizmetleri sağlayan güvenli şekilde URI sınıfının bir örneğini alır, karşılık gelen aşırı olmalıdır. |
| CA1055 | [CA1055: URI dönüş değerleri dizeler olmamalıdır](../code-quality/ca1055.md) | Bu kural, yöntemin URI döndürdüğünü varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. System.Uri sınıfı bu hizmetleri güvenli bir şekilde sağlar. |
| CA1056 | [CA1056: URI özellikleri dizeler olmamalıdır](../code-quality/ca1056.md) | Bu kural, özelliğin Tekdüzen Kaynak Tanımlayıcısı (URI) tarafından temsil edildiğini varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. System.Uri sınıfı bu hizmetleri güvenli bir şekilde sağlar. |
| CA1057 | [CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır](../code-quality/ca1057.md) | Bir tür sadece System.Uri parametresi ile dize parametresinin değiştirilmesiyle yöntem aşırı yüklemesini bildirir. Aşırı yüklemeler URI parametresiyle aşırı yüklenmiş olan dize parametresini alır. |
| CA1058 | [CA1058: Türler belli temel türleri genişletmemelidir](../code-quality/ca1058.md) | Dışarıdan görünen tür belirli temel türleri genişletir. Diğer seçenekleri kullanın. |
| CA1059 |[CA1059: Üyeler belli somut türleri göstermemelidir](../code-quality/ca1059.md) | Somut tür tam bir uygulamaya sahiptir ve bu nedenle oluşturulabilecek bir türdür. Üye yaygın kullanımını etkinleştirmek için önerilen arabirimi kullanarak somut türünü değiştirin. |
| CA1060 | [CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın](../code-quality/ca1060.md) | System. Runtime. InteropServices. DllImportAttribute özniteliği kullanılarak işaretlenenler veya ' de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Declare anahtar sözcüğü kullanılarak tanımlanan Yöntemler gibi platform çağırma yöntemleri, yönetilmeyen koda erişim. Bu yöntemler, NativeMethods, SafeNativeMethods veya UnsafeNativeMethods sınıfının üyesi olmalıdır. |
| CA1061 |[CA1061: Taban sınıf yöntemlerini gizlemeyin](../code-quality/ca1061.md) | Basit türdeki bir yöntem türetilmiş türdeki adlandırılmış yöntem tarafından gizlenmiştir, türetilmiş yöntemin parametre imzası yalnızca türetilmiş türleri ve karşılık gelen temel yöntemin parametre imzası daha zayıf türlerine göre farklı olduğunda temel türde bir yöntemin türetilmiş türle aynı adlı yöntem olarak gizlidir. |
| CA1062 | [CA1062: Genel yöntemlerin bağımsız değişkenlerini doğrulayın](../code-quality/ca1062.md) | Dışarıdan görünen yöntemlerin null'a karşı denetlenmesi için geçirilen tüm başvuru bağımsız değişkenleri. |
| CA1063 | [CA1063: IDisposable'ı doğru uygulayın](../code-quality/ca1063.md) | Tüm IDisposable türleri Dispose kalıbını doğru uygulamalıdır. |
| CA1064 | [CA1064: Özel durumlar genel olmamalıdır](../code-quality/ca1064.md) | Bir iç özel durum yalnızca kendi iç kapsamı içinde görülebilir. İç kapsam dışında kalan özel durumlardan sonra, sadece basit istisnalar istisna yakalamak için kullanılabilir. İç özel durum, <xref:System.Exception> <xref:System.SystemException>veya <xref:System.ApplicationException>öğesinden devralınmışsa, dış kod özel durumla ne yapılacağını belirlemek için yeterli bilgiye sahip olmayacaktır. |
| CA1065 | [CA1065: Beklenmedik konumlarda özel durumlar tetiklemeyin](../code-quality/ca1065.md) | İstisna atılmasını beklemeyen yöntem bir istisna atar. |
| CA1066 | [CA1066: IEquatable 'yi geçersiz kıldığınızda Uygula](../code-quality/ca1066.md) | Değer türü yöntemi geçersiz <xref:System.Object.Equals%2A> kılar, ancak uygulamaz <xref:System.IEquatable%601>. |
| CA1067 | [CA1067: IEquatable uygularken Equals geçersiz kıl](../code-quality/ca1067.md) | Bir tür uygular <xref:System.IEquatable%601>, ancak metodunu geçersiz kılmaz <xref:System.Object.Equals%2A> . |
| CA1068 | [CA1068: CancellationToken parametreleri en son gelmelidir](../code-quality/ca1068.md) | Bir yöntem, son parametre olmayan CancellationToken parametresine sahiptir. |
| CA1200 | [CA1200: ön ek ile cref etiketlerini kullanmaktan kaçının](../code-quality/ca1200.md) | XML belgesi etiketindeki [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. Derleyicinin başvuruları `cref` doğrulamasını önlediği için ön ekleri olan etiketleri kullanmaktan kaçının. Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler. |
| CA1300 | [CA1300: MessageBoxOptions belirtin](../code-quality/ca1300.md) | Doğru olarak sağdan sola okuma düzeni kullanan kültürler için bir ileti kutusu görüntülemek için Show yöntemi MessageBoxOptions numaralandırma RightAlign ve RtlReading üyeleri geçirilmelidir. |
| CA1301 | [CA1301: Yinelenen hızlandırıcılardan kaçının](../code-quality/ca1301.md) | Giriş anahtarı, bir hızlandırıcı olarak da bilinir, ALT anahtarını kullanarak klavye giriş denetimini sağlar. Birden çok denetim yinelenen erişim anahtarlarına sahip olduğunda, erişim anahtarının davranışı iyi tanımlı değildir. |
| CA1302 | [CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin](../code-quality/ca1302.md) | System.Environment.SpecialFolder numaralandırma özel sistem klasörlerine başvuran üyeleri içerir. Bu klasörlerin konumları farklı işletim sistemleri üzerinde farklı değerlere sahip olabilir; kullanıcı konumları değiştirebilir ve konumlar yerelleştirilmiştir. Environment.GetFolderPath yöntemi yerelleştirilmiş ve o anda çalışan bilgisayara uygun Environment.SpecialFolder numaralandırma ile ilişkili olan konumları döndürür. |
| CA1303 | [CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303.md) | Dışarıdan görülebilen bir yöntem, bir dize sabit değerini bir .NET oluşturucusuna veya yöntemine parametre olarak geçirir ve bu dize yerelleştirilebilir olmalıdır. |
| CA1304 | [CA1304: CultureInfo belirtin](../code-quality/ca1304.md) | Yöntem veya Oluşturucu System.Globalization.CultureInfo parametre kabul eden aşırı yüklenmiş üye arar ve yöntem veya oluşturucu CultureInfo parametresi aşırı yükleme çağıramaz. Bir CultureInfo veya System.IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir. |
| CA1305 | [CA1305: IFormatProvider belirtme](../code-quality/ca1305.md) | Yöntem veya oluşturucu System.IFormatProvider parametresini kabul eden aşırı yüklü bir veya daha fazla üye arar ve yöntem veya oluşturucu IFormatProvider parametre yüklemesini çağırmaz. Bir System.Globalization.CultureInfo veya IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir. |
| CA1306 | [CA1306: Veri türleri için yerel ayarları ayarlayın](../code-quality/ca1306.md) | Yerel ayarlar, veri için kültür-özel sunum öğelerini, örneğin para birimi sembolleri, sayısal değerler için biçimleri ve sıralama düzeni için kullanılan biçimlendirme gibi değerleri belirler. Bir DataTable veya DataSet oluşturduğunuzda, yerel ayarı açık olarak ayarlamanız gerekir. |
| CA1307 | [CA1307: StringComparison belirtin](../code-quality/ca1307.md) | StringComparison parametresi ayarlanmamış bir yöntemi aşırı bir dize karşılaştırma işleminde kullanır. |
| CA1308 |[CA1308: Dizeleri büyük harfe normalleştirin](../code-quality/ca1308.md) | Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu küçük harfe dönüştürüldüğünde gidiş dönüş yapamaz. |
| CA1309 | [CA1309: Sıralı StringComparison kullanın](../code-quality/ca1309.md) | StringComparison parametresini Ordinal ya da OrdinalIgnoreCase'a ayarlayamayan dilbilimsel olmayan dize karşılaştırma işlemi. Açıkça StringComparison.Ordinal veya StringComparison.OrdinalIgnoreCase için parametre ayarıyla kodunuz genellikle hızlanır, daha doğru olur ve daha güvenilir hale gelir. |
| CA1400 | [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400.md) |Ortak veya korumalı yöntem System.Runtime.InteropServices.DllImportAttribute özniteliği kullanılarak işaretlenir. Yönetilmeyen kitaplık bulunamadı ya da yöntem için bir işlev kitaplığında eşleştirilemedi. |
| CA1401 | [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401.md) | Ortak türde ortak veya korumalı bir yöntem System. Runtime. InteropServices. DllImportAttribute özniteliğine sahiptir (Ayrıca, içindeki [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Declare anahtar sözcüğü tarafından uygulanır). Bu tür yöntemler açıkta kalmamalıdır. |
| CA1402 |[CA1402: COM görünebilir arabirimler içinde aşırı yüklemelerden kaçının](../code-quality/ca1402.md) | Aşırı yüklenmiş yöntemler COM istemcilerine maruz kaldığında, sadece ilk yöntem aşırı yüklemesi adını korur. Sonraki aşırı yüklemeler adının sonuna alt çizgi karakteri (_) eklenerek ve aşırı yüklemenin tanımını karşılayacak şekilde bir tam sayı eklenerek benzersiz olarak yeniden adlandırılır. |
| CA1403 | [CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır](../code-quality/ca1403.md) | COM görünebilir bir değer türü, LayoutKind. Auto olarak ayarlanan System. Runtime. InteropServices. StructLayoutAttribute özniteliği kullanılarak işaretlenir. Bu türlerin düzeni .NET sürümleri arasında değişebilir, bu da belirli bir düzeni bekleyen COM istemcilerini keser. |
| CA1404 | [CA1404: P/Invoke sonrasında GetLastError çağrısı yapın](../code-quality/ca1404.md) | Marshal. GetLastWin32Error yöntemine veya denk [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError işlevine bir çağrı yapılır ve hemen önceki çağrı bir işletim sistemi çağırma yöntemine değildir. |
| CA1405 | [CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır](../code-quality/ca1405.md) | COM görünür türü, görünmeyen bir COM türünden türer. |
| CA1406 |[CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının](../code-quality/ca1406.md) | Visual Basic 6 COM istemcisi 64-bit tamsayıya erişemez. |
| CA1407 |[CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407.md) | COM statik yöntemleri desteklemez. |
| CA1408 | [CA1408: AutoDual ClassInterfaceType kullanma](../code-quality/ca1408.md) | Çift arabirim kullanan türler, belirli bir arabirim düzenine bağlanmak için istemcileri etkinleştirir. Gelecek sürümdeki değişiklikler, türün düzeni veya bazı temel türler, arayüze bağlanan COM istemcilerini kesintiye uğratır. Varsayılan olarak, ClassInterfaceAttribute özniteliği belirtilmezse, salt dağıtılan arabirim kullanılır. |
| CA1409 | [CA1409: Com görünebilir türler oluşturulabilmelidir](../code-quality/ca1409.md) |Özellikle COM görünür olarak işaretlenmiş bir başvuru türü, parametreli ortak kurucu içeriyorsa ancak genel varsayılan (parametresiz) bir oluşturucuya sahip değildir. Genel varsayılan oluşturucu olmadan tür COM istemcileri tarafından oluşturulmamalıdır. |
| CA1410 | [CA1410: COM kayıt yöntemleri eşleşmelidir](../code-quality/ca1410.md) | System.Runtime.InteropServices.ComRegisterFunctionAttribute özniteliğini kullanarak işaretlenmiş yöntem bir tür bildirir ancak System.Runtime.InteropServices.ComUnregisterFunctionAttribute özniteliğini kullanarak veya tersi durumda işaretlenmiş bir yöntemi bildirmez. |
| CA1411 | [CA1411: COM kayıt yöntemleri görünebilir olmamalıdır](../code-quality/ca1411.md) | System.Runtime.InteropServices.ComRegisterFunctionAttribute özniteliğini veya System.Runtime.InteropServices.ComUnregisterFunctionAttribute özniteliğini kullanarak işaretlenmiş bir yöntemi dışarıdan görülebilir. |
| CA1412 | [CA1412: ComSource Arabirimlerini IDispatch olarak işaretleyin](../code-quality/ca1412.md) | System.Runtime.InteropServices.ComSourceInterfacesAttribute özniteliğini kullanarak işaretlenen bir tür ve belirtilen arabirimlerden birini ayarlamak için ComInterfaceType.InterfaceIsIDispatch özniteliğine System.Runtime.InteropServices.InterfaceTypeAttribute özniteliğini kullanarak ayarlanır. |
| CA1413 | [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413.md) | COM-görünür değer türlerinin ortak olmayan örnek alanları COM istemcilerine görünürdür. Maruz kalmaması gereken, istenmeyen bir tasarım ya da güvenlik etkileri olan bilgi alanındaki içeriği gözden geçirin. |
| CA1414 | [CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile Işaretleyin](../code-quality/ca1414.md) | Boolean veri türünün, yönetimsiz kod içinde birden fazla sunumu vardır. |
| CA1415 | [CA1415: P/Invoke doğru olarak bildir](../code-quality/ca1415.md) | Bu kural, ÇAKıŞAN bir yapı parametresine işaretçi olan işlevleri hedefleyen [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] ve karşılık gelen yönetilen parametrenin bir System. Threading. nativeörtüşen yapısına yönelik bir işaretçi olmayan işletim sistemi çağırma yöntemi bildirimlerini arar. |
| CA1500 | [CA1500: Değişken adları alan adlarıyla eşleşmemelidir](../code-quality/ca1500.md) | Bir örnek yöntemi, hatalara liderlik eden derlenen türdeki örnek alanı içinde adları uyuşan bir parametre yada yerel değişken tanımlar. |
| CA1501 | [CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501.md) | Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. |
| CA1502 | [CA1502: Aşırı karmaşıklıktan kaçının](../code-quality/ca1502.md) | Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer. |
| CA1504 | [CA1504: Yanlış alan adlarını gözden geçirin](../code-quality/ca1504.md) | Bir örnek alanının adı "s_" ile başlar veya statik (Visual Basic ile paylaşılan) alanının adı "m_" ile başlar. |
| CA1505 | [CA1505: Bakımı yapılamayan kodlardan kaçının](../code-quality/ca1505.md) | Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir. |
| CA1506 | [CA1506: Aşırı sınıf bağlantısından kaçının](../code-quality/ca1506.md) | Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer. |
| CA1507 | [CA1507: dize yerine NameOf kullanın](../code-quality/ca1507.md) | Bir dize sabit değeri, bir `nameof` ifadenin kullanılabileceği bir bağımsız değişken olarak kullanılır. |
| CA1508 | [CA1508: ölü olmayan koşullu koddan kaçının](../code-quality/ca1508.md) | Bir yöntemde, her zaman çalışma zamanında olarak `true` `false` değerlendirilen koşullu kod bulunur. Bu, koşulun `false` dalındaki ölü koda yol açar. |
| CA1600 | [CA1600: Boş işlem önceliğini kullanmayın](../code-quality/ca1600.md) | İşlem önceliğini Boşta olarak ayarlamayın. Aksi durumda boş olacak ve bu nedenle beklemeyi engeller, System.Diagnostics.ProcessPriorityClass.Idle bulunan işlemleri CPU dolduracaktır. |
| CA1601 | [CA1601: Güç durumu değişikliklerini önleyen zamanlayıcılar kullanmayın](../code-quality/ca1601.md) | Yüksek frekanslı dönemsel faaliyet CPU'yu meşgul tutar ve sabit diski gösteren güç tasarruflu zamanlayıcılarla müdahale edilir. |
| CA1700 | [CA1700: Numaralandırma değerlerini 'Ayrılmış' olarak adlandırmayın](../code-quality/ca1700.md) | Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır. |
| CA1701 | [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md) | Kaynak dizedeki her sözcüğün büyük/küçük harf kurralarına dayanan belirteçler içinde bölünür. Her bir bitişik ikili-işaret kombinasyonu Microsoft yazım kitaplığı tarafından denetlenir. Tanınırsa, kelime kural ihlali üretir. |
| CA1702 | [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md) | Tanımlayıcının adı birden çok sözcük içerir ve bu sözcüklerden en az biri büyük harf kullanımı hatasına maruz kalmış birleşik kelime olarak görülür. |
| CA1703 | [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703.md) | Kaynak dizesi, Microsoft Yazım kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir. |
| CA1704 | [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md) | Dışarıdan görünen bir tanımlayıcı ad Microsoft yazım denetimi kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir. |
| CA1707 | [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707.md) | Kural gereği, tanımlayıcı adlar alt çizgi (_) karakterini içermez. Bu kural ad alanlarını, türleri, üyeleri ve parametreleri denetler. |
| CA1708 | [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708.md) | Ortak dil çalışma zamanı hedef dilleri büyük/küçük harf duyarlı olması gerekmediğinden ad alanları, türler, üyeler ve parametreler için tanımlayıcılar yalnızca büyük/küçük harfe göre farklılık göstermeyebilir. |
| CA1709 | [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709.md) | Kural gereği, parametre adları camel casing ve ad, tür ve üye adları Pascal casing kullanır. |
| CA1710 | [CA1710: Tanımlayıcıların sonekleri doğru olmalıdır](../code-quality/ca1710.md) |Kural gereği, belli uzatılan türlerin adları ya da belli arayüzlerin uygulanması, ya da bu türlerden türetilen, basit tür veya arayüzden oluşturulan son eke sahiptir. |
| CA1711 | [CA1711: Tanımlayıcıların sonekleri yanlış olmamalıdır](../code-quality/ca1711.md) | Kural gereği, yalnızca, belirli temel türleri genişleten veya bazı arabirimleri ya da bu türlerinden türetilmiş türleri uygulayan tür adları belirli ayrılmış öneklerle bitmelidir. Diğer tür adları aşağıdaki ayrılmış sonekleri kullanmamalı. |
| CA1712 | [CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712.md) | Numaralandırma üyelerinin adları, tür adı kullanılarak öneklenmemiştir, çünkü geliştirici araçlarının tür bilgisini sağlaması beklenmez. |
| CA1713 | [CA1713: Olaylarda önce veya sonra önek olmamalıdır](../code-quality/ca1713.md) | Olay adı "Önce" veya "Sonra" ile başlar. Belirli bir sırayla ilgili olayları adlandırmak için şimdiki veya geçmiş zamanı göreceli konumun sıralı eylemlerini belirtmek için kullanın. |
| CA1714 | [CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır](../code-quality/ca1714.md) | Ortak bir numaralandırma System.FlagsAttribute özniteliğine sahiptir ve adı "s" ile bitmez. Bileşik FlagsAttribute kullanarak işaretlenen öznitelik birden fazla değer belirtilebilir, çünkü çoğul adları vardır. |
| CA1715 | [CA1715: Tanımlayıcıların önekleri doğru olmalıdır](../code-quality/ca1715.md) | Dışarıdan görünen bir arabirimin adı büyük "I" ile başlamıyor. Genel tür parametresi dışarıdan görünen tür veya yöntem adı büyük "T" ile başlamıyor. |
| CA1716 | [CA1716: Tanımlayıcılar anahtar sözcüklerle eşleşmemelidir](../code-quality/ca1716.md) | Ad alanı adı veya tür adı ayrılmış anahtar sözcük bir programlama dili ile eşleşir. Tanımlayıcı adı ve türleri için ortak dil çalışma zamanı, hedef diller tarafından tanımlanan anahtar sözcüklerle aynı değildir. |
| CA1717 | [CA1717: Yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır](../code-quality/ca1717.md) | Adlandırma kuralları numaralandırma için adlandırma aynı anda birden fazla numaralandırma değeri olduğunu gösterir. |
| CA1719 | [CA1719: Parametre adları üye adlarıyla eşleşmemelidir](../code-quality/ca1719.md) | Parametre adı parametrenin anlamıyla iletişim kurmalı ve üyenin adını üye anlamıyla iliştirmelidir. Bunların aynı olduğu yerlerde nadir bir tasarım olur. Aynı üye adıyla parametreyi adlandırma sezgisel değildir ve kütüphane kullanımını zorlaştırır. |
| CA1720 |[CA1720: Tanımlayıcılar tür adları içermemelidir](../code-quality/ca1720.md) | Parametre adı dışarıdan görünen üye, veri türü adını içerir ya da açıkça görünen üyenin adı dil özellikli veri türü adı içerir. |
| CA1721 | [CA1721: Tür adları alma metotlarıyla eşleşmemelidir](../code-quality/ca1721.md) |Ortak veya korumalı bir üye adı "Get" ile başlar ve aksi durumda ortak veya korumalı özellik adıyla eşleşir. "Get" yöntemlerinin ve özelliklerinin açıkça işlevlerinden ayırt edilebilen adları olması gerekir. |
| CA1722 | [CA1722: Tanımlayıcıların önekleri yanlış olmamalıdır](../code-quality/ca1722.md) | Kural gereği, programlama öğelerinin belirli bir önek ile başlayan adları vardır. |
| CA1724 | [CA1724: Tür Adları Ad Alanlarıyla Eşleşmemelidir](../code-quality/ca1724.md) | Tür adları .NET ad alanlarının adlarıyla eşleşmemelidir. Bu kuralın ihlali kitaplığın kullanılabilirliğini azaltabilir. |
| CA1725 | [CA1725: Parametre adları taban yöntem ile eşleşmelidir](../code-quality/ca1725.md) | Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir. |
| CA1726 | [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md) | Dışarıdan görünen bir tanımlayıcının adı, tercih edilen terim varolduğunda alternatif olarak bir terim içerir. Alternatif olarak ad, "Bayrak" veya "Bayraklar" terimini içerir. |
| CA1800 | [CA1800: Gereksiz atamalar yapmayın](../code-quality/ca1800.md) | Özellikle yayınlar sıkıştırılmış yineleme deyiminde gerçekleştirildiğinde yinelenen yayınların performansını azaltır. |
| CA1801 | [CA1801: Kullanılmayan parametreleri gözden geçir](../code-quality/ca1801.md) | Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. |
| CA1802 |[CA1802: Uygun Yerlerde Değişmez Değerler Kullanın](../code-quality/ca1802.md) |Bir alan statik ve salt okunur (paylaşılan ve salt okunur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) olarak tanımlanır ve derleme zamanında oluşturulabilir bir değer kullanılarak başlatılır. Hedeflenen alana atanan değer derleme zamanında oluşturulabilir olduğundan, değerin çalışma zamanı yerine derleme zamanında hesaplanabilmesi için bildirimi const (const [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) alanı olarak değiştirin. |
| CA1804 | [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804.md) | Kullanılmayan yerel değişkenler ve gereksiz atamaların derleme boyutunu artırır ve performansı düşürür. |
| CA1806 | [CA1806: Yöntem sonuçlarını yoksaymayın](../code-quality/ca1806.md) | Yeni bir nesne oluşturulur, ancak hiç kullanılmaz veya çağrılan yeni dizeyi oluşturur ve döndürür ve yeni dize hiç kullanılmaz ya da COM veya P/Invoke yöntemi, bir HRESULT ya da hiç kullanılmayan hata kodu döndürür. |
| CA1809 |[CA1809: Aşırı yerel öğelerden kaçın](../code-quality/ca1809.md) | Bir değeri bellek yerine işlemci yazmacında tutmak yaygın bir performans iyileştirmesidir ve buna "değeri kaydetmek denir". Tüm yerel değişkenlerin kaydedilme olasılığını artırmak için yerel değişken sayısını 64 olarak sınırlandırın. |
| CA1810 | [CA1810: Başvuru türü statik alanları satır içi başlatın](../code-quality/ca1810.md) | Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik oluşturucu denetimleri performansı düşürebilir. |
| CA1811 | [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811.md) | Özel ya da iç (derleme düzeyi) üye arayanların derlemede çağırıcısı yoktur; ortak dil çalışma zamanı tarafından çağrılan değildir ve temsilci tarafından çağrılan da değildir. |
| CA1812 | [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812.md) | Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz. |
| CA1813 | [CA1813: Korumasız özniteliklerden kaçının](../code-quality/ca1813.md) | .NET özel özniteliklerin alınması için yöntemler sağlar. Varsayılan olarak, bu yöntemleri öznitelik devralma hiyerarşisinde arar. Öznitelik mühürleme kalıtım hiyerarşisi aracılığıyla aramayı ortadan kaldırır ve performansı artırabilir. |
| CA1814 | [CA1814: Basit dizileri çok boyutlu dizilere tercih edin](../code-quality/ca1814.md) | Basit bir dizi, öğeleri dizi olan bir dizidir. Öğeleri olan diziler bazı veri kümeler için daha az harcanmış önde gelen farklı boyutlarda olabilir. |
| CA1815 | [CA1815: Değer türlerinde eşittir ve işleç eşitliklerinin üzerine yazın](../code-quality/ca1815.md) | Değer türleri için, Equals'ın devralınmış uygulaması Reflection kitaplığını kullanır ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals'ı uygulamalıdır. |
| CA1816 | [CA1816: GC.SuppressFinalize öğesini doğru çağırın](../code-quality/ca1816.md) | Dispose uygulamasının bir yöntemi GC çağrısını yapmaz. SuppressFinalize ya da Dispose çağrılarının uygulanması olmayan bir yöntem GC. SuppressFinalize ya da bir yöntemi GC çağırır. SuppressFinalize ve bu (Visual Basic) dışında bir şey geçirir. |
| CA1819 | [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819.md) | Özellik salt okunur olsa bile özellikleri tarafından döndürülen dizi yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Tipik olarak, kullanıcılar bu tür bir özellik aramanın performans üzerindeki olumsuz etkilerini anlamayacaktır. |
| CA1820 | [CA1820: Dize uzunluğunu kullanarak boş dizeler için sınayın](../code-quality/ca1820.md) | String.Length özelliği veya String.IsNullOrEmpty yöntemi, Equals kullanılmasından önemli ölçüde daha hızlıdır. |
| CA1821 | [CA1821: Boş sonlandırıcıları kaldırın](../code-quality/ca1821.md) | Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Boş sonlandırıcı eklenen yükü çeker ve hiçbir avantaj sunmaz. |
| CA1822 |[CA1822: Üyeleri statik olarak işaretleyin](../code-quality/ca1822.md) | Örnek verilerine erişmeyen Üyeler veya çağrı örnekleri metotları statik (içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]paylaşılan) olarak işaretlenebilir. Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için verebilir. |
| CA1823 | [CA1823: Kullanılmayan özel alanlardan kaçının](../code-quality/ca1823.md) | Derlemede erişimi görülmeyen özel alanlar algılandı. |
| CA1824 |[CA1824: Derlemeleri NeutralResourcesLanguageAttribute ile işaretleme](../code-quality/ca1824.md) | NeutralResourcesLanguage özniteliği, bir derleme için nötr kültürün kaynaklarını göstermek için kullanılan dilin kaynak yöneticisini bilgilendirir. Bu ilk yüklediğiniz kaynak için arama performansını artırır ve çalışma kümenizi azaltabilir. |
| CA1825 |[CA1825: sıfır uzunluklu dizi ayırmaktan kaçının](../code-quality/ca1825.md) | Sıfır uzunluklu bir diziyi başlatmak gereksiz bellek ayırmaya yol açar. Bunun yerine, çağırarak <xref:System.Array.Empty%2A?displayProperty=nameWithType>statik olarak ayrılan boş dizi örneğini kullanın. Bellek ayırma, bu yöntemin tüm etkinleştirmeleri genelinde paylaşılır. |
| CA1900 | [CA1900: Değer tür alanları taşınabilir olmalıdır](../code-quality/ca1900.md) | Bu kural açık düzene bildirilen yapıları kullanarak 64-bit işletim sistemlerinde yönetilmeyen kod sıralandığı zaman doğru olarak hizalamayı denetler. |
| CA1901 | [CA1901: P/Invoke bildirimleri taşınabilir olmalıdır](../code-quality/ca1901.md) | Bu kural her parametresinin boyutu ve P/Invoke dönüş değeri olarak değerlendirilir ve parametrenin boyutu 32-bit ve 64-bit işletim sistemlerinde yönetilmeyen kodun başvuruya doğru olduğunu doğrular. |
| CA1903 | [CA1903: Yalnızca hedeflenen çerçeveden API kullanın](../code-quality/ca1903.md) | Bir üye veya tür, bir üye veya projedeki hedeflenen çerçeve ile birlikte dahil edilmemiş hizmet paketinde tanıtılmış türü kullanır. |
| CA2000 | [CA2000: Kapsamı kaybetmeden önce verileri atın](../code-quality/ca2000.md) | Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır. |
| CA2001 | [CA2001: Sorunlu yöntemleri çağırmaktan kaçının](../code-quality/ca2001.md) | Bir üye olası tehlikeli ya da sorunlu yöntemi çağırır. |
| CA2002 |[CA2002: Zayıf kimliği olan nesneleri kilitlemeyin](../code-quality/ca2002.md) |Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir. |
| CA2003 |[CA2003: Lifleri iş parçacığı olarak görmeyin](../code-quality/ca2003.md) | Yönetilen bir iş parçacığı [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] iş parçacığı olarak kabul ediliyor. |
| CA2004 | [CA2004: GC.KeepAlive'a çağrıları kaldırın](../code-quality/ca2004.md) | SafeHandle kullanımını dönüştürüyorsanız, tüm GC.KeepAlive (nesne) çağrılarını kaldırın. Bu durumda, sınıflar GC.KeepAlive'a çağrı yapmamalıdır. Bu, onların bir sonlandırıcısı olmadığını kabul eder, ancak SafeHandle'ı işletim sistemini sonlandırmasına güvenin. |
| CA2006 | [CA2006: Yerel kaynakları kapsamak için SafeHandle kullanın](../code-quality/ca2006.md) | Yönetilen kod içinde IntPtr kullanmak olası bir güvenlik ve güvenilirlik sorunu belirtebilir. IntPtr'nin tüm kullanımları onun yerine bir SafeHandle ya da benzer bir teknolojinin kullanımının gerekip gerekmediğini belirlemek için gözden geçirilmelidir. |
| CA2100 | [CA2100: SQL sorgularını güvenlik açıkları için gözden geçirin](../code-quality/ca2100.md) | Bir yöntem, yönteme dize değişkeninden oluşturulmuş dize kullanarak System.Data.IDbCommand.CommandText özelliğini ayarlar. Bu kural, dize değişkeninin kullanıcı girişi içerdiğini varsayar. Kullanıcı girişi ile oluşturulan SQL komut dizesi, SQL enjeksiyon saldırılarına karşı savunmasız durumdadır. |
| CA2101 |[CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](../code-quality/ca2101.md) | Bir platform çağırma üyesi kısmen güvenilen arayanlara izin verir, bir dize parametresine sahiptir ve dize açıkça sıralanmaz. Bu, olası bir güvenlik açığına neden olabilir. |
| CA2102 | [CA2102: CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın](../code-quality/ca2102.md) | RuntimeCompabilityAttribute tarafından işaretlenmemiş veya RuntimeCompability (WrapNonExceptionThrows = yanlış) ile işaretlenmiş derlemedeki bir üye, System.Exception işleyen yakalama bloğu içerir ve hemen arkasından gelen genel bir yakalama bloğu içermez. |
| CA2103 | [CA2103: Kesinlik temelli güvenliği gözden geçirin](../code-quality/ca2103.md) |Bir yöntem zorunlu güvenliği kullanır ve durum bilgileri veya dönüş değerlerini kullanarak izin oluşturursa, izin talebi etkin durumdayken değişebilir. Bildirime dayanan güvenliği mümkün olduğunca kullanın. |
| CA2104 |[CA2104: Salt okunur kesilebilir başvuru türleri bildirmeyin](../code-quality/ca2104.md) | Dışarıdan görünen bir tür, kesilebilir başvuru türü olan dışarıdan görünen bir salt okunur alan içerir. Kesilebilir tür, örnek verileri değiştirilebilen bir türdür. |
| CA2105 | [CA2105: Dizi alanları salt okunur olmamalıdır](../code-quality/ca2105.md) |Bir dizi içeren bir alana salt okunur (salt okunur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) değiştiricisini uyguladığınızda, alan farklı bir diziye başvuracak şekilde değiştirilemez. Bir dizinin öğeleri salt okunur bir alanda depolanmış olsa bile değiştirilebilir. |
| CA2106 | [CA2106: Bildirimlerin güvenliğini sağlayın](../code-quality/ca2106.md) | Bir yöntem izin ileri sürer ve güvenlik önlemi olmayan çağrı üzerinde gerçekleşir. Güvenlik denetimleri yapmadan herhangi bir güvenlik izni ileri sürmek, kodunuzdaki güvenlik zayıflıklarını yararlanılabilir bırakır. |
| CA2107 | [CA2107: Gözden geçirmeyi reddedin ve yalnızca kullanımına izin verin](../code-quality/ca2107.md) |Permıtonly yöntemi ve CodeAccessPermission. Deny güvenlik eylemleri yalnızca gelişmiş bir .NET güvenlik bilgisine sahip olanlar tarafından kullanılmalıdır. Bu güvenlik eylemlerini kullanan kod güvenlik incelemesi altından geçmelidir. |
| CA2108 | [CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin](../code-quality/ca2108.md) | Ortak veya korunan değer türü, Veri Erişim veya Bağlantı Talepleri tarafından güvenlik altına alınır. |
| CA2109 | [CA2109: Görünen olay işleyicileri gözden geçirin](../code-quality/ca2109.md) | Ortak veya korunan olay işleme yöntemi algılandı. Olay işleme yöntemleri kesinlikle gerekli olmadığı sürece maruz bırakılmamalıdır. |
| CA2111 |[CA2111: İşaretçiler görünür olmamalıdır](../code-quality/ca2111.md) | İşaretçi özel, içsel veya salt okunur değildir. Kötü amaçlı kod işaretçinin değerini değiştirebilir, potansiyel olarak bellekte rastgele konumlara erişme izni verebilir veya uygulama ya da sistem hatalarına neden olabilir. |
| CA2112 | [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112.md) | Ortak veya korumalı tür, ortak alanları içerir ve Bağlantı Talepleri tarafından güvenlik altına alınır. Bağlantı talebi tarafından güvenli türde bir örnek kod erişimi varsa, kod türün alanlarına erişmek için bağlantı talebine sahip değildir. |
| CA2114 | [CA2114: Yöntem güvenliği türün bir üst kümesi olmalıdır](../code-quality/ca2114.md) | Yöntem, aynı eylem için hem yöntem düzeyine hem de tür düzeyine dayanan güvenliğe sahip olmamalıdır. |
| CA2115 | [CA2115: Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın](../code-quality/ca2115.md) | Bu kural, yönetimsiz kod içinde kullanıldığı sırada yönetilmeyen kaynağın sonlandırılması nedeniyle oluşabilecek hataları algılar. |
| CA2116 | [CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır](../code-quality/ca2116.md) |APTCA (AllowPartiallyTrustedCallersAttribute) özniteliği tam olarak güvenilen bir derlemede yapılandırıldığında ve derleme, kodu kısmen güvenilmeyen çağrıcılara izin vermeyen başka bir derlemede çalıştırdığında, güvenlik yararlanması mümkündür. |
| CA2117 | [CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir](../code-quality/ca2117.md) | APTCA (AllowPartiallyTrustedCallers) özniteliği, tam olarak güvenilen bir derleme üzerinde temsil edildiğinde ve derlemedeki tür, kısmen güvenilmeyen bir çağırıcıya izin vermeyen tür tarafından devralındığında, güvenlik yararlanması mümkündür. |
| CA2118 | [CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçir](../code-quality/ca2118.md) |SuppressUnmanagedCodeSecurityAttribute, varsayılan davranışı COM birlikte çalışma veya işletim sistemi davranışını kullanan yönetilmeyen kodu çalıştıran üyeler için değiştirir. Bu öznitelik, öncelikle performansı artırmak için kullanılır; ancak, gelen performans artışı önemli güvenlik riskleri ile birlikte gelir. |
| CA2119 | [CA2119: Özel arabirimleri karşılayan yöntemleri mühürleyin](../code-quality/ca2119.md) | Devralınabilir bir ortak tür, bir iç (arkadaş [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) arabirimin geçersiz kılınabilir bir yöntem uygulamasını sağlar. Bu kuralın ihlalini düzeltmek için yöntemin, derlemenin dışından geçersiz kılınmasını önleyin. |
| CA2120 | [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120.md) | Bu türün, System.Runtime.Serialization.SerializationInfo nesnesi ve System.Runtime.Serialization.StreamingContext nesnesi (seri hale getiren yapıcı imzası) alan bir oluşturucusu vardır. Bu oluşturucu, güvenlik denetimi tarafından güvenli değildir; ancak türdeki en az bir normal oluşturucu güvenlidir. |
| CA2121 | [CA2121: Statik oluşturucular özel olmalıdır](../code-quality/ca2121.md) | Sistem, türünün ilk örneğinin oluşturulmasından önce statik oluşturucuyu çağırır veya herhangi bir statik üyeye başvurur. Statik oluşturucu özel değilse, sistem dışındaki kod tarafından çağrılabilir. Oluşturucu içinde gerçekleştirilen işlemlere bağlı olarak bu, beklenmeyen davranışlara neden olabilir. |
| CA2122 | [CA2122: Bağlantı talepleri olan yöntemleri dolaylı olarak açığa çıkarmayın](../code-quality/ca2122.md) | Ortak veya korumalı bir üye, Bağlantı Taleplerine sahiptir ve herhangi bir güvenlik denetimi gerçekleştirmeyen üye tarafından çağrılır. Bağlantı talebi, yalnızca o anki çağırıcı izinlerini denetler. |
| CA2123 | [CA2123: Geçersiz kılan bağlantı talepleri taban ile özdeş olmalıdır](../code-quality/ca2123.md) | Bu kural, arabirim ya da başka bir türdeki sanal yöntem olan temel yöntem ile başka bir yöntemi eşleştirir ve sonra her bir bağlantı talebini inceler. Bu kural ihlal edilirse kötü niyetli arayan, sadece güvensiz bir yöntem çağırarak bağlantı isteğini atlayabilir. |
| CA2124 | [CA2124: Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın](../code-quality/ca2124.md) | Ortak veya korumalı bir yöntem try/finally bloğunu içerir. Finally bloğu, güvenlik durumunu sıfırlamak için görünür ve finally bloğuna dahil değildir. |
| CA2126 | [CA2126: Tür bağlantı talepleri devralma taleplerini gerektirir](../code-quality/ca2126.md) | Ortak sonuçlandırılmamış bir tür, bağlantı isteği ile korunmalıdır ve geçersiz kılınabilir bir yöntemi vardır. Ne tür, ne de yöntem miras talebi kullanılarak korunmaktadır. |
| CA2130 | [CA2130: Güvenlik kritik sabitleri saydam olmalıdır](../code-quality/ca2130.md) | Saydamlık zorlaması, sabit değerler için zorlanmaz çünkü derleyiciler sabit değerleri satır içi hale getirir bu nedenle arama, çalışma zamanında gerekli değildir. Sabit alanlar saydam güvenlikli olmalıdır; böylece kodu gözden geçirenler saydam kodun sabitlere erişemediğini varsaymaz. |
| CA2131 | [CA2131: Güvenlik kritik türleri tür eşdeğerliğine katılamaz](../code-quality/ca2131.md) | Bir tür, türün eşdeğerliğine ve türün kendisine veya üyeye veya türün alanına katılır, SecurityCriticalAttribute özniteliği kullanılarak işaretlenir. Bu kural, herhangi kritik türler veya kritik yöntemleri içeren türler veya tür eşdeğerliğine katılan alanlar tetiklendiğinde olur. CLR böyle bir türü algıladığında, çalışma zamanında TypeLoadException ile yüklemek başarısız olur. Genellikle, bu kural yalnızca kullanıcılar içinde el ile veya türü eşdeğerlik tlbimp ve derleyiciler türü eşdeğerlik yapmak için güvenmek zorunda uyguladığınızda oluşturulur. |
| CA2132 | [CA2132: Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır](../code-quality/ca2132.md) |SecurityCriticalAttribute koduna sahip türler ve üyeler Silverlight uygulama kodu tarafından kullanılamaz. Kritik güvenlik türleri ve üyeleri, yalnızca Silverlight sınıf kütüphanesi için .NET Framework'ündeki güvenilen kod tarafından kullanılabilir. Türetilmiş sınıftaki ortak veya korumalı oluşturma, onun temel sınıfından aynı düzeyde veya daha saydam olması gerektiğinden uygulama içindeki sınıf SecurityCritical işaretlenmiş bir sınıftan türeyemez. |
| CA2133 | [CA2133: Temsilciler tutarlı saydamlığı olan yöntemlere bağlanmalıdır](../code-quality/ca2133.md) | Bu uyarı SecurityCriticalAttribute saydam veya SecuritySafeCriticalAttribute kullanılarak işaretlenmiş bir yöntem kullanılarak işaretlenmiş temsilci bağlayan bir yöntemi ortaya çıkar. Uyarı, saydam veya kritik bir yöntem için kritik derecede güvenli temsilciyi bağlayan yöntemi de tetikler. |
| CA2134 | [CA2134: Yöntemler taban yöntemleri geçersiz kılarken tutarlı saydamlığı tutmalıdır](../code-quality/ca2134.md) |Bu kural yöntem saydam olan SecurityCriticalAttribute etkisiz kılma kullanılarak işaretlendiğinde veya SecuritySafeCriticalAttribute işaretlenmesi kullanıldığında oluşturulur. Bu kural saydam yöntem olan SecurityCriticalAttribute etkisiz kılma kullanılarak işaretlendiğinde veya SecuritySafeCriticalAttribute işaretlenmesi kullanıldığında oluşturulur. Bu kural, sanal bir yöntemi geçersiz kılarken veya bir arabirim uygulanırken uygulanır. |
| CA2135 | [CA2135: Düzey 2 derlemeler LinkDemands içermemelidir](../code-quality/ca2135.md) | LinkDemands, düzey 2 güvenlik kural kümesinden kaldırılmıştır. Tam zamanlı (JIT) derleme zamanında güvenliği zorlayan LinkDemands'ı kullanmak yerine; yöntemleri, türleri ve SecurityCriticalAttribute özniteliğine sahip alanları işaretleyin. |
| CA2127 | [CA2136: Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır](../code-quality/ca2136.md) | Kritik kod yüzde 100 saydam bir derlemede oluşamaz. Bu kural, tür, alan ve yöntem düzeylerinde herhangi bir SecurityCritical ek açıklaması için yüzde 100 saydam derlemeleri analiz eder. |
| CA2136 | [CA2136: Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır](../code-quality/ca2136.md) | Saydamlık nitelikleri, geniş kapsam kodlu öğelerden daha küçük kapsamlı öğelere uygulanır. Geniş kapsamı ile kod öğelerinin saydamlık özniteliklerini ilk öğeden kapsayan kod öğelerinin saydam öznitelikleri önceliklidir. Örneğin; SecurityCriticalAttribute özniteliğiyle işaretlenmiş bir sınıf, SecuritySafeCriticalAttribute özniteliği kullanılarak işaretlenmiş bir yöntemi içeremez. |
| CA2137 | [CA2137: Saydam yöntemler yalnızca doğrulanabilir IL içermelidir](../code-quality/ca2137.md) | Bir yöntem, doğrulanamayan kodu içerir veya başvuruya göre bir tür döndürür. Bu kural, doğrulanamayan microsoft ara dili (MISL) yürütmek için güvenlik saydam kodu tarafından girişimleri tetikler. Ancak kural tam IL doğrulayıcısı içermez ve MSIL doğrulamasının çoğu ihlalini yakalamak için buluşsal yöntemler kullanır. |
| CA2138 | [CA2138: Saydam yöntemler SuppressUnmanagedCodeSecurity özniteliğine sahip yöntemleri çağırmamalıdır](../code-quality/ca2138.md) | Saydam bir güvenlik yöntemi, SuppressUnmanagedCodeSecurityAttribute özniteliği kullanılarak işaretlenmiş bir yöntemi çağırır. |
| CA2139 | [CA2139: Saydam yöntemler HandleProcessCorruptingExceptions özniteliğini kullanamaz](../code-quality/ca2139.md) | Bu kural, saydam herhangi bir yöntemi ve HandleProcessCorruptedStateExceptionsAttribute özniteliği kullanarak işlem bozucu özel durumun yakalanması için deneme yapılmasını tetikler. Özel durumu bozan bu işlem, AccessViolationException gibi özel durumların CLR 4.0 sürümü özel durum sınıflandırılmasıdır. HandleProcessCorruptedStateExceptionsAttribute özniteliği, sadece kritik güvenlik yöntemleri tarafından kullanılır ve saydam bir yöntem uygulanırsa yoksayılır. |
| CA2129 | [CA2140: Saydam kod güvenlik kritik nesnelerine başvurmamalıdır](../code-quality/ca2140.md) | SecurityTransparentAttribute ile işaretlenmiş yöntemler, SecurityCritical olarak işaretlenmiş ortak olmayan üyeleri çağırır. Bu kural, saydam/kritik karma derlemedeki tüm yöntemler ve türleri inceler ve SecurityTreatAsSafe olarak işaretlenmemiş ortak olmayan kritik saydam koddaki çağrıları işaretler. |
| CA2140 | [CA2140: Saydam kod güvenlik kritik nesnelerine başvurmamalıdır](../code-quality/ca2140.md) | SecurityCriticalAttribute özniteliğiyle işaretlenmiş bir kod, kritik güvenliktedir. Saydam bir yöntem, kritik güvenlik öğesini kullanamaz. Saydam bir tür kritik güvenlik türünü kullanmayı denerse; TypeAccessException, MethodAccessException veya FieldAccessException ortaya çıkar. |
| CA2141 |[CA2141:Transparent yöntemleri LinkDemands'i karşılamamalıdır](../code-quality/ca2141.md) | Saydam güvenlik yöntemi, bir derlemede APTCA özniteliğiyle işaretlenmiş olan yöntemi çağırır veya saydam bir güvenlik yöntemi, tür ya da yöntem için LinkDemand karşılar. |
| CA2142 | [CA2142: Saydam kod LinkDemands ile korunmamalıdır](../code-quality/ca2142.md) | Bu kural, bunlara erişmek için LinkDemands gerektiren saydam yöntemler üzerinde oluşturulur. Saydam güvenlik kodu, bir işlemin güvenlik doğrulaması için sorumlu olmamalıdır ve bu nedenle izin talep edilmemelidir. |
| CA2143 | [CA2143: Saydam yöntemler güvenlik taleplerini kullanmamalıdır](../code-quality/ca2143.md) | Saydam güvenlik kodu, bir işlemin güvenlik doğrulaması için sorumlu olmamalıdır ve bu nedenle izin talep edilmemelidir. Saydam güvenlik kodu, güvenlik kararını vermek için tüm talepleri kullanmalıdır ve güvenli kritik kod, saydam koda tüm talepleri vermek için güvenmemelidir. |
| CA2144 | [CA2144: Saydam kod derlemeleri bayt dizilerinden yüklememelidir](../code-quality/ca2144.md) | Saydam kod için güvenlik incelemesi kritik kod için güvenlik incelemesi kadar kapsamlı değildir, çünkü saydam kod güvenlik duyarlı eylemleri gerçekleştiremez. Bir bayt dizisinden yüklenen derlemeler, saydam kodda fark edilmeyebilir ve o bayt dizisi denetlenmesi gereken kritik ya da daha da önemlisi güvenli kritik kod içerebilir. |
| CA2145 | [CA2145: Saydam yöntemler SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır](../code-quality/ca2145.md) | SuppressUnmanagedCodeSecurityAttribute özniteliği ile donatılmış yöntemler, çağıran herhangi bir yöntem yerleştirilen örtülü bir LinkDemand'a sahiptir. Bu LinkDemand, çağıran kodun kritik güvenlikli olmasını gerektirir. SecurityCriticalAttribute özniteliği ile SuppressUnmanagedCodeSecurity kullanan yöntemi işaretlemek, bu gereksinimi çağıran yöntem için daha belirgin yapar. |
| CA2146 | [CA2146: Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır](../code-quality/ca2146.md) | Bu kural, kendi temel türü kadar kritik olmayan saydam güvenlik özniteliğine sahip bir tür türetildiğinde veya arabirim uygulandığında tetiklenir. Yalnızca kritik türler, kritik temel türlerden veya kritik arabirimleri uygulayanlardan türeyebilir ve sadece kritik ya da kritik güvenli türler, kritik güvenli temel türler veya kritik güvenli arabirim uygulamalarından türeyebilir. |
| CA2128 |[CA2147: Saydam türler güvenlik bildirimlerini kullanmamalıdır](../code-quality/ca2147.md) | Bu kural, bir derlemedeki tüm yöntemleri ve türleri %100 saydam ya da saydam/kritik olarak analiz eder ve herhangi bir bildirime dayalı veya kesin onaylama kullanımını işaretler. |
| CA2147 |[CA2147: Saydam türler güvenlik bildirimlerini kullanmamalıdır](../code-quality/ca2147.md) | SecurityTransparentAttribute olarak işaretlenmiş kod, onay için yeterli izinlerin verilmiş olmasını garanti etmez. |
| CA2149 | [CA2149: Saydam metotlar yerel kod içine çağırmamalıdır](../code-quality/ca2149.md) | Bu kuralın yerel kodu (örneğin, bir P/Invoke) doğrudan çağıran herhangi bir saydam yöntem olduğunda ortaya çıkar. Bu kural ihlalleri 2. seviye saydamlık modeli içindeki MethodAccessException öncülüğünde ve 1. seviye saydamlık modeli içindeki UnmanagedCode için talepte bulunur. |
| CA2151 |[CA2151: Kritik türler içeren alanlar güvenlik açısından kritik olmalıdır](../code-quality/ca2151.md) | Kritik güvenlik türlerini kullanmak için türe başvuran kod güvenliği kritik veya güvenlik güvenli kritik olmalıdır. Dolaylı başvuru olsa bile bu doğrudur. Bu nedenle, bir güvenlik saydam veya güvenlik güvenli kritik alana erişmek mümkün olmayacaktır, çünkü saydam kod hala alana erişemeyecektir. |
| CA2200 | [CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma](../code-quality/ca2200.md) | Tekrar fırlatılan bir özel durum ve fırlatma açıklamasında açıkça belirtilen özel durum. Bir özel durum throw deyiminde özel durum belirterek yeniden fırlatılırsa yöntem listesi özel durum döndüren özgün yöntem ile kaybolan geçerli yöntem arasında çağırır. |
| CA2201 | [CA2201: Ayrılmış özel durum türleri oluşturmayın](../code-quality/ca2201.md) | Bu özgün hata algılama ve hata ayıklamayı zorlaştırır. |
| CA2202 | [CA2202: Nesneleri birden çok kez atmayın](../code-quality/ca2202.md) |Yöntem uygulaması, aynı nesne üzerinde System.IDisposable.Dispose veya bir Dispose eşdeğer (örneğin, bazı türleri üzerinde Close() yöntemi) için birden fazla çağrı kodu yolları içerir. |
| CA2204 | [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204.md) | Bir yöntemin gövdesi içinde hazır bilgi dizesi Microsoft yazım denetimi kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir. |
| CA2205 | [CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın](../code-quality/ca2205.md) | Bir işletim sistemi çağırma yöntemi tanımlanır ve eşdeğer işlevselliğe sahip bir .NET yöntemi kullanılabilir. |
| CA2207 | [CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207.md) | Bir değer türü açık bir statik oluşturucu bildirir. Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın. |
| CA2208 |[CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin](../code-quality/ca2208.md) | Varsayılan (parametresiz) kurucu veya ArgumentException türeyen özel bir durum türü için çağrı yapılır veya hatalı dize bağımsız değişkeni parametreli bir kurucu veya ArgumentException türeyen bir özel durum türü iletilir. |
| CA2210 |[CA2210: Derlemelerin tanımlayıcı adı geçerli olmalıdır](../code-quality/ca2210.md) | Güçlü ad oynanmış derlemeyi bilmeden yükleyerek istemcileri korur. Güçlü adı olmayan derlemeler oldukça sınırlı sayıda senaryo dışında kullanılmamalıdır. Düzgün imzalanmamış derlemeleri paylaşırsanız veya dağıtırsanız, derleme aslı bozuabilir, ortak dil çalışma zamanı derlemeyi yükleyemeyebilir veya kullanıcı kendi bilgisayarındaki doğrulamayı devre dışı bırakabilir. |
| CA2211 |[CA2211: Sabit olmayan alanlar görünür olmamalıdır](../code-quality/ca2211.md) | Ne sabitler, ne de salt okunur olan statik alanlar güvenli iş parçacığı değildir. Böyle bir alana erişim dikkatli bir şekilde denetlenebilir ve sınıf nesnesi erişimi eşitlemek için gelişmiş programlama tekniklerini gerektirir. |
| CA2212 | [CA2212: Servis verilen bileşenleri WebMethod ile işaretlemeyin](../code-quality/ca2212.md) |System.EnterpriseServices.ServicedComponent'dan devralan türde bir yöntem System.Web.Services.WebMethodAttribute kullanılarak işaretlendi. WebMethodAttribute ve bir ServicedComponent yönteminin çakışan davranışları ve bağlam ve işlem akışı için gereksinimleri olduğu için, bazı senaryolarda yöntemin davranışı yanlış olacaktır. |
| CA2213 | [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213.md) | IDisposable uygulayan türlerin alanları System.IDisposable uygulayan bir türle bildirilir. Bir Dispose yöntemi alanının tanıtıcısının bildirim türü Dispose yöntemi tarafından çağrılmaz. |
| CA2214 | [CA2214: Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın](../code-quality/ca2214.md) | Kurucu sanal bir yöntemi çağırdığında, yapıcı yöntemini çağıran örneği işletilmemiş olabilir. |
| CA2215 | [CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215.md) | Tür atılabilen bir türden devralınırsa, kendi Dispose yönteminden basit tür olan Dispose yöntemini çağırmalıdır. |
| CA2216 |[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216.md) | System.IDisposable uygulayan yöntem ve yönetilmeyen kaynakların kullanımını öneren alanlar Object.Finalize'da açıklandığı gibi sonlandırıcıyı uygulamazlar. |
| CA2217 | [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md) |Dışarıdan görünen FlagsAttribute ile işaretlenmiş numaralandırma ve ikinin katı olmayan ya da numaralandırma üzerinde tanımlanan diğer değerlerin kombinasyonu olmayan bir ya da daha fazla değer vardır. |
| CA2218 |[CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218.md) | GetHashCode, karma algoritmalar ve karma tablolar gibi veri yapıları için uygun olan geçerli örneği temel alan bir değer döndürür. Aynı türdeki ve eşit olan iki nesnenin aynı karma kodu döndürmesi gerekir. |
| CA2219 | [CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin](../code-quality/ca2219.md) | Bir istisna sonlandırıcı ya da arıza yan tümcesine neden olduğunda, yeni istisna aktif istisnayı saklar. Filtre yan tümcesinde bir özel durum ortaya çıktığında, çalışma zamanı özel durumu sessizce yakalar. Bu özgün hata algılama ve hata ayıklamayı zorlaştırır. |
| CA2220 | [CA2220: Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır](../code-quality/ca2220.md) | Sonlandırılma, devralma hiyerarşisi aracılığıyla gönderilmelidir. Bunu güvence altına almak için, türler basit sınıflarının kendi Finalize yönteminde Finalize yöntemini çağırmalıdır. |
| CA2221 |[CA2221: Sonlandırıcılar korunmalıdır](../code-quality/ca2221.md) | Sonlandırıcılar aile erişim değiştiricisi kullanmalıdır. |
| CA2222 | [CA2222: Devralınan üye görünürlüğünü azaltmayın](../code-quality/ca2222.md) |Devralınan üyeler için erişim değiştiricisini değiştirmemelisiniz. Devralınmış bir üyeyi özel olarak değiştirme, arayanların yöntemin temel sınıf uygulamasına erişmesini engellemez. |
| CA2223 | [CA2223: Üyeler dönüş türünden daha fazla farklı olmalıdır](../code-quality/ca2223.md) | Ortak dil çalışma zamanı, aynı üyeler arasında ayrım yapmak için dönüş türleri kullanımına izin verir, ancak bu özelliği ne ortak dil belirtimi ne de .NET programlama dillerinin ortak özelliğidir. |
| CA2224 | [CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224.md) | Ortak bir tür eşitlik işlecini uygular, ancak Object.Equals'ı geçersiz kılmaz. |
| CA2225 | [CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225.md) |Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı. Adlandırılmış alternatif üye operatörün sağladığı gibi aynı fonksiyonlara erişmeyi sağlar ve aşırı yüklenmiş operatörlere destek olmayan dilleri programlayan programcılar için bunlar sağlanmıştır. |
| CA2226 | [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226.md) | Bir tür, eşitlik ya da eşitsizlik operatörünü uygular ve ters işleci uygulamaz. |
| CA2227 |[CA2227: Koleksiyon özellikleri salt okunur olmalıdır](../code-quality/ca2227.md) |Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamını farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir. |
| CA2228 | [CA2228: Yayımlanmamış kaynak biçimlerini yollamayın](../code-quality/ca2228.md) | .NET 'in yayın öncesi sürümleri kullanılarak oluşturulan kaynak dosyaları, desteklenen .NET sürümleri tarafından kullanılamayabilir. |
| CA2229 | [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229.md) | Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. |
| CA2230 | [CA2230: Değişken bağımsız değişkenler için params kullanın](../code-quality/ca2230.md) | Ortak veya korumalı tür VarArgs çağırma kuralı params anahtar sözcüğünü kullanan bir ortak veya korumalı yöntem içerir. |
| CA2231 | [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231.md) | Bir değer türü Object.Equals'ı geçersiz kılar, ama eşitlik işlecini uygulamaz. |
| CA2232 | [CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin](../code-quality/ca2232.md) | STAThreadAttribute, COM uygulama modelinin tek bir iş parçacıklı grup olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir. |
| CA2233 |[CA2233: İşlemler taşmamalıdır](../code-quality/ca2233.md) | Aritmetik işlemleri, işlenenleri doğrulamadan gerçekleştirmemelisiniz. Bu, işlemin sonucu söz konusu olan veri türleri için olası değerler aralığının dışında olduğundan emin olur. |
| CA2234 | [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234.md) | Adında "URI", "URI", "urn", "urn", "url" veya "url" içeren bir dize parametresi olan yöntem çağrısı yapıldı. Bildirim türü yöntemi, System.Uri parametresini aşırı yüklemeye uyan yöntemi içerir. |
| CA2235 | [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235.md) | Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. |
| CA2236 | [CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236.md) | Bu kural ihlalini düzeltmek için, taban türü GetObjectData yöntemini veya karşılık gelen türetilmiş yöntemden ya da oluşturucudan serileştirme oluşturucusunu çağırın. |
| CA2237 | [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237.md) | Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınması için, türler ISerializable arabirimini uygulaması aracılığıyla özel seri hale getirme yordamı kullanıldığında SerializableAttribute özniteliği kullanılarak işaretlenmelidir. |
| CA2238 |[CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238.md) | Seri hale getirme olayı tanıtan yöntem türü, doğru imzaya, dönüş türüne veya görünürlüğe sahip değil. |
| CA2239 | [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239.md) | System.Runtime.Serialization.OptionalFieldAttribute özniteliğini kullanarak işaretlenmiş alan türü ve tür, yöntemlerinin yönetilmesi seriyi kaldırma olayını sağlamaz. |
| CA2240 | [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240.md) | Bu kural ihlalini düzeltmek için GetObjectData yöntemi geçersiz kılınabilir ve bütün örnek alanların seri hale getirme işlemine dahil edildiğinden emin olun ya da NonSerializedAttribute özniteliğini kullanarak açıkça işaretleyin. |
| CA2241 | [CA2241: Biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın](../code-quality/ca2241.md) | System.String.Format için geçirilen biçim, her bir nesne bağımsız değişkeninden sorumlu olan öğe biçimini içermez. |
| CA2242 |[CA2242: NaN için doğru sınayın](../code-quality/ca2242.md) | Bu ifade, değeri Single.Nan veya Double.Nan'a karşı test eder. Single.IsNan(Single) ya da Double.IsNan(Double) değerini test etmek için kullanın. |
| CA2243 |[CA2243: Öznitelik dize harfleri doğru çözümlenmelidir](../code-quality/ca2243.md) | Bir öznitelik dize literal parametresi, URL, GUID ya da sürüm için doğru ayrıştırmaz. |
| CA5122 | [CA5122 P/Invoke bildirimleri güvenli kritik olmamalıdır](../code-quality/ca5122.md) | Güvenlik duyarlı işlem gerçekleştirildiğinde yöntemler SecuritySafeCritical olarak işaretlenir ancak saydam mod kullanılarak da güvenli olur. Saydam kod, P/Invoke aracılığıyla yerel kodu hiçbir zaman doğrudan çağırmayabilir. Bu nedenle, P/Invoke güvenlik güvenli kritik olarak işaretleme çağırmak için saydam kodu etkinleştirmez ve güvenlik çözümlemesi için yanıltıcıdır. |
