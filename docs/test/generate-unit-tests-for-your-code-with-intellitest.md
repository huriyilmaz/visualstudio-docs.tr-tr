---
title: IntelliTest ile kodunuz için birim testleri oluşturma
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: cd808e23fbb94259df0805125e7d6f3e27dbaeac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664893"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Nasıl yapılır: IntelliTest kullanarak birim testleri oluşturma

IntelliTest, test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu araştırır. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir olay Analizi gerçekleştirilir. Örneğin, `if` deyimleri, onayları ve özel durum oluşturabilecek tüm işlemler çözümlenir. Bu analiz, metotlarınızın her biri için parametreli birim testi için test verileri oluşturmak üzere kullanılır ve yüksek kod kapsamı ile birim testleri oluşturur.

IntelliTest çalıştırdığınızda, hangi testlerin başarısız olduğunu kolayca görebilir ve bunları onarmak için gerekli kodu ekleyebilirsiniz. Bir gerileme paketi sağlamak için test projesine kaydetmek üzere oluşturulan testlerin hangisi olduğunu seçebilirsiniz. Kodunuzu değiştirirken, oluşturulan testleri kod değişiklikleriyle eşitlenmiş halde tutmak için IntelliTest 'i yeniden çalıştırın.

## <a name="availability-and-extensions"></a>Kullanılabilirlik ve uzantılar

**IntelliTest oluştur** ve **IntelliTest Çalıştır** menü komutları:

* Yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

* Yalnızca C# .NET Framework hedefleyen kodu destekler.

