---
title: Python için C++ uzantıları yazma
description: Bu makale, karma mod hata ayıklama dahil olmak üzere Visual Studio, CPython ve PyBind11 kullanarak Python için C++ uzantısı oluşturma adımlarını gösterir.
ms.custom: devdivchpfy22
ms.date: 12/20/2021
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: aadcff465274916b7d872ab2a64116ab5bc3cf70
ms.sourcegitcommit: f303d052e451bcfd4722b99a9adbcb3f575d1678
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137816810"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

Genellikle C++ (veya C) ile yazılmış modüller, Python yorumlayıcının özelliklerini genişletmek için kullanılır. Alt düzey işletim sistemi özelliklerine erişimi etkinleştirmek için de bunları kullanabilirsiniz.

Modüller üç birincil türde gelir:

- **Hızlandırıcı modülleri:** Python yorumlanır bir dil olduğundan, daha yüksek performans için C++ dilinde hızlandırıcı modülleri yazabilirsiniz.
- **Sarmalayıcı modülleri:** Bu modüller mevcut C/C++ arabirimlerini Python koduna veya Python'dan kullanımı kolay bir "pythonic" API'sini ortaya çıkarır.
- **Düşük düzeyli sistem erişim modülleri:** Çalışma zamanının, işletim sisteminin veya temel alınan donanımın alt düzey özelliklerine erişmek `CPython` için bu modülleri oluşturabilirsiniz.

Bu makalede, hiperbolik tanjı hesaplarak Python kodundan çağıran bir C++ uzantısı `CPython` modülü oluşturma hakkında bilgi edinebilirsiniz. Yordam, C++ dilinde aynı yordamı uygulamanın göreli performans kazancını göstermek için ilk olarak Python'da uygulanır.

Makalede ayrıca C++ uzantısını Python'da kullanılabilir hale etmenin iki yolu da açıklanmıştır:

