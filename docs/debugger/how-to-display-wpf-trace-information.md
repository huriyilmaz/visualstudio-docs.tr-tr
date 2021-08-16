---
title: WPF Izleme bilgilerini görüntüleme | Microsoft Docs
description: Visual Studio, WPF uygulamalarından hata ayıklama izleme bilgilerini alabilir ve çıkış penceresinde görüntüleyebilir. WPF izlemeyi yönetmeyi ve özelleştirmeyi öğrenin.
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
ms.openlocfilehash: e24c418d345eb6553268b62eebecf66efd1b1b42ecd4610edab73e6142e8bd65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361983"
---
# <a name="how-to-display-wpf-trace-information"></a>Nasıl Yapılır: WPF İzleme Bilgilerini Görüntüleme
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , WPF uygulamalarından hata ayıklama izleme bilgilerini alabilir ve bu bilgileri **Çıkış** penceresinde görüntüler. Hata ayıklama izleme bilgilerini göstermek için WPF izlemenin etkinleştirilmesi gerekir.

 App.Config dosyanızda WPF izlemeyi etkinleştirebilir veya sınıfını kullanarak programlı bir şekilde etkinleştirebilirsiniz <xref:System.Diagnostics.PresentationTraceSources> . WPF izlemeyi etkinleştirmenin daha kolay bir yolu, **Seçenekler** penceresini kullanmaktır. Web uygulamaları için WPF izleme desteklenmez.

### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF izleme bilgilerini etkinleştirmek veya özelleştirmek için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. **Seçenekler** iletişim kutusunda, soldaki kutudan **hata ayıklama** düğümünü açın.

3. **Hata ayıklama** altında **Çıkış penceresi**' ye tıklayın.

4. **genel çıktı Ayarlar** altında, **tüm hata ayıklama çıktısı**' nı seçin.

5. sağ taraftaki kutuda **WPF izleme Ayarlar**' a bakın.

6. **WPF Trace Ayarlar** düğümünü açın.

7. **WPF izleme Ayarlar** altında, etkinleştirmek istediğiniz ayar kategorisine (örneğin, **veri bağlama**) tıklayın.

     **veri bağlamanın** yanındaki Ayarlar sütununda veya tıkladığınız herhangi bir kategoride açılan liste denetimi görünür.

8. Aşağı açılan listeye tıklayın ve görmek istediğiniz izleme bilgisi türünü seçin: **Tümü**, **kritik**, **hata**, **Uyarı**, **bilgi**, **ayrıntılı** veya **etkinlik izleme**.

     **Kritik** yalnızca kritik olayları izlemeye izin vermez.

     **Hata** , kritik ve hata olaylarının izlenmesini mümkün.

     **Uyarı** , kritik, hata ve uyarı olaylarının izlenmesini mümkün.

     **Bilgiler** kritik, hata, uyarı ve bilgi olaylarının izlenmesini mümkün.

     **Verbose** , kritik, hata, uyarı, bilgi ve ayrıntılı olayların izlenmesini mümkün.

     **ActivityTracing** , durdurma, başlatma, askıya alma, aktarım ve yeniden başlatma olaylarının izlenmesini mümkün.

     Bu izleme bilgilerinin ne anlama geldiğini hakkında daha fazla bilgi için bkz <xref:System.Diagnostics.SourceLevels> ..

9. **Tamam**'a tıklayın.

### <a name="to-disable-wpf-trace-information"></a>WPF izleme bilgilerini devre dışı bırakmak için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. **Seçenekler** iletişim kutusunda, soldaki kutudan **hata ayıklama** düğümünü açın.

3. **Hata ayıklama** altında **Çıkış penceresi**' ye tıklayın.

4. sağ taraftaki kutuda **WPF izleme Ayarlar**' a bakın.

5. **WPF Trace Ayarlar** düğümünü açın.

6. **WPF izleme Ayarlar** altında, etkinleştirmek istediğiniz ayar kategorisine (örneğin, **veri bağlama**) tıklayın.

     **veri bağlamanın** yanındaki Ayarlar sütununda veya tıkladığınız herhangi bir kategoride açılan liste denetimi görünür.

7. Açılan listeye tıklayın ve **kapalı**' yı seçin.

8. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [WPF'de Hata Ayıklama](../debugger/debugging-wpf.md)