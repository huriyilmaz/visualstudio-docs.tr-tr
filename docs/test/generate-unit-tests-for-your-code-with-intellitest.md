---
title: IntelliTest ile kodunuz için birim testleri oluşturma
description: IntelliTest, test verileri ve birim testi paketi oluşturmak için .NET kodunuzu keşfeder. Hangi testlerin başarısız olduğunu görmek ve bunları düzeltmek için IntelliTest çalıştırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dba46c3b111f82bdb6e03eca5442b2f497e8ad3e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083810"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Nasıl oluşturulur: IntelliTest kullanarak birim testleri oluşturma

IntelliTest, test verileri ve birim testi paketi oluşturmak için .NET kodunuzu keşfeder. Kodda yer alan her deyim için, bu deyimi yürütecek bir test girişi oluşturulur. Kodda her koşullu dal için bir durum analizi gerçekleştirilir. Örneğin `if` deyimler, onaylar ve özel durumlara neden olan tüm işlemler analiz edilir. Bu analiz, yöntemlerinizin her biri için parametreli birim testi için test verileri oluşturmak ve yüksek kod kapsamına sahip birim testleri oluşturmak için kullanılır.

IntelliTest'i çalıştırarak hangi testlerin başarısız olduğunu kolayca görebilir ve bunları düzeltmek için gerekli kodu layabilirsiniz. Regresyon paketi sağlamak için bir test projesine kaydedilen testlerden hangisini seçerek. Kodunuzu değiştirirken, oluşturulan testleri kod değişiklikleriniz ile eşit tutmak için IntelliTest'i yeniden çalıştırabilirsiniz.

## <a name="availability-and-extensions"></a>Kullanılabilirlik ve uzantılar

**IntelliTest Oluştur ve** **IntelliTest Çalıştır** menü komutları:

* Yalnızca Enterprise Sürümü Visual Studio.

* Yalnızca hedefini hedef alan C# .NET Framework.

