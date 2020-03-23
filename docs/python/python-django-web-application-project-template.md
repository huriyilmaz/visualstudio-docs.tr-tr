---
title: Python için Django web proje şablonu
description: Visual Studio Python ile Django web uygulamalarının hızlı oluşturulması için kapsamlı bir şablon sağlar.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 136c03ef11071e5d548e36e45a6a541cffce1469
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784887"
---
# <a name="django-web-project-template"></a>Django web projesi şablonu

[Django,](https://www.djangoproject.com/) hızlı, güvenli ve ölçeklenebilir web geliştirme için tasarlanmış üst düzey bir Python çerçevesidir. Visual Studio'daki Python desteği, Django tabanlı bir web uygulamasının yapısını ayarlamak için çeşitli proje şablonları sağlar. Visual Studio'da şablon kullanmak **için,** > "Django" için Dosya**Yeni** > **Projesi'ni**seçin ve **Boş Django Web Projesi, Django Web** **Projesi**ve **Anketler Django Web Project** şablonlarından seçin. Tüm şablonların gözden geçirimi için [Django'yu Öğrenin öğreticisini](learn-django-in-visual-studio-step-01-project-and-solution.md) görün.

Visual Studio, Django projeleri için tam IntelliSense sağlar:

- Şablona geçirilen bağlam değişkenleri:

    ![Bağlam değişkenleri için IntelliSense](media/template-django-intellisense.png)

- Hem yerleşik hem de kullanıcı tanımlı için etiketleme ve filtreleme:

    ![Etiketler ve filtreler için IntelliSense](media/template-django-intellisense-filter.png)

- Gömülü CSS ve JavaScript için sözdizimi boyama:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio ayrıca Django projeleri için tam [hata ayıklama desteği](debugging-python-in-visual-studio.md) sağlar:

![Kesme Noktaları](media/template-django-debugging.png)

Django projelerinin *manage.py* dosyası üzerinden yönetilmesi tipik tir, bu da Visual Studio'nun takip ettiği bir varsayımdır. Bu dosyayı giriş noktası olarak kullanmayı bırakırsanız, proje dosyasını temelolarak kırarsınız. Bu durumda, projeyi Django projesi olarak işaretlemeden [varolan dosyalardan yeniden oluşturmanız](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) gerekir.

## <a name="django-management-console"></a>Django yönetim konsolu

Django yönetim konsoluna **Proje** menüsündeki çeşitli komutlarla veya **Solution Explorer'daki**projeye sağ tıklayarak erişilir.

- **Açık Django Shell**: Uygulama bağlamınızda modellerinizi işlemenizi sağlayan bir kabuk açar:

    ![Açık Django Shell komutunun sonuçları](media/template-django-console-shell.png)

- **Django Sync DB** `manage.py syncdb` : **Etkileşimli** bir pencerede yürütür:

    ![Django Sync DB komutunun sonucu](media/template-django-console-sync-db.png)

- **Collect Static**: `manage.py collectstatic --noinput` tüm statik dosyaları `STATIC_ROOT` *settings.py.*

    ![Statik topla komutunun sonucu](media/template-django-console-collect-static.png)

- **Validate**: `manage.py validate` `INSTALLED_APPS` *settings.py:*

    ![Doğrulama komutunun sonucu](media/template-django-console-validate.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Django öğretici öğrenin](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
