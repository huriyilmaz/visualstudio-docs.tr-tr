---
title: C++ için Boost.Test kullanma
description: Bu ünitede birim testleri oluşturmak için Boost.Test Visual Studio.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 11cf28dcbb62144c59ee44b3cbc548fcf3fcbdc203261efa6073865afb5a53ef
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366588"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio'da C++ için Boost.Test'i kullanma

Bu Visual Studio 2017 ve sonraki bir yıl içinde Boost.Test test bağdaştırıcısı, Visual Studio IDE ile tümleştirilmiştir. C++ iş yüküyle **Masaüstü geliştirmenin bir bileşenidir.**

![Boost.Test için Test Bağdaştırıcısı](media/cpp-boost-component.png)

C++ ile Masaüstü geliştirme **iş yükünüz yüklüyse,** **Visual Studio Yükleyicisi.** **C++ ile masaüstü geliştirme iş yükünü** ve ardından Değiştir **düğmesini** seçin.

## <a name="install-boost"></a>Boost’u yükleyin

Boost.Test için [Boost gerekir!](https://www.boost.org/) Boost yüklü değilse Vcpkg paket yöneticisini kullanmanızı öneririz.

1. Vcpkg yüklemek için [Vcpkg: Windows C++](/cpp/vcpkg) paket yöneticisi (henüz yoksa) yönergeleri izleyin.

1. Boost.Test dinamik veya statik kitaplığını yükleyin:

    - `vcpkg install boost-test`Boost.Test dinamik kitaplığını yüklemek için çalıştırın.

       -VEYA-

    - `vcpkg install boost-test:x86-windows-static`Boost.Test statik kitaplığını yüklemek için çalıştırın.

1. Kitaplığı `vcpkg integrate install` ile Visual Studio için çalıştırın ve Boost üst bilgileri ve ikilileri yollarını dahil edin.

Visual Studio'da çözüm içinde testlerinizi yapılandırma seçeneğine sahipsiniz: Test kodunuzu test kapsamındaki projeye dahil etmek veya testlerinizi oluşturmak için ayrı bir test projesi oluşturabilirsiniz. Her iki seçeneğin de avantajları ve dezavantajları vardır.

## <a name="add-tests-inside-your-project"></a>Projenizin içine testler ekleme

2017 Visual Studio 15.6 ve sonraki sürümlerde, projenize testler için bir öğe şablonu eklemek için kullanabilirsiniz. Hem testler hem de kodunuz aynı projede yer alar. Test derlemesi oluşturmak için ayrı bir derleme yapılandırması oluşturmanız gerekir. Ayrıca testleri hata ayıklama ve sürüm derlemelerinin dışında tutmanız gerekir.

2017 Visual Studio 15.5 sürümünde Boost.Test için önceden yapılandırılmış test projesi veya öğe şablonu yoktur. Ayrı bir test projesi oluşturmak ve yapılandırmak için yönergeleri kullanın.

### <a name="create-a-boosttest-item"></a>Boost.Test öğesi oluşturma

1. Testleriniz için *bir .cpp* dosyası oluşturmak için, dosyanın içinde proje düğümüne **sağ tıklayın ve Çözüm Gezgini** **Ekle'yi**  >  **seçin.**

1. Yeni Öğe **Ekle iletişim kutusunda** Test etmek için Yüklü   >  **Visual C++**  >  **genişletin.** **Boost.Test'i** ve ardından **Ekle'yi** seçerek *Test.cpp'yi* projenize ekleyin.

   ![Boost.Test Öğesi Şablonu](media/boost_test_item_template.png)

Yeni *Test.cpp dosyası* bir örnek test yöntemi içerir. Bu dosya, kendi üst bilgi dosyalarınızı dahil etmek ve uygulamanıza testler yazmak için 2. dosyadır.

Test dosyası ayrıca test yapılandırmaları için yeni bir yordam tanımlamak `main` üzere makroları kullanır. Projenizi şimdi derlemeniz, "main.obj'de zaten tanımlanmış olan bir _main" gibi bir LNK2005 hatasıyla karşınıza alır.

### <a name="create-and-update-build-configurations"></a>Derleme yapılandırmalarını oluşturma ve güncelleştirme

1. Bir test yapılandırması oluşturmak için menü çubuğunda Derleme ve  >  Yapılandırma Yöneticisi. Yeni **Yapılandırma Yöneticisi** iletişim kutusunda Etkin çözüm yapılandırması altındaki açılan **listeyi açın ve** Yeni'yi **seçin.** Yeni Çözüm **Yapılandırması iletişim kutusunda** "UnitTests'te Hata Ayıklama" gibi bir ad girin. Ayarlarından kopyalama altında Hata **ayıkla'ya ve** ardından Tamam'ı **seçin.** 

1. Test kodunu Hata Ayıklama ve Sürüm yapılandırmalarından dışlayın: **Çözüm Gezgini'da** Test.cpp'ye sağ tıklayın ve Özellikler'i **seçin.** Özellik Sayfaları **iletişim kutusunda** Yapılandırma açılan listesinde **Tüm Yapılandırmalar'ı** seçin.  Yapılandırma **Özellikleri**  >  **Genel'i** seçin ve Derlemeden Hariç **Tutulacak özelliği için açılan listeyi** açın. **Evet'i** ve ardından **Uygula'ya** seçerek değişikliklerinizi kaydedin.

1. Test kodunu Hata Ayıklama UnitTests yapılandırmanıza dahil  etmek için Özellik Sayfaları iletişim kutusunda Yapılandırma açılan **listesinden UnitTest'lerde** Hata **Ayıkla'ya** seçin. **Derlemeden** Dışlanan **özelliğinde Hayır'ı** seçin ve ardından **tamam'ı** seçerek değişikliklerinizi kaydedin.

1. Ana kodu Hata Ayıklama UnitTests yapılandırmanız dışında tutabilirsiniz. Bu **Çözüm Gezgini** işlevinizi içeren dosyaya sağ tıklayın ve `main` Özellikler'i **seçin.** Özellik Sayfaları **iletişim kutusunda** Yapılandırma açılan **listesinden UnitTests'te** Hata **Ayıkla'ya** seçin. Yapılandırma **Özellikleri**  >  **Genel'i** seçin ve Derlemeden Hariç **Tutulacak özelliği için açılan listeyi** açın. **Evet'i** ve ardından **Tamam'ı** seçerek değişikliklerinizi kaydedin.

1. Çözüm Yapılandırmasını **UnitTests'de** Hata Ayıklama olarak ayarlayın, ardından Test Gezgini'nin yöntemini keşfetmesini **sağlamak** için projenizi derleme.

Yapılandırma adı "Hata Ayıkla" veya "Yayın" sözcükleriyle başladığı sürece ilgili Boost.Test kitaplıkları otomatik olarak açılır.

Öğe şablonu Boost.Test'in tek üst bilgili varyantını kullanır, ancak tek başına kitaplık #include yolunu değiştirebilirsiniz. Daha fazla bilgi için [bkz. Ekleme yönergeleri ekleme.](#add-include-directives)

## <a name="create-a-separate-test-project"></a>Ayrı bir test projesi oluşturma

Çoğu durumda, testleriniz için ayrı bir proje kullanmak daha kolaydır. Projeniz için özel bir test yapılandırması oluşturmanıza gerek olmayacaktır. Veya test dosyalarını Hata Ayıklama ve Yayın derlemelerinden hariç tutabilirsiniz.

### <a name="to-create-a-separate-test-project"></a>Ayrı bir test projesi oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın ve Yeni **Ekle'yi Project.**  >  

1. Yeni proje **ekle iletişim kutusunda,** filtre açılan **listelerde C++**, **Windows** **ve** Konsol'ı seçin. Konsol Uygulaması **şablonunu ve** ardından Sonraki'yi **seçin.**

1. Projeye bir ad girin ve Oluştur'a **seçin.**

1. `main` *.cpp dosyasındaki işlevini* silin.

1. Boost.Test'in tek üst bilgili veya dinamik kitaplık sürümünü kullanıyorsanız Ekleme yönergeleri [ekleme'ye gidin.](#add-include-directives) Statik kitaplık sürümünü kullanıyorsanız bazı ek yapılandırmalar da yapılandırmanız gerekir:

   a. Proje dosyasını düzenlemek için önce kaldırmanız gerekir. Bu **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yüklemeden **kaldır'ı Project.** Ardından proje düğümüne sağ tıklayın ve **\> .vcxproj <Düzenle'yi seçin.**

   b. Burada gösterildiği gibi **GenelLer özellik** grubuna iki satır ekleyin:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. *\* .vcxproj dosyasını kaydedin ve* kapatın ve projeyi yeniden yükleyin.

   d. Özellik **Sayfaları'ı açmak** için proje düğümüne sağ tıklayın ve Özellikler'i **seçin.**

   e. **C/C++ Kod**  >  **Oluşturma 'yi genişletin** ve çalışma zamanı **kitaplığını seçin.** Statik çalışma zamanı kitaplığında hata ayıklamak için **/MTd'yi** veya yayın statik çalışma zamanı kitaplığı için **/MT'yi** seçin.

   f. Linker **System 'i**  >  **genişletin.** **SubSystem'in Konsol** olarak ayar olduğunu **doğrulayın.**

   örneğin: Özellik **sayfalarını** kapatmak için Tamam'ı seçin.

## <a name="add-include-directives"></a>Ekleme yönergeleri ekleme

1. Test *.cpp dosyanıza,* program tür ve işlevlerini test koduna görünür hale eklemek için `#include` gerekli yönergeleri ekleyin. Ayrı bir test projesi kullanıyorsanız, program genellikle klasör hiyerarşisinde bir alt düzeydedir. yazmanız `#include "../"` durumunda bir IntelliSense penceresi açılır ve üst bilgi dosyasının tam yolunu seçmenize olanak sağlar.

   ![#include yönergeleri ekleme](media/cpp-gtest-includes.png)

   Tek başına kitaplığı aşağıdakilerle kullanabilirsiniz:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Veya tek üst bilgili sürümü şu şekilde kullanabilirsiniz:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Ardından, `BOOST_TEST_MODULE` tanımlayın.

Aşağıdaki örnek testin Test Gezgini'nde keşfedilebilir olması **için yeterlidir:**

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

Artık Boost testleri yazmaya ve çalıştırmaya hazır oluruz. Test [makroları hakkında bilgi için](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) Boost test kitaplığı belgelerine bakın. Test [Gezgini'ni kullanarak testlerinizi bulma,](run-unit-tests-with-test-explorer.md) çalıştırma ve gruplama hakkında bilgi için bkz. Test Gezgini ile **birim testleri çalıştırma.**

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