* [MSTest,](#extend-framework) MSTest V2, NUnit ve xUnit biçiminde test yayma desteği vardır.

* x64 yapılandırmasını desteklemez.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Keşfetme: Kodunuzu keşfetmek ve birim testleri oluşturmak için IntelliTest kullanma

Birim testleri oluşturmak için türlerinizin genel olması gerekir.

1. Çözümlerinizi Visual Studio sonra test etmek istediğiniz yöntemlerin olduğu sınıf dosyasını açın.

2. Yönteminize sağ tıklayın ve Yönteminize kod için birim testleri oluşturmak için **IntelliTest** Çalıştır'ı seçin.

   ![Birim&#45;oluşturmak için yönteminize sağ tıklayın](../test/media/runpex.png)

   IntelliTest kodunuzu birçok kez farklı girişlerle çalıştırır. Her çalıştırma, giriş testi verilerini ve sonuçta elde edilen çıkışı veya özel durumu gösteren tabloda temsil eder.

   ![Testler ile Keşif Sonuçları penceresi görüntülenir](../test/media/pexexplorationresults.png)

Bir sınıftaki tüm genel yöntemler için birim testleri oluşturmak için, belirli bir yöntem yerine sınıfta sağ tıklar ve **ardından IntelliTest Çalıştır'ı seçin.** Sınıftaki her yöntem için birim **testlerini** ve giriş verilerini görüntülemek için Araştırma Sonuçları penceresindeki açılan listeyi kullanın.

![Listeden görüntülemek istediğiniz test sonuçlarını seçin](../test/media/selectpextest.png)

Geçen testler için sonuç sütununda bildirilen sonuçların kodunuzla ilgili beklentilerinize uygun olup olamay olduğunu kontrol edin. Başarısız olan testler için kodunuzu uygun şekilde düzeltin. Ardından IntelliTest'i yeniden çalıştırarak düzeltmeleri doğrular.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Kalıcı: Birim testlerini regresyon paketi olarak kaydetme

1. Parametreli birim testiyle bir test projesine kaydetmek istediğiniz veri satırlarını seçin.

     ![Testleri seçin; sağ&#45;tıklar ve Kaydet'i seçin](../test/media/savepextests.png)

     Test projesini ve oluşturulan parametreli birim testini görüntüebilirsiniz. Satırların her biri için karşılık gelen birim testleri, test projesinde *.g.cs* dosyasına kaydedilir ve parametreli birim testi ilgili *.cs* dosyasına kaydedilir. Birim testlerini çalıştırarak, el ile oluşturduğunuz tüm birim testlerinde olduğu gibi Test Gezgini'nde sonuçları görüntüleyebilirsiniz.

     ![Birim testini görüntülemek için test yönteminde sınıf dosyasını açma](../test/media/testmethodpex.png)

     Gerekli tüm başvurular test projesine de eklenir.

     Yöntem kodu değişirse, birim testlerini değişikliklerle eşit tutmak için IntelliTest'i yeniden çalıştırabilirsiniz.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Yardım: Kod keşfine odaklanmak için IntelliTest kullanma

1. Daha karmaşık bir kodunuz varsa IntelliTest, kodunuzu keşfetmeye odaklanmanıza yardımcı olur. Örneğin, parametre olarak arabirimi olan bir yönteminiz varsa ve bu arabirimi uygulayan birden fazla sınıf varsa IntelliTest bu sınıfları keşfeder ve bir uyarı raporlar.

     Ne yapmak istediğinize karar vermek için uyarıları görüntüleme.

     ![Uyarıları görüntüleme](../test/media/pexviewwarning.png)

2. Kodu araştırarak neleri test etmek istediğinize bakarak uyarıyı düzeltebilir ve arabirimi test etmek için hangi sınıfların kullanıldığını seçebilirsiniz.

     ![Uyarıya&#45;sağ tıklar ve Düzelt'i seçin](../test/media/pexfixwarning.png)

     Bu seçim *PexAssemblyInfo.cs dosyasına* eklenir.

     `[assembly: PexUseType(typeof(Camera))]`

3. Şimdi IntelliTest'i yeniden çalıştırarak yalnızca düzelttikleri sınıfı kullanarak parametreli birim testi ve test verileri oluşturabilirsiniz.

     ![Test verilerini oluşturmak için IntelliTest'i yeniden çalıştırma](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Belirtme: Kodda belirttiğiniz doğruluk özelliklerini doğrulamak için IntelliTest kullanın

Oluşturulan birim testlerinin doğrulamasını istediğiniz girişler ve çıkışlar arasındaki genel ilişkiyi belirtin. Bu belirtim, bir test yöntemi gibi görünen ancak evrensel olarak gruplandı olan bir yöntemde kapsüllemedir. Bu parametreli birim testi yöntemidir ve IntelliTest'in oluştur oluşturamıs tüm olası giriş değerleri için onaylar tutmanız gerekir.

## <a name="q--a"></a>Soru-Cevap

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>S: IntelliTest'i, unmanaged code için kullanabilir misiniz?

**A:** Hayır, IntelliTest yalnızca yönetilen kodla çalışır.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>S: Oluşturulan bir test ne zaman geçer veya başarısız olur?

**A:** Özel durum oluşmazsa diğer birim testleri gibi geçer. Herhangi bir onaylama işlemi başarısız olursa veya test altındaki kod işlanmamış bir özel durum oluşturursa başarısız olur.

Belirli özel durumlar sızıyorsa geçebilirsiniz bir test varsa, test yöntemi, test sınıfı veya derleme düzeyinde gereksinimlerinize bağlı olarak aşağıdaki özniteliklerden birini ayarlayın:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>S: Parametreli birim testinde varsayımlar ekleyebilir miyim?

**A:** Evet, belirli bir yöntem için birim testi için gerekli olan test verilerini belirtmek üzere varsayımları kullanın. Varsayım <xref:Microsoft.Pex.Framework.PexAssume> eklemek için sınıfını kullanın. Örneğin, değişkenin aşağıdaki gibi `lengths` null olmadığının bir varsayımı eklersiniz:

`PexAssume.IsNotNull(lengths);`

Bir varsayım ekler ve IntelliTest'i yeniden çalıştırsanız, artık ilgili olan test verileri kaldırılır.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>S: Parametreli birim testinde onay ekleyebilir miyim?

**A:** Evet, IntelliTest birim testlerini çalıştırırken deyiminize neleri onaylarsanız doğru olup olmadığını kontrol edin. Onay <xref:Microsoft.Pex.Framework.PexAssert> eklemek için test çerçevesiyle birlikte gelen sınıfını veya onay API'sini kullanın. Örneğin, iki değişkenin eşit olduğu bir onay ekleyebilirsiniz.

`PexAssert.AreEqual(a, b);`

Bir onay ekler ve IntelliTest'i yeniden çalıştırmanız durumunda onaylama işleminizin geçerli olup olmadığını kontrol eder ve değilse test başarısız olur.

### <a name="q-can-i-generate-parameterized-unit-tests-without-running-intellitest-first"></a><a name="NoRun"></a> S: Önce IntelliTest çalıştırmadan parametreli birim testleri oluşturmam mümkün mü?

**A:** Evet, sınıfına veya yöntemine sağ tıklayın ve **IntelliTest Oluştur'u seçin.**

![Düzenleyiciye&#45;IntelliTest Oluştur'u seçin](../test/media/pexcreateintellitest.png)

Testlerinizi oluşturmak için varsayılan biçimi kabul etme veya projenizin ve testlerin nasıl adlandırılmış olduğunu değiştirme. Yeni bir test projesi oluşturabilir veya testlerinizi mevcut projeye kaydedebilirsiniz.

![MSTest varsayılanı ile IntelliTest oluşturma](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>S: IntelliTest ile diğer birim testi çerçevelerini kullanabilir miyim?

**A:** Evet, diğer çerçeveleri bulmak [ve yüklemek için bu adımları izleyin.](../test/install-third-party-unit-test-frameworks.md)
Test çerçevesi uzantıları, NUnit Test Oluşturucu Visual Studio [Market'te de kullanılabilir.](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371)

Yeniden başlatarak Visual Studio yeniden açtıktan sonra sınıf veya yönteme sağ tıklayın ve **IntelliTest Oluştur'u seçin.** Yüklü çerçevenizi buradan seçin:

![IntelliTest için diğer birim testi çerçevesini seçme](../test/media/pexcreateintellitestextensions.png)

Ardından, karşılık gelen *.g.cs* dosyalarında tek tek birim testleri oluşturmak için IntelliTest'i çalıştırın.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>S: Testlerin nasıl oluşturularak ilgili daha fazla bilgi edinmek istiyorum?

**A:** Evet, üst düzey bir genel bakış almak için bu [blog gönderilerini okuyun.](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
