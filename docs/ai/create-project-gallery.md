---
title: Proje oluşturma
description: azure makine öğrenme galerisinden örnek kullanarak proje oluşturma
keywords: ai, visual studio, azure makine öğrenimi
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: fb1158015f1a7065514511b8d62810c937382b7f
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638680"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio'daki Azure Machine Learning Gallery'den bir Yapay Bilgi projesi oluşturma

Azure Machine Learning, Yapay AI için Visual Studio Tools ile entegre edilmiştir. Azure sanal makineleri, Kıvılcım kümeleri ve daha fazlası gibi uzak bilgi işlem hedeflerine makine öğrenimi işleri göndermek için kullanabilirsiniz. 

Yapay bilgi [için Visual Studio Tools'u yükledikten](installation.md)sonra, Azure Machine Learning Örnek Galerisi'nde önceden yapılmış tarifleri kullanarak yeni bir Python projesi oluşturmak kolaydır.

> [!NOTE]
> Azure Machine Learning Workbench yüklü olmalıdır. Yüklemek için lütfen [Azure Machine Learning yüklemesine](/azure/machine-learning/preview/quickstart-installation) bakın

1. Visual Studio’yu başlatın. **AI Tools** menüsünü açarak ve Select **Cluster'ı** seçerek Sunucu **Gezgini'ni** açın

    ![Küme seçici](media/create-project-gallery/select-cluster.png)

2. Sunucu Gezgini'ndeki **Azure Machine Learning** düğümüne sağ tıklayarak Azure Machine Learning aboneliğinizde oturum açın ve ardından **Giriş'i** seçin ve yönergeleri izleyin.

    ![oturum aç](media/create-project-gallery/azureml-login.png)

3. **Azure Machine Learning Örnek Galerisi> Yapay AI Araçları'nı**seçin.

    ![Örnek galeri](media/create-project-gallery/gallery.png)

4. Bu Quickstart için**TensorFlow kullanarak " MNIST**" örneğini seçin ve **Yükle'yi**tıklatın. Aşağıdakileri sağlayın:

   - **Kaynak Grubu**: Meta verilerinizin depolanacağı azure kaynak grubu
   - **Hesap**: Azure Machine Learning deneme Hesabı
   - **Çalışma Alanı**: Azure Machine Learning çalışma alanı
   - **Proje Türü**: Makine öğrenimi çerçevesi. Bu durumda **TensorFlow'u** seçin
   - **Çözüme Ekle**: mevcut Visual Studio Çözümünüze mi yoksa yeni bir çözüm oluşturup açmanızı mı belirleyecek
   - **Proje Yolu**: Kodu kaydetmek için konum
   - **Proje Adı**: Tip **TensorFlowMNIST**

   ![Python Application şablonunu kullanırken ortaya çıkan proje](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio, örnekte tanımlanan `.pyproj` diğer dosyalarla birlikte proje dosyasını (diskteki bir dosya) oluşturur. "MNIST" şablonuyla proje birkaç dosya içerir.

    ![mnist](media/create-project-gallery/azml-mnist.png)

6. İşi Azure Machine Learning'e gönderin.

    ![mnist](media/create-project-gallery/submit-azml.png)

7. Docker konteynerinde veya yerel makinenizde çalıştırın

    ![mnist](media/create-project-gallery/azml-local.png)
