---
title: Verileri karşıya yüklemek için depolamaya göz atma
description: Verileri karşıya yüklemek veya modelleri ve günlükleri indirmek için uzak makinede veya Azure dosya paylaşımında tüm depolama alanlarına nasıl göz atabilirsiniz?
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053376"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Verileri karşıya yüklemek veya modelleri ve günlükleri indirmek için depolamaya göz atma

Verileri karşıya yüklemek veya modelleri ve günlükleri indirmek için uzak makinede veya Azure dosya paylaşımında tüm depolama alanlarına göz atabilirsiniz. Veya belirli bir işin günlüklerine ve iş çıkışlarına erişmek için bunu iş tarayıcısında da kullanabilirsiniz.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Uzak makine veya dosya paylaşımında tüm verilere erişmek için

1. Sunucu Gezgini. 
2. Uzak makineyi genişletin veya Batch AI bağlamını genişletin.
3. Depolama;  Ardından **Gözat'a tıklayın.**

    ![Uzak Makineler Sunucu Gezgini genişletilmiş bir dosyanın ekran görüntüsü. Depolama klasör ağacında vurgulanmış ve bağlam menüsünde Gözat seçilmiştir.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Uzak makinede veya dosya paylaşımında işe özgü verilere erişmek için

1. İş [Geçmişini açma](job-details.md)
2. İş seçin.
3. Bu **önemli günlük dosyalarına** **hızlı erişim için Çalışma Klasörü'ne veya StdOut / Stderr'a** tıklayın.

    ![İş Tarayıcısı penceresinin ekran görüntüsü Sunucu Gezgini. İş train_mnist seçilidir ve İş Ayrıntıları altında Çalışma Klasörü bağlantısı seçilidir.](media/manage-storage/job-workingfolder.png)
