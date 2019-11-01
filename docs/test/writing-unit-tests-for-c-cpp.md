---
title: C/için birim testleri yazmaC++
description: CTest, Boost. test ve Google Test dahil çeşitli test çerçeveleri kullanarak Visual Studio 'da birim testlerini yazın C++ .
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 824b928c9f89b98f9026059b824fce84969bf69a
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189107"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio 'da C/C++ için birim testleri yazma

Yalnızca diğer diller gibi C++ **Test Gezgini** penceresini kullanarak birim testlerinizi yazabilir ve çalıştırabilirsiniz. **Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Live Unit Testing, kodlanmış UI testleri ve IntelliTest gibi bazı özellikler için C++desteklenmez.

Visual Studio, gerekli C++ ek yüklemeler olmadan bu test çerçevelerini içerir:

- İçin Microsoft birim testi çerçevesiC++
- Google Test
- Boost. test
- CTest

Yüklü çerçevelere ek olarak, Visual Studio içinde kullanmak istediğiniz herhangi bir çerçeve için kendi test bağdaştırıcınızı yazabilirsiniz. Test bağdaştırıcısı, birim testlerini **Test Gezgini** penceresiyle tümleştirebilir. [Visual Studio Market](https://marketplace.visualstudio.com)birçok üçüncü taraf bağdaştırıcı mevcuttur. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 ve üzeri (Professional ve Enterprise)**

C++birim testi projeleri [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)'i destekler.

**Visual Studio 2017 ve üzeri (tüm sürümler)**

- **Google test bağdaştırıcı** , iş yüküyle **Masaüstü geliştirmenin C++**  varsayılan bir bileşeni olarak dahil edilmiştir. Bir çözüme ekleyebileceğiniz, **Çözüm Gezgini**çözüm düğümündeki **Yeni Proje Ekle** sağ tıklama menüsü ve **Araçlar** > **Seçenekler**aracılığıyla yapılandırabileceğiniz seçenekler aracılığıyla bir proje şablonu vardır. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da Google test kullanma](how-to-use-google-test-for-cpp.md).

- **Boost. test** , iş yüküyle **Masaüstü geliştirmenin C++**  varsayılan bir bileşeni olarak dahil edilmiştir. **Test Gezgini** ile tümleşiktir ancak şu anda proje şablonu yoktur, bu nedenle el ile yapılandırılması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Boost. test kullanma](how-to-use-boost-test-for-cpp.md).

