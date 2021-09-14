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
ms.openlocfilehash: 060c45fbea194167344a3efeb2a0cab2c7e02a49
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633385"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Azure Machine Learning Gallery'den bir AI projesi Visual Studio

Azure Machine Learning, AI için Visual Studio Araçları ile tümleştirilmiştir. Azure sanal makineleri, Spark kümeleri ve daha fazlası gibi uzak işlem hedeflerine makine öğrenmesi işleri göndermek için bunu kullanabilirsiniz. 

AI için [Visual Studio Araçları'yi](installation.md)yükledinizkten sonra, Azure Machine Learning Sample Gallery'de önceden yapılmış tarifler kullanarak yeni bir Python projesi oluşturabilirsiniz.

> [!NOTE]
> Azure Machine Learning Workbench yüklü olması gerekir. 

1. Visual Studio. AI **Sunucu Gezgini** menüsünü açıp **Küme Seç'i** seçerek ilgili **menüyü açın**

    ![Küme seçen](media/create-project-gallery/select-cluster.png)

2. Azure Machine Learning'Azure Machine Learning düğümüne sağ tıklayarak Sunucu Gezgini oturum  aç'ı **seçin** ve yönergeleri izleyin.

    ![oturum aç](media/create-project-gallery/azureml-login.png)

3. AI **Araçları'> Azure Machine Learning Örnek Galerisi'ni seçin.**

    ![Örnek galeri](media/create-project-gallery/gallery.png)

4. Bu Hızlı Başlangıç için **TensorFlow kullanarak " MNIST**" örneğini seçin ve Yükle'ye **tıklayın.** Şunları sağlama:

   - **Kaynak Grubu:** Meta verilerin depolandığı Azure kaynak grubu
   - **Hesap:** Azure Machine Learning deneme Hesabı
   - **Çalışma** alanı: Azure Machine Learning çalışma alanı
   - **Project Türü:** Makine öğrenmesi çerçevesi. Bu durumda **TensorFlow'ı seçin**
   - **Çözüme Ekle:** Geçerli Çözüm çözümünüze mi ek Visual Studio yoksa yeni bir çözüm oluşturma ve açma durumu belirler
   - **Project Yolu:** Kodu kaydetmek için konum
   - **Project Adı:** **TensorFlowMNIST yazın**

   ![Python Uygulama şablonu kullanırken sonuçta elde edilen proje](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio proje dosyasını `.pyproj` (diskte bir dosya) örnekte tanımlanan diğer dosyalarla birlikte oluşturur. "MNIST" şablonuyla, proje birkaç dosya içerir.

    ![TensorFlowMNIST projesinin dosyalarını gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. tf_mnist.py için kod ana pencerede gösterilir.](media/create-project-gallery/azml-mnist.png)

6. İş için Azure Machine Learning.

    ![TensorFlowMNIST projesinin bağlam menüsünü "İş Gönder..." ile gösteren Visual Studio Çözüm Gezgini ekran görüntüsü Seçili.](media/create-project-gallery/submit-azml.png)

7. Docker kapsayıcısı içinde veya yerel makinede çalıştırma

    ![Küme kullan seçeneğinin "azureml:/local" ve Başlangıç betiği "tf_mnist.py" olarak ayarlanmış şekilde İş Gönder iletişim kutusunun ekran görüntüsü.](media/create-project-gallery/azml-local.png)
