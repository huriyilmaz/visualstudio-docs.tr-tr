---
title: Proje oluşturma
description: Azure Machine Learning galerisinden örnek kullanarak proje oluşturma
keywords: AI, Visual Studio, Azure Machine Learning
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067817"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio Azure Machine Learning galerisinden bir aı projesi oluşturma

Azure Machine Learning aı için Visual Studio Araçları tümleşiktir. Azure sanal makineleri, Spark kümeleri ve daha fazlası gibi uzak işlem hedeflerine makine öğrenimi işleri göndermek için bu işlemi kullanabilirsiniz. 

[aı için Visual Studio Araçları](installation.md)yükledikten sonra, Azure Machine Learning örnek galerisinde önceden hazırlanmış tarifler kullanarak yeni bir Python projesi oluşturmak kolaydır.

> [!NOTE]
> Azure Machine Learning Çalışma ekranı yüklü olmalıdır. 

1. Visual Studio başlatın. **AI araçları** menüsünü açıp **küme Seç** ' i seçerek **Sunucu Gezgini** açın.

    ![Küme Seçicisi](media/create-project-gallery/select-cluster.png)

2. Sunucu Gezgini **Azure Machine Learning** düğümüne sağ tıklayarak Azure Machine Learning aboneliğinizde oturum açın ve **oturum aç** ' ı seçin ve yönergeleri izleyin.

    ![oturum aç](media/create-project-gallery/azureml-login.png)

3. **örnek galerisi > aı araçları**' nı Azure Machine Learning seçin.

    ![Örnek Galerisi](media/create-project-gallery/gallery.png)

4. Bu hızlı başlangıç için, "**TensorFlow kullanarak Mnist**" örneğini seçin ve ardından **Install**' a tıklayın. Aşağıdakileri sağlayın:

   - **Kaynak grubu**: meta verilerlerinizin depolanacağı Azure Kaynak grubu
   - **hesap**: Azure Machine Learning deneme hesabı
   - **çalışma alanı**: Azure Machine Learning çalışma alanı
   - **Project türü**: machine learning çerçevesi. Bu durumda **TensorFlow** ' ı seçin.
   - **çözüme ekle**: geçerli Visual Studio çözümünüze mi yoksa yeni bir çözüm oluşturup mi ekleneceğini belirler
   - **Project yolu**: kodun kaydedileceği konum
   - **Project adı**: **tensorflowmnist** yazın

   ![Python uygulama şablonu kullanılırken ortaya çıkan proje](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio, `.pyproj` örnek içinde tanımlanan diğer dosyalarla birlikte proje dosyasını (diskteki bir dosya) oluşturur. "MNIST" şablonuyla, proje birkaç dosya içerir.

    ![tensorflowmnist projesi dosyalarını gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. Tf_mnist. Kopyala için kod ana pencerede gösterilir.](media/create-project-gallery/azml-mnist.png)

6. İşi Azure Machine Learning gönder.

    !["işi gönder..." ile tensorflowmnist projesi için bağlam menüsünü gösteren Visual Studio Çözüm Gezgini ekran görüntüsü seçildiğinde.](media/create-project-gallery/submit-azml.png)

7. Bir Docker kapsayıcısında veya yerel makinenizde çalıştırın

    ![Use kümesi ile Iş Gönder iletişim kutusunun ekran görüntüsü "azureml:/yerel" olarak ayarlanmış ve başlangıç betiği "tf_mnist. Kopyala" olarak ayarlandı.](media/create-project-gallery/azml-local.png)
