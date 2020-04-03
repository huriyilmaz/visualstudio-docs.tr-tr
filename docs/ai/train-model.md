---
title: Azure Toplu İşlem AI'de model eğitmek için iş gönderme
description: tren modeli bulut
keywords: ai, visual studio, tren modeli, bulut
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 083b2cb191d627ced936ead6a90b363970a9e7e0
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638769"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Toplu AI'de AI modellerini eğitin

Batch AI, veri bilimcilerinin ve yapay zeka araştırmacılarının, GPU desteğine sahip sanal makineler dahil, Azure sanal makine kümelerindeki yapay zeka ve diğer makine öğrenmesi modellerini eğitmesini sağlayan bir yönetilen hizmettir. Siz işinizin gereksinimlerini, girdilerin nerede bulunacağını ve çıktıların nerede depolanacağını açıklarsınız, gerisini Batch AI yapar. [Azure Toplu İş AI hakkında daha fazla bilgi edinin](/azure/batch-ai/overview)

Azure'daki eğitim modellerini dinamik olarak ölçeklendirebilmeniz için AI için Visual Studio Tools ile entegre edilmiştir.  Yapay bilgi [için Visual Studio Tools'u yükledikten](installation.md)sonra, Azure Machine Learning Örnek Galerisi'nde önceden yapılmış tarifleri kullanarak yeni bir Python projesi oluşturmak kolaydır.

1. Visual Studio’yu başlatın. **AI Tools** menüsünü açarak ve Select **Cluster'ı** seçerek Sunucu **Gezgini'ni** açın

    ![Küme seçici](media/train-model/select-cluster.png)

2. **AI araçlarını**genişletin. Sahip olduğunuz Toplu AI kaynakları otomatik olarak algılanır ve Sunucu Gezgini'nde görünür.

    ![Örnek galeri](media/train-model/batchai.png)

3. GitHub veya Azure DevOps'> bağlanabileceğiniz **ekip gezgini** penceresini açmak veya bir depo yumülemek için Team **Explorer'ı görüntüle'yi** seçin.

    ![Azure DevOps, GitHub ve bir depoyu klonlama gösteren takım gezgini penceresi](media/train-model/team-explorer-devops.png)

4. **Yerel Git Depoları**altında URL alanında `https://github.com/Microsoft/samples-for-ai`, girin , klonlanmış dosyalar için bir klasör girin ve **Klon**seçin.

    > [!Tip]
    > Team Explorer'da belirttiğiniz klasör, klonlanan dosyaları almak için belirli klasördür. Komutun `git clone` aksine, Team Explorer'da bir klon oluşturmak otomatik olarak deponun adını içeren bir alt klasör oluşturmaz.

5. Klonlama **tamamlandığında, Dosya > Çözüm > Projesi / Solution'ı** tıklatın

    ![Örnek galeri](media/train-model/open-solution.png)

6. Depoyu klonladığınız dizinde **örnekleri aç-for-ai\TensorFlowExamples\TensorFlowExamples.sln**

    ![Örnek galeri](media/train-model/tensorflowexamples.png)

7. MNIST projesini **Başlangıç Projesi** olarak ayarlama

    ![Örnek galeri](media/train-model/mnist-startup.png)

8. <strong>Sağ tıklayın **MNIST projesi,** **İş Gönder**</strong>

    ![Örnek galeri](media/train-model/submit-job.png)
9. Azure **Toplu Toplu AI** kümenizi seçin ve sonra **İçe Aktar'ı**tıklatın. Hangi `AzureBatchAI_TF_MNIST.json` Docker Image'ın kullanılacağı gibi bazı varsayılan değerleri hızla doldurmak için dosyayı seçin. Ardından **Gönder'i** tıklatın

    ![Örnek galeri](media/train-model/submit-batch.png)
