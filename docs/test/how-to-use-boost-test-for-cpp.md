---
title: İçin Boost. test kullanmaC++
description: Visual Studio 'da birim testleri oluşturmak için Boost. test kullanın.
ms.date: 05/06/2019
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 966983fa15b60db33f11645b25561a74ad5fadbe
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983440"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio C++ 'da Boost. test kullanma

Visual Studio 2017 ve üzeri sürümlerde, Boost. test test bağdaştırıcısı, iş yüküyle **Masaüstü geliştirmenin C++**  bir bileşeni olarak Visual Studio IDE ile tümleşiktir.

![Boost. test için test bağdaştırıcısı](media/cpp-boost-component.png)

İş yükü yüklü **masaüstü geliştirmesi C++**  yoksa **Visual Studio yükleyicisi**açın. İş yüküyle **Masaüstü geliştirmeyi C++**  seçin, sonra **Değiştir** düğmesini seçin.

## <a name="install-boost"></a>Yükseltme yüklemesi

Boost. test için [Boost](https://www.boost.org/)! Yükseltme yüklü değilse, Vcpkg paket yöneticisini kullanmanızı öneririz.

1. Vcpkg 'daki yönergeleri izleyin: vcpkg 'yi yüklemek için [bir C++ Windows Paket Yöneticisi](/cpp/vcpkg) (henüz yoksa).

1. Boost. test dinamik veya statik kitaplığını yükler:

    - Boost. test dinamik kitaplığını yüklemek için **vcpkg Install Boost-test** ' i çalıştırın.

       Veya

    - **Vcpkg Install Boost-test: x86-Windows-static** ' i çalıştırarak Boost. test statik kitaplığını yüklemek için.

1. Visual Studio 'Yu kitaplıkla yapılandırmak için **vcpkg tümleştirin Install** komutunu çalıştırın ve yükseltme üst bilgilerine ve ikili dosyalarına yollar ekleyin.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Öğe şablonunu ekleme (Visual Studio 2017 sürüm 15,6 ve üstü)

1. Testleriniz için bir *. cpp* dosyası oluşturmak üzere **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve **Yeni öğe Ekle**' yi seçin.

   ![Boost. test öğesi şablonu](media/boost_test_item_template.png)

1. Yeni dosya bir örnek test yöntemi içerir. **Test Gezgini** 'nin yöntemi bulmasını sağlamak için projenizi derleyin.

Öğe şablonu, Boost. test öğesinin tek üst bilgi çeşidini kullanır, ancak tek başına kitaplık türevini kullanmak için #include yolunu değiştirebilirsiniz. Daha fazla bilgi için bkz. [içerme yönergeleri ekleme](#add-include-directives).

## <a name="create-a-test-project"></a>Test projesi oluşturma

Visual Studio 2017 sürüm 15,5 ' de, Boost. test için önceden yapılandırılmış test projesi veya öğe şablonları yoktur. Bu nedenle, testlerinizi tutmak için bir konsol uygulaması projesi oluşturmanız ve yapılandırmanız gerekir.

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

1. Sol bölmede, **Windows Masaüstü** > **seçin C++**  ve ardından **Windows konsol uygulaması** şablonunu seçin.

1. Projeye bir ad verin ve **Tamam**' ı seçin.

1. *. Cpp* dosyasındaki `main` işlevini silin.

1. Boost. test ' in tek üstbilgi veya dinamik kitaplık sürümünü kullanıyorsanız [ekleme yönergeleri Ekle](#add-include-directives)' ye gidin. Statik kitaplık sürümünü kullanıyorsanız, bazı ek yapılandırmalar gerçekleştirmeniz gerekir:

   a. Proje dosyasını düzenlemek için önce onu kaldırın. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Projeyi Kaldır**' ı seçin. Ardından, proje düğümüne sağ tıklayın ve **\>. vcxproj < adı Düzenle**' yi seçin.

   b. **Genel** Özellikler grubuna burada gösterildiği gibi iki satır ekleyin:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   ,. *\*. vcxproj* dosyasını kaydedip kapatın ve ardından projeyi yeniden yükleyin.

   TID. **Özellik sayfalarını**açmak için, proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.

   TID. **CC++ /**  > **kod üretimini**genişletin ve sonra **çalışma zamanı kitaplığı**' nı seçin. Statik çalışma zamanı kitaplığı hata ayıklaması için **/MTD** 'yi, sürüm statik çalışma zamanı kitaplığı için **/MT** seçin.

   vadeli. **Bağlayıcı** > **sistem**' i genişletin. **Alt sistemin** **konsol**olarak ayarlandığını doğrulayın.

   Acil. Özellik sayfalarını kapatmak için **Tamam ' ı** seçin.

## <a name="add-include-directives"></a>İçerme yönergeleri ekleme

1. Test *. cpp* dosyanızda, programınızın türlerini ve işlevlerini test koduna görünür hale getirmek için gerekli `#include` yönergelerini ekleyin. Genellikle, program klasör hiyerarşisinde bir düzey yukarı açılır. `#include "../"`yazarsanız, bir IntelliSense penceresi görünür ve üst bilgi dosyasının tam yolunu seçmenizi sağlar.

   ![#İnclude yönergeleri ekleme](media/cpp-gtest-includes.png)

   Tek başına kitaplığı ile birlikte kullanabilirsiniz:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Ya da, ile tek üst bilgi sürümünü kullanın:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Ardından `BOOST_TEST_MODULE`tanımlayın.

Test **Gezgini**'nde, testin keşfedilebilir olması için aşağıdaki örnek yeterlidir:

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

Artık yükseltme testleri yazmaya ve çalıştırmaya hazırsınız. Test makroları hakkında bilgi için bkz. [Test kitaplığını destekleme belgeleri](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) . **Test Gezgini**'ni kullanarak testlerinizi bulma, çalıştırma ve gruplandırma hakkında bilgi için bkz. [Test Gezgini Ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [C/için birim testleri yazmaC++](writing-unit-tests-for-c-cpp.md)
