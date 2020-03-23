---
title: Performans Veri Dosyaları ile Sembol Bilgilerini Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 74137752900d082c545dd5e5271b7700ec81fa01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778303"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans Veri Dosyalarıyla Birlikte Sembol Bilgilerini Kaydetme

Dosyaları çözümlemek için Visual Studio IDE kullanıyorsanız ve VSP dosyanızı farklı bir bilgisayara taşımayı planlıyorsanız, rapor dosyanızdaki sembolleri kaydetmek veya *seri hale getirmek* için performans proje ayarlarını ayarlamanız gerekir. Bu, bir rapor dosyasının boyutunu artırır. Sembolleri serileştirme iki nedenden dolayı gereklidir:

- Hedef derlemeler geçici depolamadaki konumlarından kaybolmadan önce kod sembollerini performans raporuna yerleştirmek için.

- Farklı sembollere sahip olabilecek başka bir bilgisayarda analiz için rapor açıldığında, performans raporunun profilli bilgisayardan taşınabilir olması ve aynı bilgileri çıkarabilmesi için sembolleri korumak için.

Visual Studio IDE'den veya komut satırından sembolleri seri hale getirebilirsiniz:

- IDE'deki sembolleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serihale getirmek için menü çubuğundaki **Araçlar'ı** işaret edin ve ardından **Seçenekler'i**tıklatın. **Seçenekler** penceresinde Performans **Araçları'nı**seçin ve ardından **otomatik olarak serihale sembolü bilgi** onay kutusunu seçin.

- PACKSYMBOLS, rapor dosyalarını kaydettiğinizde eşdeğer komut satırı seçeneğidir. Sembolleri serihale getirmek için **vsperfreport /summary yazın:tüm /packsymbols filename.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Sorun Giderme Sembol Sorunları

Kendi kodunuzda herhangi bir sembol görmüyorsanız, bazı ortak çözümler kullanılabilir:

- Profil oluşturucu bileşenlerinin sembol bilgilerini yüklendiği yerlerin tam listesini ve kullanılan sembol dosyalarının projenizin kullandığı dosyalarla eşleşip eşleşmediğini göstermek için bir komut satırında vsperfreport /debugsympath çalıştırın.

- /PACKSYMBOLS bayrağıyla vsperfreport çalıştırdığınızdan veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE'de genel performans gezgini seçeneklerinde serileştirme simge bilgileri seçeneğine sahip olduğunuzdan emin olun.

- Tür verileri topladıysanız, vsperfreport komut satırına /SUMMARY:TYPE ekleyin.

  Windows veya diğer Microsoft programlarından gelen sembolleri görmüyorsanız:

- Windows simge önbelleğinin yolunu ayarladığınızdan emin olun. Simge önbellek yolunu ayarlamak için aşağıdakilerden birini yapın:

  - Hata ayıklama >Sembolleri seçeneğini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE'de doğru yola ayarlayın.

  - Sembollerinizi eklemek için VSPerfReport komut satırına -symbolpath seçeneğini ekleyin.

- Herhangi bir sembol [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]görmüyorsanız, ASP sunucusu için doğru ayarlanmış sembol sunucusuolduğundan emin olun.

## <a name="repacking-symbols"></a>Sembolleri Yeniden Paketleme

Sembolleri bir rapora yeniden paketlemek istiyorsanız, bunu VsPerfReport komut satırı aracını kullanarak yapabilirsiniz. Aşağıdaki komut satırlarını kullanın:

VsPerfReport -clearpacked symbols filename.vsp

VsPerfReport -packsymbols -özet:tüm filename.vsp

## <a name="see-also"></a>Ayrıca bkz.

[Performans Araçları Veri](../profiling/saving-and-exporting-performance-tools-data.md)
Kaydetme ve Dışa[Aktarma: Başvuru Windows Symbol Information](../profiling/how-to-reference-windows-symbol-information.md)
[VSPerfReport](../profiling/vsperfreport.md)
