---
title: C/C++ için birim testleri yazma
description: ctest, Boost. test ve Google Test dahil çeşitli test çerçeveleri kullanarak Visual Studio C++ birim testlerini yazın.
ms.date: 01/17/2022
ms.custom: devdivchpfy22
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: ce92e9a813d1c443094f719e6825d29cc3681852
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650306"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio 'de C/C++ için birim testleri yazma

**Test Gezgini** penceresini kullanarak C++ birim testlerinizi yazabilir ve çalıştırabilirsiniz. Diğer diller için olduğu gibi çalışmaktadır. **Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Live Unit Testing, kodlanmış UI testleri ve IntelliTest gibi bazı özellikler C++ için desteklenmez.

Visual Studio, ek karşıdan yüklemeler gerekmeden bu C++ test çerçevelerini içerir:

- C++ için Microsoft birim testi çerçevesi
- Google Test
- Boost. test
- CTest

Yüklü çerçeveleri kullanabilir veya Visual Studio içinde kullanmak istediğiniz herhangi bir çerçeve için kendi test bağdaştırıcınızı yazabilirsiniz. Test bağdaştırıcısı, birim testlerini **Test Gezgini** penceresiyle tümleştirir. [Visual Studio marketi](https://marketplace.visualstudio.com)'nde birçok üçüncü taraf bağdaştırıcı mevcuttur. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 ve üzeri (Professional ve Enterprise)**

C++ birim testi projeleri [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)'i destekler.

**Visual Studio 2017 ve üzeri (tüm sürümler)**

- **Google test bağdaştırıcı** , C++ iş yüküne **sahip masaüstü geliştirmenin** varsayılan bir bileşeni olarak dahil edilmiştir. Bir çözüme ekleyebileceğiniz bir proje şablonu vardır. **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve kısayol menüsünde yeni **Project ekle**' yi seçerek  >   proje şablonunu ekleyin. Ayrıca **Araçlar** seçeneklerini kullanarak yapılandırabileceğiniz seçeneklere sahiptir  >  . Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Google test kullanma](how-to-use-google-test-for-cpp.md).

- **Boost. test** , C++ iş yüküne **sahip masaüstü geliştirmenin** varsayılan bir bileşeni olarak dahil edilmiştir. **Test Gezgini** ile tümleşiktir, ancak şu anda bir proje şablonu yoktur. El ile yapılandırılması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Boost. test kullanma](how-to-use-boost-test-for-cpp.md).

