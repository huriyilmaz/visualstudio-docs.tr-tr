---
title: Python ile CookieCutter şablonlarını kullanma
description: Visual Studio, Python kodu için şablonları bulmaya ve bu şablonlardan projeler oluşturmaya yönelik grafik Cookiecutter uzantısını destekler.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 920822cca275f0285f922fc49a60af3a3b152d6b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625334"
---
# <a name="use-the-cookiecutter-extension"></a>Cookiecutter uzantısını kullanma

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve üzeri sürümlerde bulunur ve Visual Studio önceki sürümlerinde ayrı olarak yüklenebilir.

Cookiecutter, Python 3,3 veya üzeri (32-bit veya 64-bit) veya Anaconda 3 4,2 veya üzeri (32-bit veya 64-bit) gerektirir. uygun bir Python yorumlayıcı yoksa Visual Studio bir uyarı görüntüler. Visual Studio çalışırken bir Python yorumlayıcı yüklerseniz, yeni yüklenen yorumlayıcı algılamak için Cookiecutter araç çubuğundaki **giriş** düğmesini seçin. (Genel olarak ortamlar hakkında daha fazla bilgi için bkz. [Python ortamları](managing-python-environments-in-visual-studio.md) .)

Yüklendikten sonra,   >  **Cookiecutter Gezginini** görüntüle ' yi seçerek penceresini açın:

