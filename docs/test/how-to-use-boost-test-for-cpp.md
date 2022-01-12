---
title: C++ için Boost. test kullanma
description: Visual Studio birim testleri oluşturmak için Boost. test kullanın.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: e7e422322d1d2d03839fd16807c639c9c2420a9b
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804772"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio C++ için Boost. test kullanma

Visual Studio 2017 ve üzeri sürümlerde, Boost. test test bağdaştırıcısı Visual Studio ıde ile tümleşiktir. Bu, C++ iş yüküne **sahip masaüstü geliştirme** bileşenidir.

![Boost. test için test bağdaştırıcısı](media/cpp-boost-component.png)

C++ iş yükünün yüklü **olduğu masaüstü geliştirmesi** yoksa **Visual Studio Yükleyicisi** açın. C++ iş yükü **Ile masaüstü geliştirmeyi** seçin, sonra **Değiştir** düğmesini seçin.

## <a name="install-boost"></a>Boost’u yükleyin

Boost. test için [Boost](https://www.boost.org/)! Yükseltme yüklü değilse, Vcpkg paket yöneticisini kullanmanızı öneririz.

1. vcpkg yüklemek için (henüz yoksa) [Windows için vcpkg: bir C++ paket yöneticisi](/cpp/vcpkg) ' nde bulunan yönergeleri izleyin.

1. Boost. test dinamik veya statik kitaplığını yükler:

    - `vcpkg install boost-test`Boost. test dinamik kitaplığını yüklemek için öğesini çalıştırın.

       -VEYA-

    - `vcpkg install boost-test:x86-windows-static`Boost. test statik kitaplığını yüklemek için ' i çalıştırın.

1. `vcpkg integrate install`' i kitaplıkla Visual Studio yapılandırmak ve arttırma üst bilgilerine ve ikili dosyalarına yollar eklemek için komutunu çalıştırın.

Visual Studio çözümünüzde testlerinizin içinde testlerinizi yapılandırma seçeneğiniz vardır: test altındaki projeye test kodunuzu dahil edebilir veya testleriniz için ayrı bir test projesi oluşturabilirsiniz. Her iki seçenek de olumlu ve olumsuz yönleri vardır.

## <a name="add-tests-inside-your-project"></a>Projenizin içine testler ekleme

Visual Studio 2017 sürüm 15,6 ve sonraki sürümlerde, projenize testler için bir öğe şablonu ekleyebilirsiniz. Hem testler hem de kodunuz aynı projede canlı. Bir test derlemesi oluşturmak için ayrı bir yapı yapılandırması oluşturmanız gerekecektir. Ve, testleri hata ayıklama ve yayın derlemelerinizden dışarı tutmanız gerekir.

Visual Studio 2017 sürüm 15,5 ' de, Boost. test için önceden yapılandırılmış bir test projesi veya öğe şablonu yok. Ayrı bir test projesi oluşturmak ve yapılandırmak için yönergeleri kullanın.

### <a name="create-a-boosttest-item"></a>Boost. test öğesi oluşturma

1. Testleriniz için bir *. cpp* dosyası oluşturmak üzere **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**  >  **Visual C++**  >  **Test**' i genişletin. **Boost. test**' i seçin ve ardından projenize *test. cpp* eklemek için **Ekle** ' yi seçin.

   ![Boost. test öğesi şablonu](media/boost_test_item_template.png)

Yeni *test. cpp* dosyası bir örnek test yöntemi içerir. Bu dosya, kendi başlık dosyalarınızı ekleyebileceğiniz ve uygulamanız için yazma testlerine sahip olduğunuz yerdir.

Test dosyası ayrıca test yapılandırmalarına yönelik yeni bir yordam tanımlamak için makroları kullanır `main` . Projenizi şimdi oluşturursanız, "_main zaten Main. obj içinde tanımlanmış bir LNK2005 hatası görürsünüz.

### <a name="create-and-update-build-configurations"></a>Derleme yapılandırması oluşturma ve güncelleştirme

1. Test yapılandırması oluşturmak için, menü çubuğunda **derleme**  >  **Configuration Manager**' yi seçin. **Configuration Manager** iletişim kutusunda, **etkin çözüm yapılandırması** altında açılan menüyü açın ve **Yeni**' yi seçin. **Yeni çözüm yapılandırması** iletişim kutusunda, "hata ayıklama unittests" gibi bir ad girin. **Ayarları** Seç ' ın altından **Hata Ayıkla**' nın altında **Tamam**' ı seçin.

1. Hata ayıklama ve yayın yapılandırmalarınızın test kodunu dışlayın: **Çözüm Gezgini** Içinde, test. cpp öğesine sağ tıklayın ve **Özellikler**' i seçin. **Özellik sayfaları** iletişim kutusunda, **yapılandırma** açılan menüsünde **tüm yapılandırmalar** ' ı seçin. **Yapılandırma özelliklerini**  >  **genel** ' i seçin ve **derleme özelliğinden dışlanan** açılan menüsünü açın. **Evet**' i seçin, sonra değişikliklerinizi kaydetmek için **Uygula** ' yı seçin.

1. Hata ayıklama UnitTests yapılandırmanıza test kodu eklemek için, **Özellik sayfaları** **Iletişim kutusunda** **unittests hata ayıkla** ' yı seçin. **Derleme özelliğinden hariç** **değil** ' i seçin ve ardından değişikliklerinizi kaydetmek için **Tamam** ' ı seçin.

1. Hata ayıklama UnitTests yapılandırmanızda ana kodu dışlayın. **Çözüm Gezgini**, işlevinizi içeren dosyaya sağ tıklayın `main` ve **Özellikler**' i seçin. **Özellik sayfaları** iletişim kutusu ' nda, **yapılandırma** açılan menüsünde **unittests hata ayıkla** ' yı seçin. **Yapılandırma özelliklerini**  >  **genel** ' i seçin ve **derleme özelliğinden dışlanan** açılan menüsünü açın. **Evet**' i seçin ve ardından değişikliklerinizi kaydetmek için **Tamam** ' ı seçin.

1. Çözüm yapılandırmasını, **UnitTests hata ayıklaması** için ayarlayın ve ardından **Test Gezgini** 'nin yöntemi bulmasını sağlamak için projenizi derleyin.

Oluşturduğunuz yapılandırma adı "Debug" veya "Release" kelimeleri ile başladığı sürece, karşılık gelen Boost. test kitaplıkları otomatik olarak kullanıma alınır.

Öğe şablonu, Boost. test öğesinin tek üst bilgi çeşidini kullanır, ancak tek başına kitaplık türevini kullanmak için #include yolunu değiştirebilirsiniz. Daha fazla bilgi için bkz. [içerme yönergeleri ekleme](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Ayrı bir test projesi oluşturma

Çoğu durumda, testleriniz için ayrı bir proje kullanmak daha kolay olur. Projeniz için özel bir test yapılandırması oluşturmanız gerekmez. Ya da hata ayıklama ve sürüm Derlemeleriyle test dosyalarını hariç tutun.

### <a name="to-create-a-separate-test-project"></a>Ayrı bir test projesi oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

1. **yeni proje ekle** iletişim kutusunda, filtre açılır penceresinde **C++**, **Windows** ve **konsol** ' ı seçin. **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

1. Projeye bir ad verin ve **Oluştur**' a tıklayın.

1. `main` *. Cpp* dosyasındaki işlevini silin.

1. Boost. test için tek üst bilgi veya dinamik kitaplık sürümünü kullanıyorsanız [ekleme yönergeleri Ekle](#add-include-directives)' ye gidin. Statik kitaplık sürümünü kullanıyorsanız, bazı ek yapılandırmalar yapmanız gerekir:

   a. Proje dosyasını düzenlemek için önce onu kaldırın. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Project kaldır**' ı seçin. Ardından, proje düğümüne sağ tıklayın ve **<adı \> . vcxproj** öğesini seçin.

   b. **Genel** Özellikler grubuna burada gösterildiği gibi iki satır ekleyin:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. *\* . Vcxproj* dosyasını kaydedip kapatın ve ardından projeyi yeniden yükleyin.

   d. **Özellik sayfalarını** açmak için, proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.

   e. **C/C++**  >  **kod üretimini** genişletin ve sonra **çalışma zamanı kitaplığı**' nı seçin. Statik çalışma zamanı kitaplığı hata ayıklaması için **/MTD** 'yi, sürüm statik çalışma zamanı kitaplığı için **/MT** seçin.

   f. **Bağlayıcı**  >  **sistemi**' ni genişletin. **Alt sistemin** **konsol** olarak ayarlandığını doğrulayın.

   örneğin: Özellik sayfalarını kapatmak için **Tamam ' ı** seçin.

## <a name="add-include-directives"></a>İçerme yönergeleri ekleme

1. Test *. cpp* dosyanızda, `#include` programınızın türlerini ve işlevlerini test koduna görünür hale getirmek için gerekli yönergeleri ekleyin. Ayrı bir test projesi kullanıyorsanız, genellikle program klasör hiyerarşisinde eşdüzey düzeyindedir. Yazarsanız `#include "../"` , bir IntelliSense penceresi görünür ve üst bilgi dosyasının tam yolunu seçmenizi sağlar.

   ![#İnclude yönergeleri ekleme](media/cpp-gtest-includes.png)

   Tek başına kitaplığı ile birlikte kullanabilirsiniz:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Ya da, ile tek üst bilgi sürümünü kullanın:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Ardından, tanımlayın `BOOST_TEST_MODULE` .

Test **Gezgini**'nde, testin keşfedilebilir olması için aşağıdaki örnek yeterlidir:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp> //single-header
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

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
