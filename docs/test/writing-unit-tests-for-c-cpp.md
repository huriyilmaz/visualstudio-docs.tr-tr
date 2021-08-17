---
title: C/C++ için birim testleri yazma
description: CTest, Boost.Test ve Visual Studio test çerçevelerini kullanarak C++ birim testlerini Google Test.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 254d3462403018d1110bedcd2a75cb0d5e6fbc978f9a7ee969d6fc7b7332531e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226681"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio'de C/C++ için birim testleri yazma

Test Gezgini penceresini kullanarak C++ birim testlerinizi yazabilir **ve çalıştırabilirsiniz.** Diğer dillerde olduğu gibi çalışır. Test Gezgini'ni kullanma hakkında **daha fazla bilgi için** [bkz. Test Gezgini ile birim testleri çalıştırma.](run-unit-tests-with-test-explorer.md)

> [!NOTE]
> Live Unit Testing, Kodlanmış UI Testleri ve IntelliTest gibi bazı özellikler C++ için desteklenmiyor.

Visual Studio indirmeye gerek yoktur ve bu C++ test çerçevelerini içerir:

- C++ için Microsoft Birim Testi Çerçevesi
- Google Test
- Boost.Test
- CTest

Yüklü çerçeveleri kullanmanın yanı sıra, kendi test bağdaştırıcınızı kendi test bağdaştırıcınızı da kendi içinde kullanmak Visual Studio. Test bağdaştırıcısı, birim testlerini Test Gezgini **penceresiyle** tümleştirebilirsiniz. Market'te çeşitli üçüncü taraf [bağdaştırıcılar Visual Studio kullanılabilir.](https://marketplace.visualstudio.com) Daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme.](install-third-party-unit-test-frameworks.md)

**Visual Studio 2017 ve sonrası (Professional ve Enterprise)**

