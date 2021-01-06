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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4800c2ca44c2c52b2059685d9c5bc4fe38ed08
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903980"
---
# <a name="how-to-display-wpf-trace-information"></a>Nasıl Yapılır: WPF İzleme Bilgilerini Görüntüleme
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , WPF uygulamalarından hata ayıklama izleme bilgilerini alabilir ve bu bilgileri **Çıkış** penceresinde görüntüler. Hata ayıklama izleme bilgilerini göstermek için WPF izlemenin etkinleştirilmesi gerekir.

 App.Config dosyanızda WPF izlemeyi etkinleştirebilir veya sınıfını kullanarak programlı bir şekilde etkinleştirebilirsiniz <xref:System.Diagnostics.PresentationTraceSources> . WPF izlemeyi etkinleştirmenin daha kolay bir yolu, **Seçenekler** penceresini kullanmaktır. Web uygulamaları için WPF izleme desteklenmez.

### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF izleme bilgilerini etkinleştirmek veya özelleştirmek için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. **Seçenekler** iletişim kutusunda, soldaki kutudan **hata ayıklama** düğümünü açın.

3. **Hata ayıklama** altında **Çıkış penceresi**' ye tıklayın.

4. **Genel çıkış ayarları** altında **tüm hata ayıklama çıktısı**' nı seçin.

5. Sağ taraftaki kutuda **WPF Izleme ayarları**' na bakın.

6. **WPF Izleme ayarları** düğümünü açın.

7. **WPF Izleme ayarları** altında, etkinleştirmek istediğiniz ayar kategorisine tıklayın (örneğin, **veri bağlama**).

     **Veri bağlamanın** yanındaki ayarlar sütununda veya tıklattığınız kategoride açılan liste denetimi görünür.

8. Aşağı açılan listeye tıklayın ve görmek istediğiniz izleme bilgisi türünü seçin: **Tümü**, **kritik**, **hata**, **Uyarı**, **bilgi**, **ayrıntılı** veya **etkinlik izleme**.

     **Kritik** yalnızca kritik olayları izlemeye izin vermez.

     **Hata** , kritik ve hata olaylarının izlenmesini mümkün.

     **Uyarı** , kritik, hata ve uyarı olaylarının izlenmesini mümkün.

     **Bilgiler** kritik, hata, uyarı ve bilgi olaylarının izlenmesini mümkün.

     **Verbose** , kritik, hata, uyarı, bilgi ve ayrıntılı olayların izlenmesini mümkün.

     **ActivityTracing** , durdurma, başlatma, askıya alma, aktarım ve yeniden başlatma olaylarının izlenmesini mümkün.

     Bu izleme bilgilerinin ne anlama geldiğini hakkında daha fazla bilgi için bkz <xref:System.Diagnostics.SourceLevels> ..

9. **Tamam**’a tıklayın.

### <a name="to-disable-wpf-trace-information"></a>WPF izleme bilgilerini devre dışı bırakmak için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. **Seçenekler** iletişim kutusunda, soldaki kutudan **hata ayıklama** düğümünü açın.

3. **Hata ayıklama** altında **Çıkış penceresi**' ye tıklayın.

4. Sağ taraftaki kutuda **WPF Izleme ayarları**' na bakın.

5. **WPF Izleme ayarları** düğümünü açın.

6. **WPF Izleme ayarları** altında, etkinleştirmek istediğiniz ayar kategorisine tıklayın (örneğin, **veri bağlama**).

     **Veri bağlamanın** yanındaki ayarlar sütununda veya tıklattığınız kategoride açılan liste denetimi görünür.

7. Açılan listeye tıklayın ve **kapalı**' yı seçin.

8. **Tamam**’a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [WPF'de Hata Ayıklama](../debugger/debugging-wpf.md)