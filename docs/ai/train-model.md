---
title: Azure Batch AI modeli eğitme işi gönder
description: Model bulutu eğitme
keywords: AI, Visual Studio, eğitme modeli, bulut
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: dec70c9e9aeb9c916b511241a74b550354aff175
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915768"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Batch AI AI modellerini eğitme

Batch AI, veri bilimcilerinin ve AI araştırmacılarının, GPU desteğine sahip VM’ler dahil olmak üzere Azure sanal makine kümeleri üzerinde AI ve diğer makine öğrenimi modelleri ile eğitimler vermesine olanak tanıyan, yönetilen bir hizmettir. Siz işinizin gereksinimlerini, girdilerin nerede bulunacağını ve çıktıların nerede depolanacağını açıklarsınız, gerisini Batch AI yapar. [Azure Batch AI hakkında daha fazla bilgi edinin](/azure/batch-ai/overview)

Azure 'da eğitim modellerini dinamik olarak ölçeklendirebilmeniz için Visual Studio Tools for AI tümleşiktir.  [Visual Studio Tools for AI](installation.md)yükledikten sonra, Azure Machine Learning örnek galerisinde önceden hazırlanmış yemek tariflerini kullanarak yeni bir Python projesi oluşturmak kolaydır.

1. Visual Studio'yu başlatın. **AI araçları** menüsünü açıp **küme Seç** ' i seçerek **Sunucu Gezgini** açın.

    ![Küme Seçicisi](media/train-model/select-cluster.png)

2. **AI araçları**' nı genişletin. Sahip olduğunuz tüm Batch AI kaynakları otomatik olarak algılanır ve Sunucu Gezgini görünür.

    ![Örnek galerisi](media/train-model/batchai.png)

3. GitHub veya Azure DevOps 'a bağlanabildiğinizi veya bir depoyu klonlayabileceğiniz **Takım Gezgini** penceresini açmak için **Görünüm > Takım Gezgini..** . öğesini seçin.

    ![Azure DevOps, GitHub ve bir depoyu klonlama gösteren Takım Gezgini penceresi](media/train-model/team-explorer-devops.png)

4. **Yerel Git depoları**altındaki URL alanında `https://github.com/Microsoft/samples-for-ai`girin, kopyalanmış dosyalar için bir klasör girin ve **Kopyala**' yı seçin.

    > [!Tip]
    > Takım Gezgini içinde belirttiğiniz klasör klonlanan dosyaları almak için özel klasördür. `git clone` komutundan farklı olarak, Takım Gezgini bir kopyanın oluşturulması, otomatik olarak deponun adı ile bir alt klasör oluşturmaz.

5. Kopyalama tamamlandığında **dosya > çözüm > proje/çözüm aç** ' a tıklayın

    ![Örnek galerisi](media/train-model/open-solution.png)

6. Depoyu Klonladığınız dizinde **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** açın

    ![Örnek galerisi](media/train-model/tensorflowexamples.png)

7. MNIST projesini **Başlangıç projesi** olarak ayarla

    ![Örnek galerisi](media/train-model/mnist-startup.png)

8. <strong>**Mnist projesi** ' ne sağ tıklayın, **işi gönder**</strong>

    ![Örnek galerisi](media/train-model/submit-job.png)
9. **Azure Batch AI** kümenizi seçip **içeri aktar**' a tıklayın. Hangi Docker görüntüsünün kullanılacağı gibi bazı varsayılan değerleri hızlıca doldurmak için `AzureBatchAI_TF_MNIST.json` dosyasını seçin. Sonra **Gönder** ' e tıklayın.

    ![Örnek galerisi](media/train-model/submit-batch.png)
