---
title: Hızlı Başlangıç - Cookiecutter kullanarak Python projeleri oluşturma
description: Bu hızlı başlangıçta, Bir Cookiecutter Visual Studio Python için yeni bir proje oluşturuluyor.
ms.date: 02/25/2019
ms.topic: quickstart
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: c124610bab413b59ec2dc00798f8bc63b7221eb5
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968351"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Hızlı Başlangıç: Cookiecutter şablonundan proje oluşturma

Visual Studio'da [Python](installing-python-support-in-visual-studio.md)desteğini yüklediniz mi, bir Cookiecutter şablonundan yeni bir proje oluşturmak kolaydır ve bu şablonda yayımlanmış olan birçok proje GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için bir grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve sonraki sürümlere dahil edilir ve önceki sürümlerde ayrı Visual Studio.

1. Bu hızlı başlangıçta ilk olarak burada gösterilen Cookiecutter şablonu için gerekli Python paketlerini içeren Anaconda3 Python dağıtımını yükleyin. Uygulama yükleyicisini Visual Studio, Değiştir'i **seçin,** sağ tarafta **Python** geliştirme seçeneklerini genişletin ve **Anaconda3'ü** (32 bit veya 64 bit) seçin. Yüklemenin İnternet hızınıza bağlı olarak biraz zaman alsa da gerekli paketleri yüklemenin en kolay yolu olduğunu unutmayın.

1. Visual Studio.

1.   >    >  **Cookiecutter'dan Dosya Yeni'yi seçin.** Bu komut, şablonlarda Visual Studio bir pencere açar.

    ![Cookiecutter Project yeni bir uygulama](media/projects-from-cookiecutter1.png)

1. **Microsoft/python-sklearn-classifier-cookiecutter şablonunu** seçtikten sonra Sonraki'yi **seçin.** (Belirli bir şablonu ilk kez kullanırsanız işlem birkaç dakika sürebilir çünkü Visual Studio Python paketleri yüklenir.)

1. Sonraki adımda, Yeni proje için Oluştur alanında  bir konum ayarlayın ve ardından Oluştur ve Aç'ı **Project.**

    ![Cookiecutter kullanarak ikinci adım, proje özelliklerini ayarlama](media/projects-from-cookiecutter2.png)

1. İşlem tamamlandığında Şablon kullanarak dosyalar başarıyla **oluşturuldu... iletisiyle karşılanır.** Proje otomatik olarak Çözüm Gezgini açılır.

1. Programı **çalıştırmak için Ctrl** + **F5** **tuşlarına basın veya** Hata Ayıklama Olmadan  >  **Başlat'ı** seçin.

    ![python-sklearn-classifier-cookiecutter şablon projesinin çıkışı](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Python ile Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md)
- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteğini yükleme](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
