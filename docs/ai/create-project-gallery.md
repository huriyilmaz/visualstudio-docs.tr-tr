---
title: Proje oluştur
description: Azure Machine Learning galerisinden örnek kullanarak proje oluşturma
keywords: AI, Visual Studio, Azure Machine Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6f84051e4450926136064b9af7f3c09e2e91a2f9
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188578"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio 'da Azure Machine Learning galerisinden bir AI projesi oluşturma

Azure Machine Learning Visual Studio Tools for AI tümleşiktir. Azure sanal makineleri, Spark kümeleri ve daha fazlası gibi uzak işlem hedeflerine makine öğrenimi işleri göndermek için bu işlemi kullanabilirsiniz. 

[Visual Studio Tools for AI](installation.md)yükledikten sonra, Azure Machine Learning örnek galerisinde önceden hazırlanmış yemek tariflerini kullanarak yeni bir Python projesi oluşturmak kolaydır.

> [!NOTE]
> Azure Machine Learning Workbench yüklü olmalıdır. Yüklemek için lütfen [Azure Machine Learning yükleme hızlı başlangıç](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation) bölümüne bakın

1. Visual Studio'yu başlatın. **AI araçları** menüsünü açıp **küme Seç** ' i seçerek **Sunucu Gezgini** açın.

    ![Küme Seçicisi](media/create-project-gallery/select-cluster.png)

2. Sunucu Gezgini **Azure Machine Learning** düğümüne sağ tıklayarak Azure Machine Learning aboneliğinizde oturum açın ve **oturum aç** ' ı seçin ve yönergeleri izleyin.

    ![LOGIN](media/create-project-gallery/azureml-login.png)

3. **Örnek galerisi > AI araçları**' nı Azure Machine Learning seçin.

    ![Örnek Galerisi](media/create-project-gallery/gallery.png)

4. Bu hızlı başlangıç için, "**TensorFlow kullanarak Mnist**" örneğini seçin ve ardından **Install**' a tıklayın. Aşağıdakileri sağlayın:

   - **Kaynak grubu**: meta verilerlerinizin depolanacağı Azure Kaynak grubu
   - **Hesap**: Azure Machine Learning deneme hesabı
   - **Çalışma alanı**: Azure Machine Learning çalışma alanı
   - **Proje türü**: Machine Learning çerçevesi. Bu durumda **TensorFlow** ' ı seçin.
   - **Çözüme Ekle**: geçerli Visual Studio çözümünüze mi yoksa yeni bir çözüm oluşturma ve açma için mi ekleneceğini belirler
   - **Proje yolu**: kodun kaydedileceği konum
   - **Proje adı**: tür **Tensorflowmnist**

   ![Python uygulama şablonu kullanılırken ortaya çıkan proje](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio, örnek içinde tanımlanan diğer dosyalarla birlikte proje dosyasını (diskte bir `.pyproj` dosyası) oluşturur. "MNIST" şablonuyla, proje birkaç dosya içerir.

    ![mnıst veritabanını kullanacaksınız](media/create-project-gallery/azml-mnist.png)

6. İşi Azure Machine Learning gönder.

    ![mnıst veritabanını kullanacaksınız](media/create-project-gallery/submit-azml.png)

7. Bir Docker kapsayıcısında veya yerel makinenizde çalıştırın

    ![mnıst veritabanını kullanacaksınız](media/create-project-gallery/azml-local.png)