C++ birim testi projeleri [CodeLens'i destekler.](../ide/find-code-changes-and-other-history-with-codelens.md)

**Visual Studio 2017 ve sonraki sürümler (tüm sürümler)**

- **Google Test Bağdaştırıcısı,** C++ iş yüküyle **Masaüstü geliştirmenin varsayılan bileşeni olarak** dahil edilir. Bir çözüme ek olarak ekleyebilirsiniz bir proje şablonuna sahip. Yeni **Ekle seçeneğini Project** eklemek için yeni düğümdeki çözüm düğümünde **Çözüm Gezgini** tıklayın. Ayrıca Araçlar Seçenekleri aracılığıyla yapılandırabilirsiniz seçenekleri  >  **vardır.** Daha fazla bilgi için [bkz. Nasıl Google Test: Visual Studio.](how-to-use-google-test-for-cpp.md)

- **Boost.Test,** C++ iş yüküyle Masaüstü **geliştirmenin varsayılan bir bileşeni olarak** dahil edilir. Test Gezgini ile **tümleştirilmiştir,** ancak şu anda bir proje şablonuna sahip değildir. El ile yapılandırılması gerekir. Daha fazla bilgi için [bkz. How to: Use Boost.Test in Visual Studio](how-to-use-boost-test-for-cpp.md).

- **CTest** desteği, C++ iş yüküyle Masaüstü geliştirmenin bir parçası olan **C++ CMake** **araçları bileşenine** dahildir. Daha fazla bilgi için, [bkz. How to: Use CTest in Visual Studio.](how-to-use-ctest-for-cpp.md)

**Visual Studio 2015 ve önceki sürümler**

Google Test Market'Google Test Boost.Test Bağdaştırıcısı uzantılarını Visual Studio indirebilirsiniz. Bunları, için [Boost.Test ve](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) Test bağdaştırıcısı [için Test bağdaştırıcısı'nda Google Test.](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde C++ birim testiyle çalışmaya başlamaya başlamanın temel adımları yer alıyor. Temel yapılandırma hem Microsoft hem de Google Test benzerdir. Boost.Test için el ile bir test projesi oluşturmanız gerekir.

::: moniker range=">=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019'da test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlar ve çalıştırın. Projeleri test etmek istediğiniz kodla aynı çözümde oluşturabilirsiniz. Mevcut bir çözüme yeni bir test projesi eklemek için, 'de Çözüm düğümüne sağ **Çözüm Gezgini.** Açılır menüde Yeni Ekle'yi **seçin**  >  **ve Project.** **Dil'i** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki çizimde **C++** ile Masaüstü Geliştirme ve **UWP** Geliştirme iş yükü yüklü olduğunda kullanılabilen test projeleri gösterilmiştir:

![VIsual Studio 2019'da C++ Test Projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017'de test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlar ve çalıştırın. Projeleri test etmek istediğiniz kodla aynı çözümde oluşturabilirsiniz. Yeni bir test projesi eklemek için, projedeki Çözüm düğümüne sağ **tıklayın ve Çözüm Gezgini** Ekle'yi **Project.**  >   Sol bölmede Test 'i **Visual C++ seçin.** Ardından orta bölmeden proje türlerinden birini seçin. Aşağıdaki **çizimde, C++** ile Masaüstü Geliştirme iş yükü yüklü olduğunda kullanılabilen test projeleri gösterilmiştir:

![C++ Test Projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvuru oluşturma

Test altındaki projedeki işlevlere erişimi etkinleştirmek için test projenize bir başvuru ekleyin. Açılan menü için Çözüm Gezgini **proje** düğümüne sağ tıklayın. Başvuru **Ekle'yi**  >  **seçin.** Başvuru Ekle iletişim kutusunda test etmek istediğiniz projeleri seçin.

![Başvuru ekleme](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu test etmek istediğiniz işlevleri dışarı aktaramazsa, test projesinin bağımlılıklarına .obj veya .lib çıktısı dosyalarını ekebilirsiniz. Daha fazla bilgi için [bkz. Testleri nesne veya kitaplık dosyalarına bağlama.](how-to-use-microsoft-test-framework-for-cpp.md#object_files)

### <a name="add-include-directives-for-header-files"></a>Üst #include için yeni yönergeler ekleme

Ardından, birim testi *.cpp dosyanıza,* test etmek istediğiniz türleri ve işlevleri bildiren tüm üst bilgi `#include` dosyaları için bir yönerge ekleyin. Yazın, `#include "` ardından IntelliSense, seçmenize yardımcı olmak için etkinleştirecek. Ek üst bilgiler için tekrarlayın.

![IntelliSense'Çözüm Gezgini üst #include vurgulayan bir #include yönergesi ekleniyor ifadesini gösteren ekran görüntüsü.](media/cpp-add-includes-test-project.png)

Kaynak dosyada her bir include deyimine tam yol yazmamak için, gerekli klasörleri Project Özellikler C/C++ Genel Ek Ekleme  >    >    >    >  **Dizinleri'ne ebilirsiniz.**

### <a name="write-test-methods"></a>Test yöntemleri yazma

> [!NOTE]
> Bu bölümde C/C++ için Microsoft Birim Testi Çerçevesi'nin söz dizimi yer almaktadır. Burada belgelenmiş: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API başvurusu.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) Daha Google Test için bkz. [Google Test.](https://github.com/google/googletest/blob/master/docs/primer.md) Boost.Test için [bkz. Boost Test kitaplığı: Birim testi çerçevesi.](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html)

Test *projenizin .cpp* dosyasında sizin için tanımlanmış bir saplama sınıfı ve yöntemi vardır. Test kodu yazma örneği gösterir. İmzalar, TEST_CLASS ve TEST_METHOD test gezgini penceresinden keşfedilebilir hale gelen **makroları** kullanır.

![TEST_CLASS ve TEST_METHOD makrolarını kullanarak saplama sınıfı ve yöntemi içeren unittest1.cpp kod dosyasını gösteren Test Gezgini penceresinin ekran görüntüsü.](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD, Microsoft Yerel Test [Çerçevesi'nin bir parçası.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) **Test Gezgini,** desteklenen diğer çerçevelerde test yöntemlerini benzer şekilde keşfeder.

Bir TEST_METHOD void döndürür. Bir test sonucu üretmek için sınıfındaki statik yöntemleri kullanarak `Assert` gerçek sonuçları beklenen sonuçlara göre test etmek için kullanın. Aşağıdaki örnekte, bir `MyClass` alan bir oluşturucusu olduğunu varsayalım. `std::string` Oluşturucus un sınıfı beklendiği gibi başlatarak şu şekilde test olabiliriz:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, çağrının sonucu testin `Assert::AreEqual` başarılı olup olmadığını belirler. Assert sınıfı, beklenen sonuçları ve gerçek sonuçları karşılaştırmak için birçok farklı yöntem içerir.

Test *sahiplerini, önceliğini* ve diğer bilgileri belirtmek için test yöntemlerine nitelikler ebilirsiniz. Daha sonra Test Gezgini'nde testleri sıralamak ve grup etmek için bu **değerleri kullanabilirsiniz.** Daha fazla bilgi için [bkz. Test Gezgini ile birim testleri çalıştırma.](run-unit-tests-with-test-explorer.md)

### <a name="run-the-tests"></a>Testleri çalıştırma

1. Test menüsünde **Test** **Gezgini'Windows**  >  **seçin.** Aşağıdaki çizimde, testleri henüz çalıştırmamış olan bir test projesi gösterilmiştir.

   ![Testleri çalıştırmadan önce Test Gezgini](media/cpp-test-explorer.png)

   > [!NOTE]
   > Test Gezgini ile CTest **tümleştirmesi** henüz kullanılamıyor. CMake ana menüsünden CTest testlerini çalıştırın.

1. Tüm testlerinizi pencerede görünmüyorsa, projedeki düğümüne sağ tıklar ve Derleme veya Yeniden Derleme'yi **Çözüm Gezgini** **projesini** **derleme.**

1. **Test Gezgini'nde,** **Tüm Testleri** Çalıştır'ı seçin veya çalıştırmak istediğiniz testleri seçin. Diğer seçenekler için bir teste sağ tıklayın ve kesme noktaları etkin hata ayıklama modunda çalıştırmayı da içerir. Tüm testleri çalıştırdıktan sonra, pencerede hangi testlerin başarılı olduğu ve hangilerinin başarısız olduğu gösterilir:

![Testler çalıştır çalıştırktan sonra Test Gezgini](media/cpp-test-explorer-passed.png)

Başarısız testler için ileti, nedeni tanılamaya yardımcı olan ayrıntılar sunar. Açılan menü için başarısız olan teste sağ tıklayın. Hatanın **meydana geldiği işlevde** adım adım ilerlerken Seçili Testlerde Hata Ayıkla'ya seçin.

Test Gezgini'ni kullanma hakkında **daha fazla bilgi için** [bkz. Test Gezgini ile birim testleri çalıştırma.](run-unit-tests-with-test-explorer.md)

Birim testiyle ilgili daha fazla bilgi için [bkz. Birim testi temelleri](unit-test-basics.md)

## <a name="use-codelens"></a>CodeLens kullanma

**Visual Studio 2017 ve sonraki sürümler (Professional ve Enterprise sürümleri)**

[CodeLens,](../ide/find-code-changes-and-other-history-with-codelens.md) kod düzenleyicisinden ayrılmadan birim testinin durumunu hızla görmenizi sağlar.

C++ birim testi projesi için CodeLens'i şu yöntemlerden birini kullanarak başlatabilirsiniz:

- Test projenizi veya çözümlerinizi düzenleyin ve derleme.
- Projenizi veya çözümlerinizi yeniden oluşturma.
- Test Gezgini **penceresinden testleri** çalıştırın.

Başlatıldıktan sonra, her birim testinin üzerinde test durumu simgelerini görebilirsiniz.

![C++ CodeLens Simgeleri](media/cpp-test-codelens-icons.png)

Daha fazla bilgi için simgeye tıklayın veya birim testini çalıştırmak veya hata ayıklamak için:

![C++ CodeLens Çalıştırma ve Hata Ayıklama](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](unit-test-your-code.md)
