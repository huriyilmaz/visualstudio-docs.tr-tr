---
title: Python için C++ uzantıları yazma
description: Bu makale, karma mod hata ayıklama dahil olmak üzere Visual Studio, CPython ve PyBind11 kullanarak Python için C++ uzantısı oluşturma adımlarını gösterir.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973446"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

C++ (veya C) dilinde yazılan modüller genellikle Python yorumlayıcının özelliklerini genişletmek için kullanılır. Alt düzey işletim sistemi özelliklerine erişimi etkinleştirmek için de kullanılır. 

Modüller üç birincil türde gelir:

- **Hızlandırıcı modülleri:** Python yorumlanır bir dil olduğundan, daha yüksek performans için C++ dilinde hızlandırıcı modülleri yazabilirsiniz.
- **Sarmalayıcı modülleri:** Bu modüller, mevcut C/C++ arabirimlerini Python koduna veya Python'dan kullanımı kolay bir "pythonic" API'sini ortaya çıkarır.
- **Düşük düzeyli sistem erişim modülleri:** Çalışma zamanının, işletim sisteminin veya temel alınan donanımın alt düzey özelliklerine erişmek `CPython` için bu modülleri oluşturabilirsiniz.

Bu makalede, hiperbolik tanjı hesaplarak Python kodundan çağıran bir C++ uzantısı `CPython` modülü oluşturma hakkında bilgi edinebilirsiniz. Yordam, C++ dilinde aynı yordamı uygulamanın göreli performans kazancını göstermek için ilk olarak Python'da uygulanır.

Makalede ayrıca C++ uzantısını Python'da kullanılabilir hale etmenin iki yolu da açıklanmıştır:

