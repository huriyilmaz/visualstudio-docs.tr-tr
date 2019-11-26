---
title: IntelliTest ile kodunuz için birim testleri oluşturun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.assetid: cd9ff940-e948-4d28-a72c-b291ef5c1e90
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f03490fc7ea3513a006254e3931cc1113f3bc159
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302591"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Intellitest ile kodunuz için birim testleri oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Intellitest, test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu keşfeden. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Koddaki her koşullu şube için bir vaka analizi yapılır. Örneğin, deyimler, Onaylamalar ve özel durum oluşturabilecek tüm işlemler çözümlenmekte. Bu analiz, yüksek kod kapsamı ile birim testleri oluşturma, yöntemlerinizin her biri için parametreleştirilmiş birim testi için test verilerini oluşturmak için kullanılır.

 Intellitest çalıştırdığınızda, hangi testlerin başarısız oluyor ve onları düzeltmek için tüm gerekli kodu eklemek kolayca görebilirsiniz. Hangi testlerin bir regresyon paketi sağlamak için bir test projesine kaydetmek için seçebilirsiniz. Kodunuzu değiştikçe, üretilen testler, kod değişikliğine eşitlenmiş şekilde tutmanızı sağlayacak Intellitest yeniden çalıştırın.

 IntelliTest yalnızca için C# kullanılabilir ve x64 yapılandırmasını desteklemez.

## <a name="get-started-with-intellitest"></a>IntelliTest ile çalışmaya başlama
 Visual Studio Enterprise gerekir.

