---
title: C++ için Microsoft Birim Testi Çerçevesini Kullanma
description: C++ Kodunuzun birim testlerini oluşturmak C++ Için Microsoft birim testi çerçevesini kullanın.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: 789430e18dfe8e5f7db19273e7298af2f078c0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755560"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Microsoft birim testi çerçevesi Visual Studio'da C++ için kullanın

C++ için Microsoft birim testi çerçevesi varsayılan olarak dahil edilen **C++ ile masaüstü geliştirme** iş yükü.

## <a name="separate_project"></a> Ayrı bir projede birim testleri yazma

Genellikle, test kodunuzu test etmek istediğiniz kodu aynı çözümde kendi projesi içinde çalıştırın. Ayarlama ve yeni bir test projesi yapılandırma için bkz: [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="same_project"></a> Aynı projede birim testleri yazma

Bazı durumlarda, örneğin, bir DLL 'de verilemeyen işlevleri test ederken, test etmekte olduğunuz programla aynı projede testleri oluşturmanız gerekebilir. Aynı projede birim testleri yazmak için:

1. Proje özelliklerini, üst bilgiler ve birim testi için gerekli olan kitaplık dosyalarını içerecek şekilde değiştirin.

   1. Çözüm Gezgini, test ettiğiniz projenin kısayol menüsünde **Özellikler**' i seçin. Proje Özellikleri penceresi açılır.

   1. Özellik sayfaları iletişim kutusunda, **VC + + dizinleri** > **yapılandırma özellikleri** ' ni seçin.

   1. Aşağıdaki satırlardaki aşağı oka tıklayın ve **\<> Düzenle**' yi seçin. Şu yolları ekleyin:

      | Directory | Özellik |
      |-| - |
      | **Ekleme kodu dizinleri** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\include** |
      | **Kitaplık dizinleri** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\lib** |

1. Bir C++ birim testi dosyası ekleyin:

   - **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve > **Yeni öğe** >  **C++ dosyası (. cpp)** **Ekle** ' yi seçin.

## <a name="object_files"></a> Testleri nesneye veya kitaplık dosyalarına bağlama

Test edilen kod test etmek istediğiniz işlevleri dışa aktarmazsa, Output **. obj** veya **. lib** dosyasını test projesinin bağımlılıklarına ekleyebilirsiniz. Test projesinin özelliklerini, birim testi için gereken üst bilgileri ve kitaplığı ya da nesne dosyalarını içerecek şekilde değiştirin.

1. Çözüm Gezgini, test projesinin kısayol menüsünde **Özellikler**' i seçin. Proje Özellikleri penceresi açılır.

1. **Yapılandırma özellikleri** > **bağlayıcı** > **giriş** sayfası ' nı seçin ve ardından **ek bağımlılıklar**' ı seçin.

   Seçin **Düzenle**ve adını ekleyin **.obj** veya **.lib** dosyaları. Tam yol adlarını kullanmayın.

1. **Yapılandırma özellikleri** > **bağlayıcı** > **genel** sayfasını seçin ve ardından **Ek kitaplık dizinleri**' ni seçin.

   Seçin **Düzenle**ve dizin yolunu ekleyin **.obj** veya **.lib** dosyaları. Genellikle test edilen projenin derleme klasörü içindeki yoldur.

1.  > **VC + + dizinleri** sayfasında **yapılandırma özellikleri** ' ni seçin ve ardından **dizinleri dahil et**' i seçin.

   Seçin **Düzenle**ve ardından test edilen projenin üstbilgi dizinini ekleyin.

## <a name="write-the-tests"></a>Testleri yazma

Tüm *.cpp* test sınıflarında dosyasıyla "CppUnitTest.h" içerir ve kullanarak bir deyim için `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Test projesi için zaten yapılandırıldı. Ayrıca bir ad alanı tanımını içerir ve bir TEST_CLASS başlamanızı sağlayacak bir TEST_METHOD ile başlatıldı. Ad alanı adını ve adları, sınıf ve Yöntem makrolarında parantez içinde değiştirebilirsiniz.

Test çerçevesi, test modüllerini, sınıfları ve yöntemleri başlatmak ve testlerin tamamlandıktan sonra kaynakların temizlenmesi için özel makrolar tanımlar. Bu makrolar bir sınıf veya yönteme ilk kez erişildikten sonra ve son test çalıştıktan sonra yürütülecek kodu oluşturur. Daha fazla bilgi için [başlatma ve Temizleme](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Statik yöntemleri kullanın [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) sınıfı test koşulları tanımlayın. Kullanım [Günlükçü](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) sınıfı için ileti yazmak için **çıkış penceresine**. Test yöntemleri için öznitelik Ekle

## <a name="run-the-tests"></a>Testleri çalıştırın

1. Üzerinde **Test** menüsünde seçin **Windows** > **Test Gezgini**.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**, ya da belirli testleri çalıştırmak istediğiniz seçin. Bir test etkin kesme noktaları ile hata ayıklama modunda çalıştırmak dahil, diğer seçenekler için sağ tıklayın.

1. **Çıkış Penceresi** `Logger` sınıfı tarafından yazılmış iletileri görüntülemek için açılan kutuda **testler** ' i seçin:

   ![C++ çıkış penceresine sınama iletileri gösterme](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Gruplandırma etkinleştirmek için özellikleri tanımlayın

Test **Gezgini**'nde testleri kategorilere ayırmanıza ve gruplandırmalarına olanak tanıyan test yöntemlerinde nitelikler tanımlayabilirsiniz. Ayırt edici nitelik tanımlamak için `TEST_METHOD_ATTRIBUTE` makrosu. Örneğin, adlı bir ayırt edici nitelik tanımlamak için `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Tanımlanan niteliği birim testlerinizde kullanmak için:

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

### <a name="c-trait-attribute-macros"></a>C++ ayırt edici öznitelik makroları

Aşağıdaki önceden tanımlanmış nitelikler bulunan `CppUnitTest.h`. Daha fazla bilgi için [Microsoft birim testi çerçevesi için C++ API Başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makrosu|Açıklama|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Ayırt edici nitelik tanımlamak için test_method_attrıbute makrosunu kullanın.|
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış sahip ayırt edici niteliğini kullanın.|
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelikler atamak için önceden tanımlanmış öncelik ayırt edici niteliğini kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: temelli geliştirme, Test Gezgini ile Test](../test/quick-start-test-driven-development-with-test-explorer.md)
