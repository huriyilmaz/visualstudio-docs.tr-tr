---
title: C/C++ için birim testleri yazma
description: CTest, Boost. test ve Google Test dahil çeşitli test çerçeveleri kullanarak Visual Studio 'da birim testlerini yazın C++ .
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 354ccad121884c99541057a2e0e0a47d9d2a4341
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937549"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio'da C/C++ için birim testleri yazma

C++ **Test Gezgini** penceresini kullanarak birim testlerinizi yazabilir ve çalıştırabilirsiniz. Diğer diller için olduğu gibi çalışmaktadır. **Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> C++ için Live Unit Testing, kodlanmış UI testleri ve Intellitest gibi bazı özellikler desteklenmez.

Visual Studio bu C++ test çerçeveleri, gereken ek hiçbir yüklemeleriyle içerir:

- Microsoft birim testi çerçevesi için C++
- Google Test
- Boost.Test
- CTest

Yüklü çerçeveleri kullanmaya birlikte, Visual Studio 'da kullanmak istediğiniz çerçeve için kendi test bağdaştırıcınızı yazabilirsiniz. Test bağdaştırıcısı, birim testlerini **Test Gezgini** penceresiyle tümleştirebilir. [Visual Studio Market](https://marketplace.visualstudio.com)birçok üçüncü taraf bağdaştırıcı mevcuttur. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 ve üzeri (Professional ve Enterprise)**

C++birim testi projeleri [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)'i destekler.

**Visual Studio 2017 ve üzeri (tüm sürümler)**

- **Google test bağdaştırıcı** , iş yüküyle **Masaüstü geliştirmenin C++**  varsayılan bir bileşeni olarak dahil edilmiştir. Bir çözüme ekleyebileceğiniz bir proje şablonu vardır. Eklemek için **Çözüm Gezgini** çözüm düğümündeki **Yeni Proje Ekle** sağ tıklama menüsünü kullanın. Ayrıca **araçlar** > **seçenekleri**aracılığıyla yapılandırabileceğiniz seçeneklere sahiptir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da Google test kullanma](how-to-use-google-test-for-cpp.md).

- **Boost. test** , iş yüküyle **Masaüstü geliştirmenin C++**  varsayılan bir bileşeni olarak dahil edilmiştir. **Test Gezgini**ile tümleşiktir, ancak şu anda bir proje şablonu yoktur. El ile yapılandırılması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Boost. test kullanma](how-to-use-boost-test-for-cpp.md).

