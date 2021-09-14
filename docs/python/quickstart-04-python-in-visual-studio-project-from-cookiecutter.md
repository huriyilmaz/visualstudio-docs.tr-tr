---
title: Hızlı başlangıç-Cookiecutter kullanarak Python projeleri oluşturma
description: bu hızlı başlangıçta, bir Cookiecutter şablonu kullanarak Python için bir Visual Studio projesi oluşturacaksınız.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 26e65a7aeee0d24b3c75b7251d6e4072103500f8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726789"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Hızlı başlangıç: Cookiecutter şablonundan proje oluşturma

[Visual Studio 'de Python desteğini](installing-python-support-in-visual-studio.md)yükledikten sonra, GitHub yayımlanan çok sayıda dahil olmak üzere bir Cookiecutter şablonundan yeni bir proje oluşturmak kolaydır. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve üzeri sürümlerde bulunur ve Visual Studio önceki sürümlerinde ayrı olarak yüklenebilir.

1. Bu hızlı başlangıçta, burada gösterilen Cookiecutter şablonu için gerekli Python paketlerini içeren Anaconda3 Python dağıtımını yüklemeniz gerekir. Visual Studio yükleyiciyi çalıştırın, **değiştir**' i seçin, sağ taraftaki **Python geliştirme** seçeneklerini genişletin ve **Anaconda3** (32-bit veya 64-bit) seçeneğini belirleyin. Yükleme, Internet hızınıza bağlı olarak biraz zaman alabilir, ancak bu, gerekli paketleri yüklemenin en kolay yoludur.

1. Visual Studio başlatın.

1.   >    >  **Cookiecutter 'ten** yeni dosya seçin. bu komut, Visual Studio ' de şablonlara gözatabileceğiniz bir pencere açar.

    ![Cookiecutter şablonundan yeni Project](media/projects-from-cookiecutter1.png)

1. **Microsoft/Python-sköğren-sınıflandırıcı-cookiecutter** şablonunu seçtikten sonra **İleri**' yi seçin. (Visual Studio gerekli Python paketlerini yüklediği için, işlem belirli bir şablonu ilk kez kullandığınızda birkaç dakika sürebilir.)

1. Sonraki adımda, **Oluştur** alanında yeni proje için bir konum ayarlayın **ve ardından Project oluştur ve aç**' ı seçin.

    ![Cookiecutter kullanarak ikinci adım, proje özelliklerini ayarlama](media/projects-from-cookiecutter2.png)

1. İşlem tamamlandığında, **şablon kullanarak dosyaları başarıyla oluşturdu** iletisini görürsünüz... Proje otomatik olarak Çözüm Gezgini açılır.

1.  + Programı çalıştırmak için CTRL **F5** tuşuna basın veya **hata ayıklama**  >  **olmadan Başlat** ' ı seçin.

    ![Python-sköğren-sınıflandırıcı-cookiecutter şablon projesinin çıkışı](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'de Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md)
- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteği yüklemesi](installing-python-support-in-visual-studio.md)
- [Konum yüklemeleri](installing-python-support-in-visual-studio.md#install-locations)
