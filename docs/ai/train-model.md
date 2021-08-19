---
title: Model eğitmek için iş gönderme
description: Azure Batch AI kullanarak model eğitmek için iş Azure Batch AI
ms.custom: SEO-VS-2020
keywords: ai, visual studio, train model, cloud
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: e1efd5101ae606588b40a09a0c6ed5e24c171eb8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037557"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Batch AI'de AI modellerini Azure Batch AI

Batch AI, veri bilimcilerinin ve yapay zeka araştırmacılarının, GPU desteğine sahip sanal makineler dahil, Azure sanal makine kümelerindeki yapay zeka ve diğer makine öğrenmesi modellerini eğitmesini sağlayan bir yönetilen hizmettir. Siz işinizin gereksinimlerini, girdilerin nerede bulunacağını ve çıktıların nerede depolanacağını açıklarsınız, gerisini Batch AI yapar. [Azure Batch AI hakkında daha fazla bilgi Azure Batch AI](/azure/batch-ai/overview)

Azure'da eğitim modellerinin Visual Studio Araçları ölçeğini dinamik olarak ölçeklendiresiniz.  AI için [Visual Studio Araçları'yi](installation.md)yükledinizkten sonra, Azure Machine Learning Sample Gallery'de önceden yapılmış tarifler kullanarak yeni bir Python projesi oluşturabilirsiniz.

1. Visual Studio. AI **Sunucu Gezgini** menüsünü açıp **Küme Seç'i** seçerek ilgili **menüyü açın**

    ![Küme seçen](media/train-model/select-cluster.png)

2. AI **Araçları'nın kapsamını genişletin.** Sahip Batch AI tüm kaynaklar otomatik olarak algılanır ve kaynak Sunucu Gezgini.

    ![Sunucu Gezgini'da AI Araçları için genişletilmiş klasör ağacının ekran görüntüsü, Azure Batch AI ve Azure Machine Learning.](media/train-model/batchai.png)

3. > Takım Gezgini' **> Takım Gezgini...** **öğesini** seçerek Takım Gezgini veya GitHub Azure DevOps depoya bağlanabilirsiniz.

    ![Depoyu kopyalama, Azure DevOps GitHub ve kopyalamayı gösteren takım gezgini penceresi](media/train-model/team-explorer-devops.png)

4. Yerel Git Depoları altındaki URL **alanına** girin, kopyalanan dosyalar için bir klasör `https://github.com/Microsoft/samples-for-ai` girin ve Kopyala'ya **tıklayın.**

    > [!Tip]
    > Dosyalarda belirttiğiniz Takım Gezgini, kopyalanan dosyaları almak için belirli bir klasördür. Komutun aksine, Takım Gezgini otomatik olarak depo adıyla bir alt `git clone` klasör oluşturmaz.

5. Kopyalama tamamlandığında, Dosya Ve Çözüm > **/ Çözüm'e > Project'ye tıklayın**

    ![Sunucu Gezgini Aç komutunun seçili olduğu ve bağlam menüsünde Project/Çözüm seçeneğinin seçili olduğu dosya menüsünün bir bölümünü gösteren ekran görüntüsü.](media/train-model/open-solution.png)

6. Depoyu kopyalamış dizinde **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln'yi** açın

    ![Samples-for-ai deposundaki TensorflowExamples klasörünün içeriğinde listelenen TensorflowExamples.sln çözüm dosyasını gösteren ekran görüntüsü.](media/train-model/tensorflowexamples.png)

7. MNIST projesini Başlangıç Kümesi **olarak Project**

    ![MNIST projesinin Project menüsünde Başlangıç Olarak Ayarla seçeneğinin seçili olduğunu gösteren ekran Çözüm Gezgini.](media/train-model/mnist-startup.png)

8. <strong>**MNIST projesi, İş Gönder'e** **sağ tıklayın**</strong>

    ![Çözüm Gezgini'da MNIST projesinin bağlam menüsünde seçilen işi gönder seçeneğini gösteren Çözüm Gezgini.](media/train-model/submit-job.png)
9. Kümenizi **seçin Azure Batch AI** İçeri Aktar'a **tıklayın.** Docker `AzureBatchAI_TF_MNIST.json` Görüntüsü gibi bazı varsayılan değerleri hızla doldurmak için dosyasını seçin. Ardından **Gönder'e tıklayın**

    ![Kümeyi kullan, Başlangıç betiği, İş adı, Görüntü adı, StdOutErr yol ön eki ve CLI parametreleri için doldurulan değerlerin yer alan İş Gönder iletişim kutusunun ekran görüntüsü.](media/train-model/submit-batch.png)
