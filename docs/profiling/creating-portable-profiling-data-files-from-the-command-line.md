---
title: Komut Satırından Taşınabilir Profil Oluşturma Veri Dosyaları Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8caa1a4976da39b155edde36d538ca193bd1addd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779499"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Komut satırından taşınabilir profil oluşturma veri dosyaları oluşturma
Profil oluşturma verilerinin paylaşımını kolaylaştırmak için, [vsperfReport](../profiling/vsperfreport.md) komut satırı aracını kullanarak profil oluşturma işlemine giriş için sembolleri katıştırabilirsiniz. *vsp* dosyası.

 Ayrıca önceden analiz edilmiş bir profil oluşturma verileri de oluşturabilirsiniz (.* vsps*) dosyası daha küçüktür ve IDE'ye yüklenir.

> [!NOTE]
> Sembolün (.* pdb*) dosyaları **VSPerfReport**için kullanılabilir. Daha fazla bilgi için [bkz: Komut satırından sembol dosya konumlarını belirtin.](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)
>
> **VSReport**yolu hakkında bilgi için [bkz.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)
>
> Bir profil oluşturma verileri . *vsps* dosyası filtrelenemez.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Profil oluşturma işleminin sembollerini bir profil oluşturma verilerine gömmek için (.* vsp*) dosyası

- Komut istemi penceresinde aşağıdaki komutu yazın:

   \<Yol><strong>VSPerfReport \< </strong>VSP Dosya> **/PackSymbols**

   Varsayılan olarak, . *vsps* dosyasının temel adı ile adlandırılır. *vsp* dosyası. **Çıktı** seçeneğini kullanarak alternatif bir ad belirtebilirsiniz.

### <a name="to-create-a-summary-profiling-data-file"></a>Özet profil oluşturma veri dosyası oluşturmak için

- Komut istemi penceresinde aşağıdaki komutu yazın:

   \<Yol><strong>VSPerfReport \< </strong>VSP Dosya> **/SummaryFile** [**/Çıktı:**\<Dosya Adı>]

   Varsayılan olarak, . *vsps* dosyasının temel adı ile adlandırılır. *vsp* dosyası. **Çıktı** seçeneğini kullanarak alternatif bir ad belirtebilirsiniz.