### <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Keşfedin: kullanım Intellitest kodunuzu keşfetmek ve Birim testler üretmek
 Birim testler üretmek için türler genel olmalıdır. Aksi takdirde, önce [birim testlerini](#NoRun) oluşturmadan önce oluşturun.

1. Çözümünüzü Visual Studio'da açın. Ardından test etmek istediğiniz yöntemi içeren sınıf dosyasını açın.

2. Kodunuzda bir yönteme sağ tıklayın ve yöntemdeki kod için birim testleri oluşturmak üzere **IntelliTest Çalıştır** ' ı seçin.

     ![Birim&#45;testleri oluşturmak için yönteminizi sağ tıklatın](../test/media/runpex.png "RunPEX")

     Intellitest kodunuz, farklı giriş ile birden çok kez çalışır. Her bir çalıştırmanın giriş test verileri ve elde edilen çıkış gösteren tablo ya da özel durum gösterilir.

     ![Araştırma sonuçları penceresi testlerle birlikte görüntülenir](../test/media/pexexplorationresults.png "Pexaraştırması Ationresults")

     Bir sınıfta tüm genel metotlar için birim testleri üretmek için yalnızca belirli bir yöntem yerine sınıfı sağ tıklayın. Sonra **IntelliTest Çalıştır**' ı seçin. Sınıf içindeki her yöntemin birim testlerini ve giriş verilerini göstermek için araştırma sonuçları penceresindeki açılan listeyi kullanın.

     ![Listeden görüntülenecek test sonuçlarını seçin](../test/media/selectpextest.png "SelectPEXTest")

     Geçmek için kontrol testler için bildirilen sonuçları Sonuç sütunundaki kodunuz için beklentilerinizi. Başarısız testler için kodunuzu uygun şekilde düzeltin. Ardından düzeltmeler doğrulamak için Intellitest yeniden çalıştırın.

### <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Kalıcı: birim testlerini bir regresyon paketi Kaydet

1. Parametreli birim test projesine kaydetmek istediğiniz veri satırları seçin.

     ![Testleri seçin; sağ&#45;tıklayın ve Kaydet ' i seçin](../test/media/savepextests.png "SavePEXTests")

     Oluşturulan test projesini ve parametreli birim testini görüntüleyebilirsiniz. her satıra karşılık gelen tek birim testleri, Test projesindeki. g.cs dosyasında kaydedilir ve parametreli birim testi karşılık gelen. cs dosyasına kaydedilir. Birim testlerini çalıştırmak ve el ile oluşturduğunuz herhangi bir birim test için yaptığınız gibi Test Explorer sonuçları görüntüleyin.

     ![Birim testini görüntülemek için test yönteminde sınıf dosyası aç](../test/media/testmethodpex.png "TestMethodPEX")

     Gerekli tüm başvuruları da test projesine eklenir.

     Yöntem kodunu değişirse birim testlerini değişiklikleri ile eşitlenmiş tutmak için Intellitest yeniden çalıştırın.

### <a name="assist-use-intellitest-to-focus-code-exploration"></a>Yardımcı: Odağı kod araştırma kullanım Intellitest

1. Daha karmaşık bir kod varsa, Intellitest araştırma, kodunuzun odaklanarak ile yardımcı olur. Örneğin, bir parametre olarak arabirime sahip bir yöntemi varsa ve bu arabirimi uygulayan birden fazla sınıf, Intellitest söz konusu sınıfın bulur ve bir uyarı bildirir.

     Yapmak istediğinize karar verirken uyarıları görüntüleyin.

     ![Uyarıları görüntüle](../test/media/pexviewwarning.png "PEXViewWarning")

2. Kodu inceleme ve test etmek istediğiniz anlamak sonra arabirimi sınamak üzere kullanmak için hangi sınıfların seçmek için uyarı düzeltebilirsiniz.

     ![Uyarıya&#45;sağ tıklayın ve düzeltir ' ı seçin.](../test/media/pexfixwarning.png "PEXFixWarning")

     Bu seçim PexAssemblyInfo.cs dosyasına eklenir.

     `[assembly: PexUseType(typeof(Camera))]`

3. Artık bir parametreli birim testi oluşturma ve verileri yalnızca, sabit sınıfı kullanarak test etmek için Intellitest yeniden çalıştırabilirsiniz.

     ![Test verilerini oluşturmak için IntelliTest 'i yeniden çalıştırın](../test/media/pexwarningsfixed.png "PEXWarningsFixed")

### <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Belirtin: kullanım Intellitest kodda belirten doğruluk özellikleri doğrulamak
 Giriş ve çıkışları doğrulamak için üretilmiş birim testlerini istediğiniz genel ilişkisi belirtin. Bu belirtim, bir test yöntemi gibi görünüyor, ancak Evrensel amaçlarıyla bir yöntem içinde kapsüllenir. Parametreli birim test yöntem budur ve yaptığınız herhangi bir onayları Intellitest oluşturabilen olası tüm giriş değerlerini tutmanız gerekir.

## <a name="QandALink"></a>soru-cevap &

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Intellitest yönetilmeyen kod için kullanabilir miyim?
 Y **:** Hayır, IntelliTest yalnızca yönetilen kodla birlikte kullanılabilir.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>S: ne zaman oluşturulan bir test geçti başarısız veya?
 Y **:** Özel durum oluşursa diğer birim testleri gibi geçirir. Herhangi bir onaylama işlemi başarısız olursa veya test edilen kod işlenmemiş bir özel durum oluşturursa başarısız olur.

 Özel bazı durumlar oluşursa, geçirilebilecek bir test varsa, test yöntemi, test sınıfına veya derleme gereksinimlerinize göre aşağıdaki özniteliklerden birini düzeyi ayarlayabilirsiniz:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Parametreli birim testine varsayımlar ekleyebilir miyim?
 Y **:** Evet, belirli bir yöntem için birim testi için gerekli olmayan test verilerini belirtmek için varsayımlar kullanın. Varsayımlar eklemek için <xref:Microsoft.Pex.Framework.PexAssume> sınıfını kullanın. Örneğin, bir varsayım uzunluk değişkeni şu şekilde null olmadığından ekleyebilirsiniz.

 `PexAssume.IsNotNull(lengths);`

 Bir varsayım ekleyip Intellitest yeniden yitirmesi test verileri kaldırılır.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Parametreli birim testine onaylar ekleyebilir miyim?
 Y **:** Evet, IntelliTest, birim testlerini çalıştırdığında deyiminizde neleri bulduhangilerinin gerçekten doğru olduğunu denetlemekte. Onaylama eklemek için test çerçevesiyle birlikte gelen <xref:Microsoft.Pex.Framework.PexAssert> sınıfını veya onaylama API 'sini kullanın. Örneğin, iki değişken eşit olduğunu onaylama ekleyebilirsiniz.

 `PexAssert.AreEqual(a, b);`

 Onaylama Ekle ve Intellitest yeniden çalıştırın, değerinizi geçerli olduğunu ve yüklü değilse test başarısız olduğunu denetler.

### <a name="NoRun"></a>S: önce IntelliTest çalıştırmadan parametreli birim testleri oluşturabilir miyim?
 Y **:** Evet, sınıfa veya yöntemine sağ tıklayıp **IntelliTest oluştur**' u seçin.

 ![Düzenleyiciyi&#45;sağ tıklatın, IntelliTest oluştur ' u seçin.](../test/media/pexcreateintellitest.png "Pexcreateıntellitest")

 Testleriniz oluşturulmaya veya projenizin ve testleri nasıl adlandırıldığı değiştirmek için varsayılan biçimi kabul edin. Yeni bir test projesi oluşturun veya var olan bir projeye testlerinizi kaydedin.

 ![MSTest varsayılana sahip IntelliTest oluşturma](../test/media/pexcreateintellitestmstest.png "Pexcreateıntellitestmstest")

### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Intellitest ile diğer birim testi çerçeveleri kullanabilir miyim?
 Y **:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin. Visual Studio 'Yu yeniden başlattıktan sonra çözümünüzü yeniden açtıktan sonra, sınıfı veya yöntemine sağ tıklayıp **IntelliTest oluştur**' u seçin. Burada yüklü Çerçevenizi seçin:

 ![IntelliTest için diğer birim test çerçevesini seçin](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")

 Ardından, ilgili. g.cs dosyalarında ayrı birim testleri oluşturmak için IntelliTest çalıştırın.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Testleri nasıl oluşturulacağını hakkında daha fazla bilgi miyim?
 Y **:** Evet, üst düzey bir genel bakış edinmek için bu [blog gönderisini](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)okuyun.