- **Ctest** desteği,  **C++ CMake araçları** bileşenine dahildir ve iş yükü **ile C++ masaüstü geliştirmenin** bir parçasıdır. Ancak, CTest henüz **Test Gezgini**ile tam olarak tümleştirmemiştir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da CTest kullanma](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 ve öncesi**

Google Test bağdaştırıcısını ve Boost. test bağdaştırıcısı uzantılarını, [Google test Için](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)yükseltme ve test bağdaştırıcısı [için test bağdaştırıcısında](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) Visual Studio Market indirebilirsiniz.

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde, birim testi ile C++ çalışmaya başlamanıza yönelik temel adımlar gösterilmektedir. Temel yapılandırma, Microsoft ve Google Test çerçeveleri için çok benzerdir. Boost. test, el ile bir test projesi oluşturmanızı gerektirir.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019 'de test projesi oluşturma

Testleri, test etmek istediğiniz kodla aynı çözümde olan bir veya daha fazla test projesi içinde tanımlar ve çalıştırırsınız. Varolan bir çözüme yeni bir test projesi eklemek için **Çözüm Gezgini** çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin. **Dil** ayarla C++ ve arama kutusuna "test" yazın. Aşağıdaki çizim, **ile C++ masaüstü geliştirme** ve **UWP geliştirme** iş yükü yüklü olduğunda kullanılabilir olan test projelerini göstermektedir:

![C++VIsual Studio 2019 ' de test projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017 'de test projesi oluşturma

Testleri, test etmek istediğiniz kodla aynı çözümde olan bir veya daha fazla test projesi içinde tanımlar ve çalıştırırsınız. Varolan bir çözüme yeni bir test projesi eklemek için **Çözüm Gezgini** çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin. Ardından sol bölmede **görsel C++ test** ' i seçin ve orta bölmeden proje türlerinden birini seçin. Aşağıdaki çizimde, iş yüküyle **masaüstü geliştirme C++**  yüklendiğinde kullanılabilir olan test projeleri gösterilmektedir:

![C++Test projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvurular oluşturma

Test kodunuzun test edilecek projedeki işlevlere erişmesini sağlamak için, test projenizdeki projeye bir başvuru ekleyin. **Çözüm Gezgini** ' deki test projesi düğümüne sağ tıklayın ve > **başvuru** **Ekle** ' yi seçin. Ardından iletişim kutusunda, test etmek istediğiniz projeleri seçin.

![Başvuru Ekle](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu test etmek istediğiniz işlevleri dışa aktarmazsa, output. obj veya. lib dosyalarını test projesinin bağımlılıklarına ekleyebilirsiniz. [Testleri nesne veya kitaplık dosyalarına bağlamak için](how-to-use-microsoft-test-framework-for-cpp.md)bkz.

### <a name="add-include-directives-for-header-files"></a>Üst bilgi dosyaları için #include yönergeleri ekleme

Ardından, birim testi *. cpp* dosyanızda, test etmek istediğiniz türleri ve işlevleri bildiren tüm üst bilgi dosyaları için bir `#include` yönergesi ekleyin. `#include "` yazın ve IntelliSense ' i seçmenize yardımcı olacak şekilde etkinleştireceğinize. Ek üstbilgiler için tekrarlayın.

![İçerme yönergeleri ekleme](media/cpp-add-includes-test-project.png)

Kaynak dosyadaki her bir Include deyimindeki tam yolu yazmak zorunda kalmamak için, **Proje** > **Özellikler** > **C/C++**  > **genel** > **Ek ekleme ' ye gerekli klasörleri ekleyebilirsiniz Dizinler**.

### <a name="write-test-methods"></a>Yazma testi yöntemleri

> [!NOTE]
> Bu bölümde, C/C++Için Microsoft birim testi çerçevesi sözdizimi gösterilmektedir. Burada belgelenmiştir: [Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test belgeler için bkz. [Google test öncü](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Boost. test için bkz. [Boost test Kitaplığı: birim test çerçevesi](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Test projenizdeki *. cpp* dosyası, test kodunun nasıl yazılacağını gösteren bir örnek olarak, sizin için tanımlanan bir saplama sınıfına ve yöntemine sahiptir. İmzaların TEST_CLASS ve TEST_METHOD makrolarını kullandığına dikkat edin. Bu, yöntemleri **Test Gezgini** penceresinden bulunabilir hale getirir.

![İçerme yönergeleri ekleme](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD, [Microsoft yerel test çerçevesinin](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)bir parçasıdır. **Test Gezgini** , diğer desteklenen çerçeveler içindeki test yöntemlerini benzer bir şekilde bulur.

Bir TEST_METHOD, void döndürür. Bir test sonucu oluşturmak için, gerçek sonuçları beklenerek test etmek üzere `Assert` sınıfındaki statik yöntemleri kullanın. Aşağıdaki örnekte, `MyClass` `std::string`alan bir oluşturucuya sahip olduğunu varsayalım. Oluşturucunun sınıfı şu şekilde beklendiği gibi başlattığında, test edebilirsiniz:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, `Assert::AreEqual` çağrısının sonucu testin başarılı veya başarısız olup olmadığını belirler. Onaylama sınıfı, beklenen ve gerçek sonuçları karşılaştırmak için birçok farklı yöntem içerir.

Test sahiplerini, öncelik ve diğer bilgileri belirtmek için test yöntemlerine *nitelikler* ekleyebilirsiniz. Daha sonra bu değerleri **Test Gezgini**'nde testleri sıralamak ve gruplandırmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Windows** > **Test Gezgini**' ni seçin. Aşağıdaki çizimde, testleri henüz çalıştırılmayan bir test projesi gösterilmektedir.

   ![Testler çalıştırılmadan önce test Gezgini](media/cpp-test-explorer.png)

   > [!NOTE]
   > **Test Gezgini** Ile ctest tümleştirmesi henüz kullanılamıyor. CMake ana menüsünden CTest testlerini çalıştırın.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinken hata ayıklama modunda çalıştırmak dahil diğer seçenekler için teste sağ tıklayın. Tüm testleri çalıştırdıktan sonra pencere hangi testlerin geçtiğini ve hangilerinin başarısız olduğunu gösterir:

![Testler çalıştırıldıktan sonra test Gezgini](media/cpp-test-explorer-passed.png)

Başarısız testler için, iletinin nedenini tanılamaya yardımcı olan ayrıntılar sunulmaktadır. Başarısız teste sağ tıklayıp Hatanın gerçekleştiği işlevin içinde ilerlemek için **Seçili testlerin hatalarını ayıkla** ' yı seçebilirsiniz.

**Test Gezgini**'ni kullanma hakkında daha fazla bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

Birim testi ile ilgili en iyi uygulamalar için bkz. [birim testi temelleri](unit-test-basics.md)

## <a name="use-codelens"></a>CodeLens kullanma

**Visual Studio 2017 ve üzeri (Professional ve Enterprise sürümleri)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) , kod düzenleyicisinden çıkmadan bir birim testinin durumunu hızlıca görmenizi sağlar. Aşağıdaki yollarla bir C++ birim testi projesi Için CodeLens 'i başlatabilirsiniz:

- Test projenizi veya çözümünüzü düzenleyin ve oluşturun.
- Projenizi veya çözümünüzü yeniden derleyin.
- Test **Gezgini** penceresinden test (ler) i çalıştırın.

**CodeLens** başlatıldıktan sonra, her birim testinin üzerinde test durumu simgelerini görebilirsiniz.

![C++CodeLens simgeleri](media/cpp-test-codelens-icons.png)

Daha fazla bilgi için simgeye tıklayın veya birim testini çalıştırmak veya hata ayıklamak için:

![C++CodeLens Run ve hata ayıklama](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](unit-test-your-code.md)
