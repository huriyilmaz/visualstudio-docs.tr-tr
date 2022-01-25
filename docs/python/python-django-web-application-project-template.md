---
title: Python için Django web projesi şablonu
description: Visual Studio Python ile Django web uygulamalarının hızlı bir şekilde oluşturulması için kapsamlı bir şablon sağlar.
ms.date: 01/19/2022
ms.topic: conceptual
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: c7b626bfd9914f832a12ffac51e978b849ad1ae8
ms.sourcegitcommit: f81a8f381bcdbac96d112f815737ba1df55d97a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137667388"
---
# <a name="django-web-project-template"></a>Django web projesi şablonu
::: moniker range="vs-2017"
[Django](https://www.djangoproject.com/) hızlı, güvenli ve ölçeklenebilir web geliştirme için tasarlanmış üst düzey bir Python çerçevesidir. Visual Studio Python desteği, Django tabanlı bir web uygulamasının yapısını ayarlamak için çeşitli proje şablonları sağlar. Visual Studio'de şablon kullanmak için Dosya Yeni  >    >  **Project'yi** seçin, "Django" araması yazın ve **Boş Django Web Project**, **Django Web Project** ve **Polls Django Web** Project şablonlarını seçin. Tüm [şablonların izlenecek yolu](learn-django-in-visual-studio-step-01-project-and-solution.md) için Bkz. Learn Django öğreticisi.
::: moniker-end
::: moniker range=">=vs-2019"
[Django](https://www.djangoproject.com/) hızlı, güvenli ve ölçeklenebilir web geliştirme için tasarlanmış üst düzey bir Python çerçevesidir. Visual Studio Python desteği, Django tabanlı bir web uygulamasının yapısını ayarlamak için çeşitli proje şablonları sağlar. Visual Studio'de şablon kullanmak için Dosya Yeni  >    >  **Project'yi** seçin, "Django" araması yazın ve **Boş Django Web Project** ve **Django Web** Project seçin. Tüm [şablonların izlenecek yolu](learn-django-in-visual-studio-step-01-project-and-solution.md) için Bkz. Learn Django öğreticisi.
::: moniker-end
Visual Studio Django projeleri için tam IntelliSense sağlar:

- Şablona geçirilen bağlam değişkenleri:

    ![Bağlam değişkenleri için IntelliSense](media/template-django-intellisense.png)

- Hem yerleşik hem de kullanıcı tanımlı için etiketleme ve filtreleme:

    ![Etiketler ve filtreler için IntelliSense](media/template-django-intellisense-filter.png)

- Ekli CSS ve JavaScript için söz dizimi renklendirmesi:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio Django [projeleri için tam hata](debugging-python-in-visual-studio.md) ayıklama desteği de sağlar:

![Kesme noktaları](media/template-django-debugging.png)

Django projeleri tipik olarak kendi manage.py  dosyası aracılığıyla yönetilir. Bu, projelerin Visual Studio varsayımdır. Bu dosyayı giriş noktası olarak kullanmayı durdurursanız, temelde proje dosyasını bozabilirsiniz. Bu durumda projeyi Django [projesi olarak işaretlemeden](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) mevcut dosyalardan yeniden oluşturmanız gerekir.

## <a name="django-management-console"></a>Django yönetim konsolu

Django yönetim konsoluna, Project menüsündeki çeşitli komutlar aracılığıyla veya **Çözüm Gezgini.** 

- **Django Shell'i** açın: Uygulama bağlamında modellerinizi işlemenizi sağlayan bir kabuk açar:

    ![Open Django Shell komutunun sonuçları](media/template-django-console-shell.png)

- **Django Sync DB:** Etkileşimli `manage.py syncdb` pencerede **yürütülür:**

    ![Django Sync DB komutunun sonucu](media/template-django-console-sync-db.png)

- **Statik Toplama:** tüm statik dosyaları dosyanız içinde tarafından belirtilen `manage.py collectstatic --noinput` yola kopyalamak için `STATIC_ROOT` *settings.py.*

    ![Statik Topla komutunun sonucu](media/template-django-console-collect-static.png)

- **Doğrulama:**, tarafından belirtilen yüklü modellerde doğrulama hatalarını `manage.py validate` raporlayan yürütülür ve `INSTALLED_APPS` settings.py:

    ![Doğrula komutunun sonucu](media/template-django-console-validate.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Django öğreticisi hakkında bilgi edin](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
