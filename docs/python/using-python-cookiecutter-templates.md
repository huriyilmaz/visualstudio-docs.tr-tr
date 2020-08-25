---
title: Python ile CookieCutter şablonlarını kullanma
description: Visual Studio, Python kodu için şablonları bulmaya ve bu şablonlardan projeler oluşturmaya yönelik grafik Cookiecutter uzantısını destekler.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2d58462b90039e14ae98fe450812ca4cfdb6cbbd
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801587"
---
# <a name="use-the-cookiecutter-extension"></a>Cookiecutter uzantısını kullanma

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve üzeri sürümlerde bulunur ve Visual Studio 'nun önceki sürümlerinde ayrı olarak yüklenebilir.

Cookiecutter, Python 3,3 veya üzeri (32-bit veya 64-bit) veya Anaconda 3 4,2 veya üzeri (32-bit veya 64-bit) gerektirir. Uygun bir Python yorumlayıcı yoksa, Visual Studio bir uyarı görüntüler. Visual Studio çalışırken bir Python yorumlayıcı yüklerseniz, yeni yüklenen yorumlayıcı algılamak için Cookiecutter araç çubuğundaki **giriş** düğmesini seçin. (Genel olarak ortamlar hakkında daha fazla bilgi için bkz. [Python ortamları](managing-python-environments-in-visual-studio.md) .)

Yüklendikten sonra, **View**  >  **Cookiecutter Gezginini** görüntüle ' yi seçerek penceresini açın:

