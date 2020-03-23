---
title: Quickstart - Cookiecutter kullanarak bir Python projesi oluşturma
description: Bu hızlı başlangıçta, Bir Cookiecutter şablonu kullanarak Python için bir Visual Studio projesi oluşturursunuz.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f3e7f56f4a36a7958cba9bd7092f38d735123d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62954524"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Hızlı başlatma: Cookiecutter şablonundan proje oluşturma

[Visual Studio'ya Python desteğini yükledikten](installing-python-support-in-visual-studio.md)sonra, GitHub'da yayınlanan birçok proje de dahil olmak üzere Bir Cookiecutter şablonundan yeni bir proje oluşturmak kolaydır. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları keşfetmek, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için grafiksel bir kullanıcı arabirimi sağlar. Visual Studio 2017 ve daha sonraki sürümlerinde ayrıca yüklenebilir.

1. Bu hızlı başlangıç için, ilk burada gösterilen Cookiecutter şablonu için gerekli Python paketleri içeren Anaconda3 Python dağıtım yükleyin. Visual Studio yükleyicisini çalıştırın, **Değiştir'i**seçin, sağ **taraftaPython geliştirme** seçeneklerini genişletin ve **Anaconda3'ü** (32 bit veya 64 bit) seçin. Yüklemenin Internet hızınıza bağlı olarak biraz zaman alabileceğini, ancak gerekli paketleri yüklemenin en basit yolunun bu olduğunu unutmayın.

1. Visual Studio’yu başlatın.

1. **Cookiecutter'dan****Yeni** >  **Dosya'yı** > seçin. Bu komut Visual Studio'da şablonlara göz atabileceğiniz bir pencere açar.

    ![Cookiecutter şablonundan yeni proje](media/projects-from-cookiecutter1.png)

1. **Microsoft/python-sklearn-classifier-cookiecutter** şablonunu seçin ve **ardından İleri'yi**seçin. (Visual Studio gerekli Python paketlerini yüklediğinizde, belirli bir şablonu ilk kullandığınızda işlem birkaç dakika sürebilir.)

1. Bir sonraki adımda, **Oluşturul alanı'ndaki** yeni proje için bir konum ayarlayın ve **ardından Project Oluştur ve Aç'ı**seçin.

    ![Cookiecutter kullanarak ikinci adım, proje özelliklerini ayarlama](media/projects-from-cookiecutter2.png)

1. İşlem tamamlandığında, **şablonu kullanarak dosyaları başarıyla oluşturulan**iletiyi görürsünüz... . Proje Solution Explorer'da otomatik olarak açılır.

1. **Ctrl**+**F5** tuşuna basın veya programı çalıştırmak için Hata Ayıklama olmadan **Hata Ayıklama** > **Başlat'ı** seçin.

    ![Python-sklearn-classifier-cookiecutter şablonu projesinin çıktısı](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md)
- [Varolan bir Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki gün Python desteğini yükleyin](installing-python-support-in-visual-studio.md)
- [Konumları yükleme](installing-python-support-in-visual-studio.md#install-locations)
