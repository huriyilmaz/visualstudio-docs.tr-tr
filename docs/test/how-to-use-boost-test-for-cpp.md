---
title: Boost.Test için C++ kullanma
description: Visual Studio 'da birim testleri oluşturmak için Boost. test kullanın.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922915"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio'da C++ için Boost.Test kullanma

Visual Studio 2017 ve üzeri sürümlerde, Boost. test test bağdaştırıcısı, Visual Studio IDE ile tümleşiktir. Bu, iş yüküyle **masaüstü geliştirme C++**  bileşenidir.

![Boost.Test için test bağdaştırıcısı](media/cpp-boost-component.png)

İş yükü yüklü **masaüstü geliştirmesi C++**  yoksa **Visual Studio yükleyicisi**açın. Seçin **C++ ile masaüstü geliştirme** iş yükü, ardından **Değiştir** düğmesi.

## <a name="install-boost"></a>Boost yükleyin

Boost.Test gerektirir [Boost](https://www.boost.org/)! Yükseltme yüklü değilse, Vcpkg paket yöneticisini kullanmanızı öneririz.

1. Konumundaki yönergeleri [Vcpkg: C++ Paket Yöneticisi Windows için](/cpp/vcpkg) vcpkg yükleme (Bu yoksa).

1. Boost.Test dinamik veya statik Kitaplığı'nı yükleyin:

    - Boost. test dinamik kitaplığını yüklemek için `vcpkg install boost-test` çalıştırın.

       \- VEYA -

    - Boost. test statik kitaplığını yüklemek için `vcpkg install boost-test:x86-windows-static` çalıştırın.

1. Visual Studio 'Yu kitaplıkla yapılandırmak için `vcpkg integrate install` çalıştırın ve arttırma üst bilgilerine ve ikili dosyalarına yollar ekleyin.

Visual Studio 'daki çözümünüzde testlerinizi yapılandırma seçeneğiniz vardır: test kapsamındaki projeye test kodunuzu dahil edebilir veya testleriniz için ayrı bir test projesi oluşturabilirsiniz. Her iki seçenek de olumlu ve olumsuz yönleri vardır.

## <a name="add-tests-inside-your-project"></a>Projenizin içine testler ekleme

Visual Studio 2017 sürüm 15,6 ve sonraki sürümlerde, projenize testler için bir öğe şablonu ekleyebilirsiniz. Hem testler hem de kodunuz aynı projede canlı. Bir test derlemesi oluşturmak için ayrı bir yapı yapılandırması oluşturmanız gerekecektir. Ve, testleri hata ayıklama ve yayın derlemelerinizden dışarı tutmanız gerekir.

Visual Studio 2017 sürüm 15.5, önceden yapılandırılmış test proje veya öğe şablonları Boost.Test için kullanılabilir. Ayrı bir test projesi oluşturmak ve yapılandırmak için yönergeleri kullanın.

### <a name="create-a-boosttest-item"></a>Boost. test öğesi oluşturma

1. Testleriniz için bir *. cpp* dosyası oluşturmak üzere **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve > **Yeni öğe** **Ekle** ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda, **yüklü** >  **C++ görsel** > **Test**' i genişletin. **Boost. test**' i seçin ve ardından projenize *test. cpp* eklemek için **Ekle** ' yi seçin.

   ![Boost.Test öğe şablonu](media/boost_test_item_template.png)

Yeni *test. cpp* dosyası bir örnek test yöntemi içerir. Bu dosya, kendi başlık dosyalarınızı ekleyebileceğiniz ve uygulamanız için yazma testlerine sahip olduğunuz yerdir.

Test dosyası ayrıca test yapılandırması için yeni bir `main` yordamı tanımlamak üzere makroları kullanır. Projenizi şimdi oluşturursanız, "_main zaten Main. obj içinde tanımlanmış bir LNK2005 hatası görürsünüz.

### <a name="create-and-update-build-configurations"></a>Derleme yapılandırması oluşturma ve güncelleştirme

1. Test yapılandırması oluşturmak için, menü çubuğunda > **oluştur** **Configuration Manager**' ı seçin. **Configuration Manager** iletişim kutusunda, **etkin çözüm yapılandırması** altında açılan menüyü açın ve **Yeni**' yi seçin. **Yeni çözüm yapılandırması** iletişim kutusunda, "hata ayıklama unittests" gibi bir ad girin. **Ayarları** Seç ' ın altından **Hata Ayıkla**' nın altında **Tamam**' ı seçin.

1. Hata ayıklama ve yayın yapılandırmalarınızın test kodunu dışlayın: **Çözüm Gezgini**Içinde, test. cpp öğesine sağ tıklayın ve **Özellikler**' i seçin. **Özellik sayfaları** iletişim kutusunda, **yapılandırma** açılan menüsünde **tüm yapılandırmalar** ' ı seçin. **Yapılandırma özelliklerini** **genel** > seçin ve **derleme özelliğinden dışlanan** ' ı açmak için açılan listeyi açın. **Evet**' i seçin, sonra değişikliklerinizi kaydetmek için **Uygula** ' yı seçin.

1. Hata ayıklama UnitTests yapılandırmanıza test kodu eklemek için, **Özellik sayfaları** **Iletişim kutusunda** **unittests hata ayıkla** ' yı seçin. **Derleme özelliğinden hariç** **değil** ' i seçin ve ardından değişikliklerinizi kaydetmek için **Tamam** ' ı seçin.

1. Hata ayıklama UnitTests yapılandırmanızda ana kodu dışlayın. **Çözüm Gezgini**, `main` işlevinizi içeren dosyaya sağ tıklayın ve **Özellikler**' i seçin. **Özellik sayfaları** iletişim kutusu ' nda, **yapılandırma** açılan menüsünde **unittests hata ayıkla** ' yı seçin. **Yapılandırma özelliklerini** **genel** > seçin ve **derleme özelliğinden dışlanan** ' ı açmak için açılan listeyi açın. **Evet**' i seçin ve ardından değişikliklerinizi kaydetmek için **Tamam** ' ı seçin.

1. Çözüm yapılandırmasını, **UnitTests hata ayıklaması**için ayarlayın ve ardından **Test Gezgini** 'nin yöntemi bulmasını sağlamak için projenizi derleyin.

Oluşturduğunuz yapılandırma adı "Debug" veya "Release" kelimeleri ile başladığı sürece, karşılık gelen Boost. test kitaplıkları otomatik olarak kullanıma alınır.

Boost.Test tek üstbilgi çeşidini öğesi şablonu kullanır ancak değiştirebilirsiniz #include tek başına kitaplığı değişken kullanılacak yol. Daha fazla bilgi için [Ekle ekleme yönergelerini](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Ayrı bir test projesi oluşturma

Çoğu durumda, testleriniz için ayrı bir proje kullanmak daha kolay olur. Projeniz için özel bir test yapılandırması oluşturmanız gerekmez. Ya da hata ayıklama ve sürüm Derlemeleriyle test dosyalarını hariç tutun.

### <a name="to-create-a-separate-test-project"></a>Ayrı bir test projesi oluşturmak için

1. İçinde **Çözüm Gezgini**çözüm düğümüne sağ tıklayın ve seçin **Ekle** > **yeni proje**.

1. **Yeni Proje Ekle** iletişim kutusunda, filtre açılır penceresinde **C++** , **Windows**ve **konsol** ' ı seçin. **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

1. Projeye bir ad verin ve **Oluştur**' a tıklayın.

1. Silme `main` işlevi *.cpp* dosya.

1. Boost. test için tek üst bilgi veya dinamik kitaplık sürümünü kullanıyorsanız [ekleme yönergeleri Ekle](#add-include-directives)' ye gidin. Statik kitaplık sürümünü kullanıyorsanız, bazı ek yapılandırmalar yapmanız gerekir:

   a. Projeyi dosyasını düzenlemek için önce bunu kaldırın. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve seçin **projeyi**. Ardından proje düğümünü sağ tıklatın ve seçin **Düzenle < adı\>.vcxproj**.

   b. İçin iki satırı ekleyin **Globals** burada gösterildiği gibi özellik grubu:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Kaydet ve Kapat  *\*.vcxproj* dosyasını bulun ve ardından projeyi yeniden yükleyin.

   d. Açmak için **özellik sayfaları**, proje düğümüne sağ tıklayın ve seçin **özellikleri**.

   e. Genişletin **C/C++**  > **kod oluşturma**ve ardından **çalışma zamanı kitaplığı**. Seçin **/mtd** için hata ayıklama statik çalışma zamanı kitaplığı veya **/MT** yayın statik çalışma zamanı kitaplığı.

   f. Genişletin **bağlayıcı** > **sistem**. **Alt sistemin** **konsol**olarak ayarlandığını doğrulayın.

   g. Seçin **Tamam** özellik sayfalarını kapatmak için.

## <a name="add-include-directives"></a>Ekleme yönergelerinde

1. Testinizde *.cpp* dosya, gerekli ekleyin `#include` programınızın türleri ve işlevleri test kodu görünür yapmak için yönergeleri. Ayrı bir test projesi kullanıyorsanız, genellikle program klasör hiyerarşisinde eşdüzey düzeyindedir. Yazarsanız `#include "../"`, IntelliSense penceresi görünür ve üst bilgi dosyasının tam yolu seçmenize olanak sağlar.

   ![Ekle #include](media/cpp-gtest-includes.png)

   Tek başına kitaplığı ile kullanabilirsiniz:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Veya, tek üst bilgi sürümüyle kullanın:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Daha sonra tanımlamak `BOOST_TEST_MODULE`.

Aşağıdaki örnek olarak bulunabilir olması test için yeterliyse **Test Gezgini**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Yazma ve testleri çalıştırma

Artık yazmak ve Boost testleri çalıştırmak hazırsınız. Bkz: [Boost test kitaplığı belgeleri](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) test makrolar hakkında daha fazla bilgi için. Bkz: [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) kullanarak testlerinizi gruplandırma bulma ve çalıştırma hakkında bilgi için **Test Gezgini**.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
