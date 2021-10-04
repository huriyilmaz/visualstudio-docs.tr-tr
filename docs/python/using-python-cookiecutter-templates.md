---
title: Python ile CookieCutter şablonlarını kullanma
description: Visual Studio Python kodu şablonlarını bulmak ve bu şablonlardan projeler oluşturmak için grafik Cookiecutter uzantısını destekler.
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
ms.openlocfilehash: b2e8be7668109bcd7409e5c8c17fe0ae95ec1190
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430553"
---
# <a name="use-the-cookiecutter-extension"></a>Cookiecutter uzantısını kullanma

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için bir grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve sonraki sürümlere dahil edilir ve önceki sürümlerde ayrı olarak Visual Studio.

Cookiecutter için Python 3.3 veya sonraki (32 bit veya 64 bit) veya Anaconda 3 4.2 veya sonraki bir (32 bit veya 64 bit) gerekir. Uygun bir Python yorumlayıcı yoksa, Visual Studio görüntüler. Çalışma sırasında bir Python yorumlayıcı Visual Studio, yeni yüklenen  yorumlayıcıyı algılamak için Cookiecutter araç çubuğundaki Giriş düğmesini seçin. (Genel [olarak ortamlar](managing-python-environments-in-visual-studio.md) hakkında daha fazla bilgi için bkz. Python ortamları.)

Yüklendikten sonra, penceresini **açmak**  >  **için Cookiecutter Gezginini** Görüntüle'yi seçin:

