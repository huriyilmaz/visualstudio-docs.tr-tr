---
title: Verileri karşıya yüklemek için depolamaya gözatamıyorum
description: Verileri karşıya yüklemeyi veya modelleri ve günlükleri indirmeyi sağlamak için uzak makinedeki veya Azure dosya paylaşımındaki tüm depolamaya nasıl gözatacağınızı öğrenin.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 1b0e7098519374a41042f02f8ac8cba4b9071b15
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633358"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Verileri karşıya yüklemek veya modelleri ve günlükleri indirmek için depolamaya gözatamıyorum

Verileri karşıya yüklemeyi veya modelleri ve günlükleri indirmeyi sağlamak için uzak makinedeki veya Azure dosya paylaşımındaki tüm depolamaya gözatabilmeniz gerekir. Ya da, belirli bir iş için günlüklere ve iş çıktılarına erişmek istiyorsanız, bu işlemi iş tarayıcısına de yapabilirsiniz.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Uzak makinedeki veya dosya paylaşımındaki tüm verilere erişmek için

1. **Sunucu Gezgini** açın.
2. Uzak makineyi veya Batch AI işlem bağlamını genişletin.
3. **Depolama** öğesine sağ tıklayın; ardından, **Araştır**' a tıklayın.

    ![Uzak makineler klasörü genişletilmiş Sunucu Gezgini ekran görüntüsü. Depolama, klasör ağacında vurgulanır ve bağlam menüsünde tarama seçilidir.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Uzak makinedeki veya dosya paylaşımındaki işe özgü verilere erişmek için

1. [Iş geçmişini](job-details.md) açın
2. İşi seçin.
3. Bu önemli günlük dosyalarına hızlı erişim için **çalışma klasörü** ' ne veya **stdout/stderr** ' e tıklayın.

    ![Sunucu Gezgini 'de Iş tarayıcısı penceresinin ekran görüntüsü. Train_mnist işi seçilidir ve çalışma klasörü bağlantısı Iş ayrıntıları altında seçilidir.](media/manage-storage/job-workingfolder.png)
