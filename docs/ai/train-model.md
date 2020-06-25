---
title: Azure Batch AI modeli eğitme işi gönder
description: Model bulutu eğitme
keywords: AI, Visual Studio, eğitme modeli, bulut
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 4d705cbff1ce4e25892dfc5df896418e6d58b632
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371657"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Batch AI AI modellerini eğitme

Batch AI, veri bilimcilerinin ve yapay zeka araştırmacılarının, GPU desteğine sahip sanal makineler dahil, Azure sanal makine kümelerindeki yapay zeka ve diğer makine öğrenmesi modellerini eğitmesini sağlayan bir yönetilen hizmettir. Siz işinizin gereksinimlerini, girdilerin nerede bulunacağını ve çıktıların nerede depolanacağını açıklarsınız, gerisini Batch AI yapar. [Azure Batch AI hakkında daha fazla bilgi edinin](/azure/batch-ai/overview)

Azure 'da eğitim modellerini dinamik olarak ölçeklendirebilmeniz için Visual Studio Tools for AI tümleşiktir.  [Visual Studio Tools for AI](installation.md)yükledikten sonra, Azure Machine Learning örnek galerisinde önceden hazırlanmış yemek tariflerini kullanarak yeni bir Python projesi oluşturmak kolaydır.

1. Visual Studio’yu başlatın. **AI araçları** menüsünü açıp **küme Seç** ' i seçerek **Sunucu Gezgini** açın.

    ![Küme Seçicisi](media/train-model/select-cluster.png)

2. **AI araçları**' nı genişletin. Sahip olduğunuz tüm Batch AI kaynakları otomatik olarak algılanır ve Sunucu Gezgini görünür.

    ![Örnek Galerisi](media/train-model/batchai.png)

3. GitHub veya Azure DevOps 'a bağlanabildiğinizi veya bir depoyu klonlayabileceğiniz **Takım Gezgini** penceresini açmak için **Görünüm > Takım Gezgini..** . öğesini seçin.

    ![Azure DevOps, GitHub ve bir depoyu klonlama gösteren Takım Gezgini penceresi](media/train-model/team-explorer-devops.png)

4. **Yerel Git depoları**altındaki URL alanında, `https://github.com/Microsoft/samples-for-ai` öğesini girin, kopyalanmış dosyalar için bir klasör girin ve **Kopyala**' yı seçin.

    > [!Tip]
    > Takım Gezgini içinde belirttiğiniz klasör klonlanan dosyaları almak için özel klasördür. Komutun aksine `git clone` , Takım Gezgini bir kopyanın oluşturulması, otomatik olarak deponun adı ile bir alt klasör oluşturmaz.

5. Kopyalama tamamlandığında **dosya > çözüm > proje/çözüm aç** ' a tıklayın

    ![Örnek Galerisi](media/train-model/open-solution.png)

6. Depoyu Klonladığınız dizinde **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** açın

    ![Örnek Galerisi](media/train-model/tensorflowexamples.png)

7. MNIST projesini **Başlangıç projesi** olarak ayarla

    ![Örnek Galerisi](media/train-model/mnist-startup.png)

8. <strong>**Mnist projesi** ' ne sağ tıklayın, **işi gönder**</strong>

    ![Örnek Galerisi](media/train-model/submit-job.png)
9. **Azure Batch AI** kümenizi seçip **içeri aktar**' a tıklayın. `AzureBatchAI_TF_MNIST.json`Hangi Docker görüntüsünün kullanılacağı gibi bazı varsayılan değerleri hızlıca doldurmak için dosyayı seçin. Sonra **Gönder** ' e tıklayın.

    ![Örnek Galerisi](media/train-model/submit-batch.png)
