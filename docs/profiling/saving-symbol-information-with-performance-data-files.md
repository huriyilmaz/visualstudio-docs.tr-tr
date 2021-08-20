---
title: Simge bilgilerini performans veri dosyalarıyla kaydetme | Microsoft Docs
description: Rapor dosyanızdaki sembolleri kaydetmek veya seri hale getirmek için performans projesi ayarlarını nasıl ayarlayabileceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b37a56776d70127f52c17224ba3366e79439e3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157377"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans Veri Dosyalarıyla Birlikte Sembol Bilgilerini Kaydetme

dosyaları çözümlemek için Visual Studio ıde 'yi kullanıyorsanız ve VSP dosyanızı farklı bir bilgisayara taşımayı planlıyorsanız, performans projesi ayarlarını rapor dosyanızdaki sembolleri kaydetmek veya *seri hale* getirmek için ayarlamanız gerekir. Bu, bir rapor dosyasının boyutunu artırır. İki nedenle sembolleri serileştirmek gereklidir:

- Hedef derlemeler geçici depolamadaki konumlarından kaybolmadan önce bir performans raporuna kod sembolleri eklemek için.

- Sembolleri korumak için, performans raporunun profili oluşturulmuş bilgisayardan taşınabilir olması ve rapor başka bir bilgisayarda analiz için açılırsa farklı sembolleri olabilen aynı bilgileri çıkışları.

sembolleri Visual Studio ıde 'den veya komut satırından seri hale getirebilirsiniz:

- IDE 'de sembolleri seri hale getirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menü çubuğundaki **Araçlar** ' ın üzerine gelin ve ardından **Seçenekler**' e tıklayın. **Seçenekler** penceresinde, **performans araçları**' nı seçin ve ardından **sembol bilgilerini otomatik olarak seri hale getirme** onay kutusunu seçin.

- Rapor dosyalarını kaydettiğinizde, PACKSYMBOLS, eşdeğer komut satırı seçeneğidir. Sembolleri seri hale getirmek için **VSPerfReport/summary: all/packsymbols filename. vsp** yazın.

## <a name="troubleshooting-symbol-problems"></a>Sembol sorunlarını giderme

Kendi kodunuzda herhangi bir sembol görmüyorsanız bazı yaygın çözümler kullanılabilir:

- Profiler bileşenlerinin sembol bilgilerini yüklediği konumların ve kullanılan sembol dosyalarının projenizin kullandığı dosyalarla eşleşip eşleşmeksizin, bir komut satırında VSPerfReport/debugsympath komutunu çalıştırın.

- VSPerfReport komutunu/PACKSYMBOLS bayrağıyla veya IDE 'de, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genel performans Gezgini seçeneklerinde serileştirme sembol bilgisi seçeneğinin seçili olduğundan emin olun.

- Tür verisi topladıysanız, VSPerfReport komut satırına/SUMMARY: TYPE ekleyin.

  Windows veya diğer Microsoft programlarından sembolleri görmüyorsanız:

- Windows sembol önbelleğinizin yolunu ayarladığınızdan emin olun. Sembol önbelleği yolunu ayarlamak için aşağıdakilerden birini yapın:

  - IDE 'deki Debugger->sembolleri seçeneğini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doğru yola ayarlayın.

  - Sembollerinizi dahil etmek için VSPerfReport komut satırına-SymbolPath seçeneğini ekleyin.

- İçinde herhangi bir sembol görmüyorsanız [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , sembol sunucusunun ASP sunucusu için doğru şekilde ayarlandığından emin olun.

## <a name="repacking-symbols"></a>Simgeleri yeniden paketleme

Sembolleri bir rapora yeniden paketetmek isterseniz, bunu komut satırı aracı VsPerfReport ' u kullanarak yapabilirsiniz. Aşağıdaki komut satırlarını kullanın:

VsPerfReport-clearpackedsymbols filename. vsp

VsPerfReport-packsymbols-Summary: tüm filename. vsp

## <a name="see-also"></a>Ayrıca bkz.

[Performans araçları verilerini](../profiling/saving-and-exporting-performance-tools-data.md) 
 kaydetme ve dışarı aktarma [nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md) 
 [VSPerfReport](../profiling/vsperfreport.md)
