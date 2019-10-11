---
title: Intellitest ile kodunuz için birim testleri oluşturma
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1d3a86d9ef5823b5935ad99facd6a82bf3af9789
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018933"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Nasıl yapılır: IntelliTest kullanarak birim testleri oluşturma

Intellitest, test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu keşfeden. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Koddaki her koşullu şube için bir vaka analizi yapılır. Örneğin, `if` deyimleri, onaylamalar ve özel durumlar oluşturabilecek tüm işlemler analiz edilir. Bu analiz, yüksek kod kapsamı ile birim testleri oluşturma, yöntemlerinizin her biri için parametreleştirilmiş birim testi için test verilerini oluşturmak için kullanılır.

Intellitest çalıştırdığınızda, hangi testlerin başarısız oluyor ve onları düzeltmek için tüm gerekli kodu eklemek kolayca görebilirsiniz. Hangi testlerin bir regresyon paketi sağlamak için bir test projesine kaydetmek için seçebilirsiniz. Kodunuzu değiştikçe, üretilen testler, kod değişikliğine eşitlenmiş şekilde tutmanızı sağlayacak Intellitest yeniden çalıştırın.

## <a name="availability-and-extensions"></a>Kullanılabilirlik ve uzantıları

**Intellitest oluşturma** ve **Intellitest Çalıştır** menü komutları:

* Yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

* .NET Framework'ü hedefleyen yalnızca C# kodunu destekler.

