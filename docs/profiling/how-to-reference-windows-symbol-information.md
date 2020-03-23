---
title: 'Nasıl kullanılır: Başvuru Windows Symbol Information | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 28bbd4b584d679c03c58ba8532ced3f28f16d6aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774919"
---
# <a name="how-to-reference-windows-symbol-information"></a>Nasıl yapılır: Başvuru pencereleri sembol bilgileri
Visual Studio Profil Oluşturma Araçları sembolü (.* pdb*) dosyaları program ikililerinde işlev adları gibi sembolik adları çözmek için. Doğru'yu otomatik olarak indirmek ve güncelleştirmek için aşağıdaki adımları izleyebilirsiniz. yerel bilgisayarda Windows sürümü için *pdb* dosyaları.

> [!NOTE]
> Bu ayar varolan raporları etkilemez. Yalnızca sembol sunucusu belirtildikten sonra oluşturulan raporlarda sembol bilgileri olur.

 Daha fazla bilgi için [bkz.* pdb*) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft sembol sunucusunu kullanmak için

1. C:\SymbolCache gibi sembol dosya bilgilerini içerecek bir klasör oluşturun.

2. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

     **Seçenekler** iletişim kutusu görüntülenir.

3. Hata **Ayıklama** ağacını genişletin ve ardından **Semboller'i**tıklatın.

4. Sembol **dosyası (.pdb) konumlarında** **Microsoft Symbol Sunucularını** seçin

5. Sembol **sunucusundan bu dizine önbellek sembollerinde,** örneğin adım 1'de oluşturulan klasörün yolunu yazın:

     **C:\SymbolÖnbellek**

     Ayrıca elipsis düğmesini **(...**) tıklatıp **klasöre Gözat** iletişim kutusundan bir dizin seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Nasıl kullanılır: Sembol bilgilerini serihale](../profiling/how-to-serialize-symbol-information.md)
