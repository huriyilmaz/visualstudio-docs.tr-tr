---
title: Python için docgo Web projesi şablonu
description: Visual Studio Python ile docgo web uygulamalarının hızlı bir şekilde oluşturulmasına yönelik kapsamlı bir şablon sağlar.
ms.date: 11/12/2018
ms.topic: conceptual
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 6df9a619e55be2cead9cc5cc98d8c1d852a97148
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971120"
---
# <a name="django-web-project-template"></a>Django web projesi şablonu
::: moniker range="vs-2017"
[Docgo](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir Web geliştirme için tasarlanan üst düzey bir Python çerçevesidir. Visual Studio 'de Python desteği, bir docgo tabanlı web uygulamasının yapısını ayarlamak için çeşitli proje şablonları sağlar. Visual Studio bir şablon kullanmak için, **dosya**  >  **yeni**  >  **Project** seçin, "docgo" araması yapın ve **boş docgo web Project**, **docgo web Project**' nden seçim yapın ve **docgo web Project şablonlarını yoklar** . Tüm şablonlar hakkında bir anlatım için bkz. [Docgo öğreticisi](learn-django-in-visual-studio-step-01-project-and-solution.md) .
::: moniker-end
::: moniker range=">=vs-2019"
[Docgo](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir Web geliştirme için tasarlanan üst düzey bir Python çerçevesidir. Visual Studio 'de Python desteği, bir docgo tabanlı web uygulamasının yapısını ayarlamak için çeşitli proje şablonları sağlar. Visual Studio bir şablon kullanmak için **dosya**  >  **yeni**  >  **Project** seçin, "docgo" araması yapın ve **boş docgo web Project** ve **docgo web Project** şablonlarından seçim yapın. Tüm şablonlar hakkında bir anlatım için bkz. [Docgo öğreticisi](learn-django-in-visual-studio-step-01-project-and-solution.md) .
::: moniker-end
Visual Studio docgo projeleri için tam ıntellisense sağlar:

- Şablona geçirilen bağlam değişkenleri:

    ![Bağlam değişkenleri için IntelliSense](media/template-django-intellisense.png)

- Hem yerleşik hem de Kullanıcı tanımlı için etiketleme ve filtreleme:

    ![Etiketler ve filtreler için IntelliSense](media/template-django-intellisense-filter.png)

- Katıştırılmış CSS ve JavaScript için sözdizimi renklendirme:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio ayrıca, docgo projeleri için tam [hata ayıklama desteği](debugging-python-in-visual-studio.md) sağlar:

![Kesme noktaları](media/template-django-debugging.png)

docgo projelerinin *manage.py* dosyası aracılığıyla yönetilmesi normaldir, bu da Visual Studio bir varsayımlar. Bu dosyayı giriş noktası olarak kullanmayı durdurursanız, aslında proje dosyasını kesebilirsiniz. Bu durumda, projeyi bir Docgo projesi olarak işaretlemeden [mevcut dosyalardan yeniden oluşturmanız](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) gerekir.

## <a name="django-management-console"></a>Docgo Yönetim Konsolu

docgo yönetim konsoluna **Project** menüsündeki çeşitli komutlar aracılığıyla veya **Çözüm Gezgini** içindeki projeye sağ tıklanarak erişilir.

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
