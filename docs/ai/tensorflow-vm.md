---
title: Bulutta tensorFlow modeli çalıştırma
description: azure derin öğrenme vm bir tensorflow modeli çalıştırın
keywords: ai, visual studio, derin öğrenme sanal makine
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 9cb06220c99abb86c24808f6831cf98280133f2e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75915835"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Bulutta bir TensorFlow modelini eğitin

Bu eğitimde, Azure [Derin Öğrenme](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) sanal makinesindeki [MNIST veri kümesini](http://yann.lecun.com/exdb/mnist/) kullanarak bir TensorFlow modelini eğiteceğiz.

MNIST veritabanında 60.000 örnekten oluşan bir eğitim kümesi ve 10.000 el yazısı basamak örneği bir test kümesi vardır.

## <a name="prerequisites"></a>Önkoşullar
Başlamadan önce, aşağıdakileri yüklediğinizden ve yapılandırdığınızdan emin olun:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Kurulum Azure Derin Öğrenme Sanal Makine

> [!NOTE]
> **İşletim sistemi türünü** Linux'a ayarlayın.

Derin Öğrenme Sanal Makine kurmak için talimatlar [burada](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm)bulabilirsiniz.

### <a name="remove-comment-in-parens"></a>Parenlerde yorumu kaldırma

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Örnek kodu indirin

TensorFlow, CNTK, Theano ve daha fazla derin öğrenime başlamak için örnekler içeren bu [GitHub deposunu](https://github.com/Microsoft/samples-for-ai) indirin.

## <a name="open-project"></a>Projeyi açma

- Visual Studio'u başlatın ve **Dosya > Açık > Projesi/Çözümü'nü**seçin.

- İndirilen örnek deposundan **Tensorflow Örnekleri** klasörünü seçin ve **TensorflowExamples.sln** dosyasını açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Açık çözüm](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Azure Uzak VM Ekle

Server Explorer'da, Yapay Ah Araçlar düğümünün altındaki **Uzak Makineler** düğümüne sağ tıklayın ve "Ekle..." seçeneğini belirleyin. Uzak Makine ekran adını, IP ana bilgisayarını, SSH bağlantı noktasını, kullanıcı adını ve parola/anahtar dosyasını girin.

![Yeni bir uzak makine ekleme](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>İşi Azure VM'ye gönderme
**Solution Explorer'daki** MNIST projesine sağ tıklayın ve **İş Gönder'i**seçin.

![Uzak bir makineye iş gönderme](media/tensorflow-vm/job-submission.png)

Gönderme penceresinde:

- **Kullanılacak Küme**listesinde, işi göndermek için uzak makineyi ("rm:" öneki yle) seçin.

- Bir **İş adı**girin.

- **Gönder'i**tıklatın.

## <a name="check-status-of-job"></a>İşin durumunu denetleme
İşlerin durumunu ve ayrıntılarını görmek için: İşi Sunucu **Gezgini'nde**gönderdiğiniz sanal makineyi genişletin. **İşler'e**çift tıklayın.

![İş tarayıcısı](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Yakın gelecekte kullanmayı planlıyorsanız VM'yi durdurun. Bu öğreticiyi bitirdiyseniz, kaynaklarınızı temizlemek için aşağıdaki komutu çalıştırın:

```azurecli-interactive
az group delete --name myResourceGroup
```