![Cookiecutter ana penceresi](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter iş akışı

Cookiecutter ile çalışmak, bir şablona göz atma ve şablon seçme, şablonu yerel bilgisayarınıza kopyalama, seçenekleri ayarlama ve ardından aşağıdaki bölümlerde açıklandığı gibi bu şablondan kod oluşturma işlemidir.

### <a name="browse-templates"></a>Şablonlara göz atma

Cookiecutter giriş sayfasında, aşağıdaki gruplara göre düzenlenmiş, seçim yapmak için bir şablon listesi görüntülenir:

| Grup | Açıklama |
| --- | --- |
| **Yüklendi** | Yerel bilgisayarınıza yüklenmiş şablonlar. Çevrimiçi bir şablon kullanılırken, deposu *~/.cookiecutters alt klasörüne otomatik olarak kopya edilir.* Sil'e basarak seçili bir yüklü şablonu **silebilirsiniz.** |
| **Önerilen** | Önerilen akıştan yüklenen şablonlar. Varsayılan akış, Microsoft tarafından özetlenmiştir. Akışı özelleştirme hakkında ayrıntılı bilgi için aşağıdaki [Cookiecutter](#cookiecutter-options) seçeneklerine bakın. |
| **GitHub** | GitHub cookiecutter anahtar sözcüğü için arama sonuçlarını ekleyin. Bu GitHub sonuçları sayfalara geri döner; daha fazla sonuç varsa **listenin** sonunda Daha Fazla Yükle görüntülenir. |
| **Özel** | Arama kutusuna özel bir konum girilirse, bu grupta görünür. Depolama deposunun tam yolunu veya yerel disk GitHub klasörün tam yolunu yazabilirsiniz. |

### <a name="cloning"></a>Kopyalama

Bir şablonu ve ardından Sonraki 'yi **seçerek** Cookiecutter'ın yerel kopyasının üzerinde çalışabilirsiniz.

Önerilen veya GitHub gruplarından bir  şablon seçer veya arama kutusuna özel bir URL girer ve bu şablonu seçerse, şablon kopyalanmış ve yerel bilgisayarınıza yüklenmiştir.  Bu şablon önceki bir Visual Studio yüklendiyse otomatik olarak silinir ve en son sürüm kopyalanmış olur.

Yüklü grubundan bir  şablon seçer veya arama kutusuna özel bir klasör yolu girer ve bu şablonu Visual Studio kopyalamadan yüklersiniz.

> [!Important]
> Cookiecutter şablonları tek bir *~/.cookiecutters klasörüne kopyalandı.* Her alt klasör, git deposu adından sonra adlandırılmıştır ve bu ad, GitHub adını içermez. Farklı yazarlardan gelen aynı adla farklı şablonları kopyalarsanız çakışmalar ortaya çıkabilir. Bu durumda Cookiecutter, var olan şablonun üzerine aynı adla farklı bir şablon yazmanız engel olur. Diğer şablonu yüklemek için önce mevcut şablonu silmeniz gerekir.

### <a name="set-template-options"></a>Şablon seçeneklerini ayarlama

Şablon yerel olarak yüklendikten sonra Cookiecutter, Cookiecutter'ın diğer seçeneklerle birlikte dosya oluşturması istediğiniz yeri belirtebilirsiniz bir seçenek sayfası görüntüler:

![Cookiecutter seçenekler sayfası](media/cookiecutter-template-options.png)

Her Cookiecutter şablonu kendi seçenek kümelerini tanımlar ve her biri için varsayılan bir değer belirtir (her giriş alanında önerilen metin olarak görüntülenir). Varsayılan değer, genellikle diğer seçenekleri kullanan dinamik bir değer olduğunda bir kod parçacığı olabilir.

Bir kullanıcı yapılandırma dosyasıyla belirli seçenekler için varsayılan değerleri özelleştirmek mümkündür. Cookiecutter uzantısı bir kullanıcı yapılandırma dosyası algılasa, şablonun varsayılan değerlerinin üzerine kullanıcı yapılandırmasının varsayılan değerlerini alır. Bu davranış, Cookiecutter [belgelerinin](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) Kullanıcı Yapılandırması bölümünde ele alınmıştır.

Şablon, kod oluşturma Visual Studio çalıştıracak belirli görevleri belirtirse, bu görevleri iptal etmek için ek bir Tamamlamada ek görevler çalıştır seçeneği görüntülenir.  Görevlerin en yaygın kullanımı bir web tarayıcısı açmak, dosyaları düzenleyicide açmak, bağımlılıkları yüklemek ve bu şekilde devam etmektir.

### <a name="create"></a>Oluştur

Seçeneklerinizi ayar verdiktan sonra Kod oluşturmak **için** Oluştur'a tıklayın (çıkış klasörü boş değilse bir uyarı görüntülenir). Şablonun çıktısını biliyorsanız ve dosyaların üzerine yazmaktan rahatsız değilsanız uyarıyı yok sayabilirsiniz. Aksi takdirde **İptal'i** seçin, boş bir klasör belirtin ve ardından oluşturulan dosyaları boş olmayan çıkış klasörünüze el ile kopyalayın.

Dosyalar başarıyla oluşturulduktan sonra Cookiecutter dosyaları dosyalarda açmak için bir **Çözüm Gezgini:**

![Komut satırı gösteren cookiecutter Çözüm Gezgini tanımlama bilgisi](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter seçenekleri

Cookiecutter seçenekleri Araçlar **Seçenekleri**  >    >  **Cookiecutter aracılığıyla kullanılabilir:**

![Cookiecutter seçenekleri](media/cookiecutter-tools-options.png)

| Seçenek | Açıklama |
| --- | --- |
| **Önerilen akış URL'si** | Önerilen şablonlar akışı konumu. Url veya yerel dosyanın yolu olabilir. Varsayılan Microsoft tarafından özel akışı kullanmak için URL'yi boş bırakın. Akış, şablon konumlarının yeni çizgilerle ayrılmış basit bir listesini sağlar. Curated akışında değişiklik isteğinde [GitHub.](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt) |
| **Yardımı Göster** | Cookiecutter penceresinin üst kısmında yer alan yardım bilgileri çubuğunun görünürlüğünü kontrol eder. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Tanımlama bilgileri için Cookiecutter şablonlarını Visual Studio

Cookiecutter şablonu yazmanın temelleri için [Cookiecutter belgelerine bakın.](https://cookiecutter.readthedocs.io/en/latest/first_steps.html) Visual Studio Için Cookiecutter uzantısı, Cookiecutter v1.4 için oluşturulan şablonları destekler.

Şablon değişkenlerinin varsayılan işlemesi, veri türüne (dize veya liste) bağlıdır:

- Dize: Değişken adı için etiket, değer girmek için metin kutusu ve varsayılan değeri gösteren bir filigran. Metin kutusunda araç ipucu varsayılan değeri gösterir.
- Liste: Değişken adı etiketi, bir değer seçmek için birleşik giriş kutusu. Birleşik giriş kutusunda araç ipucu varsayılan değeri gösterir.

*Cookiecutter.json* dosyanıza özel ek meta veriler belirterek (ve Cookiecutter CLI tarafından yoksayılır) Visual Studio bu işlemeyi geliştirmek mümkündür. Tüm özellikler isteğe bağlıdır:

| Özellik | Açıklama |
| --- | --- |
| Etiketle | Değişkenin adı yerine düzenleyicinin üzerinde görünenleri belirtir. |
| Description | Bu değişkenin varsayılan değeri yerine düzenleme denetimi üzerinde görünen araç ipucu'nı belirtir. |
| URL | Etiketi, URL'yi gösteren bir araç ipucuyla birlikte köprüye değiştirir. Köprü seçerek kullanıcının varsayılan tarayıcısını bu URL'ye açar. |
| Seçici | Bir değişken için düzenleyicinin özelleştirilmesine izin verir. Şu anda aşağıdaki seçiciler de destektedir:<ul><li>`string`: Standart metin kutusu, dizeler için varsayılan.</li><li>`list`: Standart birleşik giriş kutusu, listeler için varsayılan.</li><li>`yesno`: Dizeler için ve arasında `y` seçim yapmak için birleşik giriş `n` kutusu.</li><li>`odbcConnection`: Veritabanı bağlantısı **iletişim kutusu** getiren ... düğmesinin yer alan metin kutusu.</li></ul> |

Örnek:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2"],
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

### <a name="run-visual-studio-tasks"></a>Görevleri Visual Studio çalıştırma

Cookiecutter, dosyalar üretdikten sonra rastgele Python kodu çalıştırmaya olanak sağlayan *Post-Generate Hooks* adlı bir özelsteğe sahiptir. Esnek olsa da, veritabanına kolay erişim Visual Studio.

örneğin, Visual Studio düzenleyicisinde veya web tarayıcısında bir dosyayı açmak veya kullanıcıdan bir sanal ortam oluşturmasını ve paket gereksinimlerini yüklemesini isteyen Visual Studio kullanıcı arabirimini tetiklemeniz gerekebilir.

Visual Studio bu senaryolara izin vermek için, *cookiecutter. json* dosyasında, kullanıcı oluşturulan dosyaları **Çözüm Gezgini** veya var olan bir projeye eklendikten sonra çalıştırılacak komutları açıklayan genişletilmiş meta verileri arar. (Yine de Kullanıcı, şablon seçeneklerinde **tamamlandığında ek görevleri Çalıştır** ' ı temizleyerek görevleri çalıştırmayı tercih edebilir.)

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

Komutlar ad ile belirtilir ve yerelleştirilmiş Visual Studio yüklemeleri üzerinde çalışmak için yerelleştirilmemiş (Ingilizce) adı kullanmalıdır. komut adlarını Visual Studio **komut** penceresinde test edebilir ve keşfedebilirsiniz.

Tek bir bağımsız değişken geçirmek istiyorsanız, önceki örnekte olduğu gibi bir dize olarak belirtin.

Bir bağımsız değişken iletmeniz gerekmiyorsa, boş bir dize bırakın veya JSON 'dan atlayın:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Birden çok bağımsız değişken için bir dizi kullanın. Anahtarlar için anahtarı ve değerini ayrı bağımsız değişkenlere böler ve uygun tırnak içine kullanın. Örnek:

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

Bağımsız değişkenler, diğer Cookiecutter değişkenlerine başvurabilir. Yukarıdaki örneklerde, iç `_output_folder_path` değişken oluşturulan dosyalara mutlak bir yol oluşturmak için kullanılır.

`Python.InstallProjectRequirements`Komutun yalnızca mevcut bir projeye dosya eklerken çalıştığına unutmayın. Bu sınırlama, komut **Çözüm Gezgini**' de Python projesi tarafından işlendiği ve **Çözüm Gezgini**  -  **klasör görünümünde** iletiyi alacak bir proje bulunmadığından oluşur. Gelecek bir sürümü kazanmanızı (ve genel olarak daha iyi **klasör görünümü** desteği sağlamayı) umuyoruz.

## <a name="troubleshooting"></a>Sorun giderme

### <a name="error-loading-template"></a>Şablon yüklenirken hata oluştu

Bazı şablonlar, *cookiecutter. JSON* içinde Boole gibi geçersiz veri türlerini kullanıyor olabilir. Şablon bilgileri bölmesindeki **sorunlar** bağlantısını seçerek şablon yazarına bu tür örnekler bildirin.

### <a name="hook-script-failed"></a>Kanca betiği başarısız oldu

Bazı şablonlar, Cookiecutter Kullanıcı arabirimiyle uyumlu olmayan oluşturma sonrası betikleri kullanabilir. Örneğin, Kullanıcı girişi için sorgulama yapan betikler, Terminal konsoluna sahip olmadığı için başarısız olur.

### <a name="hook-script-not-supported-on-windows"></a>Kanca betiği Windows desteklenmiyor

post betiği *. sh* ise, Windows bilgisayarınızdaki bir uygulamayla ilişkili olmayabilir. Windows deposunda uyumlu bir uygulama bulmanızı isteyen bir Windows iletişim kutusu görebilirsiniz.

### <a name="templates-with-known-issues"></a>Bilinen sorunları olan şablonlar

Kopyalama başarısızlığı:

- **yavaya balık/cookiecutter-docgo-CRUD** ( `|` alt klasör adında geçersiz karakter)
- **cookiecutter-pyvanguard** ( `|` alt klasör adında geçersiz karakter)

Yükleme başarısızlığı:

- **chrisdev/Wagtail-cookiecutter-Foundation** ( *cookiecutter. JSON* içinde Boole türü kullanır)
- **quintoandar/cookiecutter-Android** (şablon klasörü yok)

Çalıştırma sorunları:

- **ıknite/cookiecutter-anerişilebilir-rol** (Post kanca betiği için konsol girişi gerekir)
- **benregn/cookiecutter-docgo-anerişilebilir** (jınja hatası)

Bash kullanır (önemli değil):

- **OpenStack-dev/cookiecutter**
