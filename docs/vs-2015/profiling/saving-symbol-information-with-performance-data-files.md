---
title: Simge bilgilerini performans veri dosyalarıyla kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9d2e8b0414746523d0f76e8266f6463d9c05574
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160292"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans Veri Dosyalarıyla Birlikte Sembol Bilgilerini Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dosyaları çözümlemek için tümleşik geliştirme ortamı (IDE) kullanıyorsanız ve VSP dosyanızı farklı bir bilgisayara taşımayı planlıyorsanız, performans projesi ayarlarını rapor dosyanızdaki sembolleri kaydetmek veya *seri hale* getirmek için ayarlamanız gerekir. Bu, bir rapor dosyasının boyutunu artırır. İki nedenle sembolleri serileştirmek gereklidir:  
  
- Hedef derlemeler geçici depolamadaki konumlarından kaybolmadan önce bir performans raporuna kod sembolleri eklemek için.  
  
- Sembolleri korumak için, performans raporunun profili oluşturulmuş bilgisayardan taşınabilir olması ve rapor başka bir bilgisayarda analiz için açılırsa farklı sembolleri olabilen aynı bilgileri çıkışları.  
  
  **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Sembolleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 'den veya komut satırından seri hale getirebilirsiniz:  
  
- IDE 'de sembolleri seri hale getirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menü çubuğundaki **Araçlar** ' ın üzerine gelin ve ardından **Seçenekler**' e tıklayın. **Seçenekler** penceresinde, **performans araçları**' nı seçin ve ardından **sembol bilgilerini otomatik olarak seri hale getirme** onay kutusunu seçin.  
  
- Rapor dosyalarını kaydettiğinizde, PACKSYMBOLS, eşdeğer komut satırı seçeneğidir. Sembolleri seri hale getirmek için **VSPerfReport/summary: all/packsymbols filename. vsp**yazın.  
  
## <a name="troubleshooting-symbol-problems"></a>Sembol sorunlarını giderme  
 Kendi kodunuzda herhangi bir sembol görmüyorsanız bazı yaygın çözümler kullanılabilir:  
  
- Profiler bileşenlerinin sembol bilgilerini yüklediği konumların ve kullanılan sembol dosyalarının projenizin kullandığı dosyalarla eşleşip eşleşmeksizin, bir komut satırında VSPerfReport/debugsympath komutunu çalıştırın.  
  
- VSPerfReport komutunu/PACKSYMBOLS bayrağıyla veya IDE 'de, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genel performans Gezgini seçeneklerinde serileştirme sembol bilgisi seçeneğinin seçili olduğundan emin olun.  
  
- Tür verisi topladıysanız, VSPerfReport komut satırına/SUMMARY: TYPE ekleyin.  
  
  Windows veya diğer Microsoft programlarından sembolleri görmüyorsanız:  
  
- Windows sembol önbelleğinizin yolunu ayarladığınızdan emin olun. Sembol önbelleği yolunu ayarlamak için aşağıdakilerden birini yapın:  
  
  - IDE 'deki Debugger->sembolleri seçeneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doğru yola ayarlayın.  
  
  - Sembollerinizi dahil etmek için VSPerfReport komut satırına-SymbolPath seçeneğini ekleyin.  
  
- İçinde herhangi bir sembol görmüyorsanız [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , sembol sunucusunun ASP sunucusu için doğru şekilde ayarlandığından emin olun.  
  
## <a name="repacking-symbols"></a>Simgeleri yeniden paketleme  
 Sembolleri bir rapora yeniden paketetmek isterseniz, bunu komut satırı aracı VsPerfReport ' u kullanarak yapabilirsiniz. Aşağıdaki komut satırlarını kullanın:  
  
 VsPerfReport-clearpackedsymbols filename. vsp  
  
 VsPerfReport-packsymbols-Summary: tüm filename. vsp  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans araçları verilerini kaydetme ve dışarı aktarma](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
