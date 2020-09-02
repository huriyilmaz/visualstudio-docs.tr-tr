---
title: 'Nasıl yapılır: Windows sembol bilgilerine başvuru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7a123a42c1a46faf67fb5b63b1ab4ef300735f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822696"
---
# <a name="how-to-reference-windows-symbol-information"></a>Nasıl yapılır: Başvuru Pencereleri Sembol Bilgileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profil Oluşturma Araçları sembol (. pdb) dosyalarını, program ikili dosyalarında işlev adları gibi sembolik adları çözümlemek için kullanın. Yerel bilgisayardaki Windows sürümüne yönelik doğru. pdb dosyalarını otomatik olarak indirmek ve güncelleştirmek için bu adımları izleyebilirsiniz.  
  
> [!NOTE]
> Bu ayar varolan raporları etkilemez. Yalnızca sembol sunucusu belirttikten sonra oluşturulan raporların sembol bilgisi olacaktır.  
  
 Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft symbol Server 'ı kullanmak için  
  
1. C:\symbolcachegibi sembol dosyası bilgilerini içerecek bir klasör oluşturun.  
  
2. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.  
  
     **Seçenekler** iletişim kutusu görüntülenir.  
  
3. **Hata ayıklama** ağacını genişletin ve ardından **semboller**' e tıklayın.  
  
4. **Sembol dosyası (. pdb) konumlarında** **Microsoft sembol sunucuları** ' nı seçin.  
  
5. **Sembol sunucusundan bu dizine önbellek sembolleri**, 1. adımda oluşturulan klasörün yolunu yazın, örneğin:  
  
     **C:\SymbolCache**  
  
     Ayrıca üç nokta düğmesine (**...**) tıklayabilir ve sonra **klasöre gözatamıyorum** iletişim kutusundan bir dizin seçebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Nasıl yapılır: Sembol Bilgilerini Serileştirme](../profiling/how-to-serialize-symbol-information.md)
