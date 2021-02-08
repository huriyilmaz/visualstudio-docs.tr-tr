---
title: Proje oluşturma
description: Azure Machine Learning galerisinden örnek kullanarak proje oluşturma
keywords: AI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: e6c5b8201b39f82e4c4645196ca543e2567b6e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841555"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio 'da Azure Machine Learning galerisinden bir AI projesi oluşturma

Azure Machine Learning Visual Studio Tools for AI tümleşiktir. Azure sanal makineleri, Spark kümeleri ve daha fazlası gibi uzak işlem hedeflerine makine öğrenimi işleri göndermek için bu işlemi kullanabilirsiniz. 

[Visual Studio Tools for AI](installation.md)yükledikten sonra, Azure Machine Learning örnek galerisinde önceden hazırlanmış yemek tariflerini kullanarak yeni bir Python projesi oluşturmak kolaydır.

> [!NOTE]
> Azure Machine Learning Workbench yüklü olmalıdır. 

1. Visual Studio 'Yu başlatın. **AI araçları** menüsünü açıp **küme Seç** ' i seçerek **Sunucu Gezgini** açın.

    ![Küme Seçicisi](media/create-project-gallery/select-cluster.png)

2. Sunucu Gezgini **Azure Machine Learning** düğümüne sağ tıklayarak Azure Machine Learning aboneliğinizde oturum açın ve **oturum aç** ' ı seçin ve yönergeleri izleyin.

    ![oturum aç](media/create-project-gallery/azureml-login.png)

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

5. Visual Studio, `.pyproj` örnek içinde tanımlanan diğer dosyalarla birlikte proje dosyasını (diskte bulunan bir dosya) oluşturur. "MNIST" şablonuyla, proje birkaç dosya içerir.

    ![TensorFlowMNIST projesi dosyalarını gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. Tf_mnist. Kopyala için kod ana pencerede gösterilir.](media/create-project-gallery/azml-mnist.png)

6. İşi Azure Machine Learning gönder.

    !["Işi gönder..." ile TensorFlowMNIST projesinin bağlam menüsünü gösteren Visual Studio Çözüm Gezgini ekran görüntüsü seçildiğinde.](media/create-project-gallery/submit-azml.png)

7. Bir Docker kapsayıcısında veya yerel makinenizde çalıştırın

    ![Use kümesi ile Iş Gönder iletişim kutusunun ekran görüntüsü "azureml:/yerel" olarak ayarlanmış ve başlangıç betiği "tf_mnist. Kopyala" olarak ayarlandı.](media/create-project-gallery/azml-local.png)
