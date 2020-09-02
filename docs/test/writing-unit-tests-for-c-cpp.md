---
title: C/C++ için birim testleri yazma
description: CTest, Boost. test ve Google Test dahil çeşitli test çerçeveleri kullanarak Visual Studio 'da C++ birim testlerini yazın.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 0eaf41dc0bf3e21dfbf4018261844181d594f0d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649609"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio 'da C/C++ için birim testleri yazma

**Test Gezgini** penceresini kullanarak C++ birim testlerinizi yazabilir ve çalıştırabilirsiniz. Diğer diller için olduğu gibi çalışmaktadır. **Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Live Unit Testing, kodlanmış UI testleri ve IntelliTest gibi bazı özellikler C++ için desteklenmez.

Visual Studio, ek karşıdan yüklemeler gerekmeden bu C++ test çerçevelerini içerir:

- C++ için Microsoft birim testi çerçevesi
- Google Test
- Boost. test
- CTest

Yüklü çerçeveleri kullanmaya birlikte, Visual Studio 'da kullanmak istediğiniz çerçeve için kendi test bağdaştırıcınızı yazabilirsiniz. Test bağdaştırıcısı, birim testlerini **Test Gezgini** penceresiyle tümleştirebilir. [Visual Studio Market](https://marketplace.visualstudio.com)birçok üçüncü taraf bağdaştırıcı mevcuttur. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 ve üzeri (Professional ve Enterprise)**

C++ birim testi projeleri [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)'i destekler.

**Visual Studio 2017 ve üzeri (tüm sürümler)**

- **Google test bağdaştırıcı** , C++ iş yüküne **sahip masaüstü geliştirmenin** varsayılan bir bileşeni olarak dahil edilmiştir. Bir çözüme ekleyebileceğiniz bir proje şablonu vardır. Eklemek için **Çözüm Gezgini** çözüm düğümündeki **Yeni Proje Ekle** sağ tıklama menüsünü kullanın. Ayrıca **Araçlar**seçeneklerini kullanarak yapılandırabileceğiniz seçeneklere sahiptir  >  **Options**. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da Google test kullanma](how-to-use-google-test-for-cpp.md).

- **Boost. test** , C++ iş yüküne **sahip masaüstü geliştirmenin** varsayılan bir bileşeni olarak dahil edilmiştir. **Test Gezgini**ile tümleşiktir, ancak şu anda bir proje şablonu yoktur. El ile yapılandırılması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Boost. test kullanma](how-to-use-boost-test-for-cpp.md).

