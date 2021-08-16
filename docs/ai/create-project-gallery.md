---
title: Proje oluşturma
description: Azure Machine Learning galerisinden örnek kullanarak proje oluşturma
keywords: ai, visual studio, azure machine learning
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 0fd77c91e64cfc9cd6c425a03d58ed663ce3e28c6ea82b8400af78fe2c87aa4d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121329194"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio'daki Azure Machine Learning Galerisi'nde bir AI Visual Studio

Azure Machine Learning, AI için Visual Studio Araçları ile tümleştirilmiştir. Azure sanal makineleri, Spark kümeleri ve daha fazlası gibi uzak işlem hedeflerine makine öğrenmesi işleri göndermek için bunu kullanabilirsiniz. 

AI için [Visual Studio Araçları](installation.md)yükledinizkten sonra, Azure Machine Learning Sample Gallery'de önceden yapılmış tarifler kullanarak yeni bir Python projesi oluşturabilirsiniz.

> [!NOTE]
> Azure Machine Learning Workbench'in yüklü olması gerekir. 

1. Visual Studio. AI **Sunucu Gezgini** menüsünü açıp **Küme Seç'i** seçerek ilgili **menüyü açın**

    ![Küme seçen](media/create-project-gallery/select-cluster.png)

2. Azure Machine Learning düğümünde Azure Machine Learning tıklayarak Sunucu Gezgini oturum Sunucu Gezgini  yönergeleri izleyin. 

    ![oturum aç](media/create-project-gallery/azureml-login.png)

3. AI **Araçları'> Azure Machine Learning Örnek Galerisi'ni seçin.**

    ![Örnek galeri](media/create-project-gallery/gallery.png)

4. Bu Hızlı Başlangıç için **TensorFlow kullanarak " MNIST**" örneğini seçin ve Yükle'ye **tıklayın.** Şunları sağlama:

   - **Kaynak Grubu:** Meta verilerin depolandığı Azure kaynak grubu
   - **Hesap:** Azure Machine Learning deneme Hesabı
   - **Çalışma** alanı: Azure Machine Learning çalışma alanı
   - **Project Türü:** Makine öğrenmesi çerçevesi. Bu durumda **TensorFlow'ı seçin**
   - **Çözüme Ekle:** Geçerli Çözüm çözümünüze ekleme Visual Studio yeni bir çözüm oluşturma ve açma olup olmadığını belirler
   - **Project Yolu:** Kodu kaydetmek için konum
   - **Project Adı:** **TensorFlowMNIST yazın**

   ![Python Uygulama şablonu kullanırken sonuçta elde edilen proje](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio proje dosyasını `.pyproj` (diskte bir dosya) örnekte tanımlanan diğer dosyalarla birlikte oluşturur. "MNIST" şablonuyla, proje birkaç dosya içerir.

    ![TensorFlowMNIST projesinin dosyalarını gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. tf_mnist.py için kod ana pencerede gösterilir.](media/create-project-gallery/azml-mnist.png)

6. İş için Azure Machine Learning.

    ![TensorFlowMNIST projesinin bağlam menüsünü "İş Gönder..." ile gösteren çalışma Visual Studio Çözüm Gezgini ekran görüntüsü Seçili.](media/create-project-gallery/submit-azml.png)

7. Docker kapsayıcısı içinde veya yerel makinede çalıştırma

    ![Küme kullan seçeneğinin "azureml:/local" ve Başlangıç betiği "tf_mnist.py" olarak ayarlanmış şekilde İş Gönder iletişim kutusunun ekran görüntüsü.](media/create-project-gallery/azml-local.png)
