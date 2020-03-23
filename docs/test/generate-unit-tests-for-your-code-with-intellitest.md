---
title: IntelliTest ile kodunuz için birim testleri oluşturma
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65b1de58f195b957d080bd21144c22479b1aafed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589597"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Nasıl yapilir: IntelliTest kullanarak birim testleri oluşturma

IntelliTest, test verileri ve bir birim testi paketi oluşturmak için .NET kodunuzu inceler. Koddaki her deyim için, bu deyimi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir servis talebi çözümlemesi gerçekleştirilir. Örneğin, `if` özel durumlar atabilen ifadeler, iddialar ve tüm işlemler çözümlenir. Bu çözümleme, her bir yönteminizin parametreli birim testi için test verileri oluşturmak ve yüksek kod kapsamına sahip birim testleri oluşturmak için kullanılır.

IntelliTest çalıştırdığınızda, hangi testlerin başarısız olduğunu kolayca görebilir ve bunları düzeltmek için gerekli kodları ekleyebilirsiniz. Bir regresyon paketi sağlamak için bir test projesine kaydetmek için oluşturulan testlerden hangisini seçebilirsiniz. Kodunuzu değiştirirken, oluşturulan testleri kod değişikliklerinizle eşit tutmak için IntelliTest'i yeniden çalıştırın.

## <a name="availability-and-extensions"></a>Kullanılabilirlik ve uzantılar

**IntelliTest oluştur** ve Çalıştır **IntelliTest** menü komutları:

* Yalnızca Visual Studio'nun Enterprise Edition'ında mevcuttur.

* .NET Framework'u hedefleyen yalnızca C# kodunu destekleyin.

