---
title: 'Nasıl yapılır: ek Izleme seçeneklerini belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794732"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Nasıl yapılır: Ek İzleme Seçeneklerini Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İkili dosyaları [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Tümleşik geliştirme ortamından (IDE) veya komut satırı araçlarını kullanarak seçebilirsiniz. IDE içinden bir ikili değer verirseniz, [vsinstr](../profiling/vsinstr.md) aracına ek izleme seçenekleri belirterek, izleme sırasında toplanan veri hacminin denetimini yapabilirsiniz. Bu seçenekler oturumda veya hedef düzeyinde kullanılabilir. Örneğin, izleme işlemi sırasında belirli işlevleri dahil etmek veya hariç tutmak için, hedef düzeyinde ek izleme seçeneğini kullanın.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Eklenen her araştırma, özgün programın davranışını biraz değiştirir. Bu değişiklik çözümleme sırasında ek yüke neden olur. Bu ek yükün yaklaşık bir nedeni kaldırılmış olsa da, çok iş parçacıklı uygulamalar üzerinde hala hafif zamanlama etkileri vardır. [Vsinstr](../profiling/vsinstr.md) aracı seçenekleri, profil oluşturma sırasında veri toplamayı denetlemenize yardımcı olur.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Ek izleme seçeneğini belirtmek için  
  
1. **Performans Gezgini**' de, **performans oturumu** ' nu seçin ve ardından sağ tıklayıp **Özellikler**' i seçin.  
  
2. **Özellikler sayfalarında** **Gelişmiş** Özellikler ' e tıklayın.  
  
3. **Ek izleme seçenekleri** kutusunda seçenekler yazın.  
  
     Örneğin, profil oluşturma düzeyini belirtmek için/CONTROL: THREAD komutunu kullanın. Seçeneklerin tamamı listesi için bkz. [vsinstr](../profiling/vsinstr.md).  
  
4. **Tamam**’a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)