- **Ctest** desteği,  **C++ CMake araçları** bileşenine dahildir ve iş yükü **ile C++ masaüstü geliştirmenin** bir parçasıdır. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da CTest kullanma](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 ve öncesi**

Google Test bağdaştırıcısını indirebilir ve Visual Studio Market Boost. test bağdaştırıcısı uzantılarını indirebilirsiniz. Bunları, [Google test için](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)test ve test bağdaştırıcısı [için test bağdaştırıcısında](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) bulabilirsiniz.

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde, C++ birim testi başlamanıza yardımcı olmak için temel adımları gösterilmektedir. Temel yapılandırma hem Microsoft hem de Google Test çerçeveleri için benzerdir. Boost.Test el ile bir test projesi oluşturmanız gerekir.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019 'de test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlayıp çalıştırırsınız. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz. Varolan bir çözüme yeni bir test projesi eklemek için **Çözüm Gezgini**çözüm düğümüne sağ tıklayın. Açılır menüden > **Yeni proje** **Ekle** ' yi seçin. **Dil** ayarla C++ ve arama kutusuna "test" yazın. Aşağıdaki çizim, **ile C++ masaüstü geliştirme** ve **UWP geliştirme** iş yükü yüklü olduğunda kullanılabilir olan test projelerini göstermektedir:

![C++VIsual Studio 2019 ' de test projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017 'de test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlayıp çalıştırırsınız. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz. Yeni bir test projesi eklemek için **Çözüm Gezgini** çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin. Sol bölmede **görsel C++ test**' i seçin. Ardından, orta bölmeden proje türlerinden birini seçin. Aşağıdaki çizimde, iş yüküyle **masaüstü geliştirme C++**  yüklendiğinde kullanılabilir olan test projeleri gösterilmektedir:

![C++ Test projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvuruları oluşturma

Test kapsamındaki projedeki işlevlere erişimi etkinleştirmek için test projenizdeki projeye bir başvuru ekleyin. Bir açılır menü için **Çözüm Gezgini** test projesi düğümüne sağ tıklayın.  > **başvuru** **Ekle** ' yi seçin. Başvuru Ekle iletişim kutusunda, test etmek istediğiniz proje (ler) i seçin.

![Başvuru ekleme](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu test etmek istediğiniz işlevleri dışa aktarmazsa, output. obj veya. lib dosyalarını test projesinin bağımlılıklarına ekleyebilirsiniz. Daha fazla bilgi için, bkz. [Testleri nesne veya kitaplık dosyalarına bağlama](/visualstudio/test/how-to-use-microsoft-test-framework-for-cpp#object_files).

### <a name="add-include-directives-for-header-files"></a>Ekle #include için üst bilgi dosyaları

Ardından, birim testi *. cpp* dosyanızda, test etmek istediğiniz türleri ve işlevleri bildiren tüm üst bilgi dosyaları için bir `#include` yönergesi ekleyin. `#include "` yazın ve IntelliSense ' i seçmenize yardımcı olacak şekilde etkinleştireceğinize. Ek üst bilgilere için yineleyin.

![Ekleme yönergelerinde](media/cpp-add-includes-test-project.png)

Kaynak dosyadaki her bir Include deyimindeki tam yolu yazmak zorunda kalmamak için, > **Özellikler** > **C++ C/**  > **genel** > **ek içerme dizinleri** **' ne** gerekli klasörleri ekleyebilirsiniz.

### <a name="write-test-methods"></a>Test yöntemleri yazın

> [!NOTE]
> Bu bölüm, C/C++ için Microsoft birim testi çerçevesi için söz dizimini gösterir. Burada belgelenmiştir: [Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test belgeler için bkz. [Google test öncü](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Boost. test için bkz. [Boost test Kitaplığı: birim test çerçevesi](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Test projenizdeki *. cpp* dosyasında, sizin için tanımlanan bir saplama sınıfı ve yöntemi vardır. Test kodunun nasıl yazılacağını gösteren bir örnek gösterir. İmzalar TEST_CLASS ve TEST_METHOD makrolarını kullanır, bu da yöntemleri **Test Gezgini** penceresinden bulunabilir hale getirir.

![Ekleme yönergelerinde](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD, [Microsoft yerel test çerçevesinin](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)bir parçasıdır. **Test Gezgini** , diğer desteklenen çerçeveler içindeki test yöntemlerini benzer bir şekilde bulur.

Bir TEST_METHOD void döndürür. Bir test sonucu oluşturmak için, gerçek sonuçları beklenerek test etmek üzere `Assert` sınıfındaki statik yöntemleri kullanın. Aşağıdaki örnekte, `MyClass` `std::string`alan bir oluşturucuya sahip olduğunu varsayalım. Oluşturucu beklendiği gibi sınıfı başlatır sınayabiliriz şu şekilde:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, `Assert::AreEqual` çağrısının sonucu testin başarılı veya başarısız olup olmadığını belirler. Assert sınıfı, beklenen gerçek sonuçlar karşılaştırma için birçok yöntem içerir.

Test sahiplerini, öncelik ve diğer bilgileri belirtmek için test yöntemlerine *nitelikler* ekleyebilirsiniz. Daha sonra bu değerleri **Test Gezgini**'nde testleri sıralamak ve gruplandırmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Testleri çalıştırın

1. **Test** menüsünde **Windows** > **Test Gezgini**' ni seçin. Aşağıdaki çizim bir test projesi olan testleri henüz çalıştırılmamış gösterir.

   ![Testleri çalıştırmadan önce test Gezgini](media/cpp-test-explorer.png)

   > [!NOTE]
   > **Test Gezgini** Ile ctest tümleştirmesi henüz kullanılamıyor. CMake ana menüden CTest testleri çalıştırın.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin veya çalıştırmak istediğiniz belirli testleri seçin. Bir test etkin kesme noktaları ile hata ayıklama modunda çalıştırmak dahil, diğer seçenekler için sağ tıklayın. Tüm testleri çalıştırdıktan sonra hangi testleri geçti ve hangilerinin başarısız pencere gösterir:

![Testler çalıştıktan sonra test Gezgini](media/cpp-test-explorer-passed.png)

Başarısız testler için ileti nedenini tanılamaya yardımcı olan ayrıntılar sunar. Bir açılır menü için başarısız teste sağ tıklayın. Hatanın oluştuğu işlevin içinde ilerlemek için **Seçili testlerin hatalarını ayıkla** ' yı seçin.

**Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

Birim testi ile ilgili daha fazla bilgi için bkz. [birim testi temelleri](unit-test-basics.md)

## <a name="use-codelens"></a>CodeLens kullanın

**Visual Studio 2017 ve üzeri (Professional ve Enterprise sürümleri)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) , kod düzenleyicisinden çıkmadan bir birim testinin durumunu hızlıca görmenizi sağlar.

CodeLens, bir C++ birim testi projesi şu yollardan birinde için başlatabilirsiniz:

- Düzenle ve test projenizi veya çözümünüzü oluşturun.
- Proje veya çözümü yeniden oluşturun.
- Testleri **Test Gezgini** penceresinden çalıştırın.

Başlatıldıktan sonra, her birim testinin üzerinde test durumu simgelerini görebilirsiniz.

![C++ CodeLens simgeler](media/cpp-test-codelens-icons.png)

Daha fazla bilgi edinmek veya çalıştırmak veya birim testi hata ayıklama için simgesine tıklayın:

![C++ CodeLens çalıştırma ve hata ayıklama](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](unit-test-your-code.md)
