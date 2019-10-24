---
title: Verileri karşıya yüklemek için depolamaya gözatamıyorum
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 7d0f2522117f4c5a5b85e99e2779d10cffcb7f22
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777406"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Verileri karşıya yüklemek veya modelleri ve günlükleri indirmek için depolamaya gözatamıyorum

Verileri karşıya yüklemeyi veya modelleri ve günlükleri indirmeyi sağlamak için uzak makinedeki veya Azure dosya paylaşımındaki tüm depolamaya gözatabilmeniz gerekir. Ya da, belirli bir iş için günlüklere ve iş çıktılarına erişmek istiyorsanız, bu işlemi iş tarayıcısına de yapabilirsiniz.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Uzak makinedeki veya dosya paylaşımındaki tüm verilere erişmek için

1. **Sunucu Gezgini**açın.
2. Uzak makineyi veya Batch AI işlem bağlamını genişletin.
3. **Depolama alanı**' na sağ tıklayın; ardından, **Araştır**' a tıklayın.

    ![depolama](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Uzak makinedeki veya dosya paylaşımındaki işe özgü verilere erişmek için

1. [Iş geçmişini](job-details.md) açın
2. İşi seçin.
3. Bu önemli günlük dosyalarına hızlı erişim için **çalışma klasörü** ' ne veya **stdout/stderr** ' e tıklayın.

    ![depolama](media/manage-storage/job-workingfolder.png)
