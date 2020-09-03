---
title: Proje oluşturma
description: Azure Machine Learning galerisinden örnek kullanarak proje oluşturma
keywords: AI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 4bcc1932bad5b34d9695257feb163654f6b99514
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371631"
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

    ![mnıst veritabanını kullanacaksınız](media/create-project-gallery/azml-mnist.png)

6. İşi Azure Machine Learning gönder.

    ![mnıst veritabanını kullanacaksınız](media/create-project-gallery/submit-azml.png)

7. Bir Docker kapsayıcısında veya yerel makinenizde çalıştırın

    ![mnıst veritabanını kullanacaksınız](media/create-project-gallery/azml-local.png)
