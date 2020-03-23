---
title: C/C++ için birim testleri yazma
description: CTest, Boost.Test ve Google Test gibi çeşitli test çerçevelerini kullanarak Visual Studio'da C++ birim testleri yazın.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 354ccad121884c99541057a2e0e0a47d9d2a4341
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78937549"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio'da C/C++ için birim testleri yazma

**Test Gezgini** penceresini kullanarak C++ birim testlerinizi yazabilir ve çalıştırabilirsiniz. Diğer dillerde olduğu gibi çalışıyor. **Test Gezgini'ni**kullanma hakkında daha fazla bilgi için test [gezgini ile birim testlerini çalıştır'a](run-unit-tests-with-test-explorer.md)bakın.

> [!NOTE]
> Canlı Birim Testi, Kodlu UI Testleri ve IntelliTest gibi bazı özellikler C++ için desteklenmez.

Visual Studio, ek indirme gerektirmeden bu C++ test çerçevelerini içerir:

- C++ için Microsoft Birim Test Çerçevesi
- Google Testi
- Boost.Test
- CTest

Yüklü çerçeveleri kullanmanın yanı sıra, Visual Studio içinde kullanmak istediğiniz çerçeve için kendi test bağdaştırıcınızı yazabilirsiniz. Bir test bağdaştırıcısı birim testlerini **Test Gezgini** penceresiile tümleştirebilir. Birkaç üçüncü taraf adaptörleri [Visual Studio Marketplace](https://marketplace.visualstudio.com)mevcuttur. Daha fazla bilgi için [bkz.](install-third-party-unit-test-frameworks.md)

**Visual Studio 2017 ve sonrası (Profesyonel ve Kurumsal)**

C++ birim test projeleri [CodeLens'i](../ide/find-code-changes-and-other-history-with-codelens.md)destekler.

**Visual Studio 2017 ve sonrası (tüm sürümler)**

- **Google Test Bağdaştırıcısı,** C++ iş **yüküyle Masaüstü geliştirmenin** varsayılan bileşeni olarak dahildir. Bir çözüme ekleyebileceğiniz bir proje şablonu vardır. Eklemek için **Solution Explorer'daki** çözüm düğümündeki **Yeni Proje Ekle** menüsünü kullanın. Ayrıca **Araç** > **Seçenekleri**ile yapılandırabileceğiniz seçenekler de vardır. Daha fazla bilgi için [bkz: Visual Studio'da Google Test'i kullanın.](how-to-use-google-test-for-cpp.md)

- **Boost.Test,** C++ iş **yüküne sahip Masaüstü geliştirmenin** varsayılan bileşeni olarak dahildir. **Test Gezgini**ile tümleşik, ancak şu anda bir proje şablonu yok. El ile yapılandırılmalıdır. Daha fazla bilgi için [bkz: Visual Studio'da Boost.Test'i kullanın.](how-to-use-boost-test-for-cpp.md)

- **CTest** desteği, C++ iş yüküyle **Masaüstü geliştirmenin** bir parçası olan **C++ CMake araçları** bileşenine dahildir. Daha fazla bilgi için [bkz: Visual Studio'da CTest'i kullanın.](how-to-use-ctest-for-cpp.md)

**Visual Studio 2015 ve daha önce**

Visual Studio Marketplace'te Google Test bağdaştırıcısını ve Boost.Test Adaptörü uzantılarını indirebilirsiniz. Bunları Google Test için Boost.Test ve [Test bağdaştırıcısı için](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)Test [bağdaştırıcısı](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) olarak bulun.

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde C++ birim testi ile başlamanıza neden olan temel adımlar gösterin. Temel yapılandırma, hem Microsoft hem de Google Test çerçeveleri için benzerdir. Boost.Test, el ile bir test projesi oluşturmanızı gerektirir.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Visual Studio 2019'da bir test projesi oluşturun

Bir veya daha fazla test projesi içinde testleri tanımlar ve çalıştırın. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz. Varolan bir çözüme yeni bir test projesi eklemek için **Çözüm Gezgini'ndeki Çözüm**düğümüne sağ tıklayın. Açılan menüde**Yeni Proje** **Ekle'yi** > seçin. **Dil'i** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Aşağıdaki resimde, **C++ ile Masaüstü Geliştirme** ve **UWP Geliştirme** iş yükü yüklendiğinde kullanılabilen test projeleri gösterilmektedir:

![VIsual Studio 2019'da C++ Test Projeleri](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Visual Studio 2017'de test projesi oluşturun

Bir veya daha fazla test projesi içinde testleri tanımlar ve çalıştırın. Projeleri, test etmek istediğiniz kodla aynı çözümde oluşturursunuz. Yeni bir test projesi eklemek **için, Çözüm Gezgini'ndeki** Çözüm düğümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. Sol bölmede Visual **C++ Testi'ni**seçin. Ardından, merkez bölmesinden proje türlerinden birini seçin. Aşağıdaki resimde, C++ iş **yüküne sahip Masaüstü Geliştirme** yüklendiğinde kullanılabilen test projeleri gösterilmektedir:

![C++ Test Projeleri](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere referanslar oluşturma

Test altındaki projedeki işlevlere erişimi etkinleştirmek için, test projenizdeki projeye bir başvuru ekleyin. Açılır menü için **Solution Explorer'daki** test proje düğümüne sağ tıklayın. **Referans** **Ekle'yi** > seçin. Başvuru Ekle iletişim kutusunda, test etmek istediğiniz proje(ler)'i seçin.

![Başvuru ekleme](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Nesne veya kitaplık dosyalarına bağlantı

Test kodu sınamak istediğiniz işlevleri dışa aktarmazsa, test projesinin bağımlılıklarına .obj veya .lib dosyaları ekleyebilirsiniz. Daha fazla bilgi için [bkz.](/visualstudio/test/how-to-use-microsoft-test-framework-for-cpp#object_files)

### <a name="add-include-directives-for-header-files"></a>Üstbilgi dosyaları için #include yönergeleri ekleme

Ardından, birim testi *.cpp* dosyanızda, test etmek istediğiniz türleri ve işlevleri bildiren üstbilgi dosyaları için bir `#include` yönerge ekleyin. Yazın `#include "` ve sonra IntelliSense seçim yardımcı olmak için etkinleştirecektir. Ek üstbilgi için tekrarlayın.

![Ekle yönergeleri](media/cpp-add-includes-test-project.png)

Kaynak dosyadaki her bir include deyiminde tam yol yazmak zorunda kalmamak için, **Project** > **Properties** > **C/C++** > **Genel** > Ek Dahil**Dizinler'e**gerekli klasörleri ekleyebilirsiniz.

### <a name="write-test-methods"></a>Test yöntemleri yazma

> [!NOTE]
> Bu bölümde C/C++ için Microsoft Birim Sınama Çerçevesi sözdizimi gösterilmektedir. Burada belgelenmiştir: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API başvuru](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test belgeleri için [Google Test astarına](https://github.com/google/googletest/blob/master/googletest/docs/primer.md)bakın. Boost.Test için [bkz.](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html)

Test projenizdeki *.cpp* dosyasında sizin için tanımlanmış bir saplama sınıfı ve yöntemi vardır. Test kodunun nasıl yazılalalabildiğini gösteren bir örnek gösterirler. İmzalar, yöntemleri **Test Gezgini** penceresinden keşfedilebilir hale getiren TEST_CLASS ve TEST_METHOD makroları kullanır.

![Ekle yönergeleri](media/cpp-write-test-methods.png)

TEST_CLASS ve [TEST_METHOD, Microsoft Yerel Test Çerçevesi'nin](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)bir parçasıdır. **Test Gezgini,** desteklenen diğer çerçevelerde benzer şekilde test yöntemlerini keşfeder.

Bir TEST_METHOD geçersiz olarak geri döner. Bir test sonucu oluşturmak için, gerçek `Assert` sonuçları beklenene göre test etmek için sınıftaki statik yöntemleri kullanın. Aşağıdaki örnekte, `MyClass` bir `std::string`. alan bir oluşturucu varsayalım Oluşturucunun sınıfı beklendiği gibi başlatmasını test edebiliriz:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, `Assert::AreEqual` arama nın sonucu testin geçip geçmediğini veya başarısız olup olmadığını belirler. Assert sınıfı, beklenen ve gerçek sonuçları karşılaştırmak için birçok yöntem içerir.

Test sahiplerini, önceliği ve diğer bilgileri belirtmek için test yöntemlerine *özellikler* ekleyebilirsiniz. Daha sonra test **gezgininde**testleri sıralamak ve gruplandırmak için bu değerleri kullanabilirsiniz. Daha fazla bilgi için test [gezgini ile birim testlerini çalıştır'a](run-unit-tests-with-test-explorer.md)bakın.

### <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Windows** > **Test Gezgini'ni**seçin. Aşağıdaki resimde, testleri henüz çalışmamış bir test projesi gösterilmektedir.

   ![Testleri çalıştırmadan önce Gezgini test edin](media/cpp-test-explorer.png)

   > [!NOTE]
   > **Test Gezgini** ile CTest tümleştirmesi henüz kullanılamıyor. CMake ana menüsünden CTest testlerini çalıştırın.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini'ndeki** düğümünü sağ tıklayarak ve **Yap** veya **Yeniden Oluştur'u**seçerek test projesini oluşturun.

1. **Test Gezgini'nde,** **Tümünü Çalıştır'ı**seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinleştirilmiş hata ayıklama modunda çalıştırmak da dahil olmak üzere diğer seçenekler için bir teste sağ tıklayın. Tüm testleri çalıştırdıktan sonra, pencere hangi testlerin geçtiğini ve hangilerinin başarısız olduğunu gösterir:

![Testler çalıştırıladıktan sonra Gezgintest](media/cpp-test-explorer-passed.png)

Başarısız testler için ileti, nedenini tanılamaya yardımcı olan ayrıntılar sunar. Açılır menü için başarısız olan teste sağ tıklayın. Hata **Ayıklama Seçili Testler'i** seçerek hatanın oluştuğu işlevi gözden geçirin.

**Test Gezgini'ni**kullanma hakkında daha fazla bilgi için test [gezgini ile birim testlerini çalıştır'a](run-unit-tests-with-test-explorer.md)bakın.

Birim testi ile ilgili daha fazla bilgi için [Birim test temellerine](unit-test-basics.md) bakın

## <a name="use-codelens"></a>CodeLens kullanın

**Visual Studio 2017 ve sonrası (Profesyonel ve Kurumsal sürümleri)**

[CodeLens,](../ide/find-code-changes-and-other-history-with-codelens.md) kod düzenleyicisini bırakmadan birim testinin durumunu hızlı bir şekilde görmenizi sağlar.

Bir C++ birimi test projesi için CodeLens'i şu yollardan herhangi biri ile başolarak alabilirsiniz:

- Test projenizi veya çözümünüzü edin ve oluşturun.
- Projenizi veya çözümünüzü yeniden oluşturun.
- **Test Gezgini** penceresinden testleri çalıştırın.

Para yada başharfe biçüldikten sonra, her birim testinin üstündeki test durumu simgelerini görebilirsiniz.

![C++ CodeLens Simgeleri](media/cpp-test-codelens-icons.png)

Daha fazla bilgi için simgeye tıklayın veya birim testini çalıştırmak veya hata ayıklamak için:

![C++ CodeLens Çalıştır ve Hata Ayıklama](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Birim kodunuzu test edin](unit-test-your-code.md)
