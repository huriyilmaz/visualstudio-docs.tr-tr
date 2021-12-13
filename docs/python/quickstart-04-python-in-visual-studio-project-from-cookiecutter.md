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
ms.openlocfilehash: 7325e16558435ab1603e9e29ff1f0606956fbd2f
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134713687"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Hızlı Başlangıç: Cookiecutter şablonundan proje oluşturma

Visual Studio'da [Python](installing-python-support-in-visual-studio.md)desteğini yüklediniz, bir Cookiecutter şablonundan yeni bir proje oluşturmak kolaydır ve bu şablonda yayımlanmış olan birçok proje GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için bir grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ve sonraki sürümlere dahil edilir ve önceki sürümlerde ayrı Visual Studio.

1. Bu hızlı başlangıçta ilk olarak burada gösterilen Cookiecutter şablonu için gerekli Python paketlerini içeren Anaconda3 Python dağıtımını yükleyin. Uygulama yükleyicisini Visual Studio, Değiştir'i **seçin,** sağ tarafta **Python** geliştirme seçeneklerini genişletin ve **Anaconda3'ü** (32 bit veya 64 bit) seçin. Yüklemenin İnternet hızınıza bağlı olarak biraz zaman alsa da gerekli paketleri yüklemenin en kolay yolu olduğunu unutmayın.

1. Visual Studio.

1.   >    >  **Cookiecutter'dan Dosya Yeni'yi seçin.** Bu komut, şablonlarda Visual Studio bir pencere açar.

    ![Cookiecutter Project yeni uygulama](media/projects-from-cookiecutter1.png)

1. **Microsoft/python-sklearn-classifier-cookiecutter şablonunu** seçtikten sonra Sonraki'yi **seçin.** (Belirli bir şablonu ilk kez kullanıyorsanız işlem birkaç dakika sürebilir, Visual Studio Python paketlerini yükleyebilirsiniz.)

1. Sonraki adımda, Yeni proje için Oluştur alanında  bir konum ayarlayın ve ardından Oluştur ve Aç'ı **Project.**

    ![Cookiecutter kullanarak proje özelliklerini ayarlama ikinci adım](media/projects-from-cookiecutter2.png)

1. İşlem tamamlandığında Şablon kullanarak dosyalar başarıyla **oluşturuldu... iletisiyle karşılanır.** Proje otomatik olarak Çözüm Gezgini açılır.

1. Programı **çalıştırmak için Ctrl** + **F5** **tuşlarına basın veya** Hata Ayıklama Olmadan  >  **Başlat'ı** seçin.

    ![python-sklearn-classifier-cookiecutter şablon projesinin çıkışı](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Python ile Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md)
- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment) 
 [Visual Studio'da Python desteğini Windows](installing-python-support-in-visual-studio.md#how-to-install-python-support-in-visual-studio-on-windows)
- [Python araçları yükleme dizini](installing-python-support-in-visual-studio.md#install-locations)
