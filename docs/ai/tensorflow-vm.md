---
title: Bulutta bir TensorFlow modeli çalıştırma
description: Azure derin öğrenme VM 'de bir TensorFlow modeli çalıştırma
keywords: AI, Visual Studio, derin öğrenme sanal makinesi
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633305"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Bulutta TensorFlow modelini eğitme

bu öğreticide, Azure [derin Learning](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) sanal makinesinde bulunan [mnist veri kümesini](http://yann.lecun.com/exdb/mnist/) kullanarak bir tensorflow modeli eğeceğiz.

MNIST veritabanı, 60.000 örnek bir eğitim kümesine ve el yazısı rakamlarının bir dizi 10.000 örneklerine sahiptir.

## <a name="prerequisites"></a>Önkoşullar
Başlamadan önce, aşağıdakilerin yüklü ve yapılandırılmış olduğundan emin olun:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Azure derin Learning sanal makinesini kurma

> [!NOTE]
> **Işletim sistemi türünü** Linux olarak ayarlayın.

derin Learning sanal makine ayarlamaya yönelik yönergeler [burada](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm)bulunabilir.

### <a name="remove-comment-in-parens"></a>Açıklamaları parleştirir kaldır

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Örnek kodu indir

tensorflow, CNTK, theano ve daha birçok konuda derin öğrenime başlarken örnekleri içeren bu [GitHub depoyu](https://github.com/Microsoft/samples-for-ai) indirin.

## <a name="open-project"></a>Projeyi açma

- Visual Studio başlatın ve **dosya > seçin > Project/çözüm açın**.

- İndirilen örnek deposundan **TensorFlow örnekleri** klasörünü seçin ve **tensorflowexamples. sln** dosyasını açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Çözümü aç](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Azure uzak VM ekleme

Sunucu Gezgini, AI araçları düğümünün altındaki **uzak makineler** düğümüne sağ tıklayın ve "Ekle..." öğesini seçin. Uzak makine görünen adını, IP konağını, SSH bağlantı noktasını, Kullanıcı adını ve parolayı/anahtar dosyasını girin.

![Yeni bir uzak makine ekleyin](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Azure VM 'ye iş gönderme
**Çözüm Gezgini** ' de mnist projesine sağ tıklayın ve **işi gönder**' i seçin.

![Uzak makineye iş gönderme](media/tensorflow-vm/job-submission.png)

Gönderim penceresinde:

- **Kullanılacak küme** listesinde, işi göndermek için uzak makineyi ("RM:" ön eki ile) seçin.

- Bir **iş adı** girin.

- **Gönder**' e tıklayın.

## <a name="check-status-of-job"></a>İşin durumunu denetleme
İşlerin durumunu ve ayrıntılarını görmek için: işi **Sunucu Gezgini** gönderdiğiniz sanal makineyi genişletin. **İşler**' e çift tıklayın.

![İş tarayıcısı](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Yakın gelecekte kullanmayı planlıyorsanız VM 'yi durdurun. Bu öğreticiyle işiniz bittiğinde, kaynaklarınızı temizlemek için aşağıdaki komutu çalıştırın:

```azurecli-interactive
az group delete --name myResourceGroup
```
