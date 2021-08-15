---
title: Bir modeli eğitme işi gönderme
description: Azure Batch AI kullanarak bir modeli eğitme işi gönderme
ms.custom: SEO-VS-2020
keywords: AI, Visual Studio, eğitme modeli, bulut
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 317a80db384468709676acf7c400152e6d49365a8b44cc6d03fafda60c9c6ab7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121313360"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Batch AI AI modellerini eğitme

Batch AI, veri bilimcilerinin ve yapay zeka araştırmacılarının, GPU desteğine sahip sanal makineler dahil, Azure sanal makine kümelerindeki yapay zeka ve diğer makine öğrenmesi modellerini eğitmesini sağlayan bir yönetilen hizmettir. Siz işinizin gereksinimlerini, girdilerin nerede bulunacağını ve çıktıların nerede depolanacağını açıklarsınız, gerisini Batch AI yapar. [Azure Batch AI hakkında daha fazla bilgi edinin](/azure/batch-ai/overview)

Azure 'da eğitim modellerini dinamik olarak ölçeklendirebilmeniz için aı için Visual Studio Araçları tümleşiktir.  [aı için Visual Studio Araçları](installation.md)yükledikten sonra, Azure Machine Learning örnek galerisinde önceden hazırlanmış tarifler kullanarak yeni bir Python projesi oluşturmak kolaydır.

1. Visual Studio başlatın. **AI araçları** menüsünü açıp **küme Seç** ' i seçerek **Sunucu Gezgini** açın.

    ![Küme Seçicisi](media/train-model/select-cluster.png)

2. **AI araçları**' nı genişletin. Sahip olduğunuz tüm Batch AI kaynakları otomatik olarak algılanır ve Sunucu Gezgini görünür.

    ![Sunucu Gezgini içindeki AI araçları için genişletilmiş klasör ağacının ekran görüntüsü, Azure Batch AI ve Azure Machine Learning için genişletilmiş alt klasörler gösteriliyor.](media/train-model/batchai.png)

3. GitHub veya Azure DevOps 'e bağlanabildiğinizi veya bir depoyu klonlayabileceğiniz **Takım Gezgini** penceresini açmak için **görünüm > Takım Gezgini..** . öğesini seçin.

    ![bir depoyu Azure DevOps, GitHub ve kopyalamayı gösteren takım gezgini penceresi](media/train-model/team-explorer-devops.png)

4. **Yerel Git depoları** altındaki URL alanında, `https://github.com/Microsoft/samples-for-ai` öğesini girin, kopyalanmış dosyalar için bir klasör girin ve **Kopyala**' yı seçin.

    > [!Tip]
    > Takım Gezgini içinde belirttiğiniz klasör klonlanan dosyaları almak için özel klasördür. Komutun aksine `git clone` , Takım Gezgini bir kopyanın oluşturulması, otomatik olarak deponun adı ile bir alt klasör oluşturmaz.

5. kopyalama tamamlandığında **dosya > çözüm > Project/çözüm aç** ' a tıklayın

    ![Sunucu Gezgini dosya menüsünün bir bölümünü aç komutu seçili ve bağlam menüsünde Project/solution seçiliyken gösteren ekran görüntüsü.](media/train-model/open-solution.png)

6. Depoyu Klonladığınız dizinde **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** açın

    ![-For-AI deposundaki tensorflowsamples klasörünün içeriğinde listelenen TensorflowExamples. sln çözüm dosyasını gösteren ekran görüntüsü.](media/train-model/tensorflowexamples.png)

7. MNIST projesini **başlangıç Project** olarak ayarla

    ![Çözüm Gezgini içindeki mnist projesinin bağlam menüsünde başlangıç Project olarak ayarla ' nın seçili olduğunu gösteren ekran görüntüsü.](media/train-model/mnist-startup.png)

8. <strong>**Mnist projesi** ' ne sağ tıklayın, **işi gönder**</strong>

    ![Çözüm Gezgini içindeki MNIST projesi için bağlam menüsünde seçilen gönder Işini gösteren ekran görüntüsü.](media/train-model/submit-job.png)
9. **Azure Batch AI** kümenizi seçip **içeri aktar**' a tıklayın. `AzureBatchAI_TF_MNIST.json`Hangi Docker görüntüsünün kullanılacağı gibi bazı varsayılan değerleri hızlıca doldurmak için dosyayı seçin. Sonra **Gönder** ' e tıklayın.

    ![Küme, başlangıç betiği, Iş adı, görüntü adı, StdOutErr yol öneki ve CLı parametreleri için doldurulan değerlerle Iş Gönder iletişim kutusunun ekran görüntüsü.](media/train-model/submit-batch.png)
