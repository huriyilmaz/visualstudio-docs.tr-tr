---
title: Bulutta TensorFlow modeli çalıştırma
description: Azure Derin Öğrenme vm'sinde tensorflow modeli çalıştırma
keywords: ai, visual studio, derin öğrenme sanal makinesi
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0a73a22397f05660cd0b5e2c90633f6528297848
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037583"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Bulutta TensorFlow modelini eğitme

Bu öğreticide, Azure [Deep Learning](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) sanal makinesi [](http://yann.lecun.com/exdb/mnist/) üzerinde MNIST veri kümesi kullanarak tensorFlow modelini eğitecek.

MNIST veritabanında 60.000 örnekli bir eğitim kümesi ve el yazısı basamaklardan 10.000 örnekli bir test kümesi vardır.

## <a name="prerequisites"></a>Önkoşullar
Başlamadan önce, aşağıdakilerin yüklü ve yapılandırılmış olduğundan emin olmak için:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Azure Deep Learning Virtual Machine'i ayarlama

> [!NOTE]
> Işletim **sistemi türünü** Linux olarak ayarlayın.

Ayrıntılı Sanal Makine Learning yönergeleri burada [bulunabilir.](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm)

### <a name="remove-comment-in-parens"></a>Ayrıştıranlarda açıklama kaldırma

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Örnek kodu indirme

TensorFlow GitHub, CNTK, Theano ve daha fazlası hakkında derin öğrenmeye başlamaya yönelik örnekler içeren bu depoyu indirin. [](https://github.com/Microsoft/samples-for-ai)

## <a name="open-project"></a>Projeyi açma

- Dosya **Visual Studio/Çözüm'> Aç'ı > Project'yi seçin.**

- İndirilen **örnek deposundan Tensorflow** Örnekleri klasörünü seçin ve **TensorflowExamples.sln dosyasını** açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Çözümü açma](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Azure Uzak VM ekleme

Bu Sunucu Gezgini, AI **Araçları** düğümünün altındaki Uzak Makineler düğümüne sağ tıklayın ve "Ekle..." öğesini seçin. Uzak Makine görünen adı, IP ana bilgisayarı, SSH bağlantı noktası, kullanıcı adı ve parola/anahtar dosyasını girin.

![Yeni bir uzak makine ekleme](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Azure VM'ye iş gönderme
Dosyada MNIST projesine sağ **tıklayın Çözüm Gezgini** **gönder'i seçin.**

![Uzak makineye iş gönderme](media/tensorflow-vm/job-submission.png)

Gönderim penceresinde:

- Kullanmak için **Küme listesinde,** işi göndermek için uzak makineyi ("rm:" ön eki ile) seçin.

- bir İş **adı girin.**

- **Gönder'e tıklayın.**

## <a name="check-status-of-job"></a>İş durumunu denetleme
İşlerin durumunu ve ayrıntılarını görmek için: aşağıdaki içinde işi göndererek sanal makineyi **Sunucu Gezgini.** İşler'e çift **tıklayın.**

![İş tarayıcısı](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Yakın gelecekte kullanmayı planlıyorsanız VM'yi durdurun. Bu öğreticiyi tamamladıysanız, kaynaklarınızı temizlemek için aşağıdaki komutu çalıştırın:

```azurecli-interactive
az group delete --name myResourceGroup
```