* [Genişletilebilir](#extend-framework) ve Testleri MSTest, MSTest v2, NUnit ve xUnit biçiminde yaymayı destekler.

* X64 yapılandırmasını desteklemez.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Keşfet: kodunuzu araştırmak ve birim testleri oluşturmak için IntelliTest kullanın

Birim testleri oluşturmak için, türleriniz ortak olmalıdır.

1. Çözümünüzü Visual Studio 'da açın ve ardından test etmek istediğiniz yöntemlere sahip sınıf dosyasını açın.

2. Bir yönteme sağ tıklayın ve yöntemdeki kod için birim testleri oluşturmak üzere **IntelliTest Çalıştır** ' ı seçin.

   ![Birim&#45;testleri oluşturmak için yönteminizi sağ tıklatın](../test/media/runpex.png)

   IntelliTest, kodunuzu farklı girişlerle birçok kez çalıştırır. Her çalıştırma, giriş testi verilerini ve sonuçta elde edilen çıktıyı veya özel durumu gösteren tabloda gösterilir.

   ![Araştırma sonuçları penceresi testlerle birlikte görüntülenir](../test/media/pexexplorationresults.png)

Bir sınıftaki tüm ortak yöntemler için birim testleri oluşturmak üzere, belirli bir yöntem yerine sınıfına sağ tıklayıp ardından **IntelliTest Çalıştır**' ı seçin. Sınıf içindeki her yöntemin birim testlerini ve giriş verilerini göstermek için **araştırma sonuçları** penceresindeki açılan listeyi kullanın.

![Listeden görüntülenecek test sonuçlarını seçin](../test/media/selectpextest.png)

Geçen testler için, sonuç sütunundaki rapor sonuçlarının kodunuzun beklentilerinizi eşleşip eşleştiğinden emin olun. Başarısız olan testler için kodunuzu uygun şekilde onarın. Sonra düzeltmeleri doğrulamak için IntelliTest 'i yeniden çalıştırın.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Kalıcı: birim testlerini regresyon paketi olarak kaydetme

1. Parametreli birim testiyle bir test projesine kaydetmek istediğiniz veri satırlarını seçin.

     ![Testleri seçin; sağ&#45;tıklayın ve Kaydet ' i seçin](../test/media/savepextests.png)

     Oluşturulan test projesini ve parametreli birim testini görüntüleyebilirsiniz. her bir satır için karşılık gelen tek birim testleri, Test projesindeki *. g.cs* dosyasında kaydedilir ve parametreli birim testi karşılık gelen öğesine kaydedilir *. CS* dosyası. Birim testlerini çalıştırabilir ve test Gezgini 'nden, el ile oluşturduğunuz tüm birim testlerinde yaptığınız gibi sonuçları görüntüleyebilirsiniz.

     ![Birim testini görüntülemek için test yönteminde sınıf dosyası aç](../test/media/testmethodpex.png)

     Gerekli başvurular da test projesine eklenir.

     Yöntem kodu değişirse, birim testlerini değişikliklerle eşitlenmiş halde tutmak için IntelliTest 'i yeniden çalıştırın.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Yardım: kod Gezginine odaklanmak için IntelliTest kullanma

1. Daha karmaşık kodunuz varsa, IntelliTest kodunuzun odaklanarak araştırmasına yardımcı olur. Örneğin, parametresi olarak bir arabirimi olan bir yönteminiz varsa ve bu arabirimi uygulayan birden fazla sınıf varsa, IntelliTest bu sınıfları bulur ve bir uyarı bildirir.

     Ne yapmak istediğinize karar vermek için uyarıları görüntüleyin.

     ![Uyarıları görüntüle](../test/media/pexviewwarning.png)

2. Kodu araştırdıktan ve test etmek istediğinizi anladıktan sonra, arabirimi test etmek için kullanılacak sınıfları seçmek üzere uyarıyı çözebilirsiniz.

     ![Uyarıya&#45;sağ tıklayın ve düzeltir ' ı seçin.](../test/media/pexfixwarning.png)

     Bu seçim *PexAssemblyInfo.cs* dosyasına eklenir.

     `[assembly: PexUseType(typeof(Camera))]`

3. Artık, düzeltilen sınıfı kullanarak parametreli birim testi ve test verileri oluşturmak için IntelliTest 'i yeniden çalıştırabilirsiniz.

     ![Test verilerini oluşturmak için IntelliTest 'i yeniden çalıştırın](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Belirtin: kodda belirttiğiniz doğruluk özelliklerini doğrulamak için IntelliTest kullanın

Oluşturulan birim testlerinin doğrulamak istediğiniz girişler ve çıktılar arasındaki genel ilişkiyi belirtin. Bu belirtim, bir test yöntemi gibi görünen ancak evrensel olarak oluşan bir yöntemde kapsüllenir. Bu parametreli birim testi yöntemidir ve tüm Onaylamalar IntelliTest 'in oluşturabileceği tüm olası giriş değerleri için tutmalıdır.

## <a name="q--a"></a>soru-cevap &

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>S: yönetilmeyen kod için IntelliTest kullanabilir miyim?

Y **:** Hayır, IntelliTest yalnızca yönetilen kodla birlikte kullanılabilir.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>S: oluşturulan bir test başarılı veya başarısız olduğunda?

Y **:** Özel durum oluşursa diğer birim testleri gibi geçirir. Herhangi bir onaylama başarısız olursa veya test altındaki kod işlenmeyen bir özel durum oluşturursa başarısız olur.

Belirli özel durumlar oluşursa geçebilmeniz gereken bir testiniz varsa, test yöntemi, test sınıfı veya derleme düzeyi ' nde gereksinimlerinize göre aşağıdaki özniteliklerden birini ayarlayabilirsiniz:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>S: parametreli birim testine varsayımlar ekleyebilir miyim?

Y **:** Evet, belirli bir yöntem için birim testi için gerekli olmayan test verilerini belirtmek için varsayımlar kullanın. Varsayımlar eklemek için <xref:Microsoft.Pex.Framework.PexAssume> sınıfını kullanın. Örneğin, `lengths` değişkeninin şu şekilde null olmadığı varsayımını ekleyebilirsiniz:

`PexAssume.IsNotNull(lengths);`

Bir varsayım ekler ve IntelliTest 'i yeniden çalıştırırsanız, artık alakalı olmayan test verileri kaldırılır.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>S: parametreli birim testine onaylama ekleyebilir miyim?

Y **:** Evet, IntelliTest, birim testlerini çalıştırdığında deyiminizde neleri bulduhangilerinin gerçekten doğru olduğunu denetlemekte. Onaylama eklemek için test çerçevesiyle birlikte gelen <xref:Microsoft.Pex.Framework.PexAssert> sınıfını veya onaylama API 'sini kullanın. Örneğin, iki değişkenin eşit olduğu bir onaylama ekleyebilirsiniz.

`PexAssert.AreEqual(a, b);`

Bir onaylama ekler ve IntelliTest 'i yeniden çalıştırırsanız, onayınızın geçerli olduğunu ve testin başarısız olup olmadığını kontrol eder.

### <a name="NoRun"></a>S: önce IntelliTest çalıştırmadan parametreli birim testleri oluşturabilir miyim?

Y **:** Evet, sınıfa veya yöntemine sağ tıklayıp **IntelliTest oluştur**' u seçin.

![Düzenleyiciyi&#45;sağ tıklatın, IntelliTest oluştur ' u seçin.](../test/media/pexcreateintellitest.png)

Testlerinizi oluşturmak için varsayılan biçimi kabul edin veya projenizin ve testlerinizin adlandırıldığını değiştirin. Yeni bir test projesi oluşturabilir veya testlerinizi var olan bir projeye kaydedebilirsiniz.

![MSTest varsayılana sahip IntelliTest oluşturma](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>S: diğer birim test çerçevelerini IntelliTest ile kullanabilir miyim?

Y **:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin.
Test çerçevesi uzantıları Visual Studio Market de mevcuttur, örneğin [NUnit test Oluşturucu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Visual Studio 'Yu yeniden başlattıktan sonra çözümünüzü yeniden açtıktan sonra, sınıfı veya yöntemine sağ tıklayıp **IntelliTest oluştur**' u seçin. Yüklü çatısını buradan seçin:

![IntelliTest için diğer birim test çerçevesini seçin](../test/media/pexcreateintellitestextensions.png)

Ardından, ilgili *. g.cs* dosyalarında ayrı birim testleri oluşturmak Için IntelliTest çalıştırın.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>S: testlerin nasıl oluşturulduğu hakkında daha fazla bilgi alabilir miyim?

Y **:** Evet, üst düzey bir genel bakış edinmek için bu [blog gönderisini](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)okuyun.
