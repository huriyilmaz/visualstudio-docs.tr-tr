---
title: C++ dll 'Leri için birim testleri yazma
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 3bfbe5fd0147a04d6fc6142fd1d722f8f2304586
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287044"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Visual Studio 'da C++ dll 'Leri için birim testleri yazma

Test etmek istediğiniz işlevleri dışa aktarıp vermediğine bağlı olarak, DLL kodunu test etmenin birkaç yolu vardır. Aşağıdaki yollarla birini seçin:

**Birim testleri yalnızca dll 'den aktarılmış işlevleri çağırır:** [C/C++ Için yazma birim testlerinde](writing-unit-tests-for-c-cpp.md)açıklandığı şekilde ayrı bir test projesi ekleyin. Test projesinde, DLL projesine bir başvuru ekleyin.

[DLL projesinden içe aktarılmış işlevlere başvurma](#projectRef)yordamına gidin.

**DLL, bir. exe dosyası olarak oluşturulmuştur:** Ayrı bir test projesi ekleyin. Çıktı nesne dosyasına bağlayın.

[Testleri nesne veya kitaplık dosyalarına bağlamak için](#objectRef)yordama gidin.

**Birim Testlerı dll 'den verilmeyen üye olmayan işlevleri çağırır ve DLL statik kitaplık olarak oluşturulabilir:** DLL projesini bir *. lib* dosyasına derlenmek üzere değiştirin. Test edilen projeye başvuran ayrı bir test projesi ekleyin.

Bu yaklaşım, testlerin dışarıya aktarılmamış üyeleri kullanmasına izin vermenin avantajına sahiptir, ancak yine de testleri ayrı bir projede tutar.

[DLL 'yi bir statik kitaplığa değiştirme](#staticLink)yordamına gidin.

**Birim testleri, verilmeyen üye olmayan işlevleri çağırmalıdır ve kodun bir dinamik bağlantı kitaplığı (dll) olarak oluşturulması gerekir:** Birim testlerini ürün koduyla aynı projeye ekleyin.

[Aynı projedeki birim testlerini ekleme](#sameProject)yordamına gidin.

## <a name="create-the-tests"></a>Testleri oluşturma

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a>DLL 'yi bir statik kitaplığa dönüştürmek için

- Testlerinizin, DLL projesi tarafından dışarıya aktarılmamış üyeleri kullanması gerekiyorsa ve test edilen proje dinamik bir kitaplık olarak derlendiğinden, onu statik bir kitaplığa dönüştürmeyi düşünün.

  1. **Çözüm Gezgini**' de, test altındaki projenin kısayol menüsünde **Özellikler**' i seçin. Proje **özellikleri** penceresi açılır.

  2. **Yapılandırma özellikleri**  >  **genel**' i seçin.

  3. **Yapılandırma türünü** **statik kitaplık (. lib)** olarak ayarlayın.

  [Testleri nesne veya kitaplık dosyalarına bağlama](#objectRef)yordamıyla devam edin.

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a>Test projesinden içe aktarılmış DLL işlevlerine başvurmak için

- DLL projesi test etmek istediğiniz işlevleri dışa aktardığında, test projesinden kod projesine bir başvuru ekleyebilirsiniz.

  1. Yerel birim testi projesi oluşturun.

      ::: moniker range="vs-2019"

      1. **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin. **Yeni Proje Ekle** iletişim kutusunda, **dili** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Ardından **yerel birim test projesini**seçin.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **Dosya** menüsünde, **Yeni** > **Proje** > **Visual C++** > **Test** > **C++ birim testi projesi**' ni seçin.

      ::: moniker-end

  1. **Çözüm Gezgini**' de, test projesine sağ tıklayın ve ardından başvuru **Ekle**' yi seçin  >  **Reference**.

  1. **Projeler**ve ardından sınanacak proje ' yi seçin.

       **Ekle** düğmesini seçin.

  1. Test projesinin özelliklerinde, test edilen projenin konumunu Içerme dizinlerine ekleyin.

       **Yapılandırma özellikleri**  >  **VC + + dizinler**  >  **içerme dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

  [Birim testlerini yazmak](#addTests)için gidin.

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a>Testleri nesne veya kitaplık dosyalarına bağlamak için

- DLL test etmek istediğiniz işlevleri dışa aktarmaz, Output *. obj* veya *. lib* dosyasını test projesinin bağımlılıklarına ekleyebilirsiniz.

  1. Yerel birim testi projesi oluşturun.

      ::: moniker range="vs-2019"

      1. **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin. **Yeni Proje Ekle** iletişim kutusunda, **dili** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Ardından **yerel birim test projesini**seçin.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **Dosya** menüsünde, **Yeni** > **Proje** > **Visual C++** > **Test** > **C++ birim testi projesi**' ni seçin.

      ::: moniker-end

  2. **Çözüm Gezgini**, test projesinin kısayol menüsünde **Özellikler**' i seçin.

  3. **Yapılandırma özellikleri**  >  **bağlayıcı**  >  **Input**  >  **ek bağımlılıklar**gir ' i seçin.

       **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının adlarını ekleyin. Tam yol adlarını kullanmayın.

  4. **Yapılandırma özellikleri**  >  **Bağlayıcısı**  >  **genel**  >  **Ek kitaplık dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının dizin yolunu ekleyin. Yol, genellikle test kapsamındaki projenin Build klasöründedir.

  5. **Yapılandırma özellikleri**  >  **VC + + dizinler**  >  **içerme dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

  [Birim testlerini yazmak](#addTests)için gidin.

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a>Aynı projeye birim testleri eklemek için

1. Ürün kodu proje özelliklerini, birim testi için gereken üst bilgileri ve kitaplık dosyalarını içerecek şekilde değiştirin.

   1. **Çözüm Gezgini**' de, test altındaki projenin kısayol menüsünde, **Özellikler**' i seçin. Proje **özellikleri** penceresi açılır.

   2. **Yapılandırma özellikleri**  >  **VC + + dizinleri**' ni seçin.

   3. Ekleme ve kitaplık dizinlerini düzenleyin:

       |Dizin|Özellik|
       |-|-|
       |**Dizinleri dahil et** | **$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Kitaplık dizinleri** | **$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. C++ birim testi dosyası Ekle:

   - **Çözüm Gezgini**, projenin kısayol menüsünde **Add**  >  **Yeni öğe**Ekle  >  **C++ birim testi**' ni seçin.

   [Birim testlerini yazmak](#addTests)için gidin.

## <a name="write-the-unit-tests"></a><a name="addTests"></a>Birim testlerini yazma

1. Her birim test kodu dosyasında, `#include` test edilen projenin üst bilgileri için bir ifade ekleyin.

2. Birim test kodu dosyalarına test sınıfları ve yöntemleri ekleyin. Örneğin:

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

## <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Windows**  >  **Test Gezgini**' ni seçin.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinken hata ayıklama modunda çalıştırmak dahil diğer seçenekler için teste sağ tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
- [Microsoft. VisualStudio. TestTools. CppUnitTestFramework API başvurusu](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [İzlenecek yol: Dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İçeri ve dışarı aktarma](/cpp/build/importing-and-exporting)
- [Hızlı başlangıç: Test Gezgini ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)
