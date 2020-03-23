---
title: Dinamik sembolik yürütme | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e5a3248d3f081bcab08c08110d305f0aa6235817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302625"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Dinamik sembolik yürütme kullanarak giriş oluşturma

IntelliTest, programdaki şube koşullarını analiz ederek [parametreli birim testleri](test-generation.md#parameterized-unit-testing) için girişler oluşturur. Test girişleri, programın yeni dallanma davranışlarını tetikleyip tetiklemeyeceğine bağlı olarak seçilir. Analiz artımlı bir süreçtir. Bu resmi test giriş `q: I -> {true, false}` parametreleri `I`üzerinde bir yüklem geliştirir. `q`IntelliTest'in gözlemlediği davranış kümesini temsil eder. Başlangıçta, `q := false`, hiçbir şey henüz gözlenen beri.

Döngünün adımları şunlardır:

1. IntelliTest, [bir kısıtlama](#constraint-solver) `q(i)=false` çözücü kullanarak girişleri belirler. `i` İnşaat olarak, giriş `i` daha önce görülmemiş bir yürütme yolu alacaktır. Başlangıçta, bu `i` herhangi bir giriş olabileceği anlamına gelir, çünkü henüz hiçbir yürütme yolu keşfedilmemiştir.

1. IntelliTest seçilen giriş `i`ile testi yürütür ve test ve test altındaki programın yürütülmesini izler.

1. Yürütme sırasında, program programın tüm koşullu dalları tarafından belirlenen belirli bir yol alır. Yürütmeyi belirleyen tüm koşulların kümesine, biçimsel giriş parametreleri `p: I -> {true, false}` üzerinde yüklem olarak yazılan *yol koşulu*denir. IntelliTest bu yüklemin bir temsilini hesaplar.

1. IntelliTest `q := (q or p)`setleri . Başka bir deyişle, temsil edilen yolu gördüğü gerçeğini `p`kaydeder.

1. Adım 1'e git.

IntelliTest'in [kısıtlama çözücüsi](#constraint-solver) .NET programlarında görünebilecek her türlü değerle başa çıkabilir:

* [İnstayörler](#integers-and-floats) ve [Şamandıralar](#integers-and-floats)
* [Nesneler](#objects)
* [Yapılar](#structs)
* [Diziler](#arrays-and-strings) ve [Dizeleri](#arrays-and-strings)

IntelliTest, belirtilen varsayımları ihlal eden girişleri filtreler.

Hemen girişlerin [(parametreli birim testlerine](test-generation.md#parameterized-unit-testing)bağımsız değişkenler) yanı sıra, bir test [PexSelect](static-helper-classes.md#pexchoose) statik sınıfından daha fazla giriş değeri çizebilir. Seçenekler aynı zamanda [parametreli alayların](#parameterized-mocks)davranışını da belirler.

## <a name="constraint-solver"></a>Kısıtlama çözücü

IntelliTest, bir testin ve test altındaki programın ilgili giriş değerlerini belirlemek için bir kısıtlama çözücü kullanır.

IntelliTest [Z3](https://github.com/Z3Prover/z3/wiki) kısıtlama çözücü kullanır.

## <a name="dynamic-code-coverage"></a>Dinamik kod kapsamı

Çalışma zamanı izlemenin bir yan etkisi olarak, IntelliTest dinamik kod kapsama verilerini toplar.
IntelliTest yalnızca yürütülen kod hakkında bilgi edindiği için *dinamik* olarak adlandırılır, bu nedenle kapsama alanı için diğer kapsama aracının genellikle yaptığı gibi mutlak değerler veremez.

Örneğin, IntelliTest dinamik kapsamı 5/10 temel blok olarak bildirdiğinde, bu, analizle şimdiye kadar ulaşılan tüm yöntemlerdeki toplam blok sayısının (test altındaki derlemede var olan tüm yöntemlerin aksine) on bloktan beşinin kapsandığı anlamına gelir.
Daha sonra yapılan analizde, daha fazla ulaşılabilir yöntem keşfedildikçe, hem sayı (bu örnekte 5) hem de payda (10) artabilir.

## <a name="integers-and-floats"></a>Tamsayılar ve kayan noktalı sayılar

IntelliTest'in [kısıtlama çözücüsi,](#constraint-solver) test ve test altındaki program için farklı yürütme yollarını tetiklemek için **bayt,** **int,** **float**ve diğerleri gibi ilkel türlerin test giriş değerlerini belirler.

## <a name="objects"></a>Nesneler

IntelliTest, [varolan .NET sınıflarının örneklerini oluşturabilir](#existing-classes)veya belirli bir arabirimi otomatik olarak uygulayan ve kullanıma bağlı olarak farklı şekillerde görünen [sahte nesneler oluşturmak](#parameterized-mocks) için IntelliTest'i kullanabilirsiniz.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Varolan sınıfları anında

**Sorun ne?**

IntelliTest, bir test ve test altındaki programı çalıştırdığında yürütülen yönergeleri izler. Özellikle, alanlara tüm erişimi izler. Daha sonra, nesneler ve alan değerleri de dahil olmak üzere, test ve test altındaki programın başka ilginç şekillerde de işleyecek şekilde yeni test girişlerini belirlemek için bir [kısıtlama çözücü](#constraint-solver) kullanır.

Bu, IntelliTest'in belirli türdeki nesneleri oluşturmak ve alan değerlerini ayarlamak için olması gerektiği anlamına gelir. Sınıf [görünürse](#visibility) ve [görünür](#visibility) bir varsayılan oluşturucu varsa, IntelliTest sınıfın bir örneğini oluşturabilir.
Sınıfın tüm alanları [görünürse,](#visibility)IntelliTest alanları otomatik olarak ayarlayabilir.

Tür görünmüyorsa veya alanlar [görünmüyorsa,](#visibility)IntelliTest nesneleri oluşturmak ve maksimal kod kapsamı elde etmek için bunları ilginç durumlara getirmek için yardıma ihtiyaç duyar. IntelliTest, örnekleri rasgele şekillerde oluşturmak ve başlatmak için yansımayı kullanabilir, ancak nesneyi normal program yürütmesi sırasında asla gerçekleşmeyecek bir duruma getirebileceğinden bu genellikle istenmez. Bunun yerine, IntelliTest kullanıcıdan gelen ipuçlarına dayanır.

## <a name="visibility"></a>Görünürlük

.NET ayrıntılı bir görünürlük modeline sahiptir: türleri, yöntemleri, alanları ve diğer üyeler **özel,** **genel,** **dahili,** ve daha fazlası olabilir.

IntelliTest testler oluşturduğunda, oluşturulan testler bağlamında .NET görünürlük kuralları yla ilgili olarak yalnızca yasal olan eylemleri (yapıcıları, yöntemleri ve ayar alanlarını çağırma gibi) gerçekleştirmeye çalışır.

Kurallar aşağıdaki gibidir:

* **Dahili üyelerin görünürlüğü**
  * IntelliTest, oluşturulan testlerin, çevreleyen [PexClass](attribute-glossary.md#pexclass)tarafından görülebilen dahili üyelere erişeceğini varsayar.
  .NET, dahili üyelerin görünürlüğünü diğer derlemelere genişletmek için **InternalsVisibleToAttribute'e** sahiptir.

* **[PexClass'ın](attribute-glossary.md#pexclass) özel ve aile üyelerinin görünürlüğü (C#'da korunur)**
  * IntelliTest her zaman oluşturulan testleri doğrudan [PexClass'a](attribute-glossary.md#pexclass) veya bir alt sınıfa yerleştirir. Bu nedenle, IntelliTest tüm görünür aile üyeleri (C #**korumalı)** kullanabilirsiniz varsayar.
  * Oluşturulan testler doğrudan [PexClass'a](attribute-glossary.md#pexclass) yerleştirilirse (genellikle kısmi sınıflar kullanılarak), IntelliTest [PexClass'ın](attribute-glossary.md#pexclass)tüm özel üyelerini de kullanabileceğini varsayar.

* **Kamu üyelerinin görünürlüğü**
  * IntelliTest, [PexClass](attribute-glossary.md#pexclass)bağlamında görünen tüm dışa aktarılan üyeleri kullanabileceğini varsayar.

## <a name="parameterized-mocks"></a>Parametreli sahte nesneler

Arabirim türünde parametresi olan bir yöntem nasıl sınanır? Ya da mühürsüz bir sınıftan? IntelliTest, bu yöntem çağrıldığında hangi uygulamaların daha sonra kullanılacağını bilmiyor. Ve belki de test zamanında gerçek bir uygulama bile mevcut değildir.

Geleneksel cevap, müstehcen davranışla *sahte nesneler* kullanmaktır.

Sahte bir nesne arabirimi uygular (veya mühürsüz bir sınıfı genişletir). Gerçek bir uygulamayı temsil etmez, ancak sahte nesneyi kullanarak testlerin yürütülmesine izin veren bir kısayoldur. Davranışı, kullanıldığı her test çalışmasının bir parçası olarak el ile tanımlanır. Sahte nesneleri ve beklenen davranışlarını tanımlamayı kolaylaştıran birçok araç vardır, ancak bu davranış yine de el ile tanımlanmalıdır.

Sahte nesnelerdeki sabit kodlu değerler yerine, IntelliTest değerleri oluşturabilir. [Parametreli birim testini](test-generation.md#parameterized-unit-testing)sağladığı gibi, IntelliTest de parametreli alaylara olanak sağlar.

Parametreli alayların iki farklı yürütme modu vardır:

* **seçme**: kod keşfederken, parametreli mocks ek test girişleri kaynağı dır ve IntelliTest ilginç değerler seçmek için çalışacağız
* **yeniden oynatma**: önceden oluşturulmuş bir testi yürütürken, parametreli alaylar davranışla saplamalar gibi davranışlar sergiler (diğer bir deyişle, önceden tanımlanmış davranış).

Parametreli alaylar için değer elde etmek için [PexSelect'i](static-helper-classes.md#pexchoose) kullanın.

## <a name="structs"></a>Yapılar

IntelliTest'in **yapı** değerleri hakkındaki muhakemesi, [nesnelerle](#objects)olan başa çıkma şekline benzer.

## <a name="arrays-and-strings"></a>Diziler ve dizeler

IntelliTest, bir test ve test altındaki programı çalıştırırken yürütülen yönergeleri izler. Özellikle, program bir dize veya dizi (ve alt sınırları ve çok boyutlu bir dizi uzunlukları) uzunluğuna bağlı olduğunda gözlemler.
Ayrıca, programın bir dize veya dizinin farklı öğelerini nasıl kullandığını da gözlemler. Daha sonra, testin ve test altındaki programın ilginç şekillerde şekilde çalışmasına neden olabilecek uzunlukları ve öğe değerlerinin belirlemek için bir [kısıtlama çözücü](#constraint-solver) kullanır.

IntelliTest, ilginç program davranışlarını tetiklemek için gereken dizilerin ve dizelerin boyutunu en aza indirmeye çalışır.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Ek girişler elde etme

[PexSelect](static-helper-classes.md#pexchoose) statik sınıfı bir teste ek girişler elde etmek için kullanılabilir ve [parametreli alayları](#parameterized-mocks)uygulamak için kullanılabilir.

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.

## <a name="further-reading"></a>Daha fazla bilgi

* [Nasıl çalışır?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
