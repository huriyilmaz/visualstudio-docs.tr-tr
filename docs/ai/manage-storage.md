---
title: Verileri karşıya yüklemek için depolamaya gözatamıyorum
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 188ebee353261ba49f6677a0f96db68b7e8d46d9
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371618"
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
