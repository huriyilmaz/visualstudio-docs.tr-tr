---
title: Hızlı başlangıç-Cookiecutter kullanarak Python projeleri oluşturma
description: Bu hızlı başlangıçta, bir Cookiecutter şablonu kullanarak Python için bir Visual Studio projesi oluşturacaksınız.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902433"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Hızlı başlangıç: Cookiecutter şablonundan proje oluşturma

[Visual Studio 'Da Python desteğini](installing-python-support-in-visual-studio.md)yükledikten sonra, GitHub 'da yayımlanan çok sayıda de dahil olmak üzere bir Cookiecutter şablonundan yeni bir proje oluşturmak kolaydır. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve üzeri sürümlerde bulunur ve Visual Studio 'nun önceki sürümlerinde ayrı olarak yüklenebilir.

1. Bu hızlı başlangıçta, burada gösterilen Cookiecutter şablonu için gerekli Python paketlerini içeren Anaconda3 Python dağıtımını yüklemeniz gerekir. Visual Studio yükleyicisi 'ni çalıştırın, **Değiştir**' i seçin, sağ taraftaki **Python geliştirme** seçeneklerini genişletin ve **Anaconda3** (32-bit ya da 64-bit) seçeneğini belirleyin. Yükleme, Internet hızınıza bağlı olarak biraz zaman alabilir, ancak bu, gerekli paketleri yüklemenin en kolay yoludur.

1. Visual Studio 'Yu başlatın.

1.   >    >  **Cookiecutter 'ten** yeni dosya seçin. Bu komut, Visual Studio 'da şablonlara gözatabileceğiniz bir pencere açar.

    ![Cookiecutter şablonundan yeni proje](media/projects-from-cookiecutter1.png)

1. **Microsoft/Python-sköğren-sınıflandırıcı-cookiecutter** şablonunu seçtikten sonra **İleri**' yi seçin. (Visual Studio gerekli Python paketlerini yüklediğinde, işlem belirli bir şablonu ilk kez kullandığınızda birkaç dakika sürebilir.)

1. Sonraki adımda, **Oluştur** alanında yeni proje için bir konum ayarlayın **ve ardından proje oluştur ve aç**' ı seçin.

    ![Cookiecutter kullanarak ikinci adım, proje özelliklerini ayarlama](media/projects-from-cookiecutter2.png)

1. İşlem tamamlandığında, **şablon kullanarak dosyaları başarıyla oluşturdu** iletisini görürsünüz... Proje otomatik olarak Çözüm Gezgini açılır.

1.  + Programı çalıştırmak için CTRL **F5** tuşuna basın veya **hata ayıklama**  >  **olmadan Başlat** ' ı seçin.

    ![Python-sköğren-sınıflandırıcı-cookiecutter şablon projesinin çıkışı](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md)
- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteği 'ni yükler](installing-python-support-in-visual-studio.md)
- [Konum yüklemeleri](installing-python-support-in-visual-studio.md#install-locations)
