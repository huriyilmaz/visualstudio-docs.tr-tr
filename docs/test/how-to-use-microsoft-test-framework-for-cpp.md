---
title: C++ için Microsoft Birim Testi Çerçevesini Kullanma
description: C++ kodunuz için birim testleri oluşturmak için C++ için Microsoft Birim Test Çerçevesi'ni kullanın.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75755560"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Visual Studio'da C++ için Microsoft Birim Test Çerçevesini kullanma

C++ için Microsoft Birim Sınama Çerçevesi varsayılan olarak C++ iş **yüküne sahip Masaüstü Geliştirme'ye** dahildir.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a>Birim testlerini ayrı bir projeye yazmak için

Genellikle, test kodunuzu test etmek istediğiniz kodla aynı çözümde kendi projesinde çalıştırın. Yeni bir test projesi kurmak ve yapılandırmak [için C/C++ için birim testleri yazma'ya](writing-unit-tests-for-c-cpp.md)bakın.

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>Aynı projede birim testleri yazmak için

Bazı durumlarda, örneğin bir DLL'de dışa aktarılmaz işlevleri sınarken, sınama yaptığınız programla aynı projede testler oluşturmanız gerekebilir. Aynı projede birim testleri yazmak için:

1. Birim sınama için gerekli olan üstbilgi ve kitaplık dosyalarını içerecek şekilde proje özelliklerini değiştirin.

   1. Çözüm Gezgini'nde, test ettiğiniz projenin kısayol menüsünde **Özellikler'i**seçin. Proje özellikleri penceresi açılır.

   1. Özellik Sayfaları iletişim kutusunda, **Configuration Properties** > **VC++ Dizinlerini**seçin.

   1. Aşağıdaki satırlarda aşağı ok tıklayın ve ** \<>edit **seçin. Bu yolları ekleyin:

      | Dizin | Özellik |
      |-| - |
      | **Dizinleri Dahil Et** | **$(VCInstallDir)Yardımcı\VS\UnitTest\include** |
      | **Kütüphane Dizinleri** | **$(VCInstallDir)Yardımcı\VS\UnitTest\lib** |

1. C++ Birim Test dosyası ekle:

   - **Solution Explorer'daki** proje düğümüne sağ tıklayın ve**Yeni Öğe** > C++ Dosyası **Ekle'yi** > **(.cpp)** seçin.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a>Testleri nesne veya kitaplık dosyalarına bağlamak için

Test altındaki kod, test etmek istediğiniz işlevleri dışa aktarmazsa, test projesinin bağımlılıklarına **.obj** veya **.lib** dosyası çıktısını ekleyebilirsiniz. Test projesinin özelliklerini birim sınama için gerekli üstbilgi ve kitaplık veya nesne dosyalarını içerecek şekilde değiştirin.

1. Çözüm Gezgini'nde, test projesinin kısayol menüsünde **Özellikler'i**seçin. Proje özellikleri penceresi açılır.

1. Yapılandırma **Özellikleri** > **Bağlayıcı** > **Giriş** sayfasını seçin ve ek **bağımlılıkları**seçin.

   **Edit'i**seçin ve **.obj** veya **.lib** dosyalarının adlarını ekleyin. Tam yol adlarını kullanmayın.

1. Yapılandırma **Özellikleri** > **Bağlantı Genel** > **General** sayfasını seçin ve ardından **Ek Kitaplık Dizinleri'ni**seçin.

   **Edit'i**seçin ve **.obj** veya **.lib** dosyalarının dizin yolunu ekleyin. Yol genellikle test altındaki projenin yapı klasöründedir.

1. Yapılandırma **Özellikleri** > **VC++ Dizinleri** sayfasını seçin ve ardından **Dizinleri Ekle'yi**seçin.

   **Edit'i**seçin ve ardından projenin üstbilgi dizinini test altında ekleyin.

## <a name="write-the-tests"></a>Testleri yazın

Test sınıfları içeren herhangi bir *.cpp* dosyası "CppUnitTest.h" içermeli ve `using namespace Microsoft::VisualStudio::CppUnitTestFramework`.. Test projesi zaten sizin için yapılandırılmıştır. Ayrıca bir ad alanı tanımı ve başlamak için bir TEST_METHOD ile TEST_CLASS içerir. Sınıf ve yöntem makrolarında ad alanı adını ve parantez içinde adları değiştirebilirsiniz.

Test çerçevesi, test modüllerini, sınıfları ve yöntemlerini başlatma ve testler tamamlandıktan sonra kaynakların temizlenmesi için özel makrolar tanımlar. Bu makrolar, bir sınıf veya yönteme ilk erişilmeden önce ve son sınama çalıştırıldıktan sonra yürütmek için kod oluşturur. Daha fazla bilgi [için, Bkz. Başlangıç ve temizleme.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)

Test koşullarını tanımlamak için [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) sınıfındaki statik yöntemleri kullanın. **Çıkış Penceresine**ileti yazmak için [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) sınıfını kullanın. Test yöntemlerine öznitelikleri ekleme

## <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Windows** > **Test Gezgini'ni**seçin.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini'ndeki** düğümünü sağ tıklayarak ve **Yap** veya **Yeniden Oluştur'u**seçerek test projesini oluşturun.

1. **Test Gezgini'nde,** **Tümünü Çalıştır'ı**seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinleştirilmiş hata ayıklama modunda çalıştırmak da dahil olmak üzere diğer seçenekler için bir teste sağ tıklayın.

1. `Logger` Çıktı **Penceresinde,** sınıf tarafından yazılan iletileri görüntülemek için açılan daki **Testleri** seçin:

   ![C++ Çıkış Penceresi test iletilerini gösteriyor](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Gruplandırmayı etkinleştirmek için özellikleri tanımlama

**Test**Gezgini'nde testleri kategorilere ayırmanızı ve gruplandırmanızı sağlayan test yöntemleriyle ilgili özellikler tanımlayabilirsiniz. Bir özellik tanımlamak için `TEST_METHOD_ATTRIBUTE` makroyu kullanın. Örneğin, adlı `TEST_MY_TRAIT`bir özellik tanımlamak için:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Birim testlerinizde tanımlanan özelliği kullanmak için:

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

### <a name="c-trait-attribute-macros"></a>C++ özellik öznitelik makroları

Aşağıdaki önceden tanımlanmış özellikler . `CppUnitTest.h` Daha fazla bilgi için [C++ API başvurusu için Microsoft Birimi Test Çerçevesi'ne](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)bakın.

|Makro|Açıklama|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Bir özellik tanımlamak için TEST_METHOD_ATTRIBUTE makroyu kullanın.|
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış Sahip özelliğini kullanın.|
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelikleri atamak için önceden tanımlanmış Öncelik özelliğini kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Quickstart: Test Gezgini ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)
