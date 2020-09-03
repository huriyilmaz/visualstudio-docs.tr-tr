---
title: C++ için Microsoft Birim Testi Çerçevesini Kullanma
description: C++ kodunuz için birim testleri oluşturmak üzere C++ için Microsoft birim testi çerçevesini kullanın.
ms.date: 01/08/2020
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a9393fd248f4e6520c261d405bc624a75d8cf69f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287122"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Visual Studio 'da C++ için Microsoft birim testi çerçevesini kullanma

C++ için Microsoft birim testi çerçevesi, C++ iş yüküne **sahip masaüstü geliştirmeye** varsayılan olarak dahildir.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Birim testlerini ayrı bir projede yazmak için

Genellikle, test kodunuzu test etmek istediğiniz kodla aynı çözümde kendi projesinde çalıştırırsınız. Yeni bir test projesi ayarlamak ve yapılandırmak için bkz. [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Aynı projedeki birim testlerini yazmak için

Bazı durumlarda, örneğin, bir DLL 'de verilemeyen işlevleri test ederken, test etmekte olduğunuz programla aynı projede testleri oluşturmanız gerekebilir. Aynı projedeki birim testlerini yazmak için:

1. Proje özelliklerini, birim testi için gereken üst bilgileri ve kitaplık dosyalarını içerecek şekilde değiştirin.

   1. Çözüm Gezgini, test ettiğiniz projenin kısayol menüsünde **Özellikler**' i seçin. Proje Özellikleri penceresi açılır.

   1. Özellik sayfaları iletişim kutusunda, **yapılandırma özellikleri**  >  **VC + + dizinleri**' ni seçin.

   1. Aşağıdaki satırlarda aşağı oka tıklayın ve öğesini seçin **\<Edit>** . Şu yolları ekleyin:

      | Dizin | Özellik |
      |-| - |
      | **Dizinleri dahil et** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\include** |
      | **Kitaplık dizinleri** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\lib** |

1. C++ birim testi dosyası Ekle:

   - **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve **Add**  >  **Yeni öğe**  >  **C++ dosyası (. cpp)** Ekle ' yi seçin.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Testleri nesne veya kitaplık dosyalarına bağlamak için

Test edilen kod test etmek istediğiniz işlevleri dışa aktarmazsa, Output **. obj** veya **. lib** dosyasını test projesinin bağımlılıklarına ekleyebilirsiniz. Test projesinin özelliklerini, birim testi için gereken üst bilgileri ve kitaplığı ya da nesne dosyalarını içerecek şekilde değiştirin.

1. Çözüm Gezgini, test projesinin kısayol menüsünde **Özellikler**' i seçin. Proje Özellikleri penceresi açılır.

1. **Yapılandırma özellikleri**  >  **bağlayıcı**  >  **giriş** sayfasını seçin ve ardından **ek bağımlılıklar**' ı seçin.

   **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının adlarını ekleyin. Tam yol adlarını kullanmayın.

1. **Yapılandırma özellikleri**  >  **bağlayıcı**  >  **genel** sayfasını seçin ve ardından **Ek kitaplık dizinleri**' ni seçin.

   **Düzenle**' yi seçin ve **. obj** veya **. lib** dosyalarının dizin yolunu ekleyin. Yol, genellikle test kapsamındaki projenin Build klasöründedir.

1. **Yapılandırma özellikleri**  >  **VC + + dizinler** sayfasını seçin ve ardından **dizinleri dahil et**' i seçin.

   **Düzenle**' yi seçin ve ardından test altında projenin üstbilgi dizinini ekleyin.

## <a name="write-the-tests"></a>Testleri yazma

Test sınıflarıyla olan herhangi bir *. cpp* dosyası "CppUnitTest. h" içermelidir ve için bir using ifadesine sahip olmalıdır `using namespace Microsoft::VisualStudio::CppUnitTestFramework` . Test projesi sizin için zaten yapılandırılmış. Ayrıca, bir ad alanı tanımı ve başlamanızı sağlamak için TEST_METHOD bir TEST_CLASS içerir. Ad alanı adını ve adları, sınıf ve Yöntem makrolarında parantez içinde değiştirebilirsiniz.

Test çerçevesi, test modüllerini, sınıfları ve yöntemleri başlatmak ve testlerin tamamlandıktan sonra kaynakların temizlenmesi için özel makrolar tanımlar. Bu makrolar bir sınıf veya yönteme ilk kez erişildikten sonra ve son test çalıştıktan sonra yürütülecek kodu oluşturur. Daha fazla bilgi için bkz. [başlatma ve Temizleme](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Test koşullarını tanımlamak için [onaylama](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) sınıfındaki statik yöntemleri kullanın. **Çıkış penceresi**ileti yazmak için [günlükçü](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) sınıfını kullanın. Test yöntemlerine öznitelik ekleme

## <a name="run-the-tests"></a>Testleri çalıştırma

1. **Test** menüsünde **Windows**  >  **Test Gezgini**' ni seçin.

1. Tüm testleriniz pencerede görünmüyorsa, **Çözüm Gezgini** ' de düğümüne sağ tıklayıp **Derle** veya **yeniden oluştur**' u seçerek test projesi oluşturun.

1. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin veya çalıştırmak istediğiniz belirli testleri seçin. Kesme noktaları etkinken hata ayıklama modunda çalıştırmak dahil diğer seçenekler için teste sağ tıklayın.

1. **Çıkış penceresi** , sınıf tarafından yazılmış iletileri görüntülemek için açılan kutuda **testler** ' i seçin `Logger` :

   ![Test iletilerini gösteren C++ Çıkış Penceresi](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Gruplamayı etkinleştirmek için nitelikleri tanımlama

Test **Gezgini**'nde testleri kategorilere ayırmanıza ve gruplandırmalarına olanak tanıyan test yöntemlerinde nitelikler tanımlayabilirsiniz. Bir nitelik tanımlamak için, makrosunu kullanın `TEST_METHOD_ATTRIBUTE` . Örneğin, adlı bir nitelik tanımlamak için `TEST_MY_TRAIT` :

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Birim testlerinizde tanımlı nitelik kullanmak için:

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

### <a name="c-trait-attribute-macros"></a>C++ nitelik öznitelik makroları

Aşağıdaki önceden tanımlanmış nitelikler içinde bulunur `CppUnitTest.h` . Daha fazla bilgi için bkz. [C++ API başvurusu Için Microsoft birim testi çerçevesi](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makroya|Description|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Bir nitelik tanımlamak için TEST_METHOD_ATTRIBUTE makrosunu kullanın.|
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış Owner nitelik kullanın.|
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelikler atamak için önceden tanımlanmış Priority nitelik kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: Test Gezgini ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)
