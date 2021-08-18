---
title: Ek Izleme seçeneklerini belirtin | Microsoft Docs
description: Visual Studio ıde 'yi kullanarak veya komut satırı araçlarını kullanarak ikili dosyaları nasıl kullanabileceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c62f001f2714a90b250f34e43cd3a582d1f5f099
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150137"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Nasıl yapılır: Ek izleme seçeneklerini belirtme

ikili dosyaları Visual Studio ıde 'yi kullanarak veya komut satırı araçlarını kullanarak bırakabilirsiniz. IDE içinden bir ikili değer verirseniz, [vsinstr](../profiling/vsinstr.md) aracına ek izleme seçenekleri belirterek, izleme sırasında toplanan veri hacminin denetimini yapabilirsiniz. Bu seçenekler oturumda veya hedef düzeyinde kullanılabilir. Örneğin, izleme işlemi sırasında belirli işlevleri dahil etmek veya hariç tutmak için, hedef düzeyinde ek izleme seçeneğini kullanın.

> [!IMPORTANT]
> Eklenen her araştırma, özgün programın davranışını biraz değiştirir. Bu değişiklik çözümleme sırasında ek yüke neden olur. Bu ek yükün yaklaşık bir nedeni kaldırılmış olsa da, çok iş parçacıklı uygulamalar üzerinde hala hafif zamanlama etkileri vardır. [Vsinstr](../profiling/vsinstr.md) aracı seçenekleri, profil oluşturma sırasında veri toplamayı denetlemenize yardımcı olur.

## <a name="to-specify-additional-instrumentation-option"></a>Ek izleme seçeneğini belirtmek için

1. **Performans Gezgini**' de, **performans oturumu** ' nu seçin ve ardından sağ tıklayıp **Özellikler**' i seçin.

2. **Özellikler sayfalarında** **Gelişmiş** Özellikler ' e tıklayın.

3. **Ek izleme seçenekleri** kutusunda seçenekler yazın.

     Örneğin, profil oluşturma düzeyini belirtmek için/CONTROL: THREAD komutunu kullanın. Seçeneklerin tamamı listesi için bkz. [vsinstr](../profiling/vsinstr.md).

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
