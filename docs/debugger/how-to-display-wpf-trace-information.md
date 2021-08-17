---
title: WPF İzleme Bilgilerini Görüntüleme | Microsoft Docs
description: Visual Studio WPF uygulamalarından hata ayıklama izleme bilgilerini alır ve Çıkış penceresinde görüntüler. WPF izlemeyi yönetmeyi ve özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6b697645cbff18ebb7053f1b9facca221de767d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128487"
---
# <a name="how-to-display-wpf-trace-information"></a>Nasıl Yapılır: WPF İzleme Bilgilerini Görüntüleme
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , WPF uygulamalarından hata ayıklama izleme bilgilerini alır ve bu bilgileri Çıkış **penceresinde** görüntüler. Hata ayıklama izleme bilgilerini görüntülemek için WPF izlemenin etkinleştirilmesi gerekir.

 WPF izlemeyi sınıfını kullanarak App.Config program aracılığıyla <xref:System.Diagnostics.PresentationTraceSources> etkinleştirebilirsiniz. WPF izlemeyi etkinleştirmenin daha kolay bir yolu Seçenekler penceresini **kullanmaktır.** Web uygulamaları için WPF izlemesi desteklenmiyor.

### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF izleme bilgilerini etkinleştirmek veya özelleştirmek için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. Seçenekler **iletişim** kutusunda, sol tarafta yer alan kutuda Hata ayıklama **düğümünü** açın.

3. Hata **Ayıklama altında,** öğesini **Çıkış Penceresi.**

4. Genel **Çıkış Ayarlar** altında Tüm hata ayıklama **çıkışı'na seçin.**

5. Sağ kutu içinde **WPF** trace Ayarlar.

6. **WPF İzleme ve Ayarlar** açın.

7. **WPF İzleme Ayarlar** altında, etkinleştirmek istediğiniz ayarlar kategorisine tıklayın (örneğin, **Veri Bağlama).**

     Veri Bağlama'nın yanındaki Ayarlar veya tıklamış olduğunuz **kategoriyi içeren** bir açılan liste denetimi görüntülenir.

8. Açılan listeye tıklayın ve görmek istediğiniz izleme bilgileri türünü **seçin:** Tüm , **Kritik**, **Hata** **,** Uyarı , **Bilgi** **,** Ayrıntılı veya **ActivityTracing**.

     **Kritik,** yalnızca Kritik olayların izlemeyi etkinleştirir.

     **Hata,** Kritik ve Hata olaylarının izlerini etkinleştirir.

     **Uyarı,** Kritik, Hata ve Uyarı olaylarının izlemesi sağlar.

     **Bilgiler** Kritik, Hata, Uyarı ve Bilgi olaylarının izlerini etkinleştirir.

     **Ayrıntılı, Kritik,** Hata, Uyarı, Bilgi ve Ayrıntılı olayların izlemesi sağlar.

     **ActivityTracing;** Durdurma, Başlatma, Askıya Alma, Aktarma ve Sürdürme olaylarını izlemeyi etkinleştirir.

     Bu izleme bilgisi düzeylerinin ne anlama geliyor hakkında daha fazla bilgi için bkz. <xref:System.Diagnostics.SourceLevels> .

9. **Tamam**'a tıklayın.

### <a name="to-disable-wpf-trace-information"></a>WPF izleme bilgilerini devre dışı bırakmak için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. Seçenekler **iletişim** kutusunda, sol tarafta yer alan kutuda Hata ayıklama **düğümünü** açın.

3. Hata **Ayıklama altında,** öğesini **Çıkış Penceresi.**

4. Sağ kutu içinde **WPF** trace Ayarlar.

5. **WPF İzleme ve Ayarlar** açın.

6. **WPF İzleme Ayarlar** altında, etkinleştirmek istediğiniz ayarlar kategorisine tıklayın (örneğin, **Veri Bağlama).**

     Veri Bağlama'nın yanındaki Ayarlar veya tıklamış olduğunuz **kategoriyi içeren** bir açılan liste denetimi görüntülenir.

7. Açılan listeye tıklayın ve Kapalı'yı **seçin.**

8. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [WPF'de Hata Ayıklama](../debugger/debugging-wpf.md)