---
title: Performans Veri Dosyaları dosyalarıyla Sembol Bilgilerini | Microsoft Docs
description: Rapor dosyanıza sembolleri kaydetmek veya serileştirmek için performans projesi ayarlarını yapmayı öğrenin.
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
ms.openlocfilehash: 341807e78a43b716c09fc063d0dadbc6ad1450851e1b0cb339d9b5efcc96e712
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410426"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans Veri Dosyalarıyla Birlikte Sembol Bilgilerini Kaydetme

Dosyaları analiz etmek için Visual Studio IDE kullanıyorsanız ve VSP dosyanızı farklı bir bilgisayara taşımayı planlıyorsanız,  rapor dosyanıza sembolleri kaydetmek veya serileştirmek için performans projesi ayarlarını yapılandırmanız gerekir. Bu, rapor dosyasının boyutunu artırır. Sembolleri seri hale getirmenin iki nedeni vardır:

- Hedef derlemeler geçici depolama konumlarından kaybedilmeden önce bir performans raporuna kod sembolleri eklemek için.

- Sembolleri korumak için, performans raporunun profili profili yapılan bilgisayardan taşınabilir olması ve raporun farklı sembollere sahip olabileceği başka bir bilgisayarda analiz için açılmasını sağlar.

IDE'den veya komut Visual Studio sembolleri seri hale getirebilirsiniz:

- IDE'de sembolleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serileştirmek için menü **çubuğundaki Araçlar'ın** üzerine gelin ve Seçenekler'e **tıklayın.** Seçenekler penceresinde **Performans** **Araçları'nın ardından Sembol** bilgilerini otomatik olarak **seri hale getir onay kutusunu** seçin.

- PACKSYMBOLS, rapor dosyalarını kaydeden eşdeğer komut satırı seçeneğidir. Sembolleri serileştirmek için **vsperfreport /summary:all /packsymbols filename.vsp yazın.**

## <a name="troubleshooting-symbol-problems"></a>Sembol Sorunlarını Giderme

Kendi kodunda herhangi bir simge görmüyorsanız, bazı yaygın çözümler kullanılabilir:

- Profil oluşturma bileşenlerinin sembol bilgilerini yükley bulunduğu konumların tam listesini ve kullanılan sembol dosyalarının projenizin kullandığı dosyalarda eş olup olmadığını görüntülemek için komut satırına vsperfreport /debugsympath komutunu çalıştırın.

- Vsperfreport'ı /PACKSYMBOLS bayrağıyla veya IDE'de genel performans gezgini seçeneklerinde sembol bilgilerini seri hale getir seçeneğinin belirlenmiş olduğundan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] emin olun.

- Tür verilerini topladıysanız vsperfreport komut satırına /SUMMARY:TYPE ekleyin.

  Microsoft programlarından veya diğer Microsoft programlarından Windows görmüyorsanız:

- Uygulama sembol önbelleğinizin yolunu ayar Windows olun. Sembol önbellek yolunu ayarlamak için aşağıdakilerden birini yapın:

  - IDE'de Debugger->Sembolleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] seçeneğini doğru yola ayarlayın.

  - Sembollerinizi eklemek için VSPerfReport komut satırına -symbolpath seçeneğini ekleyin.

- içinde herhangi bir simge [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] görmüyorsanız, ASP sunucusu için sembol sunucusunun doğru şekilde ayarlanmış olduğundan emin olun.

## <a name="repacking-symbols"></a>Sembolleri Yeniden Paketleme

Sembolleri bir rapora yeniden paketlemek için vsPerfReport komut satırı aracını kullanarak bunu yapabiliriz. Aşağıdaki komut satırlarını kullanın:

VsPerfReport -clearpackedsymbols filename.vsp

VsPerfReport -packsymbols -summary:all filename.vsp

## <a name="see-also"></a>Ayrıca bkz.

[Performans Araçları Verilerini Kaydetme ve Dışarı Aktarma](../profiling/saving-and-exporting-performance-tools-data.md) 
 [Nasıl gösterilir: Windows Sembol Bilgilerine Başvuru](../profiling/how-to-reference-windows-symbol-information.md) 
 [VSPerfReport](../profiling/vsperfreport.md)
