---
title: Python projeleri için öğe şablonları
description: Yeni Öğe Ekle iletişim kutusu aracılığıyla kullanılabilen Python projesine ait öğe şablonlarının > listesi Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e637e935e860b27337a829fc9f736e53c4428acf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726793"
---
# <a name="python-item-templates"></a>Python öğe şablonları

Öğe şablonları, Python projelerinde yeni **öğe Project** ekle menü komutu veya Çözüm Gezgini'de bağlam menüsündeki Yeni Öğe Ekle komutu  >     >   **aracılığıyla** kullanılabilir.

![Yeni Öğe Ekle iletişim kutusu](media/project-item-templates.png)

Öğe için istediğiniz adı kullanarak bir şablon genellikle projede seçili olan klasör içinde bir veya daha fazla dosya ve klasör oluşturur (bağlam menüsünü getirmek için bir klasöre sağ tıklarsanız bu klasör otomatik olarak seçilir). Bir öğe eklendiğinde bu öğe Visual Studio içerir ve öğe **Çözüm Gezgini.**

Aşağıdaki tabloda Python projesi içindeki her öğe şablonunun etkisi kısaca açık bir şekilde açık açıklamadır:

| Şablon | Şablonun oluşturduğu şey |
| --- | --- |
| **Boş Python Dosyası** | *.py* uzantısına sahip boş bir dosya. |
| **Python sınıfı** | Tek bir boş Python sınıf tanımı içeren *bir .py* dosyası. |
| **Python Paketi** | *\_ \_ Init \_ \_ .py dosyası içeren bir* klasör. |
| **Python Birim Testi** | Çerçeveyi temel alan tek bir birim testinin yanı sıra dosyada testleri çalıştırma çağrısına sahip bir *.py* `unittest` `unittest.main()` dosyası. |
| **HTML Sayfası** | Bir *.html* ve öğesi oluşan basit bir sayfa yapısına sahip bir `<head>` `<body>` dosya. |
| **JavaScript** | Boş bir  *.js* dosyası. |
| **Stil Sayfası** | için boş stil içeren *bir .css* `body` dosyası. |
| **Metin dosyası** | Boş bir *.txt* dosyası. |
| **Django 1.9 Uygulaması**<br/>**Django 1.4 Uygulaması** | [Django 1.9 için 2.2.](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) Adım olan Visual Studio'da Learn Django'da açıklanan Django uygulamasının temel dosyalarını içeren uygulamanın adını içeren klasör. Django 1.4 için *migrations* klasörü, *admin.py* dosyası ve *apps.py* dosyası dahil değildir. |
| **IronPython WPF Penceresi** | İki yan yana dosyadan oluşan bir WPF Penceresi: boş bir öğesiyle tanımlayan *bir .xaml* dosyası ve kitaplığını kullanarak XAML dosyasını yüken ilişkili `<Window>` bir `<Grid>` *.py* `wpf` dosyası. Genellikle IronPython proje şablonlarından biri kullanılarak oluşturulan bir proje içinde kullanılır. Bkz. [Python projelerini yönetme - Project şablonları.](managing-python-projects-in-visual-studio.md#project-templates) |
| **Web Rolü Destek Dosyaları** | Proje *kökünde* (projedeki seçili klasöre bakılmaksızın) bir bin klasörü. Klasör, Azure Cloud Service web rolleri için *birweb.config* dağıtım betiği ve bir dosya içerir. Şablon ayrıca ayrıntıları *readme.html* bir dosya içerir. |
| **Çalışan Rolü Destek Dosyaları** | Proje *kökünde* (projedeki seçili klasöre bakılmaksızın) bir bin klasörü. Klasör, Azure Cloud Service çalışan rolleri için bir *web.config* ve başlatma betiği içerir. Şablon ayrıca ayrıntıları *readme.html* bir dosya içerir. |
| **Azure web.config (FastCGI)** | [WsGI](https://wsgi.readthedocs.io/en/latest/) *web.config* gelen bağlantıları işlemek için uygulamalara ait girdileri içeren bir dosyadır. Bu dosya genellikle IIS çalıştıran bir web sunucusunun köküne dağıtılır. Daha fazla bilgi için [bkz. IIS için uygulama yapılandırma.](configure-web-apps-for-iis-windows.md) |
| **Azure web.config (HttpPlatformHandler)** | Gelen *web.config* yuvada dinleyen uygulamalar için girdileri içeren bir dosyadır. Bu dosya genellikle IIS çalıştıran bir web sunucusunun köküne dağıtılır, örneğin Azure App Service. Daha fazla bilgi için [bkz. IIS için uygulama yapılandırma.](configure-web-apps-for-iis-windows.md) |
| **Azure statik dosyaları web.config** | Bu *web.config* Python işlemesini devre *dışı* bırakmak için genellikle bir statik klasöre (veya statik öğeler içeren başka bir klasöre) bir dosya eklenir. Bu yapılandırma dosyası, yukarıdaki FastCGI veya HttpPlatformHandler yapılandırma dosyalarından biri ile birlikte çalışır. Daha fazla bilgi için [bkz. IIS için uygulama yapılandırma.](configure-web-apps-for-iis-windows.md) |
| **Azure Uzaktan hata ayıklama web.config** | Kullanım dışı (artık destek Azure App Service için Windows hata ayıklama için kullanılmıştır). |

## <a name="see-also"></a>Ayrıca bkz.

- [Python projelerini yönetme - Project şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- [Python web projesi şablonları](python-web-application-project-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
