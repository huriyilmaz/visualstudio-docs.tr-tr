---
title: C++ için Boost.Test nasıl kullanılır?
description: Visual Studio'da birim testleri oluşturmak için Boost.Test'i kullanın.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922915"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio'da C++ için Boost.Test nasıl kullanılır?

Visual Studio 2017 ve sonrası, Boost.Test test adaptörü Visual Studio IDE entegre edilmiştir. C++ iş **yüküne sahip Masaüstü geliştirmenin** bir bileşenidir.

![Boost.Test için Test Adaptörü](media/cpp-boost-component.png)

C++ iş yükü yüklü **Masaüstü geliştirmeniz** yoksa **Visual Studio Installer'ı**açın. C++ iş **yüküyle Masaüstü geliştirmeyi** seçin ve ardından **Değiştir** düğmesini seçin.

## <a name="install-boost"></a>Boost’u yükleyin

Boost.Test [Boost](https://www.boost.org/)gerektirir ! Boost yüklü değilseniz, Vcpkg paket yöneticisini kullanmanızı öneririz.

1. [Vcpkg'daki](/cpp/vcpkg) yönergeleri izleyin: Vcpkg yüklemek için Windows için bir C++ paket yöneticisi (zaten yoksa).

1. Boost.Test dinamik veya statik kitaplığını yükleyin:

    - Boost.Test dinamik kitaplığını yüklemek için çalıştırın. `vcpkg install boost-test`

       -VEYA-

    - Boost.Test statik kitaplığını yüklemek için çalıştırın. `vcpkg install boost-test:x86-windows-static`

1. Visual `vcpkg integrate install` Studio'yu kitaplıkla yapılandırmak ve Öne Çıkarma üstbilgilerine ve ikililerine giden yolları eklemek için çalıştırın.

Visual Studio'da çözümünüzün içinde testlerinizi yapılandırma seçeneğiniz vardır: Test kodunuzu test altında projeye ekleyebilirsiniz veya testleriniz için ayrı bir test projesi oluşturabilirsiniz. Her iki seçeneğin de avantajları ve dezavantajları vardır.

## <a name="add-tests-inside-your-project"></a>Projenizin içine testler ekleme

Visual Studio 2017 sürüm 15.6 ve sonraki sürümlerinde, projenize testler için bir öğe şablonu ekleyebilirsiniz. Hem testler hem de kodunuz aynı projede yaşar. Bir test yapısı oluşturmak için ayrı bir yapı yapılandırması oluşturmanız gerekir. Ayrıca, testleri hata ayıklama ve sürüm yapılarınızın dışında tutmanız gerekir.

Visual Studio 2017 sürüm 15.5'te Boost.Test için önceden yapılandırılmış test projesi veya öğe şablonu bulunmamaktadır. Ayrı bir test projesi oluşturmak ve yapılandırmak için yönergeleri kullanın.

### <a name="create-a-boosttest-item"></a>Boost.Test öğesi oluşturma

1. Testleriniz için bir *.cpp* dosyası oluşturmak için Çözüm **Gezgini'ndeki** proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin.

1. Yeni **Öğe Ekle** iletişim kutusunda, **Yüklü** > **Visual C++** > **Testini**genişletin. **Boost.Test'i**seçin, ardından projenize *Test.cpp* eklemek için **Ekle'yi** seçin.

   ![Boost.Test Öğesi Şablonu](media/boost_test_item_template.png)

Yeni *Test.cpp* dosyası örnek bir test yöntemi içerir. Bu dosya, kendi üstbilgi dosyalarınızı ekleyip uygulamanız için testler yazabileceğiniz dosyadır.

Test dosyası, test yapılandırmaları için `main` yeni bir yordam tanımlamak için makrolar da kullanır. Projenizi şimdi oluşturursanız, "main.obj'de zaten tanımlanmış _main" gibi bir LNK2005 hatası görürsünüz.

### <a name="create-and-update-build-configurations"></a>Yapı yapılandırmaları oluşturma ve güncelleştirme

1. Bir test yapılandırması oluşturmak için menü çubuğunda**Yapı Yapılandırma Yöneticisi'ni** **seçin.** >  Configuration **Manager** iletişim kutusunda, **Etkin çözüm yapılandırması** altında açılır başlatmayı açın ve **Yeni'yi**seçin. Yeni **Çözüm Yapılandırması** iletişim kutusunda "Hata Ayıklama UnitTests" gibi bir ad girin. Hata **Ayıklama'yı** seçin ve ardından **Tamam'ı**seçin. **Debug**

1. Hata Ayıklama ve Sürüm yapılandırmalarınızdan test kodunu hariç tut: **Solution Explorer'da,** Test.cpp'ye sağ tıklayın ve **Özellikler'i**seçin. Özellik **Sayfaları** iletişim kutusunda, **Yapılandırma** açılır **durumundaki Tüm Yapılandırmalar'ı** seçin. **Yapılandırma Özellikleri** > **Genel'i** seçin ve **Dışlanan Yapı** özelliği için açılır açılır alanı açın. **Değişikliklerinizi**kaydetmek için Evet'i seçin, ardından **Uygula'yı** seçin.

1. Hata Ayıklama UnitTests yapılandırmanıza test kodunu **özellik sayfaları** iletişim günlüğüne eklemek **için, Yapılandırma** açılır düşüşünde **Hata Ayıklama Birim Testleri'ni** seçin. **Dışlanan Yapı** özelliğinde **Hayır'ı** seçin ve değişikliklerinizi kaydetmek için **Tamam'ı** seçin.

1. Ana kodu Hata Ayıklama UnitTests yapılandırmanızdan hariç tin.'e çıkar. **Çözüm Gezgini'nde,** işlevinizi `main` içeren dosyaya sağ tıklayın ve **Özellikler'i**seçin. Özellik **Sayfaları** iletişim kutusunda, **Yapılandırma** açılır düşüşünde **Hata Ayıklama BirimiTestleri'ni** seçin. **Yapılandırma Özellikleri** > **Genel'i** seçin ve **Dışlanan Yapı** özelliği için açılır açılır alanı açın. **Evet'i**seçin, ardından değişikliklerinizi kaydetmek için **Tamam'ı** seçin.

1. Çözüm Yapılandırmasını **Hata Ayıklama UnitTests**olarak ayarlayın, ardından **Test Gezgini'nin** yöntemi keşfetmesini sağlamak için projenizi oluşturun.

Oluşturduğunuz yapılandırma adı "Hata Ayıklama" veya "Sürüm" sözcükleriyle başladığı sürece, ilgili Boost.Test kitaplıkları otomatik olarak alınır.

Öğe şablonu Boost.Test'in tek üstbilgi varyantını kullanır, ancak bağımsız kitaplık varyantını kullanmak için #include yolunu değiştirebilirsiniz. Daha fazla bilgi için [bkz.](#add-include-directives)

## <a name="create-a-separate-test-project"></a>Ayrı bir test projesi oluşturma

Çoğu durumda, testleriniz için ayrı bir proje kullanmak daha kolaydır. Projeniz için özel bir test yapılandırması oluşturmanız gerekmeyecek. Veya hata ayıklama ve Sürüm yapılarından test dosyalarını hariç tut.

### <a name="to-create-a-separate-test-project"></a>Ayrı bir test projesi oluşturmak için

1. **Çözüm Gezgini'nde,** çözüm düğümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin.

1. Yeni **proje** ekle iletişim kutusunda, filtre açılır pencerelerinde **C++**, **Windows**ve **Konsol'u** seçin. Konsol **Uygulaması** şablonu seçin ve **sonra İleri'yi**seçin.

1. Projeye bir ad verin ve **Oluştur'u**seçin.

1. `main` *.cpp* dosyasındaki işlevi silin.

1. Boost.Test'in tek üstbilgi veya dinamik kitaplık sürümünü kullanıyorsanız, [Ekle yönergelerine](#add-include-directives)gidin. Statik kitaplık sürümünü kullanıyorsanız, bazı ek yapılandırma yapmanız gerekir:

   a. Proje dosyasını yeniden yüklemek için önce boşaltın. **Çözüm Gezgini'nde**proje düğümüne sağ tıklayın ve **Project'i Boşalt'ı**seçin. Daha sonra proje düğümüne sağ tıklayın ve **.vcxproj\>** adı <edit'i seçin.

   b. Burada gösterildiği gibi **Globals** özellik grubuna iki satır ekleyin:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. * \*.vcxproj* dosyasını kaydedip kapatın ve sonra projeyi yeniden yükleyin.

   d. **Özellik Sayfalarını**açmak için proje düğümüne sağ tıklayın ve **Özellikler'i**seçin.

   e. **C/C++** > **Kod Oluşturma'yı**genişletin ve ardından **Runtime Kitaplığı'nı**seçin. Statik çalışma zamanı kitaplığını ayıklamak için **/MTd** veya serbest bırakma statik çalışma zamanı kitaplığı için **/MTd'yi** seçin.

   f. **Linker** > **Sistemini**Genişletin. **Alt Sistemin** **Konsol**olarak ayarlı olduğunu doğrulayın.

   g. Özellik sayfalarını kapatmak için **Tamam'ı** seçin.

## <a name="add-include-directives"></a>Ekle yönergeleri

1. Test *.cpp* dosyanızda, programınızın türlerini ve işlevlerini test koduna görünür hale getirmek için gerekli `#include` yönergeleri ekleyin. Ayrı bir test projesi kullanıyorsanız, genellikle program klasör hiyerarşisinde kardeş düzeyindedir. Yazarsanız, `#include "../"`Bir IntelliSense penceresi görüntülenir ve üstbilgi dosyasına giden tam yolu seçmenize olanak tanır.

   ![#include yönergeleri ekleme](media/cpp-gtest-includes.png)

   Bağımsız kitaplığı aşağıdakilerle kullanabilirsiniz:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Veya tek başlık sürümünü aşağıdakilerle kullanın:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Sonra, `BOOST_TEST_MODULE`tanımlayın.

Aşağıdaki örnek, **testin Test Gezgini'nde**bulunabilmesi için yeterlidir:

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

## <a name="write-and-run-tests"></a>Testleri yazma ve çalıştırma

Artık Boost testleri yazmaya ve çalıştırmaya hazırsınız. Test makroları hakkında bilgi için [Test kitaplığı belgelerini öne çıkarma'ya](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) bakın. **Test**Gezgini'ni kullanarak testlerinizi keşfetme, çalıştırma ve gruplandırma hakkında bilgi için [Test Gezgini ile birim testleri](run-unit-tests-with-test-explorer.md) çalıştır'a bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
