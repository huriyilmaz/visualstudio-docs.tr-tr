---
title: Sembol bilgilerini serileştirme | Microsoft Docs
description: Uygulamanızı çözümlemek için sahip olmanız gereken sembolleri nasıl seri hale getirebileceğinizi ve sembol serileştirmenin. vsp dosyasına semboller nasıl ekleyeceğini öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7bc26ef8de79ef42c2b58c9edae6ffa030310f5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076574"
---
# <a name="how-to-serialize-symbol-information"></a>Nasıl yapılır: sembol bilgilerini serileştirme
Uygulamanızı çözümlemek için sahip olmanız gereken sembolleri seri hale getirebilirsiniz. Sembol serileştirme öğesine semboller ekler. *VSP* dosyası. Öğesine sembol bilgisi ekleyerek. *VSP* dosyası, diğer bir deyişle, özgün simgelere erişim olmadan bir performans raporunu çözümleyebilir. Semboller serileştirilmeyen, özgün olarak işaretlenmiş olmalıdır. *exe* ve. analiz edilecek *pdb* dosyaları. *VSP* dosyası.

### <a name="to-automatically-serialize-symbol-information"></a>Sembol bilgilerini otomatik olarak seri hale getirmek için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

     **Seçenekler** iletişim kutusu görüntülenir.

2. **Performans araçları**' na tıklayın.

3. **Genel ayar** altında **otomatik olarak sembol bilgilerini seri hale getirme**' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)
- [Nasıl yapılır: çözümlenen rapor dosyalarını kaydetme](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