* [Genişletilebilir](#extend-framework) ve Testleri MSTest, MSTest v2, NUnit ve xUnit biçiminde yaymayı destekler.

* X64 desteklemeyen yapılandırma.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Explorer Kodunuzu araştırmak ve birim testleri oluşturmak için IntelliTest kullanın

Birim testler üretmek için türler genel olmalıdır.

1. Çözümünüzü Visual Studio 'da açın ve ardından test etmek istediğiniz yöntemlere sahip sınıf dosyasını açın.

2. Bir yönteme sağ tıklayın ve yöntemdeki kod için birim testleri oluşturmak üzere **IntelliTest Çalıştır** ' ı seçin.

   ![Sağ&#45;Birim testler üretmek için yönteminizi tıklayın](../test/media/runpex.png)

   Intellitest kodunuz, farklı giriş ile birden çok kez çalışır. Her bir çalıştırmanın giriş test verileri ve elde edilen çıkış gösteren tablo ya da özel durum gösterilir.

   ![Testlerle araştırma sonuçları penceresi görüntülenir.](../test/media/pexexplorationresults.png)

Bir sınıftaki tüm ortak yöntemler için birim testleri oluşturmak üzere, belirli bir yöntem yerine sınıfına sağ tıklayıp ardından **IntelliTest Çalıştır**' ı seçin. Aşağı açılan listeden kullanmak **araştırma sonuçları** penceresi sınıfında birim testleri ve her yöntem için giriş verilerini görüntülemek için.

![Listeden görüntülemek için test sonuçlarını seçin](../test/media/selectpextest.png)

Geçmek için kontrol testler için bildirilen sonuçları Sonuç sütunundaki kodunuz için beklentilerinizi. Başarısız testler için kodunuzu uygun şekilde düzeltin. Ardından düzeltmeler doğrulamak için Intellitest yeniden çalıştırın.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Durumunda Birim testlerini regresyon paketi olarak kaydetme

1. Parametreli birim test projesine kaydetmek istediğiniz veri satırları seçin.

     ![Testleri seçin. doğru&#45;tıklayın ve Kaydet'i seçin](../test/media/savepextests.png)

     Test projesini görüntüleyebilir ve oluşturuldu - parametreli birim testi tek tek birim testleri, her satır için karşılık gelen kaydedilir *. g.cs* test projesini ve parametreli birim testi dosyası içine kaydedildi kendi ilişkili *.cs* dosya. Birim testlerini çalıştırmak ve el ile oluşturduğunuz herhangi bir birim test için yaptığınız gibi Test Explorer sonuçları görüntüleyin.

     ![Sınıf dosyasında birim testi görüntülemek için test yöntemi](../test/media/testmethodpex.png)

     Gerekli tüm başvuruları da test projesine eklenir.

     Yöntem kodunu değişirse birim testlerini değişiklikleri ile eşitlenmiş tutmak için Intellitest yeniden çalıştırın.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Larınıza Kod Gezginine odaklanmak için IntelliTest kullanın

1. Daha karmaşık bir kod varsa, Intellitest araştırma, kodunuzun odaklanarak ile yardımcı olur. Örneğin, bir parametre olarak arabirime sahip bir yöntemi varsa ve bu arabirimi uygulayan birden fazla sınıf, Intellitest söz konusu sınıfın bulur ve bir uyarı bildirir.

     Yapmak istediğinize karar verirken uyarıları görüntüleyin.

     ![Uyarıları görüntüle](../test/media/pexviewwarning.png)

2. Kodu inceleme ve test etmek istediğiniz anlamak sonra arabirimi sınamak üzere kullanmak için hangi sınıfların seçmek için uyarı düzeltebilirsiniz.

     ![Sağ&#45;uyarıya tıklayarak ve düzeltme seçin](../test/media/pexfixwarning.png)

     Bu seçenek eklenir *PexAssemblyInfo.cs* dosya.

     `[assembly: PexUseType(typeof(Camera))]`

3. Artık bir parametreli birim testi oluşturma ve verileri yalnızca, sabit sınıfı kullanarak test etmek için Intellitest yeniden çalıştırabilirsiniz.

     ![Intellitest test verileri oluşturmak için yeniden çalıştırın](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Belirtir Kodda belirttiğiniz doğruluk özelliklerini doğrulamak için IntelliTest kullanın

Giriş ve çıkışları doğrulamak için üretilmiş birim testlerini istediğiniz genel ilişkisi belirtin. Bu belirtim, bir test yöntemi gibi görünüyor, ancak Evrensel amaçlarıyla bir yöntem içinde kapsüllenir. Parametreli birim test yöntem budur ve yaptığınız herhangi bir onayları Intellitest oluşturabilen olası tüm giriş değerlerini tutmanız gerekir.

## <a name="q--a"></a>Soru - Yanıt

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Ç Yönetilmeyen kod için IntelliTest 'i kullanabilir miyim?

**A** Hayır, IntelliTest yalnızca yönetilen kodla birlikte kullanılabilir.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Ç Oluşturulan bir test ne zaman geçer veya başarısız olur?

**A** Özel durum oluşursa diğer birim testleri gibi geçirir. Herhangi bir onaylama işlemi başarısız olursa veya test edilen kod işlenmemiş bir özel durum oluşturursa başarısız olur.

Özel bazı durumlar oluşursa, geçirilebilecek bir test varsa, test yöntemi, test sınıfına veya derleme gereksinimlerinize göre aşağıdaki özniteliklerden birini düzeyi ayarlayabilirsiniz:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Ç Parametreli birim testine varsayımlar ekleyebilir miyim?

**A** Evet, belirli bir yöntem için birim testi için gerekli olmayan test verilerini belirtmek için varsayımlar kullanın. Kullanım <xref:Microsoft.Pex.Framework.PexAssume> varsayımlar eklemek için sınıfı. Örneğin, `lengths` değişkeninin şu şekilde null olmadığı varsayımını ekleyebilirsiniz:

`PexAssume.IsNotNull(lengths);`

Bir varsayım ekleyip Intellitest yeniden yitirmesi test verileri kaldırılır.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Ç Parametreli birim testine onaylama ekleyebilir miyim?

**A** Evet, IntelliTest, birim testlerini çalıştırdığında deyiminizde neleri bulduhangilerinin gerçekten doğru olduğunu denetlemekte. Kullanım <xref:Microsoft.Pex.Framework.PexAssert> sınıfı veya onaylama Onaylamalar eklemek için test framework ile birlikte gelen API. Örneğin, iki değişken eşit olduğunu onaylama ekleyebilirsiniz.

`PexAssert.AreEqual(a, b);`

Bir onaylama ekler ve IntelliTest 'i yeniden çalıştırırsanız, onayınızın geçerli olduğunu ve testin başarısız olup olmadığını kontrol eder.

### <a name="NoRun"></a>Ç Önce IntelliTest çalıştırmadan parametreli birim testleri oluşturabilir miyim?

**A** Evet, sınıfa veya yöntemine sağ tıklayıp **IntelliTest oluştur**' u seçin.

![Sağ&#45;Düzenleyicisi, Intellitest oluşturma seçin](../test/media/pexcreateintellitest.png)

Testleriniz oluşturulmaya veya projenizin ve testleri nasıl adlandırıldığı değiştirmek için varsayılan biçimi kabul edin. Yeni bir test projesi oluşturun veya var olan bir projeye testlerinizi kaydedin.

![Intellitest MSTest varsayılan oluşturun](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Ç IntelliTest ile diğer birim test çerçevelerini kullanabilir miyim?

**A** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin.
Test çerçevesi uzantıları Visual Studio Market de mevcuttur, örneğin [NUnit test Oluşturucu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Visual Studio'yu yeniden başlatın ve çözümünüzü yeniden sonra sınıf veya yöntemi içinde sağ tıklayın ve ardından seçin **Intellitest oluşturma**. Burada yüklü Çerçevenizi seçin:

![Diğer birim testi çerçevesi için Intellitest seçin](../test/media/pexcreateintellitestextensions.png)

Ardından, ilgili tek tek birim testleri oluşturmak için Intellitest Çalıştır *. g.cs* dosyaları.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Ç Testlerin nasıl oluşturulduğu hakkında daha fazla bilgi alabilir miyim?

**A** Evet, üst düzey bir genel bakış edinmek için bu [blog gönderisini](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)okuyun.