- `CPython`Python belgelerinde açıklandığı gibi standart [uzantıları kullanın.](https://docs.python.org/3/c-api/)
- Basitliği nedeniyle C++11 için önerilen [PyBind11](https://github.com/pybind/pybind11)kullanın.

Bu kılavuzdan tamamlanmış örneği GitHub'da [python-samples-vs-cpp-extension sayfasında bulabilirsiniz.](https://github.com/Microsoft/python-sample-vs-cpp-extension)

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio Python Geliştirme iş yükü yüklü olarak 2017 veya sonraki bir sürümü yükleyin. İş yükü, yerel uzantılar için gerekli olan C++ iş yükünü ve araç takımlarını getiren Python yerel geliştirme araçlarını içerir.

    ![Python yerel geliştirme araçları seçeneğini vurgulayan Python geliştirme seçenekleri listesinin ekran görüntüsü.](media/cpp-install-native.png)

    > [!NOTE]
    > **Veri bilimi ve analitik uygulamalar** iş yükünü yüklediğinizde, Python ve **Python yerel geliştirme araçları** seçeneği varsayılan olarak yüklenir.

Yükleme seçenekleri hakkında daha fazla bilgi için bkz. [Visual Studio Için Python desteğini yükleme](installing-python-support-in-visual-studio.md). Python 'u ayrı olarak yüklerseniz, yükleyicisindeki **Gelişmiş Seçenekler** altında **hata ayıklama sembollerini indir** ' i seçtiğinizden emin olun. Bu seçenek, Python kodunuz ve yerel kodunuz arasında karışık modda hata ayıklama kullanmanız için gereklidir.

## <a name="create-the-python-application"></a>Python uygulaması oluşturma

1. **Dosya**  >  **Yeni**  >  **Proje**' ye tıklayarak Visual Studio 'da yeni bir Python projesi oluşturun. **Python** için arama yapın, **Python uygulama** şablonunu seçin, bir ad ve konum girin ve ardından **Tamam**' ı seçin.

1. Projenin *. Kopyala* dosyasında aşağıdaki kodu yapıştırın. [Python ile düzenlenen bazı özellikler](editing-python-code-in-visual-studio.md)hakkında daha fazla deneyim için kodu el ile girmeyi deneyin.  

   Bu kod, matematik kitaplığını kullanmadan bir hiperbolik tanjantı hesaplar ve yerel uzantılara göre hızlandırılırsınız.

    > [!Tip]
    > C++ ' da yeniden yazmadan önce kodunuzu saf Python 'da yazın. Bu şekilde, yerel kodunuzun doğru olduğundan emin olmak için daha kolay denetleyebilirsiniz.

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

1. Sonuçları görüntülemek için programı hata **ayıklama**  >  **olmadan Başlat** ' ı seçerek veya CTRL + F5 ' i seçerek çalıştırın. 

   Bu `COUNT` değişkeni, kıyaslama süresini değiştirmek için ayarlayabilirsiniz. Bu izlenecek yolun amacına uygun olarak, sayımı, kıyaslama iki saniye boyunca olacak şekilde ayarlayın.

   > [!TIP]
   > Değerlendirmeleri çalıştırdığınızda, her **zaman hata ayıklama**  >  **başlangıcını hata ayıklama olmadan** kullanın. Bu, kodu Visual Studio hata ayıklayıcı içinde çalıştırdığınızda, bu ek yükün oluşmasını önlemeye yardımcı olur.

## <a name="create-the-core-c-projects"></a>Core C++ projelerini oluşturma

İki özdeş C++ projesi, *superfastcode* ve *superfastcode2* oluşturmak için bu bölümdeki yönergeleri izleyin. Daha sonra, her bir projede C++ kodunu Python 'da göstermek için ayrı bir yaklaşım kullanacaksınız.

1. Bu **Çözüm Gezgini** çözümüne sağ tıklayın ve Ardından Yeni Proje **Ekle'yi**  >  **seçin.** Bir Visual Studio hem Python hem de C++ projeleri içerebilir. Bu, Python için Visual Studio avantajlarından biridir.

1. **C++ üzerinde arama,** Boş **proje'yi** seçin, ilk proje için **süper kod** veya ikinci proje için **superfastcode2** belirtin ve tamam'ı **seçin.**

    > [!Tip]
    > Alternatif olarak, Python yerel geliştirme araçları Visual Studio Python Uzantısı Modülü şablonuyla başlayabilirsiniz. Şablonda burada açıklananların büyük bir yeri zaten vardır. 
    > 
    > Ancak bu izlenecek yol için boş bir projeyle başlayarak uzantı modülünün adım adım nasıl ekli olduğunu göstereceğiz. Süreci andikten sonra, kendi uzantılarınızı yazarak zaman kazanmak için şablonu kullanabilirsiniz.

1. Yeni projede bir C++ dosyası oluşturmak için  Kaynak Dosyalar düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

1. **C++ Dosyası'ı** seçin, *module.cpp olarak ad girin ve* tamam'ı **seçin.**

    > [!Important]
    > Aşağıdaki adımlarda C++ özellik sayfalarını açmak için *.cpp* uzantısına sahip bir dosya gereklidir.

1. Ana araç çubuğunda, açılan menüyü kullanarak aşağıdakilerden birini yapın:

   * 64 bit Python çalışma zamanı için **x64 yapılandırmasını etkinleştirin.** 
   * 32 bit Python çalışma zamanı için **Win32 yapılandırmasını** etkinleştirin.

1. Bu **Çözüm Gezgini,** C++ projesine sağ tıklayın, **Özellikler'i seçin** ve ardından şunları yapın: 

   a. Yapılandırma **için** Etkin **(Hata Ayıkla) girin.**  
   b. Platform **için,** önceki adımda seçiminize bağlı olarak Etkin **(x64)** veya Etkin **(Win32)** girin.

    > [!NOTE]
    > Kendi projelerinizi oluşturmada hem hata ayıklama hem de sürüm *yapılandırmalarını* *yapılandırmanız* gerekir. Bu ünitede, yalnızca hata ayıklama yapılandırmasını yapılandıracak ve CPython yayın derlemesi kullanmak üzere ayarlanacak şekilde ayarlanacak. Bu yapılandırma, bazı hata ayıklama özelliklerini onaylar dahil, C++ çalışma zamanının devre dışı bırakır. Cpyıthon hata ayıklama ikililerini kullanma (*python_d.exe*) farklı ayarlar gerektirir.

1. Aşağıdaki tabloda açıklandığı gibi özellikleri ayarlayın:

    ::: moniker range=">=vs-2019"

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Hedef Adı** | Deyimlerdeki Python 'dan başvurmak için modülün adını belirtin `from...import` . Python için modül tanımladığınızda, C++ kodunda aynı adı kullanırsınız. Projenin adını modül adı olarak kullanmak için varsayılan değerini bırakın **$\<ProjectName>** .  İçin `python_d.exe` , `_d` adının sonuna ekleyin. |
    | | **Yapılandırma türü** | **Dinamik kitaplık (. dll)** |
    | | **Gelişmiş** > **Hedef dosya uzantısı** | **. PYD** |
    | | **Proje Varsayılanları** > **Yapılandırma türü** | **Dinamik kitaplık (. dll)** |
    | **C/C++** > **Genel** | **Ek Içerme dizinleri** | Yüklemeniz için uygun olan Python *içerme* klasörünü ekleyin (örneğin, `c:\Python36\include` ).  |
    | **C/C++** > **Önişlemci** | **Önişlemci tanımları** | Varsa, **_DEBUG** değerini **ndebug** hata ayıklama sürümü olmayan bir tthon sürümüyle eşleşecek şekilde değiştirin. *python_d.exe* kullanırken, bu değeri değiştirmeden bırakın. |
    | **C/C++** > **Kod Oluşturma** | **Çalışma Zamanı Kitaplığı** | CPython'un hata ayıklama olmayan sürümüyle eşleşmesi için çok iş parçacıklı **DLL (/MD).** python_d.exe *kullanırken,* bu değeri Çok İş Parçacıklı Hata Ayıklama **DLL'si (/MDd) olarak bırakın.** |
    | **Linker** > **Genel** | **Ek Kitaplık Dizinleri** | *.lib* dosyalarını içeren Python *kitaplık* klasörünü yüklemenize uygun şekilde ekleyin (örneğin, *c:\Python36\libs).* *.py* dosyalarını içeren *Lib* klasörünü  *değil, .lib* dosyalarını içeren *lib* klasörünü işaret edin. |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel** > **Hedef Ad** | Deyimlerde Python'dan başvurmak için modülün `from...import` adını belirtin. Python için modülü tanımlarken C++ kodunda aynı adı kullanırız. Projenin adını modül adı olarak kullanmak için varsayılan değerini **$\<ProjectName>** bırakın. `python_d.exe`için, `_d` adının sonuna ekleyin. |
    | | **Genel** > **Hedef Uzantı** | **.pyd** |
    | | **Proje Varsayılanları** > **Yapılandırma Türü** | **Dinamik Kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Dahil Dizinleri** | Python include *klasörünü* yüklemeniz için uygun şekilde ekleyin (örneğin, *c:\Python36\include*).  |
    | **C/C++** > **Önişlemci** | **Önişlemci tanımları** | Varsa, **_DEBUG** değerini **ndebug** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde değiştirin `CPython` . Kullanırken `python_d.exe` , bu değeri değiştirmeden bırakın. |
    | **C/C++** > **Kod oluşturma** | **Çalışma zamanı kitaplığı** | **Çok iş PARÇACıKLı dll (/MD)** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde `CPython` . Kullanırken `python_d.exe` , bu değeri değiştirmeden bırakın. |
    | **Bağlayıcı** > **Genel** | **Ek kitaplık dizinleri** | Yüklemenize uygun şekilde *. lib* dosyaları içeren Python *Kitaplıklar* klasörünü ekleyin (örneğin, *c:\Python36\libs*). *.* Lib dosyalarını içeren *LIB* klasörünü *değil* ,. *lib* dosyalarını içeren *LIBS* klasörünü işaret ettiğinizden emin olun. |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > **C/c++** sekmesi proje özelliklerinde görüntülenmiyorsa, proje c/c++ kaynak dosyaları olarak tanımladığı hiçbir dosya içermez. *. C* veya *. cpp* dosya uzantısı olmadan bir kaynak dosyası oluşturursanız bu durum oluşabilir. 
    > 
    > Örneğin, yeni öğe iletişim kutusunda *modül. cpp* yerine yanlışlıkla *Module. COO* 'U girdiyseniz, Visual Studio dosyayı oluşturur ancak dosya türünü c/ *C + Code* olarak ayarlayıp c/C++ özellikleri sekmesini etkinleştirir. Bu tür hatalı kimlik, dosyayı *. cpp* dosya uzantısıyla yeniden adlandırsanız bile kalır. 
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

1. Kodunuzun doğru olduğunu onaylamak için C++ projesini yeniden derleme.

1. Henüz bunu yapmadıysanız, önceki adımları tekrarlayın ve aynı yapılandırmaya sahip *superfastcode2 adlı ikinci* bir proje oluşturun.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projelerini Python için uzantılara dönüştürme

C++ DLL'yi Python için bir uzantı yapmak için, önce dışarı aktaran yöntemleri Python türleriyle etkileşimde bulunmak için değiştirmeniz gerekir. Ardından modülü dışarı aktaran bir işlev ve modülün yöntemlerinin tanımlarını eklersiniz.

Aşağıdaki bölümlerde hem CPython uzantılarını hem de PyBind11'i kullanarak bu adımları nasıl gerçekleştirebilirsiniz?

### <a name="use-cpython-extensions"></a>CPython uzantılarını kullanma

Bu bölümde gösterilen kod hakkında daha fazla arka plan bilgi için [Python/C API Başvuru Kılavuzu'na](https://docs.python.org/3/c-api/index.html) ve özellikle Modül Nesneleri [sayfasına](https://docs.python.org/3/c-api/module.html) bakın. Sağ üstteki açılan listeden Python sürümünizi seçmeyi tercih edin.

1. *module.cpp dosyasının en üstüne Python.h* *dosyasını dahil edersiniz:*

    ```cpp
    #include <Python.h>
    ```

1. Python türlerini `tanh_impl` (yani bir) kabul etmek ve geri dönmek için yöntemini `PyObject*` değiştirme:

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ işlevinin Python'a nasıl `tanh_impl` sunuluyor olduğunu tanımlayan bir yapı ekleyin:

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

1. Özellikle deyimini kullanarak modülü Python kodunda başvurmak istediğiniz şekilde tanımlayan bir yapı `from...import` ekleyin. 

   Bu kodda içe aktarılan ad, Yapılandırma Özellikleri Genel Hedef Adı altındaki proje **özelliklerinde yer alan**  >    >  **değerle eşleşmeli.** 

   Aşağıdaki örnekte modül adı, `"superfastcode"` içinde tanımlandığı için `from superfastcode import fast_tanh` Python'da kullanabileceğiniz `fast_tanh` anlamına `superfastcode_methods` gelir. C++ projesinin içinde yer alan *module.cpp* gibi dosya adları tutarsızdır.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Python'ın modülünü yüklerken çağıran ve adı olması gereken, C++ projesinin Genel Hedef Adı özelliğiyle tam olarak eşleşen `PyInit_<module-name>` *\<module-name>* bir   >  **yöntem** ekleyin. Başka bir ifadeyle, proje tarafından inşa edilen *.pyd* dosyasının dosya adıyla eşler.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Kodunuzu doğrulamak için C++ projesini yeniden derleme. Hatalarla karşılaşırsanız, ["sorun giderme"](#troubleshoot-compiling-failures) bölümüne bakın.

### <a name="use-pybind11"></a>PyBind11 kullanma

Önceki bölümde yer alan adımları tamamladıysanız, C++ kodu için gerekli modül yapılarını oluşturmak üzere çok sayıda ortak kod kullanıldığını kesinlikle fark etmiş olursunuz. PyBind11, aynı sonucu elde eden, ancak çok daha az kodlu bir C++ üstbilgi dosyasındaki makrolar aracılığıyla işlemi basitleştirir. 

Bu bölümdeki kod hakkında daha fazla bilgi için bkz. [PyBind11 temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst).

1. PIP: veya kullanarak PyBind11 'i yükler `pip install pybind11` `py -m pip install pybind11` . 

   Alternatif olarak, Python ortamları penceresini kullanarak PyBind11 yükleyebilirsiniz ve sonra bir sonraki adımda **PowerShell 'In aç** komutunu kullanabilirsiniz.

1. Aynı terminalde, veya öğesini `python -m pybind11 --includes` çalıştırın `py -m pybind11 --includes` . 

   Bu, projenizin **C/C++**  >  **genel**  >  **ek içerme dizinleri** özelliğine eklemeniz gereken yolların bir listesini yazdırır. Varsa `-I` , ön eki kaldırmayı unutmayın.

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

  Çözüm: proje özelliklerindeki **C/C++**  >  **genel**  >  **ek içerme dizinlerindeki** yolun, Python yüklemenizin *içerme* klasörünü işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Hata: Python kitaplıkları bulunamıyor 
 
   Çözüm: Proje özelliklerinde **Bulunan Linker** Genel Ek Kitaplık Dizinleri'nin yolunun  >    >   Python yüklemenizin *kitaplık klasörüne sahip olduğunu* doğrulayın. Çekirdek C++ projesi oluşturma [altında 6. adıma bakın.](#create-the-core-c-projects)

- Hedef mimariyle ilgili bağlantı hataları
   
   Çözüm: C++ hedefinin proje mimarisini Python yüklemenizin mimarisiyle eş olacak şekilde değiştirme. Örneğin, Win32'yi C++ projesiyle hedeflediniz ancak Python yüklemeniz 64 bit ise C++ projesini x64 olarak değiştirebilirsiniz.

## <a name="test-the-code-and-compare-the-results"></a>Kodu test etmek ve sonuçları karşılaştırmak

Artık PYTHON uzantıları olarak yapılandırılmış OLAN DLL'lere Python projesinden başvurabilirsiniz, modülleri içeri aktarabilirsiniz ve yöntemlerini kullanabilirsiniz.

### <a name="make-the-dll-available-to-python"></a>DLL'i Python'da kullanılabilir yapma

DLL'i Python için kullanılabilir hale çeşitli yöntemlerden herhangi birini yapabilirsiniz. Göz önünde bulundurarak iki yaklaşımdan birini kullanabilirsiniz: 

* Bu ilk yöntem, Python projesi ve C++ projesi aynı çözümde yer alıyorsa çalışır. Şunları yapın: 

   1. Bu **Çözüm Gezgini** Python projenizin **Başvurular** düğümüne sağ tıklayın ve Başvuru Ekle'yi **seçin.** 
   1. Görüntülenen iletişim kutusunda Projeler  sekmesini seçin, hem süper kod hem de **süperfastcode2** projelerini ve ardından Tamam'ı **seçin.** 

      !["superfastcode" projesine başvuru eklemeyi gösteren ekran görüntüsü.](media/cpp-add-reference.png)

* Alternatif bir yöntem, modülü Python ortamınıza yüklayarak modülü diğer Python projelerinde de kullanılabilir yapar. Daha fazla bilgi için [ **setuptools proje belgelerine** bakın.](https://setuptools.readthedocs.io/) Şunları yapın:

    1. Projeye sağ *tıklar ve Yeni Öğe ekle'yi* seçerek C++ projesinde setup.py adlı **bir**  >  **dosya oluşturun.** 
    
    1. **C++ Dosyası (.cpp)** öğesini seçin, dosyayı setup.py *olarak* ve tamam'ı **seçin.**
    
       Dosyayı *.py uzantısıyla* adlandırmak, C++ Visual Studio rağmen dosyayı Python dosyası olarak tanımasını sağlar. 

       Dosya düzenleyicide göründüğünde, uzantı yöntemine uygun şekilde aşağıdaki kodu dosyaya yapıştırın:
    
        **Uzantılar `CPython` için (süper kod projesi)**:
    
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
    
        **için `PyBind11` (superfastcode2 projesi)**:
    
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
    
    1. C++ projesinde *pyproject.toml* adlı ikinci bir dosya oluşturun ve içine aşağıdaki kodu yapıştırın:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Uzantıyı derlemek için *pyproject.toml* sekmesini açın ve Tam Yolu **Kopyala'yı seçin.** *Pyproject.toml adını* kullanmadan önce yoldan silebilirsiniz.
    
    1. Bu **Çözüm Gezgini,** etkin Python ortamına sağ tıklayın ve ardından Python Paketlerini **Yönet'i seçin.**
    
        > [!Tip]
        > Paketi zaten yüklemişsinizdir, burada listelenmiş olarak gösterilir. Devam etmek için **X tarak** kaldırın.
    
    1. Arama kutusuna kopyalanan yolu yapıştırın, *en sonundan pyproject.toml* dosyasını silin ve enter tarak modülü bu dizinden yükleyin.
    
        > [!Tip]
        > Yükleme bir izin hatası nedeniyle başarısız olursa sonuna *--user* ekleyin ve komutu yeniden deneyin.


### <a name="call-the-dll-from-python"></a>Python'dan DLL'i çağırma

Önceki bölümde açıklandığı gibi DLL'i Python için kullanılabilir olduktan sonra, Python kodundan ve işlevlerini çağırabilir ve bunların performansını `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` Python uygulamasıyla karşılaştırabilirsiniz. DLL'i aramak için şunları yapın:

1. DLL'lerden dışarı aktaran yöntemleri çağıran ve çıkışlarını görüntülemek için *.py* dosyanıza aşağıdaki satırları ekleyin:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Hata Ayıklama Olmadan Başlat'ı **veya**  >   Ctrl+F5 tuşlarını seçerek Python programını çalıştırın.

    > [!NOTE]
    > Hata Ayıklama **Olmadan Başlat komutu devre** dışı bırakılırsa, **Çözüm Gezgini** python projesine sağ tıklayın ve Başlangıç Projesi Olarak **Ayarla'yı seçin.**  

    C++ yordamlarının Python uygulamasından yaklaşık beş ile yirmi kat daha hızlı çalıştırılana dikkat edin. Tipik çıkış aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Farklılıkların `COUNT` daha belirgin hale gelir ve değişkenlerini artırmayı deneyin. 

    Hata ayıklama derlemesi daha az iyileştirildiğinden ve çeşitli hata denetimleri içerdiğinden, C++ modülünün *hata ayıklama* derlemesi de bir *yayın* derlemesi tarafından daha yavaş çalışır. Bu yapılandırmalar arasında geçiş yapmak için bu yapılandırmalar arasında geçiş yapabilirsiniz, ancak geri dönüp yayın yapılandırması için daha önce ayarladığınız özellikleri güncelleştirmekten çekinmeyin.

Çıktıda, PyBind11 uzantısının CPython uzantısı kadar hızlı olmadığını, ancak saf Python uygulamasından önemli ölçüde daha hızlı olması gerektiğini görebilirsiniz. Bu fark büyük ölçüde `METH_O` birden çok parametreyi, parametre adlarını veya anahtar sözcük bağımsız değişkenlerini desteklemeyen çağrısı kullanmanızdır. PyBind11, arayanlara daha fazla Python benzeri bir arabirim sağlamak için biraz daha karmaşık kod üretir. Ancak, test kodu 500.000 kez işlevi çağırdığı için sonuçlar bu yükü büyük ölçüde engelleyebilir!

Döngüyü yerel koda taşıyarak ek yükü azaltabilirsiniz `for` . Bu yaklaşım, her öğeyi işlemek için [Yineleyici protokolünü](https://docs.python.org/c-api/iter.html) (veya `py::iterable` [işlev parametresi](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)için PyBind11 türünü) kullanmayı kapsar. Python ve C++ arasındaki yinelenen geçişleri kaldırmak, diziyi işlemek için gereken süreyi azaltmak için etkili bir yoldur.

### <a name="troubleshoot-importing-errors"></a>Hataları içeri aktarma sorunlarını giderme

`ImportError`Modülünüzü içeri aktarmaya çalıştığınızda bir ileti alırsanız, bunu aşağıdaki yollarla çözebilirsiniz:

* Bir proje başvurusu aracılığıyla derleme yaparken, C++ proje özelliklerinin, özellikle *dahil etme* ve *kitaplık* dizinleri için Python projeniz için etkinleştirilen Python ortamıyla eşleştiğinden emin olun.

* Çıkış dosyanızın *superfastcode. PYD* olarak adlandırıldığından emin olun. Diğer herhangi bir ad veya uzantı içeri aktarılmasını engeller.

* Modülünüzü *Setup.py* dosyasını kullanarak yüklediyseniz, Python projeniz için etkinleştirilmiş olan Python ortamında *PIP* komutunu çalıştırdıysanız emin olun. Içinde Python ortamını Çözüm Gezgini süper kod için bir *giriş görüntülemesi gerekir.*

## <a name="debug-the-c-code"></a>C++ kodunda hata ayıklama

Visual Studio Python ve C++ kodunda birlikte hata ayıklamayı destekler. Bu bölümde, süper kod projesini kullanarak *işlemi adım adım ilerlersiniz.* Bu işlem *superfastcode2 projesi için aynıdır.*

1. Bu **Çözüm Gezgini** Python projesine sağ tıklayın, Özellikler'i  **seçin,** Hata Ayıkla sekmesini seçin ve yerel kodda hata ayıklamayı etkinleştir  >  **seçeneğini** belirleyin.

    > [!Tip]
    > Yerel kodda hata ayıklamayı etkinleştirdikten sonra, program tamam olduktan hemen sonra duraklatma devam etmek için herhangi bir tuşa bas'ı vermeden Python **çıkış penceresi kapanabilir.** 
    >
    > Çözüm: Yerel kod hata ayıklamayı etkinleştirdikten sonra duraklatma zorlamak için Hata Ayıklama sekmesindeki Yorumlayıcı Bağımsız Değişkenlerini Çalıştır `-i`   >   **alanına seçeneğini** ekleyin. Bu bağımsız değişken, kod çalıştır edildikten sonra Python yorumlayıcıyı etkileşimli moda koyar. Bu noktada Ctrl+Z ve enter tuşlarına basarak pencereyi kapatmanız gerekir. 
    >
    > Alternatif olarak, Python kodunuzu değiştirmekte sorun yoksa program sonunda `import os` ve `os.system("pause")` deyimleri abilirsiniz. Bu kod, özgün duraklatma istemini yineler.

1. Özellik   >  **değişikliklerini kaydetmek** için Dosya Kaydet'i seçin.

1. Uygulama araç Visual Studio, derleme yapılandırmasını Hata Ayıkla **olarak ayarlayın.**

    ![Araç çubuğundaki "Hata Ayıkla" ayarının Visual Studio görüntüsü.](media/cpp-set-debug.png)

1. Kodun hata ayıklayıcıda çalışması genellikle daha uzun sürer, .py dosyanız değişkenini varsayılan değerden yaklaşık beş kat daha küçük bir `COUNT` değerle değiştirmek iyi olabilir.  Örneğin, **500000 ile** **100000 arasında bir değişiklik.**

1. C++ kodunda, yönteminin ilk satırına bir kesme noktası ayarlayın ve F5'i veya Hata Ayıklamayı Başlat Hata Ayıklamayı Başlat'ı seçerek `tanh_impl` **hata**   >  **ayıklayıcıyı başlatabilirsiniz.** 

    Kesme noktası kodu çağrıldında hata ayıklayıcı durur. Kesme noktası isabet değilse, yapılandırmanın **hata ayıklama** olarak ayarlandığından ve projeyi kaydettiğiniz ve hata ayıklayıcıyı başlattığınızda otomatik olarak gerçekleşmeyen bir değer olup olmadığını kontrol edin.

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
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Ayrıca bkz.

Bu kılavuzdan tamamlanmış örneği GitHub'da [python-samples-vs-cpp-extension sayfasında bulabilirsiniz.](https://github.com/Microsoft/python-sample-vs-cpp-extension)