- **Ctest** desteği, c++ iş yükü **ile masaüstü geliştirmenin** bir parçası olan **c++ CMake araçları** bileşenine dahildir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da CTest kullanma](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 ve öncesi**

Google Test bağdaştırıcısını indirebilir ve Visual Studio Market Boost. test bağdaştırıcısı uzantılarını indirebilirsiniz. Bunları, [Google test için](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)test ve test bağdaştırıcısı [için test bağdaştırıcısında](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) bulabilirsiniz.

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde, C++ birim testi ile çalışmaya başlamanıza yönelik temel adımlar gösterilmektedir. Temel yapılandırma hem Microsoft hem de Google Test çerçeveleri için benzerdir. Boost. test, el ile bir test projesi oluşturmanızı gerektirir.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019 'de test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlayıp çalıştırırsınız. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz. Varolan bir çözüme yeni bir test projesi eklemek için **Çözüm Gezgini**çözüm düğümüne sağ tıklayın. Açılır menüden **Add**  >  **Yeni proje**Ekle ' yi seçin. **Dili** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki çizimde, **C++ Ile masaüstü geliştirme** ve **UWP geliştirme** iş yükü yüklendiğinde kullanılabilen test projeleri gösterilmektedir:

![VIsual Studio 2019 ' de C++ test projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017 'de test projesi oluşturma

Testleri bir veya daha fazla test projesi içinde tanımlayıp çalıştırırsınız. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz. Yeni bir test projesi eklemek için **Çözüm Gezgini** çözüm düğümüne sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin. Sol bölmede **Visual C++ test**' i seçin. Ardından, orta bölmeden proje türlerinden birini seçin. Aşağıdaki çizimde, C++ iş yükü **Ile masaüstü geliştirme** iş yüküyle birlikte kullanılabilir olan test projeleri gösterilmektedir:

![C++ test projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvurular oluşturma

Test kapsamındaki projedeki işlevlere erişimi etkinleştirmek için test projenizdeki projeye bir başvuru ekleyin. Bir açılır menü için **Çözüm Gezgini** test projesi düğümüne sağ tıklayın. Başvuru **Ekle**' yi seçin  >  **Reference**. Başvuru Ekle iletişim kutusunda, test etmek istediğiniz proje (ler) i seçin.

![Başvuru ekleme](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu test etmek istediğiniz işlevleri dışa aktarmazsa, output. obj veya. lib dosyalarını test projesinin bağımlılıklarına ekleyebilirsiniz. Daha fazla bilgi için, bkz. [Testleri nesne veya kitaplık dosyalarına bağlama](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Üst bilgi dosyaları için #include yönergeleri ekleme

Ardından, birim testi *. cpp* dosyanızda, `#include` test etmek istediğiniz türleri ve işlevleri bildiren herhangi bir üstbilgi dosyası için bir yönerge ekleyin. `#include "`Ardından IntelliSense 'i seçmenize yardımcı olacak şekilde etkinleştireceğinize. Ek üstbilgiler için tekrarlayın.

![İçerme yönergeleri ekleme](media/cpp-add-includes-test-project.png)

Kaynak dosyadaki her bir Include deyimindeki tam yolu yazmak zorunda kalmamak için, **Proje**  >  **özellikleri**  >  **C/C++**  >  **genel**  >  **ek içerme dizinleri**' ne gerekli klasörleri ekleyebilirsiniz.

### <a name="write-test-methods"></a>Yazma testi yöntemleri

> [!NOTE]
> Bu bölümde, C/C++ için Microsoft birim testi çerçevesi sözdizimi gösterilmektedir. Burada belgelenmiştir: [Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test belgeler için bkz. [Google test öncü](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Boost. test için bkz. [Boost test Kitaplığı: birim test çerçevesi](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Test projenizdeki *. cpp* dosyasında, sizin için tanımlanan bir saplama sınıfı ve yöntemi vardır. Test kodunun nasıl yazılacağını gösteren bir örnek gösterir. İmzalar TEST_CLASS ve TEST_METHOD makrolarını kullanır, bu da yöntemleri **Test Gezgini** penceresinden bulunabilir hale getirir.

![İçerme yönergeleri ekleme](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD, [Microsoft yerel test çerçevesinin](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)bir parçasıdır. **Test Gezgini** , diğer desteklenen çerçeveler içindeki test yöntemlerini benzer bir şekilde bulur.

TEST_METHOD void döndürür. Bir test sonucu oluşturmak için, `Assert` gerçek sonuçları beklenerek test etmek üzere sınıfındaki statik yöntemleri kullanın. Aşağıdaki örnekte, varsayımında `MyClass` bir Oluşturucu vardır `std::string` . Oluşturucunun sınıfı şu şekilde beklendiği gibi başlattığında, test edebilirsiniz:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, `Assert::AreEqual` çağrının sonucu testin başarılı mı yoksa başarısız mı olduğunu belirler. Onaylama sınıfı, beklenen ve gerçek sonuçları karşılaştırmak için birçok farklı yöntem içerir.

Test sahiplerini, öncelik ve diğer bilgileri belirtmek için test yöntemlerine *nitelikler* ekleyebilirsiniz. Daha sonra bu değerleri **Test Gezgini**'nde testleri sıralamak ve gruplandırmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Windows**  >  **Test Gezgini**' ni seçin. Aşağıdaki çizimde, testleri henüz çalıştırılmayan bir test projesi gösterilmektedir.

   ![Testleri çalıştırmadan önce test Gezgini](media/cpp-test-explorer.png)

   > [!NOTE]
   > **Test Gezgini** Ile ctest tümleştirmesi henüz kullanılamıyor. CMake ana menüsünden CTest testlerini çalıştırın.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinken hata ayıklama modunda çalıştırmak dahil diğer seçenekler için teste sağ tıklayın. Tüm testleri çalıştırdıktan sonra pencere hangi testlerin geçtiğini ve hangilerinin başarısız olduğunu gösterir:

![Testler çalıştırıldıktan sonra test Gezgini](media/cpp-test-explorer-passed.png)

Başarısız testler için, iletinin nedenini tanılamaya yardımcı olan ayrıntılar sunulmaktadır. Bir açılır menü için başarısız teste sağ tıklayın. Hatanın oluştuğu işlevin içinde ilerlemek için **Seçili testlerin hatalarını ayıkla** ' yı seçin.

**Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

Birim testi ile ilgili daha fazla bilgi için bkz. [birim testi temelleri](unit-test-basics.md)

## <a name="use-codelens"></a>CodeLens kullanma

**Visual Studio 2017 ve üzeri (Professional ve Enterprise sürümleri)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) , kod düzenleyicisinden çıkmadan bir birim testinin durumunu hızlıca görmenizi sağlar.

Aşağıdaki yollarla bir C++ birim testi projesi için CodeLens 'i başlatabilirsiniz:

- Test projenizi veya çözümünüzü düzenleyin ve oluşturun.
- Projenizi veya çözümünüzü yeniden derleyin.
- Testleri **Test Gezgini** penceresinden çalıştırın.

Başlatıldıktan sonra, her birim testinin üzerinde test durumu simgelerini görebilirsiniz.

![C++ CodeLens simgeleri](media/cpp-test-codelens-icons.png)

Daha fazla bilgi için simgeye tıklayın veya birim testini çalıştırmak veya hata ayıklamak için:

![C++ CodeLens Run ve hata ayıklama](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](unit-test-your-code.md)
