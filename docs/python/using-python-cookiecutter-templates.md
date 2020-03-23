---
title: Python ile CookieCutter şablonlarını kullanma
description: Visual Studio Python kodu için şablonları keşfetmek ve bu şablonlardan projeler oluşturmak için grafik çerez kesici uzantısını destekler.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eeea19b1d2ff4a4d24f27280a48b9ae673406908
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62832199"
---
# <a name="use-the-cookiecutter-extension"></a>Cookiecutter uzantısını kullanma

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları keşfetmek, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için grafiksel bir kullanıcı arabirimi sağlar. Visual Studio 2017 ve daha sonraki sürümlerinde ayrıca yüklenebilir.

Cookiecutter Python 3.3 veya sonraki (32-bit veya 64-bit) veya Anaconda 3 4.2 veya daha sonra (32-bit veya 64-bit) gerektirir. Uygun bir Python yorumlayıcısı yoksa, Visual Studio bir uyarı görüntüler. Visual Studio çalışırken bir Python yorumlayıcısı yüklerseniz, yeni yüklenen yorumciyi algılamak için Cookiecutter araç çubuğundaki **Ana Ekran** düğmesini tıklatın. (Genel olarak ortamlar hakkında daha fazla şey için [Python ortamları'na](managing-python-environments-in-visual-studio.md) bakın.)

Yüklendikten sonra, penceresini açmak için**Cookiecutter Explorer'ı** **Görüntüle'yi** > seçin:

![Cookiecutter ana pencere](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter iş akışı

Cookiecutter ile çalışmak, bir şablona göz atma ve seçme, yerel bilgisayarınıza klonlama, seçenekleri ayarlama ve ardından izleyen bölümlerde açıklandığı gibi bu şablondan kod oluşturma işlemidir.

### <a name="browse-templates"></a>Şablonlara göz atın

Cookiecutter ana sayfası, aşağıdaki gruplar halinde düzenlenen şablonların listesini görüntüler:

| Grup | Açıklama |
| --- | --- |
| **Yüklendi** | Yerel bilgisayarınıza yüklenen şablonlar. Çevrimiçi bir şablon kullanıldığında, deposu otomatik olarak *~/.cookiecutters*alt klasörüne klonlanır. Seçili yüklü bir şablonu **Sil**düğmesine basarak silebilirsiniz. |
| **Önerilen** | Önerilen akıştan yüklenen şablonlar. Varsayılan özet akışı Microsoft tarafından küratörlüğünü alır. Özet akışı özelleştirme yle ilgili ayrıntılar için aşağıdaki [Cookiecutter seçeneklerine](#cookiecutter-options) bakın. |
| **GitHub** | Çerez kesici anahtar kelime için GitHub arama sonuçları. GitHub sonuçları paginated geri gelir, daha fazla sonuç varsa, **Yük Daha** listenin sonunda görünür. |
| **Özel** | Arama kutusuna özel bir konum girildiğinde, bu grupta görünür. GitHub deposuna tam bir yol veya yerel diskinizdeki bir klasöre tam yol yazabilirsiniz. |

### <a name="cloning"></a>Kopyalama

**Sonraki**tarafından izlenen bir şablon seçtiğinizde, Cookiecutter çalışmak için yerel bir kopya yapar.

**Önerilen** veya **GitHub** gruplarından bir şablon seçerseniz veya arama kutusuna özel bir URL girer ve bu şablonu seçerseniz, şablon yerel bilgisayarınıza klonlanır ve yüklenir. Bu şablon Visual Studio'nun önceki oturumunda yüklenmişse, otomatik olarak silinir ve en son sürüm klonlanır.

**Yüklü** gruptan bir şablon seçerseniz veya arama kutusuna özel bir klasör yolu girer seniz ve bu şablonu seçerseniz, Visual Studio klonlama olmadan şablon uyguluyor.

> [!Important]
> Cookiecutter şablonları tek bir klasör altında klonlanır *~/.cookiecutters.* Her alt klasör, GitHub kullanıcı adını içermeyen git deposu adından sonra adlandırılmıştır. Farklı yazarlardan gelen aynı ada sahip farklı şablonları klonlarsanız çakışmalar ortaya çıkabilir. Bu durumda, Cookiecutter aynı adı taşıyan farklı bir şablonla varolan şablonu üzerine yazmanızı engeller. Diğer şablonu yüklemek için önce varolan şablonu silmeniz gerekir.

### <a name="set-template-options"></a>Şablon seçeneklerini ayarlama

Şablon yerel olarak yüklendikten sonra, Cookiecutter diğer seçeneklerle birlikte dosyaları oluşturmak için Cookiecutter'ın nerede olmasını istediğinizi belirtebileceğiniz bir seçenek sayfası görüntüler:

![Cookiecutter seçenekleri sayfası](media/cookiecutter-template-options.png)

Her Cookiecutter şablonu kendi seçenek kümesini tanımlar ve her biri için varsayılan bir değer belirtir (her giriş alanında önerilen metin olarak görüntülenir). Varsayılan değer, genellikle diğer seçenekleri kullanan dinamik bir değer olduğunda bir kod parçacığı olabilir.

Bir kullanıcı yapılandırma dosyasıyla belirli seçenekler için varsayılan değerleri özelleştirmek mümkündür. Cookiecutter uzantısı bir kullanıcı yapılandırma dosyası algıladığında, kullanıcı config varsayılan değerleri ile şablonun varsayılan değerleri üzerine yazar. Bu davranış, Cookiecutter belgelerinin [Kullanıcı Config](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) bölümünde tartışılmıştır.

Şablon, kod oluşturmadan sonra çalışacak belirli Visual Studio görevlerini belirtirse, bu görevleri devre dışı bırakmanızı sağlayan **tamamlanma seçeneğinde ek** çalıştır ek görevleri görüntülenir. Görevlerin en yaygın kullanımı bir web tarayıcısı açmak, düzenleyicide dosyaları açmak, bağımlılıkları yüklemek ve benzeri.

### <a name="create"></a>Oluşturma

Seçeneklerinizi ayarladıktan sonra kod oluşturmak için **Oluştur'u** seçin (çıktı klasörü boş değilse bir uyarı görüntülenir). Şablonun çıktısını biliyorsanız ve dosyaların üzerine yazmaktan çekinmiyorsanız, uyarıyı kapatabilirsiniz. Aksi takdirde, **Boş**bir klasör belirtin ve ardından oluşturulan dosyaları boş olmayan çıktı klasörünüze el ile kopyalayın' ı iptal et'i seçin.

Dosyalar başarıyla oluşturulduktan sonra, Cookiecutter **Solution Explorer'daki**dosyaları açma seçeneği sunar:

![Çözüm Gezgini komutunu gösteren çerez kesici](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter seçenekleri

Cookiecutter seçenekleri **Araçlar** > **Seçenekleri** > **Cookiecutter**ile kullanılabilir:

![Cookiecutter seçenekleri](media/cookiecutter-tools-options.png)

| Seçenek | Açıklama |
| --- | --- |
| **Önerilen özet akışı URL'si** | Önerilen şablonların konumu akışı. Bir URL veya yerel bir dosyaya giden bir yol olabilir. Varsayılan Microsoft küratörlüğündeki özet akışı kullanmak için URL'yi boş bırakın. Özet akışı, yeni satırlarla ayrılmış şablon konumlarının basit bir listesini sağlar. Küratörlüğünü yaptığı akışta değişiklik istemek için [GitHub'daki kaynağa](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt)karşı çekme isteğinde bulunun. |
| **Yardım Göster** | Cookiecutter penceresinin üst kısmındaki yardım bilgileri çubuğunun görünürlüğünü denetler. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Visual Studio için Cookiecutter şablonlarını optimize edin

Cookiecutter şablonu yazmatemelleri için [Cookiecutter belgelerine](https://cookiecutter.readthedocs.io/en/latest/first_steps.html)bakın. Visual Studio için Cookiecutter uzantısı, Cookiecutter v1.4 için oluşturulan şablonları destekler.

Şablon değişkenlerinin varsayılan olarak işlenmesi veri türüne (dize veya liste) bağlıdır:

- String: Değişken adı için etiket, değer girmek için metin kutusu ve varsayılan değeri gösteren bir filigran. Metin kutusundaki araç ipucu varsayılan değeri gösterir.
- Liste: Değişken adı için etiket, bir değer seçmek için açılan kutu. Açılan kutudaki araç ucu varsayılan değeri gösterir.

Visual Studio'ya özgü (ve Cookiecutter CLI tarafından göz ardı edilen) *cookiecutter.json* dosyanızda ek meta veriler belirterek bu işlemeyi geliştirmek mümkündür. Tüm özellikler isteğe bağlıdır:

| Özellik | Açıklama |
| --- | --- |
| Etiketle | Değişkenin adı yerine değişkenin düzenleyicisinin üzerinde görünenleri belirtir. |
| Açıklama | Düzenleme denetiminde görünen araç ucunu, bu değişkenin varsayılan değeri yerine belirtir. |
| URL'si | Etiketi URL'yi gösteren bir araç ucuyla bir köprüye dönüştürür. Köprüye tıkladığınızda, kullanıcının varsayılan tarayıcısı bu URL'ye açılır. |
| Seçici | Bir değişken için düzenleyicinin özelleştirilmesine izin verir. Aşağıdaki seçiciler şu anda desteklenir:<ul><li>`string`: Standart metin kutusu, dizeleri için varsayılan.</li><li>`list`: Standart açılan kutu, listeler için varsayılan.</li><li>`yesno`: Kombinasyon kutusu arasında `y` `n`ve seçmek için , dizeleri için.</li><li>`odbcConnection`: Veritabanı bağlantısı iletişim kutusunu oluşturan **...** düğmesi olan metin kutusu.</li></ul> |

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

### <a name="run-visual-studio-tasks"></a>Visual Studio görevlerini çalıştırın

Cookiecutter dosyaları oluşturulduktan sonra rasgele Python kodu çalıştırmak için izin veren *Post-Generate Hooks* adlı bir özelliği vardır. Esnek olmasına rağmen Visual Studio'ya kolay erişim edemese de.

Örneğin, Visual Studio düzenleyicisinde veya web tarayıcısında bir dosya açmak veya kullanıcıdan sanal bir ortam oluşturmasını ve paket gereksinimlerini yüklemesini isteyen Visual Studio UI'sini tetiklemek isteyebilirsiniz.

Bu senaryolara izin vermek için Visual Studio, kullanıcı **Solution Explorer'da** oluşturulan dosyaları açtıktan sonra veya dosyalar varolan bir projeye eklendikten sonra çalışacak komutları açıklayan *cookiecutter.json'da* genişletilmiş meta verileri arar. (Yine, kullanıcı şablon seçeneklerinde **tamamlanabilecek ek görevleri** temizleyerek görevleri çalıştırmayı devre dışı bırakır.)

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

Komutlar ada göre belirtilir ve Visual Studio'nun yerelleştirilmiş yüklemeleri üzerinde çalışmak için yerelleştirilmemiş (İngilizce) adı kullanmalıdır. Visual Studio **Komut penceresinde** komut adlarını test edebilir ve keşfedebilirsiniz.

Tek bir bağımsız değişkeni geçmek istiyorsanız, önceki örnekte olduğu gibi bir dize olarak belirtin.

Bir bağımsız değişkeni geçirmeniz gerekmiyorsa, boş bir dize bırakın veya JSON'dan atla:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Birden çok bağımsız değişken için bir dizi kullanın. Anahtarlar için, anahtarı ve değerini ayrı bağımsız değişkenlere bölün ve uygun alıntıyı kullanın. Örnek:

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

Bağımsız değişkenler diğer Cookiecutter değişkenlerine başvurabilir. Yukarıdaki örneklerde, iç `_output_folder_path` değişken oluşturulan dosyalara mutlak bir yol oluşturmak için kullanılır.

Komutun `Python.InstallProjectRequirements` yalnızca varolan bir projeye dosya eklerken çalıştığını unutmayın. Komut, **Solution Explorer'daki**Python projesi tarafından işlendiği nden ve Solution **Explorer** - **Klasör Görünümü'nde**yken iletiyi alacak proje olmadığından bu sınırlama vardır. Gelecekteki bir sürüm kazanma sınırlamasını kaldırmayı ve genel olarak daha iyi **Klasör Görünümü** desteği sağlamayı umuyoruz.

## <a name="troubleshooting"></a>Sorun giderme

### <a name="error-loading-template"></a>Hata yükleme şablonu

Bazı şablonlar, boolean gibi geçersiz veri türlerini *cookiecutter.json'larında*kullanıyor olabilir. Şablon bilgileri bölmesinde **Sorunlar** bağlantısını seçerek bu tür örnekleri şablon yazarına bildirin.

### <a name="hook-script-failed"></a>Kanca komut dosyası başarısız oldu

Bazı şablonlar, Cookiecutter UI ile uyumlu olmayan nesil sonrası komut dosyaları kullanabilir. Örneğin, giriş için kullanıcıyı sorgulayan komut dosyaları, terminal konsoluna sahip olmadığı için başarısız olur.

### <a name="hook-script-not-supported-on-windows"></a>Windows'da desteklenmeyen kanca komut dosyası

Post script *.sh*ise, windows bilgisayarınızdaki bir uygulama ile ilişkili olmayabilir. Windows mağazasında uyumlu bir uygulama bulmanızı isteyen bir Windows iletişim kutusu görebilirsiniz.

### <a name="templates-with-known-issues"></a>Bilinen sorunları olan şablonlar

Klon hataları:

- **wildfish/cookiecutter-django-crud** (alt `|` klasör adında geçersiz karakter)
- **cookiecutter-pyvanguard** (alt `|` klasör adında geçersiz karakter)

Yük hataları:

- **chrisdev/wagtail-cookiecutter-foundation** *(cookiecutter.json*bir boolean türü kullanır)
- **quintoandar/cookiecutter-android** (şablon klasörü yok)

Çalıştırma hataları:

- **iknite/cookiecutter-ansible-role** (post hook script konsol girişi gerektirir)
- **benregn/cookiecutter-django-ansible** (Jinja hatası)

Bash kullanır (ölümcül değil):

- **openstack-dev/cookiecutter**
