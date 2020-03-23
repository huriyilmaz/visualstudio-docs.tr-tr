---
title: C++ DL'ler için Birim testleri yazma
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279279"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Visual Studio'da C++ DL'ler için birim testleri yazın

DLL kodunu sınamak istediğiniz işlevleri dışa mı dışa aktarmadığına bağlı olarak, sınamanın birkaç yolu vardır. Aşağıdaki yollardan birini seçin:

**Birim testleri yalnızca DLL'den dışa aktarılan işlevleri çağırır:** [C/C++ için Yazma birimi testlerinde](writing-unit-tests-for-c-cpp.md)açıklandığı gibi ayrı bir test projesi ekleyin. Test projesinde, DLL projesine bir başvuru ekleyin.

Yordamı git [DLL projesinden dışa aktarılan işlevlere başvurmak](#projectRef)için.

**DLL bir .exe dosyası olarak oluşturulmuştur:** Ayrı bir test projesi ekleyin. Çıktı nesnesi dosyasına bağla.

Testleri nesne [veya kitaplık dosyalarına bağlamak için yordamı](#objectRef)gidin.

**Birim testleri, DLL'den dışa aktarılmayan üye olmayan işlevleri çağırır ve DLL statik kitaplık olarak oluşturulabilir:** DLL projesini *.lib* dosyasına derlenebilecek şekilde değiştirin. Test altında projeye başvuran ayrı bir test projesi ekleyin.

Bu yaklaşım, testlerinizin dışa aktarılmaz üyeleri kullanmasına izin vermenin, ancak testleri ayrı bir projede tutmanın avantajına sahiptir.

[DLL'yi statik kitaplık](#staticLink)olarak değiştirmek için yordama gidin.

**Birim testleri dışa aktarılmayan üye olmayan işlevleri çağırmalı ve kod dinamik bağlantı kitaplığı (DLL) olarak oluşturulmalıdır:** Birim testlerini ürün koduyla aynı projeye ekleyin.

Aynı projeye [birim testleri eklemek](#sameProject)için yordamı gidin.

## <a name="create-the-tests"></a>Testleri oluşturma

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a>DLL'yi statik kitaplık olarak değiştirmek için

- Testleriniz dll projesi tarafından dışa aktarılmaz üyeleri kullanması gerekiyorsa ve test altındaki proje dinamik bir kitaplık olarak oluşturulmuşsa, bunu statik bir kitaplık olarak dönüştürmeyi düşünün.

  1. **Çözüm Gezgini'nde,** test altındaki projenin kısayol menüsünde **Özellikler'i**seçin. Proje **Özellikleri** penceresi açılır.

  2. **Yapılandırma Özellikleri** > **Genel'i**seçin.

  3. **Yapılandırma Türünü** **Statik Kitaplık (.lib)** olarak ayarlayın.

  Testleri nesne [veya kitaplık dosyalarına bağlamak için](#objectRef)yordamı ile devam edin.

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a>Test projesinden dışa aktarılan DLL işlevlerine başvurmak için

- DLL projesi sınamak istediğiniz işlevleri dışa vuruyorsa, test projesinden kod projesine bir başvuru ekleyebilirsiniz.

  1. Yerel Birim Test Projesi oluşturun.

      ::: moniker range="vs-2019"

      1. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin. Yeni **Proje Ekle** iletişim kutusunda **Dil'i** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Ardından **Yerel Birim Test Projesi'ni**seçin.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **Dosya** menüsünde **Yeni** > **Proje** > **Görsel C++** > **Test** > **C++ Birim Test Projesi'ni**seçin.

      ::: moniker-end

  1. **Çözüm Gezgini'nde,** test projesine sağ tıklayın, ardından**Başvuru** **Ekle'yi** > seçin.

  1. **Projeler'i**ve ardından test edilecek projeyi seçin.

       **Ekle** düğmesini seçin.

  1. Test projesinin özelliklerinde, test altındaki projenin konumunu İçdizim'e ekleyin.

       **Yapılandırma Özellikleri** > **VC++ Dizinleri** > **Et Dizinleri**seçin.

       **Edit'i**seçin ve ardından projenin üstbilgi dizinini test altında ekleyin.

  Birim [testleri yaz' a](#addTests)gidin.

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a>Testleri nesne veya kitaplık dosyalarına bağlamak için

- DLL test etmek istediğiniz işlevleri dışa aktarmazsa, test projesinin bağımlılıklarına *.obj* veya *.lib* dosyası çıktısını ekleyebilirsiniz.

  1. Yerel Birim Test Projesi oluşturun.

      ::: moniker range="vs-2019"

      1. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin. Yeni **Proje Ekle** iletişim kutusunda **Dil'i** C++ olarak ayarlayın ve arama kutusuna "test" yazın. Ardından **Yerel Birim Test Projesi'ni**seçin.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. **Dosya** menüsünde **Yeni** > **Proje** > **Görsel C++** > **Test** > **C++ Birim Test Projesi'ni**seçin.

      ::: moniker-end

  2. **Çözüm Gezgini'nde**, test projesinin kısayol menüsünde **Özellikler'i**seçin.

  3. **Yapılandırma Özellikleri** > **Bağlayıcı** > **Girişi** > **Ek Bağımlılıkları**seçin.

       **Edit'i**seçin ve **.obj** veya **.lib** dosyalarının adlarını ekleyin. Tam yol adlarını kullanmayın.

  4. **Yapılandırma Özellikleri** > **Bağlantı Genel** > **General** > **Ek Kitaplık Dizinleri**seçin.

       **Edit'i**seçin ve **.obj** veya **.lib** dosyalarının dizin yolunu ekleyin. Yol genellikle test altındaki projenin yapı klasöründedir.

  5. **Yapılandırma Özellikleri** > **VC++ Dizinleri** > **Et Dizinleri**seçin.

       **Edit'i**seçin ve ardından projenin üstbilgi dizinini test altında ekleyin.

  Birim [testleri yaz' a](#addTests)gidin.

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a>Aynı projeye birim testleri eklemek için

1. Birim sınama için gerekli olan üstbilgi ve kitaplık dosyalarını içerecek şekilde ürün kodu proje özelliklerini değiştirin.

   1. **Çözüm Gezgini'nde,** test altındaki projenin kısayol menüsünde **Özellikler'i**seçin. Proje **Özellikleri** penceresi açılır.

   2. **Yapılandırma Özellikleri** > **VC++ Dizinleri'ni**seçin.

   3. Ekle ve Kitaplık dizinlerini edin:

       |Dizin|Özellik|
       |-|-|
       |**Dizinleri Dahil Et** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Kütüphane Dizinleri** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. C++ Birim Test dosyası ekle:

   - **Solution Explorer'da,** projenin kısayol menüsünde Yeni**Öğe** > **C++ Birim Testi** **Ekle'yi** > seçin.

   Birim [testleri yaz' a](#addTests)gidin.

## <a name="write-the-unit-tests"></a><a name="addTests"></a>Birim testlerini yazma

1. Her birim test kodu dosyasında, test altındaki projenin üstbilgileri için bir `#include` deyim ekleyin.

2. Birim test kodu dosyalarına test sınıfları ve yöntemleri ekleyin. Örnek:

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

1. **Test** menüsünde **Windows** > **Test Gezgini'ni**seçin.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini'ndeki** düğümünü sağ tıklayarak ve **Yap** veya **Yeniden Oluştur'u**seçerek test projesini oluşturun.

1. **Test Gezgini'nde,** **Tümünü Çalıştır'ı**seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinleştirilmiş hata ayıklama modunda çalıştırmak da dahil olmak üzere diğer seçenekler için bir teste sağ tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Başvuru](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Walkthrough: Dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İthalat ve ihracat](/cpp/build/importing-and-exporting)
- [Quickstart: Test Gezgini ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)