- **Ctest** desteği, c++ iş yükü **ile masaüstü geliştirmenin** bir parçası olan **c++ CMake araçları** bileşenine dahildir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio CTest kullanma](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 ve öncesi**

Google Test bağdaştırıcısını indirebilir ve Visual Studio market 'teki Boost. Test bağdaştırıcısı uzantılarını indirebilirsiniz. Bunları, [Google test için](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)test ve test bağdaştırıcısı [için test bağdaştırıcısında](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) bulabilirsiniz.

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde, C++ birim testi ile çalışmaya başlamanıza yönelik temel adımlar gösterilmektedir. Temel yapılandırma hem Microsoft hem de Google Test çerçeveleri için benzerdir. Boost. test, el ile bir test projesi oluşturmanızı gerektirir.

::: moniker range=">=vs-2022"

### <a name="create-a-test-project-in-visual-studio-2022"></a>Visual Studio 2022 ' de bir test projesi oluşturma

Birim testlerini bir veya daha fazla **test projesi** içinde tanımlayın ve çalıştırın. Bir test projesi, çalıştırılabilirinizdeki kodu çağıran ayrı bir uygulama oluşturur ve davranışı üzerindeki raporlarınızı raporlar. Test projelerini test etmek istediğiniz kodla aynı çözümde oluşturun.

Varolan bir çözüme yeni bir test projesi eklemek için

1. **Çözüm Gezgini** çözüm düğümüne sağ tıklayın. 
1. açılır menüden  > **yeni Project** ekle ' yi seçin. 
1. **Dili** **C++** olarak ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki çizimde, **C++ Ile masaüstü geliştirme** ve **UWP geliştirme** iş yükü yüklendiğinde kullanılabilen test projeleri gösterilmektedir:

![Visual Studio 2022 ' de C++ Test projeleri](media/vs-2022/cpp-new-test-project-vs2022.png)

::: moniker-end

::: moniker range="=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019 ' de bir test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlayın ve çalıştırın. Projeleri test etmek istediğiniz kodla aynı çözümde oluşturun. 
Varolan bir çözüme yeni bir test projesi eklemek için

1. **Çözüm Gezgini** çözüm düğümüne sağ tıklayın. 
1. açılır menüden  > **yeni Project** ekle ' yi seçin.
1. **Dili** **C++** olarak ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki çizimde, **C++ Ile masaüstü geliştirme** ve **UWP geliştirme** iş yükü yüklendiğinde kullanılabilen test projeleri gösterilmektedir:

![Visual Studio 2019 ' de C++ Test projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017 ' de bir test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlayın ve çalıştırın. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz.
Yeni bir test projesi eklemek için

1. **Çözüm Gezgini** ' deki çözüm düğümüne sağ tıklayın ve  > **yeni Project** ekle ' yi seçin.
1. Sol bölmede **Visual C++ test**' i seçin. Ardından, orta bölmeden proje türlerinden birini seçin. Aşağıdaki çizimde, C++ iş yükü **Ile masaüstü geliştirme** iş yüküyle birlikte kullanılabilir olan test projeleri gösterilmektedir:

   ![C++ test projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvurular oluşturma

Test kapsamındaki projedeki işlevlere erişimi etkinleştirmek için test projenizdeki projeye bir başvuru ekleyin. Bir açılır menü için **Çözüm Gezgini** test projesi düğümüne sağ tıklayın. Başvuru **Ekle**' yi seçin  >  . **Başvuru Ekle** iletişim kutusunda, test etmek istediğiniz proje (ler) i seçin.

![Başvuru ekleme](media/vs-2022/cpp-add-ref-test-project-2022.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu test etmek istediğiniz işlevleri dışa aktarmazsa, output. obj veya. lib dosyalarını test projesinin bağımlılıklarına ekleyin. Daha fazla bilgi için, bkz. [Testleri nesne veya kitaplık dosyalarına bağlama](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Üst bilgi dosyaları için #include yönergeleri ekleme

Ardından, birim testi *. cpp* dosyanızda, `#include` test etmek istediğiniz türleri ve işlevleri bildiren herhangi bir üstbilgi dosyası için bir yönerge ekleyin. `#include "`' İ ve ardından IntelliSense ' i seçmenize yardımcı olacak şekilde etkinleştirir. Daha fazla başlık için tekrarlayın.

![IntelliSense ile eklenen bir #include yönergesini gösteren Çözüm Gezgini ekran görüntüsü ekleme için bir üst bilgi dosyası.](media/vs-2022/cpp-add-includes-test-project-2022.png)

kaynak dosyadaki her bir ınclude deyimindeki tam yolu yazmak zorunda kalmamak için, **Project**  >  **özellikler**  >  **C/C++**  >  **genel**  >  **ek içerme dizinlerine** gerekli klasörleri ekleyin.

### <a name="write-test-methods"></a>Yazma testi yöntemleri

> [!NOTE]
> Bu bölümde, C/C++ için Microsoft birim testi çerçevesi sözdizimi gösterilmektedir. Burada belgelenmiştir: [Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test belgeler için bkz. [Google test öncü](https://github.com/google/googletest/blob/master/docs/primer.md). Boost. test için bkz. [Boost test Kitaplığı: birim test çerçevesi](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Test projenizdeki *. cpp* dosyasında, sizin için tanımlanan bir saplama sınıfı ve yöntemi vardır. Test kodunun nasıl yazılacağını gösteren bir örnek gösterir. İmzalar TEST_CLASS ve TEST_METHOD makrolarını kullanır, bu da yöntemleri **Test Gezgini** penceresinden bulunabilir hale getirir.

![TEST_CLASS ve TEST_METHOD makrolarını kullanarak bir saplama sınıfı ve yöntemi içeren UnitTest1. cpp kod dosyasını gösteren test Gezgini penceresinin ekran görüntüsü.](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD, [Microsoft yerel test çerçevesinin](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)bir parçasıdır. **Test Gezgini** , diğer desteklenen çerçeveler içindeki test yöntemlerini benzer bir şekilde bulur.

TEST_METHOD void döndürür. Bir test sonucu oluşturmak için, `Assert` gerçek sonuçları beklenen sonuçlara karşı test etmek üzere sınıfındaki statik yöntemleri kullanın. Aşağıdaki örnekte, varsayımında `MyClass` bir Oluşturucu vardır `std::string` . Bu örnek, oluşturucunun sınıfı beklenen şekilde nasıl gösterdiğini nasıl test edebilecekleri gösterilmektedir:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, `Assert::AreEqual` çağrının sonucu testin başarılı mı yoksa başarısız mı olduğunu belirler. `Assert`Sınıfı, beklenen sonuçları gerçek sonuçlarla karşılaştırmak için birçok farklı yöntem içerir.

Test sahiplerini, öncelik ve diğer bilgileri belirtmek için test yöntemlerine *nitelikler* ekleyebilirsiniz. Daha sonra bu değerleri **Test Gezgini**'nde testleri sıralamak ve gruplandırmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

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
