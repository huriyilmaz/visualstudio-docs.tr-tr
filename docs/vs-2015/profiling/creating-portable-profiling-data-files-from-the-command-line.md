---
title: Komut satırından taşınabilir profil oluşturma veri dosyaları oluşturuluyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791233"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Komut Satırından Taşınabilir Profil Oluşturma Veri Dosyaları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil oluşturma verilerinin paylaşılmasını daha kolay hale getirmek için [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracını kullanarak bir profil oluşturma çalıştırmasının sembollerini. vsp dosyasına ekleyebilirsiniz.  
  
 Daha küçük olan ve daha hızlı bir şekilde IDE 'ye daha hızlı bir şekilde çözümlenebilecek profil oluşturma verileri (. vsps) dosyası da oluşturabilirsiniz.  
  
> [!NOTE]
> Sembol (. pdb) dosyalarının **VSPerfReport**için kullanılabilir olduğundan emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: sembol dosyası konumlarını komut satırından belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> **VSReport**yolu hakkında daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Bir. vsps dosyasındaki profil oluşturma verileri filtrelenemez.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Bir profil oluşturma için sembolleri profil oluşturma verileri (. vsp) dosyasına eklemek için  
  
- Komut istemi penceresinde aşağıdaki komutu yazın:  
  
   \<Path><strong>VSPerfReport \<</strong> VSP dosyası> **/packsymbols**  
  
   Varsayılan olarak,. vsps dosyası. vsp dosyasının temel adı ile adlandırılır. **Output** seçeneğini kullanarak alternatif bir ad belirtebilirsiniz.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Özet profil oluşturma veri dosyası oluşturmak için  
  
- Komut istemi penceresinde aşağıdaki komutu yazın:  
  
   \<Path><strong>VSPerfReport \<</strong> VSP dosyası> **/summaryfile** [**/output:** \<File Name> ]  
  
   Varsayılan olarak,. vsps dosyası. vsp dosyasının temel adı ile adlandırılır. **Output** seçeneğini kullanarak alternatif bir ad belirtebilirsiniz.