* MSTest, MSTest V2, NUnit ve xUnit formatında [genişletilebilir](#extend-framework) ve destek yayan testlerdir.

* x64 yapılandırmayı desteklemeyin.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Keşfedin: Kodunuzu keşfetmek ve birim testleri oluşturmak için IntelliTest'i kullanın

Birim testleri oluşturmak için türünüzün herkese açık olması gerekir.

1. Visual Studio'da çözümünüzü açın ve test etmek istediğiniz yöntemlere sahip sınıf dosyasını açın.

2. Bir yönteme sağ tıklayın ve yönteminizdeki kod için birim testleri oluşturmak için **IntelliTest'i Çalıştır'ı** seçin.

   ![Birim testleri oluşturmak için yönteminize sağ&#45;tıklayın](../test/media/runpex.png)

   IntelliTest farklı girişlerle kodunuzu birçok kez çalıştırıyor. Her çalıştırma, giriş testi verilerini ve elde edilen çıktı veya özel durumu gösteren tabloda temsil edilir.

   ![Keşif Sonuçları penceresi testlerle görüntülenir](../test/media/pexexplorationresults.png)

Bir sınıftaki tüm ortak yöntemler için birim testleri oluşturmak için, belirli bir yöntem yerine sınıfa sağ tıklamanız ve ardından **IntelliTest'i Çalıştır'ı**seçmeniz yeterlidir. Birim testlerini ve sınıftaki her yöntemiçin giriş verilerini görüntülemek için **Arama Sonuçları** penceresindeki açılır listeyi kullanın.

![Listeden görüntülemek için test sonuçlarını seçin](../test/media/selectpextest.png)

Geçen testler için, sonuç sütununda bildirilen sonuçların kodunuziçin beklentilerinizle eşleşin. Başarısız olan testler için kodunuzu uygun şekilde düzeltin. Ardından düzeltmeleri doğrulamak için IntelliTest'i yeniden çalıştırın.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Devam: Birim testlerini bir regresyon paketi olarak kaydetme

1. Parametreli birim testi ile kaydetmek istediğiniz veri satırlarını bir test projesine seçin.

     ![Testleri seçin; sağ&#45;tıklayın ve Kaydet'i seçin](../test/media/savepextests.png)

     Test projesini ve oluşturulan parametreli birim testini görüntüleyebilirsiniz - satırların her birine karşılık gelen tek tek birim testleri, test projesindeki *.g.cs* dosyasına kaydedilir ve parametreli birim testi karşılık gelen *.cs* dosyasına kaydedilir. Birim testlerini çalıştırabilir ve test gezgininin sonuçlarını, el ile oluşturduğunuz tüm birim testlerinde olduğu gibi görüntüleyebilirsiniz.

     ![Ünite testini görüntülemek için test yönteminde sınıf dosyasını aç](../test/media/testmethodpex.png)

     Gerekli başvurular da test projesine eklenir.

     Yöntem kodu değişirse, birim testlerini değişikliklerle eşit tutmak için IntelliTest'i yeniden çalıştırın.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Yardımcı: Kod keşfine odaklanmak için IntelliTest'i kullanın

1. Daha karmaşık kodunuz varsa, IntelliTest kodunuzu odaklamada size yardımcı olur. Örneğin, arabirimi parametre olarak olan bir yönteminiz varsa ve bu arabirimi uygulayan birden fazla sınıf varsa, IntelliTest bu sınıfları keşfeder ve bir uyarı bildirir.

     Ne yapmak istediğinize karar vermek için uyarıları görüntüleyin.

     ![Uyarıları görüntüleme](../test/media/pexviewwarning.png)

2. Kodu araştırdıktan ve neyi test etmek istediğinizi anladıktan sonra, arabirimi test etmek için hangi sınıfları kullanacağınızı seçmek için uyarıyı düzeltebilirsiniz.

     ![Sağ&#45;uyarıyı tıklatın ve Düzelt'i seçin](../test/media/pexfixwarning.png)

     Bu seçenek *PexAssemblyInfo.cs* dosyasına eklenir.

     `[assembly: PexUseType(typeof(Camera))]`

3. Artık yalnızca sabitlediğiniz sınıfı kullanarak parametreli birim testi ve test verileri oluşturmak için IntelliTest'i yeniden çalıştırabilirsiniz.

     ![Test verilerini oluşturmak için IntelliTest'i yeniden çalıştırın](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Belirt: Kodda belirttiğiniz doğruluk özelliklerini doğrulamak için IntelliTest'i kullanın

Oluşturulan birim testlerinin doğrulatmasını istediğiniz girişler ve çıktılar arasındaki genel ilişkiyi belirtin. Bu belirtim, bir test yöntemi gibi görünen ancak evrensel olarak ölçülen bir yöntemde kapsüllenir. Bu parametreli birim test yöntemidir ve yaptığınız tüm iddialar IntelliTest'in oluşturabileceği tüm olası giriş değerleri için tutmanız gerekir.

## <a name="q--a"></a>Soru-Cevap

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>S: Yönetilmeyen kod için IntelliTest'i kullanabilir misiniz?

**A:** Hayır, IntelliTest yalnızca yönetilen kodla çalışır.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>S: Oluşturulan bir test ne zaman geçer veya başarısız olur?

**A:** Özel durumlar oluşmazsa, diğer birim testi gibi geçer. Herhangi bir iddia başarısız olursa veya test altındaki kod işlenmemiş bir özel durum atarsa başarısız olur.

Belirli özel durumlar atılırsa geçebilecek bir testiniz varsa, test yöntemi, test sınıfı veya derleme düzeyindeki gereksinimlerinize göre aşağıdaki özniteliklerden birini ayarlayabilirsiniz:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>S: Parametreli birim testine varsayımlar ekleyebilir miyim?

**A:** Evet, belirli bir yöntem için birim testi için hangi test verilerinin gerekli olmadığını belirtmek için varsayımları kullanın. Varsayımlar <xref:Microsoft.Pex.Framework.PexAssume> eklemek için sınıfı kullanın. Örneğin, değişkenin `lengths` şu şekilde null olmadığı varsayımı ekleyebilirsiniz:

`PexAssume.IsNotNull(lengths);`

Bir varsayım ekleyip IntelliTest'i yeniden çalıştırarsanız, artık alakalı olmayan test verileri kaldırılır.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>S: Parametreli birim testine iddialar ekleyebilir miyim?

**A:** Evet, IntelliTest, birim testlerini çalıştırdığında deyiminizde öne sürdüklerinizin doğru olup olmadığını kontrol edecektir. İddiaları <xref:Microsoft.Pex.Framework.PexAssert> eklemek için test çerçevesiile birlikte gelen sınıfı veya iddia API'sını kullanın. Örneğin, iki değişkenin eşit olduğu iddiasını ekleyebilirsiniz.

`PexAssert.AreEqual(a, b);`

Bir iddia ekler ve IntelliTest'i yeniden çalıştırın, bu iddianızın geçerli olup olmadığını ve değilse testin başarısız olduğunu denetler.

### <a name="q-can-i-generate-parameterized-unit-tests-without-running-intellitest-first"></a><a name="NoRun"></a>S: Önce IntelliTest çalıştırmadan parametreli birim testleri oluşturabilir miyim?

**A:** Evet, sınıf veya yöntemsağ tıklayın, sonra **IntelliTest oluştur'u**seçin.

![Sağ&#45;tıklatma düzenleyicisi, IntelliTest oluştur'u seçin](../test/media/pexcreateintellitest.png)

Testlerinizi oluşturmak için varsayılan biçimi kabul edin veya projenizin ve testlerinizin adlarını değiştirin. Yeni bir test projesi oluşturabilir veya testlerinizi varolan bir projeye kaydedebilirsiniz.

![MSTest varsayılanı ile IntelliTest oluşturma](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>S: IntelliTest ile diğer birim test çerçevelerini kullanabilir miyim?

**A:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin.
Test çerçevesi uzantıları da Visual Studio Marketplace mevcuttur, örneğin, [NUnit Test Generator](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Visual Studio'yu yeniden başlattıktan ve çözümünüzü yeniden açtıktan sonra, sınıfa veya yönteme sağ tıklayın ve ardından **IntelliTest Oluştur'u**seçin. Yüklü çerçevenizi buradan seçin:

![IntelliTest için diğer birim test çerçevelerini seçin](../test/media/pexcreateintellitestextensions.png)

Ardından, ilgili *.g.cs* dosyalarında tek tek birim testleri oluşturmak için IntelliTest'i çalıştırın.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>S: Testlerin nasıl oluşturulduğu hakkında daha fazla bilgi edinebilir miyim?

**A:** Evet, üst düzey bir genel bakış elde etmek için, bu [blog yazısı](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)okuyun.
