---
title: C++ için Microsoft Birim Testi Çerçevesini Kullanma
description: C++ kodunuz için birim testleri oluşturmak üzere C++ için Microsoft Birim Testi Çerçevesini kullanın.
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: f1df2935fba013a9eaafab17d9fc66fa650e2ca7242e79fbd75c598220aac358
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395188"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Visual Studio'de C++ için Microsoft Birim Testi Çerçevesi'Visual Studio

C++ için Microsoft Birim Testi Çerçevesi, C++ ile Masaüstü Geliştirme iş **yüküne varsayılan olarak** dahil edilir.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Ayrı bir projede birim testleri yazmak için

Genellikle test kodunuzu test etmek istediğiniz kodla aynı çözümde kendi projesinde çalıştırabilirsiniz. Yeni bir test projesi ayarlamak ve yapılandırmak için [bkz. C/C++ için birim testleri yazma.](writing-unit-tests-for-c-cpp.md)

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Aynı projede birim testleri yazmak için

Bazı durumlarda, örneğin bir DLL'de dışarı aktarilmeyen işlevleri test ederken testleri test etmekte olduğu programla aynı projede oluşturmanız gerekir. Aynı projede birim testleri yazmak için:

1. Birim testi için gereken üst bilgileri ve kitaplık dosyalarını içerecek şekilde proje özelliklerini değiştirin.

   1. Bu Çözüm Gezgini, test etmekte olduğunu projenin kısayol menüsünde Özellikler'i **seçin.** Proje özellikleri penceresi açılır.

   1. Özellik Sayfaları iletişim kutusunda Yapılandırma Özellikleri  >  **VC++ Dizinleri'ne tıklayın.**

   1. Aşağıdaki satırlarda aşağı oku seçin ve öğesini **\<Edit>** seçin. Şu yolları ekleyin:

      | Dizin | Özellik |
      |-| - |
      | **Dizinleri Dahil Etmek** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Kitaplık Dizinleri** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. C++ Birim Testi dosyası ekleyin:

   1. Proje düğümüne sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **seçin.**

   1. Yeni Öğe **Ekle iletişim kutusunda** C++ Dosyası **(.cpp)** öğesini seçin, uygun bir ad girin ve ekle'yi **seçin.**

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Testleri nesne veya kitaplık dosyalarına bağlama

Test altındaki kod, test etmek istediğiniz işlevleri dışarı aktaramazsa, *.obj* veya *.lib* çıktısını test projesinin bağımlılıklarına ekleyin. Birim testi için gereken üst bilgileri ve kitaplığı veya nesne dosyalarını içerecek şekilde test projesinin özelliklerini değiştirin.

1. Bu Çözüm Gezgini test projesinin kısayol menüsünde Özellikler'i **seçin.** Proje özellikleri penceresi açılır.

1. Yapılandırma Özellikleri  >  **Linker Girişi sayfasını**  >  **ve** ardından Ek **Bağımlılıklar'ı seçin.**

   **Düzenle'yi** seçin ve *.obj veya* *.lib dosyalarının adlarını* ekleyin. Tam yol adlarını kullanma.

1. Yapılandırma Özellikleri  >  **Linker Genel sayfasını**  >  **ve** ardından Ek Kitaplık **Dizinleri'ne tıklayın.**

   **Düzenle'yi** seçin ve *.obj* veya *.lib* dosyalarının dizin yolunu ekleyin. Yol genellikle test altındaki projenin derleme klasöründe bulunur.

1. Yapılandırma **Özellikleri**  >  **VC++ Dizinleri sayfasını ve** ardından Dizinleri Dahil **Edin'i seçin.**

   **Düzenle'yi** seçin ve ardından projenin üst bilgi dizinini test altına ekleyin.

## <a name="write-the-tests"></a>Testleri yazma

Test sınıflarını içeren herhangi bir *.cpp* dosyası "CppUnitTest.h" içermeli ve için bir using deyimine sahip `using namespace Microsoft::VisualStudio::CppUnitTestFramework` olmalı. Test projesi sizin için zaten yapılandırılmıştır. Ayrıca bir ad alanı tanımı ve başlamanız TEST_CLASS için TEST_METHOD bir ad alanı içerir. Sınıf ve yöntem makrolarında ad alanı adını ve adları parantez içinde değiştirebilirsiniz.

Test çerçevesi, test modüllerini, sınıflarını ve yöntemlerini başlatmaya ve testler tamamlandıktan sonra kaynakların temizlenmesine özel makrolar tanımlar. Bu makrolar, bir sınıf veya yönteme ilk erişilmeden önce ve son test çalıştırildikten sonra yürütülecek kodu üretir. Daha fazla bilgi için bkz. [Başlatma ve temizleme.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)

Test koşullarını tanımlamak için [Assert sınıfındaki](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) statik yöntemleri kullanın. Çıkış Penceresi'a ileti yazmak için [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) **sınıfını kullanın.** Test yöntemlerine öznitelik ekleme

## <a name="run-the-tests"></a>Testleri çalıştırma

1. Test menüsünde **Test** **Gezgini'Windows**  >  **seçin.**

1. Tüm testlerinizi pencerede görünmüyorsa, projedeki düğümüne sağ tıklar ve Derleme veya Yeniden Derleme'yi **Çözüm Gezgini** **projesini** **derleme.**

1. **Test Gezgini'nde,** **Tüm Testleri** Çalıştır'ı seçin veya çalıştırmak istediğiniz testleri seçin. Diğer seçenekler için bir teste sağ tıklayın ve kesme noktaları etkin hata ayıklama modunda çalıştırmayı da içerir.

1. Aşağıdaki **Çıkış Penceresi** **sınıf tarafından** yazılan iletileri görüntülemek için açılan listelerden Testler'i `Logger` seçin:

   ![Test iletilerini Çıkış Penceresi C++ kitaplığı](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Gruplamayı etkinleştirmek için nitelikler tanımlama

Testleri Test Gezgini'nde kategorilere ayırmanız ve gruplandırmanız için test yöntemlerinde **nitelikler tanımlayabilirsiniz.** Bir nitelik tanımlamak için makroyu `TEST_METHOD_ATTRIBUTE` kullanın. Örneğin, adlı bir nitelik tanımlamak `TEST_MY_TRAIT` için:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Birim testlerinde tanımlanan özelliği kullanmak için:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++ nitelik özniteliği makroları

Aşağıdaki önceden tanımlanmış nitelikler içinde *`CppUnitTest.h`* bulunur. Daha fazla bilgi için [bkz. C++ API başvurusu için Microsoft Birim Testi Çerçevesi.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)

|Makro|Açıklama|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Nitelik tanımlamak TEST_METHOD_ATTRIBUTE makrosu kullanın.|
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış Sahip özelliklerini kullanın.|
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelik atamak için önceden tanımlanmış Öncelik niteliklerini kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: Test Gezgini ile test güdümlü geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)
