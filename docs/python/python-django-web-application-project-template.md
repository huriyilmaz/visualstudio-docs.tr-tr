---
title: Python için docgo Web projesi şablonu
description: Visual Studio, Python ile Docgo Web uygulamalarının hızlı bir şekilde oluşturulmasına yönelik kapsamlı bir şablon sağlar.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0193256edb4a55285e8017a56fe7249ef5d60362
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912406"
---
# <a name="django-web-project-template"></a>Django web projesi şablonu

[Docgo](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir Web geliştirme için tasarlanan üst düzey bir Python çerçevesidir. Visual Studio 'da Python desteği, bir Docgo tabanlı Web uygulamasının yapısını ayarlamak için çeşitli proje şablonları sağlar. Visual Studio 'da bir şablon kullanmak için **Dosya**  >  **Yeni**  >  **Proje**' yi seçin, "docgo" araması yapın ve **boş docgo Web projesinden**, **docgo** Web projesinden seçim yapın ve **docgo Web projesi şablonlarını yoklar** . Tüm şablonlar hakkında bir anlatım için bkz. [Docgo öğreticisi](learn-django-in-visual-studio-step-01-project-and-solution.md) .

Visual Studio, Docgo projeleri için tam IntelliSense sağlar:

- Şablona geçirilen bağlam değişkenleri:

    ![Bağlam değişkenleri için IntelliSense](media/template-django-intellisense.png)

- Hem yerleşik hem de Kullanıcı tanımlı için etiketleme ve filtreleme:

    ![Etiketler ve filtreler için IntelliSense](media/template-django-intellisense-filter.png)

- Katıştırılmış CSS ve JavaScript için sözdizimi renklendirme:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio, Docgo projeleri için tam [hata ayıklama desteği](debugging-python-in-visual-studio.md) de sağlar:

![Kesme noktaları](media/template-django-debugging.png)

Docgo projelerinin, Visual Studio 'nun izlediği bir varsayım olan *Manage.py* dosyası aracılığıyla yönetilmesi normaldir. Bu dosyayı giriş noktası olarak kullanmayı durdurursanız, aslında proje dosyasını kesebilirsiniz. Bu durumda, projeyi bir Docgo projesi olarak işaretlemeden [mevcut dosyalardan yeniden oluşturmanız](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) gerekir.

## <a name="django-management-console"></a>Docgo Yönetim Konsolu

Docgo yönetim konsoluna, **Proje** menüsündeki çeşitli komutlar aracılığıyla veya **Çözüm Gezgini**' de projeye sağ tıklanarak erişilir.

- **Docgo kabuğunu aç**: uygulama içeriklerinizde, modellerinizi yönetmenize olanak tanıyan bir kabuk açar:

    ![Open Docgo kabuğu komutunun sonuçları](media/template-django-console-shell.png)

- **Docgo EŞITLEME DB**: `manage.py syncdb` **etkileşimli** bir pencerede yürütülür:

    ![Docgo Sync DB komutunun sonucu](media/template-django-console-sync-db.png)

- **Statik topla**: `manage.py collectstatic --noinput` tüm statik dosyaları `STATIC_ROOT` *Settings.py* içinde belirtilen yola kopyalamak için yürütülür.

    ![Statik toplama komutunun sonucu](media/template-django-console-collect-static.png)

- **Validate**: `manage.py validate` , `INSTALLED_APPS` *Settings.py* içinde tarafından belirtilen yüklü modellerdeki doğrulama hatalarını raporlayan yürütülür:

    ![Validate komutunun sonucu](media/template-django-console-validate.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Docgo öğreticisini öğrenin](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
