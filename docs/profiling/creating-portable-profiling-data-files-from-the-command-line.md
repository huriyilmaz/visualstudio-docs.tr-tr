---
title: Profil oluşturma komut satırı - Taşınabilir veri dosyaları oluşturma
description: Profil oluşturma verileri paylaşımını kolaylaştırmak için profil oluşturma VSPerfReport.exe .vsp dosyasına eklemek üzere VSPerfReport.exe komut satırı aracını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7eadad8efebfa673a7e6c12e7dc67fb8b601f884
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637233"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Komut satırına taşınabilir profil oluşturma veri dosyaları oluşturma
Profil oluşturma verileri paylaşımını kolaylaştırmak için [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracını kullanarak profil oluşturma çalıştırması için simgeleri ebilirsiniz. *vsp* dosyası.

 Ayrıca, önceden analiz amaçlı profil oluşturma verileri () oluşturabilirsiniz.*daha küçük* olan ve IDE'ye daha hızlı yüklenemeyen vsps ) dosyası.

> [!NOTE]
> simgesinin () olduğundan emin olun.*pdb*) dosyaları **VSPerfReport tarafından kullanılabilir.** Daha fazla bilgi [için, bkz. How to: Specify symbol file locations from the command line](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> **VSReport** yolu hakkında bilgi için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)
>
> içinde profil oluşturma verileri. *vsps* dosyası filtre olamaz.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Profil oluşturma sembolleri eklemek için profil oluşturma verilerine () çalıştırın.*vsp*) dosyası

- Komut istemi penceresinde aşağıdaki komutu yazın:

   \<Path><strong>VSPerfReport \<</strong> VSP Dosyası> **/PackSymbols**

   Varsayılan olarak , . *vsps* dosyası, temel adıyla adlandırılmış. *vsp* dosyası. Çıkış seçeneğini kullanarak alternatif bir ad **belirtebilirsiniz.**

### <a name="to-create-a-summary-profiling-data-file"></a>Özet profil oluşturma veri dosyası oluşturmak için

- Komut istemi penceresinde aşağıdaki komutu yazın:

   \<Path><strong>VSPerfReport \<</strong> VSP Dosyası> **/SummaryFile** [**/Output:** \<File Name> ]

   Varsayılan olarak , . *vsps* dosyası, temel adıyla adlandırılmış. *vsp* dosyası. Çıkış seçeneğini kullanarak alternatif bir ad **belirtebilirsiniz.**
