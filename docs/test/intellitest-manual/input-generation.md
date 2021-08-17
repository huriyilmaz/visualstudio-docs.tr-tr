---
title: Dinamik sembolik yürütme | Microsoft IntelliTest geliştirici test aracı
description: IntelliTest 'in, programdaki dal koşullarını çözümleyerek parametreleştirilmiş birim testleri için giriş oluşturma şeklini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 16d0c045d9f0085a462e3d7f7f55f8af6326cde6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033050"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Dinamik sembolik yürütme kullanarak giriş oluşturma

IntelliTest, programdaki dal koşullarını çözümleyerek [parametreli birim testleri](test-generation.md#parameterized-unit-testing) için girişler oluşturur. Test girdileri, programın yeni dallanma davranışlarını tetikleyebilecekleri ve bunlara göre seçilir. Analiz, artımlı bir işlemdir. `q: I -> {true, false}`Biçimsel test giriş parametreleri üzerinde bir koşulu iyileştirir `I` . `q` IntelliTest 'in zaten gözlemlediği davranışlar kümesini temsil eder. İlk olarak `q := false` , bir şey henüz gözlemlenmedi.

Döngünün adımları şunlardır:

1. IntelliTest `i` , `q(i)=false` [kısıtlama çözücü](#constraint-solver)kullanan girişleri belirler. Yapım sırasında, girişin daha `i` önce görülmeyen bir yürütme yolu alır. Başlangıçta bu, `i` herhangi bir giriş olabileceği anlamına gelir, çünkü henüz bir yürütme yolu bulunamamıştır.

1. IntelliTest, Seçili girişle testi yürütür ve testin `i` ve test altındaki programın yürütülmesini izler.

1. Yürütme sırasında program, programın tüm koşullu dallarıyla belirlenen belirli bir yolu alır. Yürütmeyi tespit eden tüm koşulların kümesine, biçimsel giriş parametreleri üzerinde koşul olarak yazılmış *yol koşulu* denir `p: I -> {true, false}` . IntelliTest bu koşulun gösterimini hesaplar.

1. IntelliTest kümeleri `q := (q or p)` . Diğer bir deyişle, tarafından temsil edilen yolu gördüğü olguyu kaydeder `p` .

1. 1. adıma gidin.

IntelliTest [kısıtlama çözücü](#constraint-solver) , .net programlarında görünebilen tüm türlerin değerleriyle uğraşmak için:

* [Tamsayılar](#integers-and-floats) ve [float](#integers-and-floats)
* [Nesneler](#objects)
* [Yapılar](#structs)
* [Diziler](#arrays-and-strings) ve [dizeler](#arrays-and-strings)

IntelliTest, belirtilen varsayımları ihlal eden girdileri filtreler.

Anlık girdilerin yanı sıra, bir test [](test-generation.md#parameterized-unit-testing), [PexChoose](static-helper-classes.md#pexchoose) statik sınıfından daha fazla giriş değeri çizebilir. Seçimler aynı zamanda [parametreli](#parameterized-mocks)davranışlarının davranışını de tespit.

## <a name="constraint-solver"></a>Kısıtlama çözücü

IntelliTest, bir testin ve test edilen programın ilgili giriş değerlerini belirlemede bir kısıtlama çözücü kullanır.

IntelliTest, [Z3](https://github.com/Z3Prover/z3/wiki) kısıtlaması çözücü kullanır.

## <a name="dynamic-code-coverage"></a>Dinamik kod kapsamı

Çalışma zamanı izlemenin yan etkisi olarak, IntelliTest dinamik kod kapsamı verilerini toplar.
Bu *dinamik* olarak adlandırılır çünkü IntelliTest yalnızca yürütülen kodu bilir ve bu nedenle, diğer kapsam araçlarının genellikle yaptığı şekilde kapsama için mutlak değerler veremeyiz.

Örneğin, IntelliTest dinamik kapsamı 5/10 temel bloklar olarak raporladığında, bu, en fazla (test edilen derlemede bulunan tüm yöntemlerin aksine) en fazla bir çözümleme tarafından ulaşılan tüm yöntemlerin toplam blok sayısının on olduğu anlamına gelir.
Daha sonra analizde daha erişilebilir yöntemler bulunduğundan, her ikisi de pay (Bu örnekteki 5) ve payda (10) artabilir.

## <a name="integers-and-floats"></a>Tamsayılar ve kayan noktalı sayılar

IntelliTest [kısıtlama çözücü](#constraint-solver) , test ve test edilen program için farklı yürütme yolları tetiklemek üzere **byte**, **Int**, **float** ve diğer basit türlerin test giriş değerlerini belirler.

## <a name="objects"></a>Nesneler

IntelliTest, [var olan .net sınıflarının örneklerini oluşturabilir](#existing-classes)veya belirli bir arabirimi uygulayan ve kullanıma bağlı olarak farklı şekillerde davranan, otomatik olarak bir [model oluşturmak](#parameterized-mocks) için IntelliTest ' i kullanabilirsiniz.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Varolan sınıfların örneğini oluşturma

**Sorun nedir?**

IntelliTest, bir testi ve test altındaki programı çalıştırdığında yürütülen yönergeleri izler. Özellikle, tüm alanlara erişimi izler. Daha sonra nesneler ve alan değerleri dahil olmak üzere yeni test girişlerini belirlemek için bir [kısıtlama çözücü](#constraint-solver) kullanır, bu nedenle test ve test altındaki program diğer ilginç yollarla davranır.

Bu, IntelliTest 'in belirli türlerde nesneler oluşturması ve alan değerlerini ayarlaması gerektiği anlamına gelir. Sınıf [görünür](#visibility) durumdaysa ve [görünür](#visibility) bir varsayılan oluşturucuya sahipse, IntelliTest sınıfın bir örneğini oluşturabilir.
Sınıfın tüm alanları [görünür](#visibility)durumdaysa, IntelliTest alanları otomatik olarak ayarlayabilir.

Tür görünür değilse veya alanlar [görünür](#visibility)değilse, IntelliTest, nesne oluşturmaya ve bunları en fazla kod kapsamı elde etmek için ilginç durumlara getirmeye yardımcı olur. IntelliTest, örnekleri rastgele şekilde oluşturmak ve başlatmak için yansıma kullanabilir, ancak nesneyi normal program yürütmesi sırasında hiçbir zaman gerçekleşmeyecek bir duruma getirebileceğinden bu genellikle istenmez. Bunun yerine, IntelliTest kullanıcının ipuçlarını kullanır.

## <a name="visibility"></a>Görünürlük

.NET, ayrıntılı görünürlük modeline sahiptir: türler, Yöntemler, alanlar ve diğer Üyeler **özel**, **genel**, **dahili** ve daha birçok iş olabilir.

IntelliTest testleri oluşturduğunda, oluşturulan testlerin bağlamı içinden .NET görünürlük kurallarına göre geçerli olan yalnızca eylemleri (oluşturucular, Yöntemler ve ayar alanları gibi) gerçekleştirmeye çalışır.

Kurallar aşağıdaki gibidir:

* **İç üyelerin görünürlüğü**
  * IntelliTest, üretilen testlerin kapsayan [PexClass](attribute-glossary.md#pexclass)tarafından görülebilen iç üyelere erişebileceğini varsayar.
  .NET, iç üyelerin görünürlüğünü diğer derlemelere genişletmek için **InternalsVisibleToAttribute** sahiptir.

* **[PexClass](attribute-glossary.md#pexclass) üyelerinin özel ve aile görünürlüğü (C# ' de korumalı)**
  * IntelliTest, oluşturulan testleri her zaman doğrudan [PexClass](attribute-glossary.md#pexclass) içinde veya bir alt sınıfa koyar. Bu nedenle, IntelliTest, tüm görünür aile üyelerini (C# ' de **korunan** ) kullanabileceği varsayılmaktadır.
  * Oluşturulan testler doğrudan [PexClass](attribute-glossary.md#pexclass) 'a (genellikle kısmi sınıflar kullanılarak) yerleştirilmişse, IntelliTest, [PexClass](attribute-glossary.md#pexclass)' ın tüm özel üyelerini de kullanabilir olduğunu varsayar.

* **Ortak üyelerin görünürlüğü**
  * IntelliTest, tüm aktarılmış üyeleri [PexClass](attribute-glossary.md#pexclass)bağlamında görünür olabileceğini varsayar.

## <a name="parameterized-mocks"></a>Parametreli sahte nesneler

Arabirim türünde parametresi olan bir yöntemi test etme. Veya korumalı olmayan bir sınıfa mi? IntelliTest, bu yöntem çağrıldığında daha sonra hangi uygulamaların kullanılacağını bilmez. Ve belki de test zamanında gerçek bir uygulama kullanılabilir değildir.

Geleneksel yanıt, *sahte nesneleri* açık davranışla kullanmaktır.

Bir sahte nesne bir arabirim uygular (veya korumalı olmayan bir sınıfı genişletir). Gerçek bir uygulamayı temsil etmez, ancak yalnızca sahte nesne kullanarak testlerin yürütülmesine izin veren bir kısayoldur. Davranışı, kullanıldığı her test çalışmasının bir parçası olarak el ile tanımlanır. Sahte nesneler ve bunların beklenen davranışlarını tanımlamanızı kolaylaştıran birçok araç mevcuttur, ancak bu davranışın yine de el ile tanımlanması gerekir.

Sahte nesnelerde sabit kodlu değerler yerine, IntelliTest değerleri oluşturabilir. Yalnızca [parametreli birim testi](test-generation.md#parameterized-unit-testing)sağladığından, IntelliTest de parametreli bir şekilde izin vermez.

Parametreli modlar iki farklı yürütme moduna sahiptir:

* **seçme**: kodu araştırırken, parametreleştirilen bir ek test girişi kaynağıdır ve IntelliTest, ilginç değerler seçmeye çalışır
* yeniden **yürütme**: daha önce oluşturulmuş bir test yürütürken parametreli bir test, davranış (diğer bir deyişle, önceden tanımlanmış davranış) ile saplamalar gibi davranır.

Parametreli bir değer elde etmek için [PexChoose öğesini](static-helper-classes.md#pexchoose) kullanın.

## <a name="structs"></a>Yapılar

IntelliTest 'in **Yapı** değerleri hakkında yöntemi, [nesnelerle](#objects)ilgilenen yönteme benzerdir.

## <a name="arrays-and-strings"></a>Diziler ve dizeler

IntelliTest, bir testi ve test altındaki programı çalıştırdığı için yürütülen yönergeleri izler. Özellikle, program bir dizenin veya dizinin uzunluğuna (ve çok boyutlu bir dizinin alt sınırlarına ve uzunluklarına) bağlı olduğunda çalışır.
Ayrıca programın bir dizenin veya dizinin farklı öğelerini nasıl kullandığını da gözlemleyen. Ardından bir [kısıtlama çözücü](#constraint-solver) kullanarak hangi uzunluklara ve öğe değerlerinin teste ve test altındaki programa ilginç yollarla davranmasına neden olabileceğini tespit edebilir.

IntelliTest, ilginç program davranışlarını tetiklemek için gereken dizilerin ve dizelerin boyutunu en aza indirmeye çalışır.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Ek girişler alma

[PexChoose](static-helper-classes.md#pexchoose) statik sınıfı, bir teste ek girişler elde etmek için kullanılabilir ve [parametreli modülleri](#parameterized-mocks)uygulamak için kullanılabilir.

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.

## <a name="further-reading"></a>Daha fazla bilgi

* [Nasıl çalışır?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