![Cookiecutter ana penceresi](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter iş akışı

Cookiecutter ile çalışma, bir şablona göz atma ve seçme, yerel bilgisayarınıza kopyalama, seçenekleri ayarlama ve bu şablondan kod oluşturma işlemlerini izleyen bölümlerde açıklandığı gibi bir işlemdir.

### <a name="browse-templates"></a>Şablonlara gözatamıyorum

Cookiecutter giriş sayfasında, aşağıdaki gruplar halinde düzenlenmiş, aralarından seçim yapabileceğiniz şablonların bir listesi görüntülenir:

| Grup | Açıklama |
| --- | --- |
| **Yüklendi** | Yerel bilgisayarınıza yüklenmiş şablonlar. Çevrimiçi bir şablon kullanıldığında, deposu otomatik olarak *~/. tanımlama bilgisi ecutters* alt klasörüne kopyalanır. Seçili yüklü bir şablonu **Sil**' i tıklatarak silebilirsiniz. |
| **Önerilen** | Önerilen akıştan yüklenen şablonlar. Varsayılan akış Microsoft tarafından yapılır. Akışı özelleştirme hakkında daha fazla bilgi için aşağıdaki [Cookiecutter seçeneklerine](#cookiecutter-options) bakın. |
| **GitHub** | cookiecutter anahtar sözcüğü için arama sonuçları GitHub. GitHub sonuçları geri dönüp, daha fazla sonuç varsa, daha **fazla yükleme** listenin sonunda görüntülenir. |
| **Özel** | Arama kutusuna özel bir konum girildiğinde, bu grupta görünür. GitHub deposunun tam yolunu ya da yerel diskinizdeki bir klasöre tam yolu yazabilirsiniz. |

### <a name="cloning"></a>Kopyalama

Bir şablonu seçip **İleri**' yi seçtiğinizde, Cookiecutter yerel bir kopyanın çalışmasına neden olur.

**önerilen** veya **GitHub** gruplarından bir şablon seçerseniz veya arama kutusuna özel bir URL girerseniz ve bu şablonu seçerseniz, bu şablon kopyalanır ve yerel bilgisayarınıza yüklenir. bu şablon Visual Studio önceki bir oturumunda yüklüyse, otomatik olarak silinir ve en son sürüm klonlanır.

**yüklü** gruptan bir şablon seçer veya arama kutusuna özel bir klasör yolu girip bu şablonu seçerseniz, Visual Studio bu şablonu kopyalamaya gerek kalmadan yükler.

> [!Important]
> Cookiecutter şablonları tek bir klasör altına kopyalanır *~/. tanımlama bilgisi ecutters*. her alt klasör, GitHub kullanıcı adını içermeyen git deposu adından sonra adlandırılır. Farklı yazarlardan gelen aynı ada sahip farklı şablonları klonladığınızda çakışmalar ortaya çıkabilir. Bu durumda, Cookiecutter, var olan şablonun aynı ada sahip farklı bir şablonla üzerine yazılmasını engeller. Diğer şablonu yüklemek için, önce mevcut olanı silmeniz gerekir.

### <a name="set-template-options"></a>Şablon seçeneklerini ayarla

Şablon yerel olarak yüklendikten sonra Cookiecutter, Cookiecutter 'in diğer seçeneklerle birlikte dosya oluşturmasını istediğiniz yeri belirtebileceğiniz bir seçenekler sayfası görüntüler:

![Cookiecutter seçenekleri sayfası](media/cookiecutter-template-options.png)

Her bir Cookiecutter şablonu kendi seçenek kümesini tanımlar ve her biri için varsayılan bir değer belirtir (her giriş alanında önerilen metin olarak gösterilir). Genellikle diğer seçenekleri kullanan dinamik bir değer olduğunda, varsayılan değer bir kod parçacığı olabilir.

Bir Kullanıcı yapılandırma dosyası ile belirli seçenekler için varsayılan değerleri özelleştirmek mümkündür. Cookiecutter uzantısı bir Kullanıcı yapılandırma dosyası algıladığında, şablonun varsayılan değerlerini kullanıcı yapılandırmasının varsayılan değerleriyle geçersiz kılar. Bu davranış, Cookiecutter belgelerinin [Kullanıcı Yapılandırması](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) bölümünde ele alınmıştır.

şablon, kod üretimi sonrasında çalıştırılacak belirli Visual Studio görevlerini belirtiyorsa, bu görevleri kapatmanıza izin veren ek bir ek **görevler çalıştır** seçeneği görüntülenir. Görevlerin en yaygın kullanımı, bir Web tarayıcısını açmak, düzenleyicide dosyaları açmak, bağımlılıkları yüklemek ve bu şekilde devam eder.

### <a name="create"></a>Oluştur

Seçeneklerinizi ayarladıktan sonra kod oluşturmak için **Oluştur** ' u seçin (çıktı klasörü boş değilse bir uyarı görünür). Şablonun çıktısını öğrenmeniz ve dosyaların üzerine yazılmayamıyorsanız, uyarıyı kapatabilirsiniz. Aksi takdirde, **iptal**' i seçin, boş bir klasör belirtin ve ardından oluşturulan dosyaları boş olmayan çıkış klasörünüze el ile kopyalayın.

Dosyalar başarıyla oluşturulduktan sonra, Cookiecutter **Çözüm Gezgini** dosyaları açmak için bir seçenek sunar:

![Çözüm Gezgini komutu gösteren Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter seçenekleri

Cookiecutter seçenekleri **Araçlar**  >  **Seçenekler**  >  **Cookiecutter** aracılığıyla kullanılabilir:

![Cookiecutter seçenekleri](media/cookiecutter-tools-options.png)

| Seçenek | Açıklama |
| --- | --- |
| **Önerilen akış URL 'SI** | Önerilen şablonlar akışı konumu. Bu bir URL veya yerel bir dosyanın yolu olabilir. Varsayılan Microsoft seçkin akışını kullanmak için URL 'YI boş bırakın. Akış, newlines ile ayrılmış, şablon konumlarının basit bir listesini sağlar. Seçkin akışta değişiklik istemek için [GitHub Kaynak üzerinde](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt)bir çekme isteği yapın. |
| **Yardımı Göster** | Cookiecutter penceresinin en üstündeki yardım bilgileri çubuğunun görünürlüğünü denetler. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Visual Studio için Cookiecutter şablonlarını iyileştirin

Cookiecutter şablonu yazma temelleri için bkz. [Cookiecutter belgeleri](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Visual Studio için Cookiecutter uzantısı, Cookiecutter v 1.4 için oluşturulan şablonları destekler.

Şablon değişkenlerinin varsayılan işlemesi, veri türüne (dize veya liste) göre değişir:

- String: değişken adı için etiket, değer girmek için metin kutusu ve varsayılan değeri gösteren bir filigran. Metin kutusundaki araç ipucu varsayılan değeri gösterir.
- List: değişken adı için etiket, bir değer seçmek için Birleşik giriş kutusu. Birleşik giriş kutusundaki araç ipucu varsayılan değeri gösterir.

Visual Studio özgü olan (ve cookiecutter clı tarafından yoksayılan) *cookiecutter. json* dosyanızda ek meta veriler belirterek bu işleme göre iyileştirebilmek mümkündür. Tüm özellikler isteğe bağlıdır:

| Özellik | Açıklama |
| --- | --- |
| Etiketle | Değişken için, değişkenin adı yerine düzenleyicinin üzerinde ne göründüğünü belirtir. |
| Description | Bu değişken için varsayılan değer yerine, düzenleme denetiminde görünen araç ipucunu belirtir. |
| URL | Etiketi, URL 'YI gösteren bir araç ipucuyla birlikte köprü haline geçirir. Köprü seçildiğinde kullanıcının varsayılan tarayıcısı Bu URL 'ye açılır. |
| Seçici | Bir değişken için düzenleyicinin özelleştirilmesine izin verir. Şu seçiciler Şu anda desteklenmektedir:<ul><li>`string`: Standart metin kutusu, dizeler için varsayılan.</li><li>`list`: Standart Birleşik giriş kutusu, listeler için varsayılan.</li><li>`yesno`: `y` Dizeler için ve arasında seçim yapabileceğiniz Birleşik giriş kutusu `n` .</li><li>`odbcConnection`: Bir veritabanı bağlantısı iletişim kutusu getiren **...** düğmesini içeren metin kutusu.</li></ul> |

Örnek:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>Visual Studio görevleri çalıştırma

Cookiecutter, dosyalar oluşturulduktan sonra rastgele Python kodu çalıştırmaya izin veren, *oluşturma sonrası kancalar* adlı bir özelliğe sahiptir. Esnek olmasına rağmen Visual Studio kolay erişime izin vermez.

Örneğin, Visual Studio düzenleyicisinde veya web tarayıcısında bir dosya açmak ya da kullanıcıdan sanal ortam oluşturmasını ve paket gereksinimlerini yüklemesini isteyen Visual Studio kullanıcı arabirimini tetiklemek istiyor olabilirsiniz.

Bu senaryolara izin vermek *Visual Studio, cookiecutter.json'da* kullanıcı oluşturulan dosyaları **Çözüm Gezgini'de** açtıktan sonra veya dosyalar mevcut projeye eklendikten sonra çalıştırılacak komutları açıklayan genişletilmiş meta verileri aramaz. (Kullanıcı, şablon seçenekleri tamamlandıktan sonra ek görevleri çalıştır'ın **temizlerini çıkararak görevleri çalıştırmayı** geri tercih ediyor olabilir.)

Örnek:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Komutlar adla belirtilir ve yerelleştirilmiş yüklemelerde çalışmak için yerelleştirilmiş olmayan (İngilizce) adı Visual Studio. Komut penceresinde komut adlarını test Visual Studio **keşfedebilirsiniz.**

Tek bir bağımsız değişken geçmek için, bunu önceki örnekte olduğu gibi bir dize olarak belirtin.

Bağımsız değişken geçmeye gerek yoksa boş bir dize bırakın veya JSON'dan atlayın:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Birden çok bağımsız değişken için bir dizi kullanın. Anahtarlar için anahtarı ve değerini ayrı bağımsız değişkenlere bölün ve düzgün alıntı kullanın. Örnek:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Bağımsız değişkenler diğer Cookiecutter değişkenlerine başvurur. Yukarıdaki örneklerde dahili `_output_folder_path` değişken, oluşturulan dosyaların mutlak yolunu oluşturmak için kullanılır.

Komutun `Python.InstallProjectRequirements` yalnızca mevcut projeye dosya eklerken çalıştığını unutmayın. Bu sınırlama, komutu Çözüm Gezgini'daki Python projesi tarafından işlendiğinden ve Klasör Görünümü'ne Çözüm Gezgini ileti **almak için** bir  -  **proje yoktur.** Sınırlamanın kaldırarak gelecek bir sürümü kazanmayı umuyoruz (ve genel olarak daha **iyi Bir** Klasör Görünümü desteği sağlarız).

## <a name="troubleshooting"></a>Sorun giderme

### <a name="error-loading-template"></a>Şablon yüklenirken hata oluştu

Bazı şablonlar *cookiecutter.json* içinde boole gibi geçersiz veri türleri kullanıyor olabilir. Şablon bilgileri bölmesindeki Sorunlar bağlantısını seçerek bu **örnekleri** şablon yazarına rapor edin.

### <a name="hook-script-failed"></a>Kanca betiği başarısız oldu

Bazı şablonlar, Cookiecutter kullanıcı arabirimiyle uyumlu olmayan son nesil betikler kullanabilir. Örneğin, kullanıcıya giriş sorgusunda yer alan betikler, terminal konsoluna sahip olunmay nedeniyle başarısız olur.

### <a name="hook-script-not-supported-on-windows"></a>Kanca betiği Windows

Post betiği *.sh* ise, uygulama bilgisayarınızda bir uygulamayla Windows olabilir. Windows Windows uyumlu bir uygulama bulmanız isteyen bir Windows olabilir.

### <a name="templates-with-known-issues"></a>Bilinen sorunları olan şablonlar

Kopyalama hataları:

- **wildfish/cookiecutter-django-crud** (alt `|` klasör adı için geçersiz karakter)
- **cookiecutter-pyvanguard** (alt `|` klasör adı için geçersiz karakter)

Yükleme hataları:

- **chrisdev/wagtail-cookiecutter-foundation** *(cookiecutter.json içinde boole türü kullanır)*
- **cookieoandar/cookiecutter-android** (şablon klasörü yok)

Çalıştırma hataları:

- **iknite/cookiecutter-ansible-role** (kanca sonrası betik konsol girişi gerektirir)
- **benregn/cookiecutter-django-ansible** (Jinja hatası)

Bash kullanır (önemli değildir):

- **openstack-dev/cookiecutter**
