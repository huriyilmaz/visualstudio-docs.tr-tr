---
title: Python projeleri için öğe şablonları
description: Visual Studio'daki Yeni Öğe > Ekle iletişim kutusunda kullanılabilen Python projesi için madde şablonlarının başvuru listesi.
ms.date: 12/06/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c093dad1364fd5209f51c8e87e3fb99b3c1d3c4a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430342"
---
# <a name="python-item-templates"></a>Python öğe şablonları

Öğe şablonları, **Project** > **Add New Item** menüsü komutu veya Çözüm **Gezgini'ndeki**bağlam menüsünde Yeni**Öğe** **Ekle** > komutu aracılığıyla Python projelerinde kullanılabilir.

![Yeni Öğe iletişim kutusu ekle](media/project-item-templates.png)

Öğe için sağladığınız adı kullanarak, şablon genellikle projede şu anda seçili klasörde bir veya daha fazla dosya ve klasör oluşturur (bağlam menüsünü getirmek için bir klasörü sağ tıklatmak bu klasörü otomatik olarak seçer). Bir öğe ekleme Visual Studio projesinde içerir ve öğe **Solution Explorer'da**görünür.

Aşağıdaki tablo, python projesindeki her öğe şablonunun etkisini kısaca açıklar:

| Şablon | Şablon ne oluşturur |
| --- | --- |
| **Boş Python Dosyası** | *.py* uzantılı boş bir dosya. |
| **Python sınıfı** | Tek bir boş Python sınıf tanımı içeren bir *.py* dosyası. |
| **Python Paketi** | * \_ \_Init\_.py dosyası içeren bir klasör.\_* |
| **Python Birim Testi** | Çerçeveye dayalı tek bir birim testine sahip bir *.py* dosyası ve dosyadaki testleri çalıştırma çağrısı. `unittest.main()` `unittest` |
| **HTML Sayfası** | A `<head>` ve `<body>` öğeden oluşan basit bir sayfa yapısına sahip bir *.html* dosyası. |
| **Javascript** | Boş bir *.js* dosyası. |
| **Stil Sayfası** | `body`Için boş bir stil içeren bir *.css* dosyası |
| **Metin dosyası** | Boş *bir .txt* dosyası. |
| **Django 1.9 Uygulaması**<br/>**Django 1.4 Uygulaması** | [Visual Studio, Adım 2-2 Django](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) 1.9 için Öğrenin Django açıklandığı gibi bir Django uygulaması için çekirdek dosyaları içeren uygulamanın adını içeren bir klasör. Django 1.4 için *geçişler* klasörü, *admin.py* dosyası ve *apps.py* dosyası dahil edilmez. |
| **IronPython WPF Penceresi** | İki yan yana dosyadan oluşan bir WPF Penceresi: boş `<Grid>` bir öğeyle `<Window>` a tanımlayan *bir .xaml* dosyası ve `wpf` kitaplığı kullanarak XAML dosyasını yükleyen ilişkili bir *.py* dosyası. Genellikle IronPython proje şablonlarından biri kullanılarak oluşturulan bir proje içinde kullanılır. Bkz. [Python projelerini yönet - Proje şablonları.](managing-python-projects-in-visual-studio.md#project-templates) |
| **Web Rolü Destek Dosyaları** | Proje kökündeki bir *depo gözü* klasörü (projedeki seçili klasörden bağımsız olarak). Klasör, varsayılan dağıtım komut dosyası ve Azure Bulut Hizmeti web rolleri için bir *web.config* dosyası içerir. Şablon ayrıca ayrıntıları açıklayan bir *readme.html* dosyası içerir. |
| **İşçi Rolü Destek Dosyaları** | Proje kökündeki bir *depo gözü* klasörü (projedeki seçili klasörden bağımsız olarak). Klasör, Azure Bulut Hizmeti çalışanı rolleri için varsayılan dağıtım ve başlatma komut dosyasının yanı sıra bir *web.config* dosyası içerir. Şablon ayrıca ayrıntıları açıklayan bir *readme.html* dosyası içerir. |
| **Azure web.config (FastCGI)** | Gelen bağlantıları işlemek için [WSGI nesnesi](https://wsgi.readthedocs.io/en/latest/) kullanan uygulamalar için girişler içeren bir *web.config* dosyası. Bu dosya genellikle IIS çalıştıran bir web sunucusunun köküne dağıtılır. Daha fazla bilgi için [IIS için bir uygulamayı Yapılandır'a](configure-web-apps-for-iis-windows.md)bakın. |
| **Azure web.config (HttpPlatformHandler)** | Gelen bağlantılar için bir soket üzerinde dinleyen uygulamaların girişlerini içeren bir *web.config* dosyası. Bu dosya genellikle Azure Uygulama Hizmeti gibi IIS çalıştıran bir web sunucusunun köküne dağıtılır. Daha fazla bilgi için [IIS için bir uygulamayı Yapılandır'a](configure-web-apps-for-iis-windows.md)bakın. |
| **Azure statik dosyalar web.config** | Bir *web.config* dosyası genellikle *statik* bir klasöre (veya statik öğeler içeren diğer klasöre) eklenen python işlemedevre dışı kalmıştır. Bu config dosyası yukarıdaki FastCGI veya HttpPlatformHandler config dosyalarından biri ile birlikte çalışır. Daha fazla bilgi için [IIS için bir uygulamayı Yapılandır'a](configure-web-apps-for-iis-windows.md)bakın. |
| **Azure Uzaktan hata ayıklama web.config** | Amortismana dahil edildi (artık desteklenmeyen Windows için Azure Uygulama Hizmeti'nde uzaktan hata ayıklama için kullanıldı). |

## <a name="see-also"></a>Ayrıca bkz.

- [Python projelerini yönetme - Proje şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- [Python web proje şablonları](python-web-application-project-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