- `CPython`Python belgelerinde açıklandığı gibi standart [uzantıları kullanın.](https://docs.python.org/3/c-api/)
- Basitliği nedeniyle C++11 için önerilen [PyBind11](https://github.com/pybind/pybind11)kullanın. Uyumluluğu sağlamak için Python'ın en son sürümlerinden biri ile çalışırkenn emin olun. 

Bu kılavuzda yer alan tamamlanmış örneği [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)GitHub üzerinde bulabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio Python Geliştirme iş yükü yüklü olarak 2017 veya sonraki bir sürümü yükleyin. İş yükü, yerel uzantılar için gerekli olan C++ iş yükünü ve araç takımlarını getiren Python yerel geliştirme araçlarını içerir.

    ![Python yerel geliştirme araçları seçeneğini vurgulayan Python geliştirme seçenekleri listesinin ekran görüntüsü.](media/cpp-install-native.png)

    > [!NOTE]
    > Veri bilimi ve **analitik uygulamalar iş yükünü yükleyseniz** Python ve Python yerel **geliştirme** araçları seçeneği varsayılan olarak yüklenir.

Yükleme seçenekleri hakkında daha fazla bilgi için bkz. Visual Studio için [Python desteğini yükleme.](installing-python-support-in-visual-studio.md) Python'ı ayrı olarak yüklüyse yükleyicisinde Gelişmiş **Seçenekler'in** altında Hata ayıklama **sembollerini indir'i** seçin. Bu seçenek, Python kodunuz ve yerel kodunuz arasında karma mod hata ayıklaması kullanmak için gereklidir.

## <a name="create-the-python-application"></a>Python uygulamasını oluşturma

1. Dosya Yeni Dosya'Visual Studio seçerek yeni bir Python  >  **projesi**  >  **Project.** 

1. **Python'ı** arayın, **Python Uygulaması** şablonunu seçin, bir ad ve konum girin ve tamam'ı **seçin.**

1. Projenin *.py dosyasına* aşağıdaki kodu yapıştırın. Python düzenleme özelliklerinden [bazılarına sahip olmak için](editing-python-code-in-visual-studio.md)kodu el ile girmeyi deneyin.  

   Bu kod, matematik kitaplığını kullanmadan hiperbolik tanjgent'ı hesaplar ve yerel uzantılarla bunu hızlandırabilirsiniz.

    > [!Tip]
    > C++ dilinde yeniden yazmadan önce kodunuzu saf Python'da yazın. Bu şekilde, yerel kodunuzun doğru olduğundan emin olmak için daha kolay bir şekilde kontrol edin.

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Sonuçları görüntülemek için Hata Ayıklama Olmadan Başlat'ı **seçerek** veya  >   **Ctrl+F5** tuşlarını kullanarak programı çalıştırın.

   Karşılaştırmanın ne `COUNT` kadar süreyle çalıştır çalıştırılması için değişkeni ayarlayabilirsiniz. Bu kılavuzda, kıyaslama yaklaşık iki saniye kadar zaman alan s sayımı ayarlayın.

   > [!TIP]
   > Karşılaştırmaları çalıştırarak Hata Ayıklama Olmadan **Başlat'ı**  >  **her zaman kullanın.** Bu, hata ayıklayıcısında kodu çalıştırarak ek yük Visual Studio yardımcı olur.

## <a name="create-the-core-c-projects"></a>Temel C++ projelerini oluşturma

bu bölümdeki yönergeleri izleyerek iki aynı C++ projesi oluşturun: *superfastcode* ve *superfastcode2*. Daha sonra, C++ kodunu Python'da göstermek için her projede ayrı bir yaklaşım kullanacağız.

1. Bu **Çözüm Gezgini,** çözüme sağ tıklayın ve ardından Yeni **Ekle'yi Project.**  >   Bir Visual Studio hem Python hem de C++ projeleri içerebilir. Bu, Python için Visual Studio avantajlarından biridir.

1. **C++ üzerinde arama,** Boş **proje'yi** seçin, ilk proje için **süper kod** veya ikinci proje için **superfastcode2** belirtin ve tamam'ı **seçin.**

    > [!Tip]
    > Alternatif olarak, Python yerel geliştirme araçları Visual Studio Python Uzantısı Modülü şablonuyla başlayabilirsiniz. Şablonda burada açıklananların büyük bir yeri zaten vardır. 
    > 
    > Ancak bu izlenecek yol için boş bir projeyle başlayarak uzantı modülünü adım adım nasıl tamamlayabilirsiniz? Süreci andikten sonra, kendi uzantılarınızı yazarak zaman kazanmak için şablonu kullanabilirsiniz.

1. Yeni projede bir C++ dosyası oluşturmak için  Kaynak Dosyalar düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

1. **C++ Dosyası'ı** seçin, *module.cpp olarak ad girin ve* tamam'ı **seçin.**

    > [!Important]
    > Aşağıdaki adımlarda C++ özellik sayfalarını açmak için *.cpp* uzantısına sahip bir dosya gereklidir.

1. Ana araç çubuğunda açılan menüyü kullanarak aşağıdaki yapılandırmalardan birini seçin:

   * 64 bit Python çalışma zamanı için **x64 yapılandırmasını etkinleştirin.** 
   * 32 bit Python çalışma zamanı için **Win32 yapılandırmasını** etkinleştirin.

1. Bu **Çözüm Gezgini,** C++ projesine sağ tıklayın, **Özellikler'i seçin** ve ardından şunları yapın: 

   a. Yapılandırma **için** Etkin **(Hata Ayıkla) girin.**  
   b. Platform **için,** önceki adımda seçiminize bağlı olarak Etkin **(x64)** veya Etkin **(Win32)** girin.

    > [!NOTE]
    > Kendi projelerinizi oluşturmada hem hata ayıklama hem de sürüm *yapılandırmalarını* *yapılandırmanız* gerekir. Bu ünitede, yalnızca hata ayıklama yapılandırmasını yapılandıracak ve CPython yayın derlemesi kullanmak üzere ayarlanacak şekilde ayarlanacak. Bu yapılandırma, onaylar dahil olmak üzere C++ çalışma zamanının bazı hata ayıklama özelliklerini devre dışı bırakıyor. CPython hata ayıklama ikililerini *(python_d.exe*) kullanmak için farklı ayarlar gerekir.

1. Özellikleri aşağıdaki tabloda açıklandığı gibi ayarlayın:

    ::: moniker range=">=vs-2019"

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Hedef Adı** | Deyiminde Python'dan başvurmak için modülün `from...import` adını belirtin. Python için modülü tanımlarken C++ kodunda aynı adı kullanırız. Projenin adını modül adı olarak kullanmak için varsayılan değerini **$\<ProjectName>** bırakın.  `python_d.exe`için, `_d` adının sonuna ekleyin. |
    | | **Yapılandırma Türü** | **Dinamik Kitaplık (.dll)** |
    | | **Gelişmiş** > **Hedef Dosya Uzantısı** | **.pyd** |
    | | **Project Varsayılanları** > **Yapılandırma Türü** | **Dinamik Kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Dahil Dizinleri** | Python include *klasörünü* yüklemeniz için uygun şekilde ekleyin (örneğin, `c:\Python36\include` ).  |
    | **C/C++** > **Önişlemci** | **Önişlemci Tanımları** | Varsa, CPython'_DEBUG olmayan sürümle eşleşmesi için hata ayıklama değerini **NDEBUG** olarak değiştirebilirsiniz.  python_d.exe *kullanırken* bu değeri değiştirmeden bırakın. |
    | **C/C++** > **Kod Oluşturma** | **Çalışma Zamanı Kitaplığı** | CPython'un hata ayıklama olmayan sürümüyle eşleşmesi için çok iş parçacıklı **DLL (/MD).** python_d.exe *kullanırken,* bu değeri Çok İş Parçacıklı Hata Ayıklama **DLL'si (/MDd) olarak bırakın.** |
    | **Bağlayıcı** > **Genel** | **Ek Kitaplık Dizinleri** | *.lib* dosyalarını içeren Python *kitaplık* klasörünü yüklemenize uygun şekilde ekleyin (örneğin, *c:\Python36\libs).* *.py* dosyalarını içeren *Lib* klasörünü  *değil, .lib* dosyalarını içeren *libs* klasörüne işaret edin. |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel** > **Hedef Ad** | Deyiminde Python'dan başvurmak için modülün `from...import` adını belirtin. Python için modülü tanımlarken C++ kodunda aynı adı kullanırız. Projenin adını modül adı olarak kullanmak için varsayılan değerini bırakın **$\<ProjectName>** . İçin `python_d.exe` , `_d` adının sonuna ekleyin. |
    | | **Genel** > **Hedef uzantısı** | **. PYD** |
    | | **Project varsayılanları** > **yapılandırma türü** | **Dinamik kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Içerme dizinleri** | Yüklemenize uygun şekilde Python *içerme* klasörünü ekleyin (örneğin, *c:\Python36\include*).  |
    | **C/C++** > **Önişlemci** | **Önişlemci tanımları** | Varsa, **_DEBUG** değerini **ndebug** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde değiştirin `CPython` . Kullanırken `python_d.exe` , bu değeri değiştirmeden bırakın. |
    | **C/C++** > **Kod oluşturma** | **Çalışma zamanı kitaplığı** | **Çok iş PARÇACıKLı dll (/MD)** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde `CPython` . Kullanırken `python_d.exe` , bu değeri değiştirmeden bırakın. |
    | **Bağlayıcı** > **Genel** | **Ek kitaplık dizinleri** | Yüklemenize uygun şekilde *. lib* dosyaları içeren Python *Kitaplıklar* klasörünü ekleyin (örneğin, *c:\Python36\libs*). *.* Lib dosyalarını içeren *LIB* klasörünü *değil* ,. *lib* dosyalarını içeren *LIBS* klasörünü işaret ettiğinizden emin olun. |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > **C/c++** sekmesi proje özelliklerinde görüntülenmiyorsa, proje c/c++ kaynak dosyaları olarak tanımlayan hiçbir dosya içermez. *. C* veya *. cpp* dosya uzantısı olmadan bir kaynak dosyası oluşturursanız bu durum oluşabilir. 
    > 
    > örneğin, yeni öğe iletişim kutusunda *modül. cpp* yerine yanlışlıkla *module. coo* 'yu girdiyseniz, Visual Studio dosyayı oluşturur, ancak c/C++ özellikleri sekmesini etkinleştiren dosya türünü *c/c + Code* olarak yapmaz. Bu tür hatalı kimlik, dosyayı *. cpp* dosya uzantısıyla yeniden adlandırsanız bile kalır. 
    > 
    > Dosya türünü düzgün şekilde ayarlamak için, **Çözüm Gezgini**' de dosyaya sağ tıklayın ve **Özellikler**' i seçin. Ardından, **dosya türü** için **C/C++ kodu**' nu seçin.

1. **Tamam**’ı seçin.

1. Yapılandırmaların (hem *hata ayıklama* hem de *yayın*) test etmek için C++ projesine sağ tıklayın ve ardından **Oluştur**' u seçin. 

   *. PYD* dosyalarını, C++ proje klasörünün kendisinde değil, *hata ayıklama* ve *yayın* altında bulunan *çözüm* klasöründe bulabilirsiniz.

1. C++ projesinin *Module. cpp* dosyasında aşağıdaki kodu ekleyin:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Kodunuzun doğru olduğunu onaylamak için C++ projesini tekrar oluşturun.

1. Daha önce yapmadıysanız, *superfastcode2* adlı ikinci bir projeyi aynı yapılandırmayla oluşturmak için önceki adımları tekrarlayın.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projelerini Python için uzantılara Dönüştür

C++ DLL 'ini Python için bir uzantı haline getirmek için, ilk olarak, içe aktarılmış yöntemleri Python türleriyle etkileşime geçmek üzere değiştirin. Daha sonra, modülün yöntemlerinin tanımlarıyla birlikte modülü dışarı aktaran bir işlev ekleyin.

Aşağıdaki bölümlerde, hem Cpyıthon uzantılarını hem de PyBind11 kullanarak bu adımları nasıl gerçekleştireceğiniz açıklanmaktadır.

### <a name="use-cpython-extensions"></a>Cpyıthon uzantılarını kullanma

Bu bölümde gösterilen koda daha fazla arka plan için, [Python/C API başvurusu el ile](https://docs.python.org/3/c-api/index.html) ve özellikle de [Modül nesneleri](https://docs.python.org/3/c-api/module.html) sayfasına bakın. Sağ üst taraftaki açılan listede Python sürümünüzü seçtiğinizden emin olun.

1. *Module. cpp* dosyasının en üstünde *Python. h* öğesini ekleyin:

    ```cpp
    #include <Python.h>
    ```

1. Metodu, `tanh_impl` Python türlerini kabul etmek ve döndürmek için değiştirin (yani, a `PyObject*` ):

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ `tanh_impl` Işlevinin Python 'a nasıl sunulduğunu tanımlayan bir yapı ekleyin:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Özel olarak, ifadesini kullandığınızda, Python kodunuzda başvurmak istediğiniz modülü tanımlayan bir yapı ekleyin `from...import` . 

   Bu kodda içeri aktarılan adın, **yapılandırma özellikleri**  >  **genel**  >  **hedef adı** altındaki proje özelliklerindeki değerle eşleşmesi gerekir. 

   Aşağıdaki örnekte, `"superfastcode"` Modül adı, `from superfastcode import fast_tanh` içinde tanımlandığı için Python 'da kullanabileceğiniz anlamına gelir `fast_tanh` `superfastcode_methods` . C++ projesine ait *modül. cpp* gibi dosya adları önemsizdir.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. `PyInit_<module-name>` *\<module-name>* C++ projesinin **genel**  >  **hedef adı** özelliğiyle tam olarak eşleşen, adlandırılmış olması gereken modül yüklediğinde Python tarafından çağrı yapan bir yöntem ekleyin. Diğer bir deyişle, proje tarafından oluşturulan *. PYD* dosyasının dosya adıyla eşleşir.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Kodunuzu doğrulamak için C++ projesini tekrar oluşturun. Hatalarda, ["sorun giderme"](#troubleshoot-compiling-failures) bölümüne bakın.

### <a name="use-pybind11"></a>PyBind11 kullanma

Önceki bölümde yer alan adımları tamamladıysanız, C++ kodu için gerekli modül yapılarını oluşturmak üzere çok sayıda ortak kod kullanıldığını fark etmiş olursunuz. PyBind11, aynı sonucu elde eden, ancak çok daha az kodlu bir C++ üstbilgi dosyasındaki makrolar aracılığıyla işlemi basitleştirir. 

Bu bölümdeki kod hakkında daha fazla bilgi için bkz. [PyBind11 temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst).

1. PIP: veya kullanarak PyBind11 'i yükler `pip install pybind11` `py -m pip install pybind11` . 

   Alternatif olarak, Python ortamları penceresini kullanarak PyBind11 yükleyebilirsiniz ve sonra bir sonraki adımda **PowerShell 'In aç** komutunu kullanabilirsiniz.

1. Aynı terminalde, veya öğesini `python -m pybind11 --includes` çalıştırın `py -m pybind11 --includes` . 

   Bu eylem, projenizin **C/C++**  >  **genel**  >  **ek içerme dizinleri** özelliğine eklemeniz gereken yolların bir listesini yazdırır. Varsa `-I` , ön eki kaldırmayı unutmayın.

1. Önceki bölümde yer alan herhangi bir değişikliği içermeyen yeni bir *Module. cpp* üst kısmında, *pybind11. h* ekleyin:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. *Module. cpp*' nin en altında, `PYBIND11_MODULE` C++ işlevine giriş noktasını tanımlamak için makrosunu kullanın:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Kodunuzu doğrulamak için C++ projesi oluşturun. Hatalarla karşılaşırsanız, çözümler için "derleme hatalarını giderme" başlıklı sonraki bölüme bakın.

### <a name="troubleshoot-compiling-failures"></a>Derleme hataları sorunlarını giderme

C++ modülü aşağıdaki nedenlerden dolayı derlenemeyebilir:

- Hata: *Python. h* bulunamıyor (**E1696: kaynak dosya "Python. h"** ve/veya **C1083: Içerme dosyası açılamıyor: "Python. h": böyle bir dosya veya dizin yok**) 

  Çözüm: proje özelliklerindeki **C/C++**  >  **genel**  >  **ek içerme dizinlerinin** yolu, Python yüklemenizin *içerme* klasörünü işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Hata: Python kitaplıkları bulunamıyor 
 
   Çözüm: yol: **bağlayıcı**  >  **genel**  >  **Ek kitaplık dizinlerinin** proje özelliklerinde, Python yüklemenizin *LIBS* klasörüne işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Hedef mimarisiyle ilgili bağlayıcı hataları
   
   Çözüm: C++ hedefinin proje mimarisini Python yüklemenizin ile eşleşecek şekilde değiştirin. Örneğin, C++ projesi ile Win32 hedefliyorsanız, ancak Python yüklemeniz 64 bit ise, C++ projesini x64 olarak değiştirin.

## <a name="test-the-code-and-compare-the-results"></a>Kodu test edin ve sonuçları karşılaştırın

Dll 'Leri artık Python uzantıları olarak yapılandırılmış olduğuna göre, bu dosyalara Python projesinden başvurabilir, modülleri içeri aktarabilir ve yöntemlerini kullanabilirsiniz.

### <a name="make-the-dll-available-to-python"></a>DLL dosyasını Python için kullanılabilir hale getirme

DLL 'yi çeşitli yollarla Python için kullanılabilir hale getirebilirsiniz. Dikkate alınması gereken iki yaklaşım aşağıda verilmiştir: 

* Python projesi ve C++ projesi aynı çözümde ise bu ilk yöntem işe yarar. Şunları yapın: 

   1. **Çözüm Gezgini**, Python projenizde **Başvurular** düğümüne sağ tıklayın ve ardından **Başvuru Ekle**' yi seçin. 
   1. Görüntülenen iletişim kutusunda, **Projeler** sekmesini seçin, hem **superfastcode** ve **superfastcode2** projelerini hem de **Tamam**' ı seçin.

      !["Superfastcode" projesine nasıl başvuru ekleneceğini gösteren ekran görüntüsü.](media/cpp-add-reference.png)

* Alternatif bir yöntem, modülü diğer Python projeleri için kullanılabilir hale getiren Python ortamınıza modülünü de yüklüyor. Daha fazla bilgi için bkz. [ **setuptools** proje belgeleri](https://setuptools.readthedocs.io/). Şunları yapın:

    1. C++ projesinde *Setup.py* adlı bir dosya oluşturun ve projeye sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin. 
    
    1. **C++ dosyası (. cpp)** öğesini seçin, dosyayı *Setup.py* olarak adlandırın ve ardından **Tamam**' ı seçin.
    
       dosyayı *. kopyala* uzantısıyla adlandırırken, C++ dosya şablonunun kullanılmasına karşın bunu bir Python dosyası olarak tanıması Visual Studio olur. 

       Dosya düzenleyicide göründüğünde, uzantı yöntemine uygun şekilde aşağıdaki kodu yapıştırın:
    
        **`CPython` Uzantılar için (superfastcode Projesi)**:
    
        ```python
        from setuptools import setup, Extension
    
        sfc_module = Extension('superfastcode', sources = ['module.cpp'])
    
        setup(
            name='superfastcode',
            version='1.0',
            description='Python Package with superfastcode C++ extension',
            ext_modules=[sfc_module]
        )
        ```
    
        **İçin `PyBind11` (superfastcode2 Projesi)**:
    
        ```python
        from setuptools import setup, Extension
        import pybind11
    
        cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']
    
        sfc_module = Extension(
            'superfastcode2',
            sources=['module.cpp'],
            include_dirs=[pybind11.get_include()],
            language='c++',
            extra_compile_args=cpp_args,
            )
    
        setup(
            name='superfastcode2',
            version='1.0',
            description='Python package with superfastcode2 C++ extension (PyBind11)',
            ext_modules=[sfc_module],
        )
        ```
    
    1. C++ projesinde *pyproject. TOML* adlı ikinci bir dosya oluşturun ve içine aşağıdaki kodu yapıştırın:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Uzantıyı derlemek için Open *pyproject. TOML* sekmesine sağ tıklayın ve ardından **tam yolu Kopyala**' yı seçin. Bu adı kullanmadan önce, *pyproject. TOML* adını yolundan silmelisiniz.
    
    1. **Çözüm Gezgini**' de, etkin Python ortamına sağ tıklayın ve ardından **Python paketlerini Yönet**' i seçin.
    
        > [!Tip]
        > Paketi zaten yüklediyseniz, burada listelendiğini görürsünüz. Devam etmeden önce **X** simgesini tıklatarak kaldırın.
    
    1. Arama kutusunda, kopyalanmış yolu yapıştırın, sonundaki *pyproject. TOML* dosyasını silin ve ardından bu dizinden modülü yüklemek için **ENTER** ' u seçin.
    
        > [!Tip]
        > Yükleme bir izin hatası nedeniyle başarısız olursa, sonuna *--User* ekleyin ve komutu yeniden deneyin.


### <a name="call-the-dll-from-python"></a>Python 'dan DLL 'i çağırma

DLL dosyasını Python için kullanılabilir hale geçirdikten sonra, önceki bölümde açıklandığı gibi, `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` Python kodundan ve işlevlerine çağrı yapabilir ve bunların performansını Python uygulamasıyla karşılaştırabilirsiniz. DLL 'yi çağırmak için aşağıdakileri yapın:

1. Dll 'lerden aktarılmış yöntemleri çağırmak ve çıktılarını göstermek için *. Kopyala* dosyanıza aşağıdaki satırları ekleyin:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Hata **ayıklama**  >  **olmadan Başlat** öğesini seçerek veya CTRL + F5 ' i seçerek Python programını çalıştırın.

    > [!NOTE]
    > **Hata ayıklama olmadan Başlat** komutu devre dışıysa, **Çözüm Gezgini**' de Python projesine sağ tıklayın ve ardından **Başlangıç Project olarak ayarla**' yı seçin.  

    C++ yordamlarının Python uygulamasından yaklaşık beş ila 20 kat daha hızlı çalışacağını gözlemleyin. Tipik çıktı aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. `COUNT`Farkların daha fazla görünmesi için değişkeni artırmayı deneyin. 

    Hata ayıklama derlemesi daha az iyileştirildiğinden ve çeşitli hata denetimleri içerdiğinden, C++ modülünün *hata ayıklama* derlemesi de bir *yayın* derlemesi tarafından daha yavaş çalışır. Bu yapılandırmalar arasında geçiş yapmak için bu yapılandırmalar arasında geçiş yapabilirsiniz, ancak geri dönüp yayın yapılandırması için daha önce ayarladığınız özellikleri güncelleştirmekten çekinmeyin.

Çıktıda, PyBind11 uzantısının CPython uzantısı kadar hızlı olmadığını, ancak saf Python uygulamasından daha hızlı olması gerektiğini görebilirsiniz. Bu fark büyük ölçüde `METH_O` birden çok parametreyi, parametre adlarını veya anahtar sözcük bağımsız değişkenlerini desteklemeyen çağrısı kullanmanızdır. PyBind11, arayanlara daha fazla Python benzeri bir arabirim sağlamak için biraz daha karmaşık kod üretir. Ancak, test kodu 500.000 kez işlevi çağırdığı için sonuçlar bu yükü büyük ölçüde engelleyebilir!

Döngüyü yerel koda taşıyarak ek yükü azaltabilirsiniz `for` . Bu yaklaşım, her öğeyi işlemek için [Yineleyici protokolünü](https://docs.python.org/c-api/iter.html) (veya `py::iterable` [işlev parametresi](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)için PyBind11 türünü) kullanmayı içerir. Python ve C++ arasındaki yinelenen geçişleri kaldırmak, diziyi işlemek için gereken süreyi azaltmak için etkili bir yoldur.

### <a name="troubleshoot-importing-errors"></a>Hataları içeri aktarma sorunlarını giderme

`ImportError`Modülünüzü içeri aktarmaya çalıştığınızda bir ileti alırsanız, bunu aşağıdaki yollarla çözebilirsiniz:

* Bir proje başvurusu aracılığıyla derleme yaparken, C++ proje özelliklerinin, özellikle *dahil etme* ve *kitaplık* dizinleri için Python projeniz için etkinleştirilen Python ortamıyla eşleştiğinden emin olun.

* Çıkış dosyanızın *superfastcode. PYD* olarak adlandırıldığından emin olun. Diğer herhangi bir ad veya uzantı içeri aktarılmasını engeller.

* Modülünüzü *Setup.py* dosyasını kullanarak yüklediyseniz, Python projeniz için etkinleştirilmiş olan Python ortamında *PIP* komutunu çalıştırdıysanız emin olun. Çözüm Gezgini 'de Python ortamının genişletilmesi, *superfastcode* için bir giriş görüntülemelidir.

## <a name="debug-the-c-code"></a>C++ kodunda hata ayıklama

Visual Studio Python ve C++ kod hatalarını birlikte ayıklamayı destekler. Bu bölümde, *superfastcode* projesini kullanarak işlemi yürürelim. İşlem, *superfastcode2* projesi için aynıdır.

1. **Çözüm Gezgini**, Python projesine sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından **Hata Ayıkla**  >  **yerel kod hata ayıklamayı etkinleştir** seçeneğini belirleyin.

    > [!Tip]
    > Yerel kod hata ayıklamasını etkinleştirdiğinizde, hiçbir zaman duraklamaya **devam etmek için herhangi bir tuşa basmanız** gerekmeden, Python çıkış penceresi, program bittikten hemen sonra kapatılabilir. 
    >
    > Çözüm: yerel kod hata ayıklamasını etkinleştirdikten sonra bir duraklama zorlamak için, `-i`   >  **hata ayıklama** sekmesindeki **yorumlayıcı bağımsız değişkenlerini** Çalıştır alanına ekleyin. Bu bağımsız değişken, kod çalıştıktan sonra Python yorumlayıcısını etkileşimli moda koyar, bu noktada CTRL + Z 'yi seçmenizi ve ardından pencereyi kapatmak için girmeniz önerilir. 
    >
    > Alternatif olarak, Python kodunuzun değiştirilmesini görmüyorsanız `import os` `os.system("pause")` programınızın sonuna ve deyimlerini ekleyebilirsiniz. Bu kod özgün duraklatma uyarısını çoğaltır.

1.   >  Özellik değişikliklerini kaydetmek için dosya **Kaydet** ' i seçin.

1. Visual Studio araç çubuğunda, derleme yapılandırmasını **hata ayıkla** olarak ayarlayın.

    ![Visual Studio araç çubuğundaki "hata ayıklama" ayarının ekran görüntüsü.](media/cpp-set-debug.png)

1. Kod hata ayıklayıcıda genellikle daha uzun sürdüğü için, `COUNT` *. Kopyala* dosyanızdaki değişkeni, varsayılan değerden beş kat daha küçük bir değere değiştirmek isteyebilirsiniz. Örneğin, **500000** ile **100000** arasında değiştirin.

1. C++ kodunuzda, yöntemin ilk satırında bir kesme noktası ayarlayın `tanh_impl` ve **F5** ' i veya **hata ayıklama**  >  **başlatma hata ayıklamayı Başlat**' ı seçerek hata ayıklayıcıyı başlatın. 

    Hata ayıklayıcı, kesme noktası kodu çağrıldığında durmaktadır. Kesme noktası isabet değilse, yapılandırmanın **hata ayıklama** olarak ayarlandığından ve projeyi kaydettiğiniz ve hata ayıklayıcıyı başlattığınızda otomatik olarak gerçekleşmeyen bir değer olup olmadığını kontrol edin.

    ![Bir kesme noktası içeren C++ kodunun ekran görüntüsü.](media/cpp-debugging.png)

1. Kesme noktasında, C++ kodunda ilerleyin, değişkenleri inceleyebilir ve benzerlerini yapabilirsiniz. Bu özellikler hakkında daha fazla bilgi için bkz. [Python ve C++ ile birlikte hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatif yaklaşımlar

Aşağıdaki tabloda açıklandığı gibi çeşitli yollarla Python uzantıları oluşturabilirsiniz. İlk iki satır, `CPython` ve `PyBind11` Bu makalede ele alınmıştır.

| Yaklaşım | Vinsat | Temsilci kullanıcılar | 
| --- | --- | --- |
| İçin C/C++ uzantı modülleri `CPython` | 1991 | Standart Kitaplık | 
| [PyBind11](https://github.com/pybind/pybind11) (C++ için önerilir) | 2015 |  |
| [Cython](https://cython.org) (C için önerilir) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HNA](https://hpyproject.org/) | 2019 | |
| [myprivc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [scryptoto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [şifreleme](https://cryptography.io/), [PyPy](https://pypy.org/) |
| YÜZIK | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost. Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Ayrıca bkz.

bu izlenecek yolda, [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)' de GitHub olan tamamlanmış örneği bulacaksınız.
