---
title: C++ DLL'leri için birim testleri yazma
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279279"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Visual Studio'da C++ DLL'leri için birim testleri yazma

DLL kodu, test etmek istediğiniz işlevleri dışa aktarır, bağlı olarak test etmek için birkaç yolu vardır. Aşağıdaki yöntemlerden birini seçin:

**Birim testleri yalnızca dll 'den aktarılmış işlevleri çağırır:** [C/C++için yazma birim testlerinde](writing-unit-tests-for-c-cpp.md)açıklandığı şekilde ayrı bir test projesi ekleyin. Test projesinde DLL projesinden bir başvuru ekleyin.

[DLL projesinden içe aktarılmış işlevlere başvurma](#projectRef)yordamına gidin.

**DLL, bir. exe dosyası olarak oluşturulmuştur:** Ayrı bir test projesi ekleyin. Bu çıkış nesnesi dosyasına bağlayın.

[Testleri nesne veya kitaplık dosyalarına bağlamak için](#objectRef)yordama gidin.

**Birim Testlerı dll 'den verilmeyen üye olmayan işlevleri çağırır ve DLL statik kitaplık olarak oluşturulabilir:** DLL projesini bir *. lib* dosyasına derlenmek üzere değiştirin. Test altındaki projeye başvuran ayrı bir test projesi ekleyin.

Bu yaklaşım, izin verilen olmayan üyeleri kullanabilirsiniz, ancak testleri ayrı bir projede hala devam testlerinizi avantajına sahiptir.

[DLL 'yi bir statik kitaplığa değiştirme](#staticLink)yordamına gidin.

**Birim testleri, verilmeyen üye olmayan işlevleri çağırmalıdır ve kodun bir dinamik bağlantı kitaplığı (dll) olarak oluşturulması gerekir:** Birim testlerini ürün koduyla aynı projeye ekleyin.

[Aynı projedeki birim testlerini ekleme](#sameProject)yordamına gidin.

## <a name="create-the-tests"></a>Testleri oluşturma

### <a name="staticLink"></a>DLL 'yi bir statik kitaplığa dönüştürmek için

- Testlerinizi DLL proje tarafından dışa aktarılmaz üyeleri kullanmalıdır ve test altındaki projeye bir dinamik kitaplık olarak oluşturulduysa, bir statik kitaplığa dönüştürmeyi düşünün.

  1. **Çözüm Gezgini**' de, test altındaki projenin kısayol menüsünde **Özellikler**' i seçin. Proje **özellikleri** penceresi açılır.

  2. **Yapılandırma özellikleri** > **genel**' i seçin.

  3. **Yapılandırma türünü** **statik kitaplık (. lib)** olarak ayarlayın.

  [Testleri nesne veya kitaplık dosyalarına bağlama](#objectRef)yordamıyla devam edin.

### <a name="projectRef"></a>Test projesinden içe aktarılmış DLL işlevlerine başvurmak için

- Ardından DLL proje test etmek istediğiniz işlevleri dışa aktarır, kod projesine test projesinden bir başvuru ekleyebilirsiniz.

  1. Yerel birim testi projesi oluşturun.

      ::: moniker range="vs-2019"

      1. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin. **Yeni Proje Ekle** Iletişim kutusunda **dil** ' i ayarlayın C++ ve arama kutusuna "test" yazın. Ardından **yerel birim test projesini**seçin.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **Dosya** menüsünde, **Yeni** > **projesi** > **Visual C++**  > **Test** >  **C++ birim testi projesi**' ni seçin.

      ::: moniker-end

  1. **Çözüm Gezgini**, test projesine sağ tıklayın ve ardından > **başvuru** **Ekle** ' yi seçin.

  1. **Projeler**ve ardından sınanacak proje ' yi seçin.

       **Ekle** düğmesini seçin.

  1. Test projesi için Özellikler'de test edilen projenin konumunu ek içerik dizinlerine ekleyin.

       **Yapılandırma özellikleri** > **VC + + dizinler** > **dizinleri içer**' i seçin.

       **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

  [Birim testlerini yazmak](#addTests)için gidin.

### <a name="objectRef"></a>Testleri nesne veya kitaplık dosyalarına bağlamak için

- DLL test etmek istediğiniz işlevleri dışa aktarmaz, Output *. obj* veya *. lib* dosyasını test projesinin bağımlılıklarına ekleyebilirsiniz.

  1. Yerel birim testi projesi oluşturun.

      ::: moniker range="vs-2019"

      1. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin. **Yeni Proje Ekle** Iletişim kutusunda **dil** ' i ayarlayın C++ ve arama kutusuna "test" yazın. Ardından **yerel birim test projesini**seçin.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **Dosya** menüsünde, **Yeni** > **projesi** > **Visual C++**  > **Test** >  **C++ birim testi projesi**' ni seçin.

      ::: moniker-end

  2. **Çözüm Gezgini**, test projesinin kısayol menüsünde **Özellikler**' i seçin.

  3. **Ek bağımlılıklar** >  > **bağlayıcı** >  **yapılandırma özellikleri** ' ni seçin.

       **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının adlarını ekleyin. Tam yol adlarını kullanmayın.

  4. **Yapılandırma özellikleri** > **bağlayıcı** > **genel** > **Ek kitaplık dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının dizin yolunu ekleyin. Genellikle test edilen projenin derleme klasörü içindeki yoldur.

  5. **Yapılandırma özellikleri** > **VC + + dizinler** > **dizinleri içer**' i seçin.

       **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

  [Birim testlerini yazmak](#addTests)için gidin.

### <a name="sameProject"></a>Aynı projeye birim testleri eklemek için

1. Üst bilgiler ve birim testi için gerekli olan kitaplık dosyalarını içerecek şekilde ürün kodu proje özelliklerini değiştirin.

   1. **Çözüm Gezgini**' de, test altındaki projenin kısayol menüsünde, **Özellikler**' i seçin. Proje **özellikleri** penceresi açılır.

   2.  > **VC + + dizinleri** **yapılandırma özellikleri** ' ni seçin.

   3. Dahil et ve kitaplık dizinlerini düzenleyin:

       |Dizin|Özellik|
       |-|-|
       |**Dizinleri dahil et** | **$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Kitaplık dizinleri** | **$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. Bir C++ birim testi dosyası ekleyin:

   - **Çözüm Gezgini**, projenin kısayol menüsünde, **Ekle** > **Yeni öğe** >  **C++ birim testi**' ni seçin.

   [Birim testlerini yazmak](#addTests)için gidin.

## <a name="addTests"></a>Birim testlerini yazma

1. Her birim test kodu dosyasında, test edilen projenin üst bilgileri için bir `#include` açıklaması ekleyin.

2. Birim testi kod dosyalarına test sınıfları ve yöntemleri ekleyin. Örneğin:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Testleri çalıştırın

1. **Test** menüsünde **Windows** > **Test Gezgini**' ni seçin.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin veya çalıştırmak istediğiniz belirli testleri seçin. Bir test etkin kesme noktaları ile hata ayıklama modunda çalıştırmak dahil, diğer seçenekler için sağ tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [C/için birim testleri yazmaC++](writing-unit-tests-for-c-cpp.md)
- [Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [İzlenecek yol: dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İçeri ve dışarı aktarma](/cpp/build/importing-and-exporting)
- [Hızlı başlangıç: Test Gezgini ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)