![Cookiecutter ana penceresi](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter iş akışı

Cookiecutter ile çalışma, bir şablona göz atma ve seçme, yerel bilgisayarınıza kopyalama, seçenekleri ayarlama ve bu şablondan kod oluşturma işlemlerini izleyen bölümlerde açıklandığı gibi bir işlemdir.

### <a name="browse-templates"></a>Şablonlara gözatamıyorum

Cookiecutter giriş sayfasında, aşağıdaki gruplar halinde düzenlenmiş, aralarından seçim yapabileceğiniz şablonların bir listesi görüntülenir:

| Grup | Açıklama |
| --- | --- |
| **Yüklendi** | Yerel bilgisayarınıza yüklenmiş şablonlar. Çevrimiçi bir şablon kullanıldığında, deposu otomatik olarak *~/. tanımlama bilgisi ecutters*alt klasörüne kopyalanır. Seçili yüklü bir şablonu **Sil**' i tıklatarak silebilirsiniz. |
| **Önerilen** | Önerilen akıştan yüklenen şablonlar. Varsayılan akış Microsoft tarafından yapılır. Akışı özelleştirme hakkında daha fazla bilgi için aşağıdaki [Cookiecutter seçeneklerine](#cookiecutter-options) bakın. |
| **GitHub** | Cookiecutter anahtar sözcüğü için GitHub arama sonuçları. GitHub sonuçları, daha fazla sonuç varsa, listenin sonunda **daha fazla yükle** görüntülenir. |
| **Özel** | Arama kutusuna özel bir konum girildiğinde, bu grupta görünür. GitHub deposunun tam yolunu ya da yerel diskinizdeki bir klasöre tam yolu yazabilirsiniz. |

### <a name="cloning"></a>Kopyalama

Bir şablonu seçip **İleri**' yi seçtiğinizde, Cookiecutter yerel bir kopyanın çalışmasına neden olur.

**Önerilen** veya **GitHub** gruplarından bir şablon seçerseniz veya arama kutusuna özel bir URL girerseniz ve bu şablonu seçerseniz, kopyalanıp yerel bilgisayarınıza yüklenir. Bu şablon, Visual Studio 'nun önceki oturumunda yüklüyse, otomatik olarak silinir ve en son sürüm klonlanır.

**Yüklü** gruptan bir şablon seçer veya arama kutusuna özel bir klasör yolu girip bu şablonu seçerseniz, Visual Studio bu şablonu kopyalamaya gerek kalmadan yükler.

> [!Important]
> Cookiecutter şablonları tek bir klasör altına kopyalanır *~/. tanımlama bilgisi ecutters*. Her alt klasör, GitHub Kullanıcı adını içermeyen git deposu adından sonra adlandırılır. Farklı yazarlardan gelen aynı ada sahip farklı şablonları klonladığınızda çakışmalar ortaya çıkabilir. Bu durumda, Cookiecutter, var olan şablonun aynı ada sahip farklı bir şablonla üzerine yazılmasını engeller. Diğer şablonu yüklemek için, önce mevcut olanı silmeniz gerekir.

### <a name="set-template-options"></a>Şablon seçeneklerini ayarla

Şablon yerel olarak yüklendikten sonra Cookiecutter, Cookiecutter 'in diğer seçeneklerle birlikte dosya oluşturmasını istediğiniz yeri belirtebileceğiniz bir seçenekler sayfası görüntüler:

![Cookiecutter seçenekleri sayfası](media/cookiecutter-template-options.png)

Her bir Cookiecutter şablonu kendi seçenek kümesini tanımlar ve her biri için varsayılan bir değer belirtir (her giriş alanında önerilen metin olarak gösterilir). Genellikle diğer seçenekleri kullanan dinamik bir değer olduğunda, varsayılan değer bir kod parçacığı olabilir.

Bir Kullanıcı yapılandırma dosyası ile belirli seçenekler için varsayılan değerleri özelleştirmek mümkündür. Cookiecutter uzantısı bir Kullanıcı yapılandırma dosyası algıladığında, şablonun varsayılan değerlerini kullanıcı yapılandırmasının varsayılan değerleriyle geçersiz kılar. Bu davranış, Cookiecutter belgelerinin [Kullanıcı Yapılandırması](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) bölümünde ele alınmıştır.

Şablon, kod üretimi sonrasında çalıştırılacak belirli Visual Studio görevlerini belirtiyorsa, bu görevleri kapatmanıza izin veren ek bir ek **Görevler Çalıştır** seçeneği görüntülenir. Görevlerin en yaygın kullanımı, bir Web tarayıcısını açmak, düzenleyicide dosyaları açmak, bağımlılıkları yüklemek ve bu şekilde devam eder.

### <a name="create"></a>Oluştur

Seçeneklerinizi ayarladıktan sonra kod oluşturmak için **Oluştur** ' u seçin (çıktı klasörü boş değilse bir uyarı görünür). Şablonun çıktısını öğrenmeniz ve dosyaların üzerine yazılmayamıyorsanız, uyarıyı kapatabilirsiniz. Aksi takdirde, **iptal**' i seçin, boş bir klasör belirtin ve ardından oluşturulan dosyaları boş olmayan çıkış klasörünüze el ile kopyalayın.

Dosyalar başarıyla oluşturulduktan sonra, Cookiecutter **Çözüm Gezgini**dosyaları açmak için bir seçenek sunar:

![Çözüm Gezgini komutu gösteren Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter seçenekleri

Cookiecutter seçenekleri **Araçlar**  >  **Seçenekler**  >  **Cookiecutter**aracılığıyla kullanılabilir:

![Cookiecutter seçenekleri](media/cookiecutter-tools-options.png)

| Seçenek | Açıklama |
| --- | --- |
| **Önerilen akış URL 'SI** | Önerilen şablonlar akışı konumu. Bu bir URL veya yerel bir dosyanın yolu olabilir. Varsayılan Microsoft seçkin akışını kullanmak için URL 'YI boş bırakın. Akış, newlines ile ayrılmış, şablon konumlarının basit bir listesini sağlar. Seçkin akışta değişiklik istemek için [GitHub 'da kaynak](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt)üzerinde bir çekme isteği oluşturun. |
| **Yardımı göster** | Cookiecutter penceresinin en üstündeki yardım bilgileri çubuğunun görünürlüğünü denetler. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Visual Studio için Cookiecutter şablonlarını iyileştirme

Cookiecutter şablonu yazma temelleri için bkz. [Cookiecutter belgeleri](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Visual Studio için Cookiecutter uzantısı, Cookiecutter v 1.4 için oluşturulan şablonları destekler.

Şablon değişkenlerinin varsayılan işlemesi, veri türüne (dize veya liste) göre değişir:

- String: değişken adı için etiket, değer girmek için metin kutusu ve varsayılan değeri gösteren bir filigran. Metin kutusundaki araç ipucu varsayılan değeri gösterir.
- List: değişken adı için etiket, bir değer seçmek için Birleşik giriş kutusu. Birleşik giriş kutusundaki araç ipucu varsayılan değeri gösterir.

Bu işleme üzerinde, Visual Studio 'ya özgü (ve Cookiecutter CLı tarafından yoksayılan) dosya *cookiecutter.js* ek meta verileri belirterek geliştirmek mümkündür. Tüm özellikler isteğe bağlıdır:

| Özellik | Açıklama |
| --- | --- |
| Etiketle | Değişken için, değişkenin adı yerine düzenleyicinin üzerinde ne göründüğünü belirtir. |
| Açıklama | Bu değişken için varsayılan değer yerine, düzenleme denetiminde görünen araç ipucunu belirtir. |
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

### <a name="run-visual-studio-tasks"></a>Visual Studio görevlerini çalıştırma

Cookiecutter, dosyalar oluşturulduktan sonra rastgele Python kodu çalıştırmaya izin veren, *oluşturma sonrası kancalar* adlı bir özelliğe sahiptir. Esnek olsa da, Visual Studio 'ya kolay erişime izin vermez.

Örneğin, Visual Studio düzenleyicisinde veya Web tarayıcısında bir dosyayı açmak ya da kullanıcıdan bir sanal ortam oluşturmasını ve paket gereksinimlerini yüklemesini isteyen Visual Studio Kullanıcı arabirimini tetiklemeniz gerekebilir.

Bu senaryolara izin vermek için, Visual Studio, Kullanıcı oluşturulan dosyaları **Çözüm Gezgini** açtıktan sonra veya var olan bir projeye eklendikten sonra çalıştırılacak komutları açıklayan, *üzerindecookiecutter.js* genişletilmiş meta verileri arar. (Yine de Kullanıcı, şablon seçeneklerinde **tamamlandığında ek görevleri Çalıştır** ' ı temizleyerek görevleri çalıştırmayı tercih edebilir.)

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

Komutlar ad ile belirtilir ve Visual Studio 'nun yerelleştirilmiş yüklemeleri üzerinde çalışmak için yerelleştirilmemiş (Ingilizce) adı kullanmalıdır. Visual Studio **komut** penceresinde komut adlarını test edebilir ve keşfedebilirsiniz.

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

`Python.InstallProjectRequirements`Komutun yalnızca mevcut bir projeye dosya eklerken çalıştığına unutmayın. Bu sınırlama, komut **Çözüm Gezgini**' de Python projesi tarafından işlendiği ve **Çözüm Gezgini**  -  **klasör görünümünde**iletiyi alacak bir proje bulunmadığından oluşur. Gelecek bir sürümü kazanmanızı (ve genel olarak daha iyi **klasör görünümü** desteği sağlamayı) umuyoruz.

## <a name="troubleshooting"></a>Sorun giderme

### <a name="error-loading-template"></a>Şablon yüklenirken hata oluştu

Bazı şablonlar, * üzerindecookiecutter.js*, Boolean gibi geçersiz veri türlerini kullanıyor olabilir. Şablon bilgileri bölmesindeki **sorunlar** bağlantısını seçerek şablon yazarına bu tür örnekler bildirin.

### <a name="hook-script-failed"></a>Kanca betiği başarısız oldu

Bazı şablonlar, Cookiecutter Kullanıcı arabirimiyle uyumlu olmayan oluşturma sonrası betikleri kullanabilir. Örneğin, Kullanıcı girişi için sorgulama yapan betikler, Terminal konsoluna sahip olmadığı için başarısız olur.

### <a name="hook-script-not-supported-on-windows"></a>Kanca betiği Windows üzerinde desteklenmez

Post betiği *. sh*Ise, Windows bilgisayarınızdaki bir uygulamayla ilişkili olmayabilir. Windows Mağazası 'nda uyumlu bir uygulama bulmanızı isteyen bir Windows iletişim kutusu görebilirsiniz.

### <a name="templates-with-known-issues"></a>Bilinen sorunları olan şablonlar

Kopyalama başarısızlığı:

- **yavaya balık/cookiecutter-docgo-CRUD** ( `|` alt klasör adında geçersiz karakter)
- **cookiecutter-pyvanguard** ( `|` alt klasör adında geçersiz karakter)

Yükleme başarısızlığı:

- **chrisdev/Wagtail-cookiecutter-Foundation** ( *cookiecutter.jsüzerinde*bir Boole türü kullanır)
- **quintoandar/cookiecutter-Android** (şablon klasörü yok)

Çalıştırma sorunları:

- **ıknite/cookiecutter-anerişilebilir-rol** (Post kanca betiği için konsol girişi gerekir)
- **benregn/cookiecutter-docgo-anerişilebilir** (jınja hatası)

Bash kullanır (önemli değil):

- **OpenStack-dev/cookiecutter**
