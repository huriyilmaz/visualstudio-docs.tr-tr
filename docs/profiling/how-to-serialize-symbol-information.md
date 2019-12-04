---
title: 'Nasıl yapılır: sembol bilgilerini serileştirme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 202c30b1786e7e3ddb27583ddaeda9180d680b53
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774893"
---
# <a name="how-to-serialize-symbol-information"></a>Nasıl yapılır: sembol bilgilerini serileştirme
Uygulamanızı çözümlemek için sahip olmanız gereken sembolleri seri hale getirebilirsiniz. Sembol serileştirme öğesine semboller ekler. *VSP* dosyası. Öğesine sembol bilgisi ekleyerek. *VSP* dosyası, diğer bir deyişle, özgün simgelere erişim olmadan bir performans raporunu çözümleyebilir. Semboller serileştirilmeyen, özgün olarak işaretlenmiş olmalıdır. *exe* ve. analiz edilecek *pdb* dosyaları. *VSP* dosyası.

### <a name="to-automatically-serialize-symbol-information"></a>Sembol bilgilerini otomatik olarak seri hale getirmek için

1. **Araçlar** menüsünde **Seçenekler**' e tıklayın.

     **Seçenekler** iletişim kutusu görüntülenir.

2. **Performans araçları**' na tıklayın.

3. **Genel ayar**altında **otomatik olarak sembol bilgilerini seri hale getirme**' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)
- [Nasıl yapılır: çözümlenen rapor dosyalarını kaydetme](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
