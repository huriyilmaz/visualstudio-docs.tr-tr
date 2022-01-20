---
title: C/C++ için birim testleri yazma
description: CTest, Boost.Test ve Visual Studio test çerçevelerini kullanarak C++ birim testlerini Google Test.
ms.date: 01/17/2022
ms.custom: devdivchpfy22
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a49766f1a9cfc32902667374e4dd4024b550cd0f
ms.sourcegitcommit: 2a8c7de72f952203289459736107c875837bb07e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137110190"
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

Yüklü çerçeveleri kullanabilir veya uygulama içinde kullanmak istediğiniz çerçeve için kendi test bağdaştırıcınızı Visual Studio. Test bağdaştırıcısı, birim testlerini Test Gezgini **penceresiyle** tümleştirin. Market'te çeşitli üçüncü taraf [bağdaştırıcılar Visual Studio kullanılabilir.](https://marketplace.visualstudio.com) Daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme.](install-third-party-unit-test-frameworks.md)

**Visual Studio 2017 ve sonrası (Professional ve Enterprise)**

C++ birim testi projeleri [CodeLens'i destekler.](../ide/find-code-changes-and-other-history-with-codelens.md)

**Visual Studio 2017 ve sonraki sürümler (tüm sürümler)**

- **Google Test Bağdaştırıcısı,** C++ iş yüküyle **Masaüstü geliştirmenin varsayılan bileşeni olarak** dahil edilir. Bir çözüme ek olarak ekleyebilirsiniz bir proje şablonuna sahip. Proje şablonunu eklemek için  Çözüm Gezgini düğümüne sağ   >  **tıklayın ve kısayol menüsünden Project** Ekle'yi seçin. Ayrıca Araçlar Seçenekleri aracılığıyla yapılandırabilirsiniz seçenekleri  >  **vardır.** Daha fazla bilgi için [bkz. Nasıl Google Test: Visual Studio.](how-to-use-google-test-for-cpp.md)

- **Boost.Test,** C++ iş yüküyle Masaüstü **geliştirmenin varsayılan bir bileşeni olarak** dahil edilir. Test Gezgini ile **tümleştirilmiştir,** ancak şu anda bir proje şablonuna sahip değildir. El ile yapılandırılması gerekir. Daha fazla bilgi için [bkz. How to: Use Boost.Test in Visual Studio.](how-to-use-boost-test-for-cpp.md)

- **CTest** desteği, C++ iş yüküyle Masaüstü geliştirmenin bir parçası olan **C++ CMake** **araçları bileşenine** dahildir. Daha fazla bilgi için, [bkz. How to: Use CTest in Visual Studio.](how-to-use-ctest-for-cpp.md)

**Visual Studio 2015 ve önceki sürümler**

Google Test Market'Google Test Boost.Test Bağdaştırıcısı uzantılarını Visual Studio indirebilirsiniz. Bunları, için [Boost.Test ve](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) Test bağdaştırıcısı [için Test bağdaştırıcısı'nda Google Test.](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde C++ birim testiyle çalışmaya başlamaya başlamanın temel adımları yer alıyor. Temel yapılandırma hem Microsoft hem de Google Test benzerdir. Boost.Test için el ile bir test projesi oluşturmanız gerekir.

::: moniker range=">=vs-2022"

### <a name="create-a-test-project-in-visual-studio-2022"></a>Visual Studio 2022'de test projesi oluşturma

Birim testlerini bir veya daha fazla test projesi içinde tanımlayın **ve çalıştırın.** Test projesi, yürütülebilir dosyanıza kodu çağıran ve davranışıyla ilgili raporlar oluşturan ayrı bir uygulama oluşturur. Test etmek istediğiniz kodla aynı çözümde test projeleri oluşturun.

Mevcut bir çözüme yeni bir test projesi eklemek için,

1. içinde Çözüm düğümüne sağ **tıklayın** Çözüm Gezgini. 
1. Açılır menüde Yeni Ekle'yi **seçin** > **ve Project.** 
1. **Dil'i** **C++ olarak** ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki çizimde **C++** ile Masaüstü Geliştirme ve **UWP** Geliştirme iş yükü yüklü olduğunda kullanılabilen test projeleri gösterilmiştir:

![VIsual Studio 2022'de C++ Test Projeleri](media/vs-2022/cpp-new-test-project-vs2022.png)

::: moniker-end

::: moniker range="=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019'da test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlama ve çalıştırma. Projeleri test etmek istediğiniz kodla aynı çözümde oluşturun. 
Mevcut bir çözüme yeni bir test projesi eklemek için,

1. içinde Çözüm düğümüne sağ **tıklayın** Çözüm Gezgini. 
1. Açılır menüde Yeni Ekle'yi **seçin** > **ve Project.**
1. **Dil'i** **C++ olarak** ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki çizimde **C++** ile Masaüstü Geliştirme ve **UWP** Geliştirme iş yükü yüklü olduğunda kullanılabilen test projeleri gösterilmiştir:

![VIsual Studio 2019'da C++ Test Projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017'de test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlama ve çalıştırma. Projeleri test etmek istediğiniz kodla aynı çözümde oluşturabilirsiniz.
Yeni bir test projesi eklemek için,

1. içinde Çözüm düğümüne sağ tıklayın ve **Çözüm Gezgini** Ekle'yi  > **Project.**
1. Sol bölmede Test 'i **Visual C++ seçin.** Ardından orta bölmeden proje türlerinden birini seçin. Aşağıdaki **çizimde, C++** ile Masaüstü Geliştirme iş yükü yüklü olduğunda kullanılabilen test projeleri gösterilmiştir:

   ![C++ Test Projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvuru oluşturma

Test altındaki projedeki işlevlere erişimi etkinleştirmek için test projenize bir başvuru ekleyin. Açılan menü için Çözüm Gezgini **proje** düğümüne sağ tıklayın. Başvuru **Ekle'yi**  >  **seçin.** Başvuru **Ekle iletişim** kutusunda test etmek istediğiniz projeleri seçin.

![Başvuru ekleme](media/vs-2022/cpp-add-ref-test-project-2022.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu test etmek istediğiniz işlevleri dışarı aktaramazsa çıkış .obj veya .lib dosyalarını test projesinin bağımlılıklarına ekleyin. Daha fazla bilgi için [bkz. Testleri nesne veya kitaplık dosyalarına bağlama.](how-to-use-microsoft-test-framework-for-cpp.md#object_files)

### <a name="add-include-directives-for-header-files"></a>Üst #include için yeni yönergeler ekleme

Ardından, birim testi *.cpp dosyanıza,* test etmek istediğiniz türleri ve işlevleri bildiren tüm üst bilgi `#include` dosyaları için bir yönerge ekleyin. Seçmenize `#include "` yardımcı olmak için yazın ve IntelliSense'i etkinleştirir. Daha fazla üst bilgi için tekrarlayın.

![IntelliSense'in Çözüm Gezgini üst bilgi dosyasını vurgulayan bir #include yönergesi ekleniyor ifadesini gösteren ekran görüntüsü.](media/vs-2022/cpp-add-includes-test-project-2022.png)

Kaynak dosyada her include deyiminde tam yolu yazmamak için, gerekli klasörleri Project  >  **Özellikler**  >  **C/C++** Genel Ek Ekleme  >    >  **Dizinleri'ne ekleyin.**

### <a name="write-test-methods"></a>Test yöntemleri yazma

> [!NOTE]
> Bu bölümde C/C++ için Microsoft Birim Testi Çerçevesi'nin söz dizimi yer almaktadır. Burada belgelenmiş: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API başvurusu.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) Daha Google Test için bkz. [Google Test bilgileri.](https://github.com/google/googletest/blob/master/docs/primer.md) Boost.Test için [bkz. Boost Test kitaplığı: Birim testi çerçevesi.](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html)

Test *projenizin .cpp* dosyasında sizin için tanımlanmış bir saplama sınıfı ve yöntemi vardır. Test kodu yazma örneği gösterir. İmzalar, TEST_CLASS ve TEST_METHOD test gezgini penceresinden keşfedilebilir hale gelen **makroları** kullanır.

![TEST_CLASS ve TEST_METHOD makrolarını kullanarak saplama sınıfı ve yöntemi içeren unittest1.cpp kod dosyasını gösteren Test Gezgini penceresinin ekran görüntüsü.](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD, Microsoft Yerel Test [Çerçevesi'nin bir parçası.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) **Test Gezgini,** desteklenen diğer çerçevelerde test yöntemlerini benzer şekilde keşfeder.

Bir TEST_METHOD void döndürür. Bir test sonucu üretmek için sınıfındaki statik yöntemleri kullanarak gerçek sonuçları beklenen sonuçlara karşı `Assert` test etmek için kullanın. Aşağıdaki örnekte, bir `MyClass` alan bir oluşturucusu olduğunu varsayalım. `std::string` Bu örnekte, oluşturucu tarafından sınıfı beklediğiniz gibi başlatan bir test nasıl yapılır?

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, çağrının sonucu testin `Assert::AreEqual` başarılı olup olmadığını belirler. sınıfı, `Assert` beklenen sonuçları gerçek sonuçlarla karşılaştırmak için birçok farklı yöntem içerir.

Test *sahiplerini, önceliğini* ve diğer bilgileri belirtmek için test yöntemlerine nitelikler ebilirsiniz. Daha sonra Test Gezgini'nde testleri sıralamak ve grup etmek için bu **değerleri kullanabilirsiniz.** Daha fazla bilgi için [bkz. Test Gezgini ile birim testleri çalıştırma.](run-unit-tests-with-test-explorer.md)

### <a name="run-the-tests"></a>Testleri çalıştırma

1. Test menüsünde **Test** **Gezgini'Windows**  >  **seçin.** Aşağıdaki çizimde, testleri henüz çalıştırmamış olan bir test projesi gösterilmiştir.

   ![Testleri çalıştırmadan önce Test Gezgini](media/vs-2022/cpp-test-explorer-2022.png)

   > [!NOTE]
   > Test Gezgini ile CTest **tümleştirmesi** henüz kullanılamıyor. CMake ana menüsünden CTest testlerini çalıştırın.

1. Testlerden herhangi biri pencerede eksikse, projedeki düğümüne sağ tıklar ve Derleme veya Yeniden **Çözüm Gezgini'yi seçerek test projesini** **derleme.** 

1. **Test Gezgini'nde,** **Tüm Testleri** Çalıştır'ı seçin veya çalıştırmak istediğiniz testleri seçin. Diğer seçenekler için bir teste sağ tıklayın ve kesme noktaları etkin hata ayıklama modunda çalıştırmayı da içerir. Tüm testleri çalıştırdıktan sonra, pencerede başarılı olan testler ve başarısız olanlar gösterilir.

   ![Testler çalıştır çalıştırktan sonra Test Gezgini](media/vs-2022/cpp-test-explorer-passed-2022.png)

Başarısız testler için ileti, nedeni tanılamaya yardımcı olan ayrıntıları görüntüler. Açılan menü için başarısız olan teste sağ tıklayın. Hata **ayıkla'ya** seçerek hatanın meydana geldiği işlevde adım adım inin.

Test Gezgini'ni kullanma hakkında **daha fazla bilgi için** [bkz. Test Gezgini ile birim testleri çalıştırma.](run-unit-tests-with-test-explorer.md)

Birim testi hakkında daha fazla bilgi için [bkz. Birim testi temelleri.](unit-test-basics.md)

## <a name="use-codelens"></a>CodeLens kullanma

**Visual Studio 2017 ve sonraki sürümler (Professional ve Enterprise sürümleri)**

[CodeLens,](../ide/find-code-changes-and-other-history-with-codelens.md) kod düzenleyicisinden ayrılmadan birim testinin durumunu hızla görmenizi sağlar.

C++ birim testi projesi için CodeLens'i aşağıdaki yöntemlerden herhangi birini kullanarak başlatabilirsiniz:

- Test projenizi veya çözümlerinizi düzenleyin ve derleme.
- Projenizi veya çözümlerinizi yeniden oluşturma.
- Test Gezgini **penceresinden testleri** çalıştırın.

Başlatıldıktan sonra, her birim testinin üzerinde test durumu simgelerini görebilirsiniz.

![C++ CodeLens Simgeleri](media/vs-2022/cpp-test-codelens-icons-2022.png)

Daha fazla bilgi için simgeye tıklayın veya birim testini çalıştırmak veya hata ayıklamak için:

![C++ CodeLens Çalıştırma ve Hata Ayıklama](media/vs-2022/cpp-test-codelens-run-debug-2022.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](unit-test-your-code.md)
