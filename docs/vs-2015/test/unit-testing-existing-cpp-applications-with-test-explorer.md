---
title: Test Gezgini ile mevcut C++ uygulamalarının Birim testi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 68bff8dbe2d0e5d85c8b18eeafaeaad06ba3982e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540081"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Test Gezgini ile mevcut C++ uygulamalarında birim testi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mevcut bir uygulamayı değiştirmeden önce, birim testlerle iyi bir kapsama sahip olduğundan emin olmanızı öneririz. Bu, değişikliklerinizin hata sunmadığından emin olmanızı sağlar. Uygulamanın zaten birim testleri yoksa, bu konuda gösterilen teknikleri kullanarak bunları ekleyebilirsiniz. Bu konu başlığı altında, kodunuzu test etme ve sonra testleri oluşturma, yazma ve son çalıştırma konularında karar vermeden itibaren mevcut Visual C++ kodu için birim testlerinin nasıl ekleneceği açıklanmaktadır.

## <a name="deciding-how-to-test-your-code"></a>Kodunuzun nasıl test olacağına karar verme
 Mevcut C++ projesini açın ve birim testlerini nasıl eklemek istediğinize karar vermek için bunu inceleyin. Koddaki bağımlılıkları görmenizi ve parçaların nasıl etkileşime gireceğini anlamanıza yardımcı olan bazı modelleme araçlarını kullanmak isteyebilirsiniz. Daha fazla bilgi için bkz. [Kodu görselleştirme](../modeling/visualize-code.md).

 Değişikliklerinizi küçük görevlere ayırmanızı öneririz. Her küçük değişiklikten önce, aynı olmaya devam edecek davranışın yönleri için birim testlerini yazın. Bu testler, değişikliği yaptıktan sonra geçiş yapmaya devam edecektir. Örneğin, bir sıralama işlevini, bir kişi listesini ilk adı yerine soyadı olacak şekilde sıralamayı planlıyorsanız, tüm giriş adlarının çıktıda göründüğünü doğrulayan bir birim testi yazabilirsiniz. Değişikliği yaptıktan sonra yeni davranış için yeni birim testleri eklemek isteyebilirsiniz.

 Pratik ise, birim testlerinizin çoğu veya hepsi yalnızca dışarıya aktarılmış işlevleri kullanmalıdır. Ancak tüm uygulamanın yalnızca küçük bir bölümünü değiştiriyorsanız, verilmeyen işlevleri kullanmak isteyebilirsiniz. Örneğin, iç işlevleri çağıran testlerin veya iç değişkenlerin değerlerini ayarlamış ve alan testlerin olmasını isteyebilirsiniz.

 Test etmek istediğiniz arabirimleri kullanıma sunduğundan bağımsız olarak, ürün kodunu test etmenin birkaç yolu vardır. Aşağıdaki yollarla birini seçin:

 **Birim testleri yalnızca test kapsamındaki koddan içe aktarılmış işlevleri kullanır:** Ayrı bir test projesi ekleyin. Test projesinde, test altındaki projeye bir başvuru ekleyin.

 [Test projesinden içe aktarılmış işlevlere başvurmak için](#projectRef)yordama gidin.

 **Test edilen kod bir. exe dosyası olarak oluşturulmuştur:** Ayrı bir test projesi ekleyin. Çıktı nesne dosyasına bağlayın.

 [Testleri nesne veya kitaplık dosyalarına bağlamak için](#objectRef)yordama gidin.

 **Birim testleri özel işlevler ve veriler kullanmalıdır ve test edilen kod statik kitaplık olarak oluşturulabilir:** Test altındaki projeyi bir. lib dosyasına derlenmek üzere değiştirin. Test edilen projeye başvuran ayrı bir test projesi ekleyin.

 Bu yaklaşım, testlerinizin özel Üyeler kullanmasına izin vermenin avantajına sahiptir, ancak yine de testleri ayrı bir projede tutar. Ancak, bir dinamik bağlantı kitaplığı (. dll) olması gereken bazı uygulamalar için uygun olmayabilir.

 [Test altındaki kodu statik bir kitaplığa değiştirme](#staticLink)yordamına gidin.

 **Birim testlerin özel işlevleri ve verileri kullanması ve kodun bir dinamik bağlantı kitaplığı (dll) olarak oluşturulması gerekir:** Birim testlerini ürün koduyla aynı projeye ekleyin.

 [Aynı projedeki birim testlerini ekleme](#sameProject)yordamına gidin.

## <a name="creating-the-tests"></a>Testleri oluşturma

### <a name="to-change-the-code-under-test-to-a-static-library"></a><a name="staticLink"></a>Test altındaki kodu statik bir kitaplığa değiştirmek için

- Testlerinizin test edilen bir proje tarafından dışarıya aktarılmamış üyeleri kullanması gerekiyorsa ve test altındaki proje dinamik bir kitaplık olarak derlendiğinden, onu statik bir kitaplığa dönüştürmeyi düşünün.

  1. Çözüm Gezgini ' de, test altındaki projenin kısayol menüsünde **Özellikler**' i seçin. Proje Özellikleri penceresi açılır.

  2. **Yapılandırma özellikleri**, **genel**' i seçin.

  3. **Yapılandırma türünü** **statik kitaplık (. lib)** olarak ayarlayın.

  [Testleri nesne veya kitaplık dosyalarına bağlama](#objectRef)yordamıyla devam edin.

### <a name="to-reference-exported-functions-from-the-test-project"></a><a name="projectRef"></a>Test projesinden aktarılmış işlevlere başvurmak için

- Test edilen bir proje test etmek istediğiniz işlevleri dışa aktardığında, test projesinden kod projesine bir başvuru ekleyebilirsiniz.

  1. C++ test projesi oluşturun.

      1. **Dosya** menüsünde, **Yeni**, **Proje**, **Visual C++, test**, **C++ birim testi projesi**' ni seçin.

  2. Çözüm Gezgini, test projesinin kısayol menüsünde, **Başvurular**' ı seçin. Proje Özellikleri penceresi açılır.

  3. **Ortak özellikler**, **çerçeve ve başvurular**' ı seçin ve ardından **Yeni Başvuru Ekle** düğmesini seçin.

  4. **Projeler**ve ardından sınanacak proje ' yi seçin.

       **Ekle** düğmesini seçin.

  5. Test projesinin özelliklerinde, test edilen projenin konumunu Içerme dizinlerine ekleyin.

       **Yapılandırma özellikleri**, **VC + + dizinleri**, **içerme dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

  [Birim testlerini yazmaya](#addTests)gidin.

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a>Testleri nesne veya kitaplık dosyalarına bağlamak için

- Test edilen kod test etmek istediğiniz işlevleri dışa aktarmadığından, Output **. obj** veya **. lib** dosyasını test projesinin bağımlılıklarına ekleyebilirsiniz.

  1. C++ test projesi oluşturun.

      1. **Dosya** menüsünde, **Yeni**, **Proje**, **Visual C++, test**, **C++ birim testi projesi**' ni seçin.

  2. Çözüm Gezgini, test projesinin kısayol menüsünde **Özellikler**' i seçin. Proje Özellikleri penceresi açılır.

  3. **Yapılandırma özellikleri**, **bağlayıcı**, **giriş**, **ek bağımlılıklar**' ı seçin.

       **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının adlarını ekleyin. Tam yol adlarını kullanmayın.

  4. **Yapılandırma özellikleri**, **bağlayıcı**, **genel**, **Ek kitaplık dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının dizin yolunu ekleyin. Yol, genellikle test kapsamındaki projenin Build klasöründedir.

  5. **Yapılandırma özellikleri**, **VC + + dizinleri**, **içerme dizinleri**' ni seçin.

       **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

  [Birim testlerini yazmaya](#addTests)gidin.

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a>Aynı projeye birim testleri eklemek için

1. Ürün kodu proje özelliklerini, birim testi için gereken üst bilgileri ve kitaplık dosyalarını içerecek şekilde değiştirin.

   1. Çözüm Gezgini ' de, test altındaki projenin kısayol menüsünde, Özellikler ' i seçin. Proje Özellikleri penceresi açılır.

   2. **Yapılandırma özellikleri**, **VC + + dizinleri**' ni seçin.

   3. Ekleme ve kitaplık dizinlerini düzenleyin:

       |Özellik|Değer|
       |-|-|
       |**Dizinleri dahil et**|**$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Kitaplık dizinleri**|**$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. C++ birim testi dosyası Ekle:

   - Çözüm Gezgini, projenin kısayol menüsünde, **Ekle**, **Yeni öğe**' yi ve ardından **C++ birim testi**' ni seçin.

   [Birim testlerini yazmaya](#addTests)gidin.

## <a name="writing-the-unit-tests"></a><a name="addTests"></a>Birim testlerini yazma

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

   Daha fazla bilgi için bkz. [Test Gezgini Ile birim testi yerel kodu](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c).

## <a name="run-the-tests"></a>Testleri çalıştırma

1. **Görünüm** menüsünde **diğer pencereler**, **Test Gezgini**' ni seçin.

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

   Daha fazla bilgi için bkz. [hızlı başlangıç: Test Gezgini Ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md).
