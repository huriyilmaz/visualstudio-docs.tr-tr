---
title: Çözüm Office sorunlarını giderme
description: Güvenlik çözümlerinin güvenliğini sağlamayla çalışırken karşılaş olabileceğiniz yaygın sorunları çözmek için Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 156494c507065d1c14fed9affe5a5ef2f592093e39625bd50fcbb505b6be2d6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121330902"
---
# <a name="troubleshoot-office-solution-security"></a>Çözüm Office sorunlarını giderme
  Bu konu, güvenlik çözümlerinin güvenliğini sağlamayla çalışırken karşılaş olabileceğiniz yaygın sorunları çözmeye Office içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Güvenilen çözümler kısıtlı sitelerden yükilemez
 Web sitesi kısıtlı siteler bölgesinde listelenmişse kullanıcılar bir web Internet Explorer çözüm yük olamaz. Çözüm güvenilir bir sertifikayla imzalanmış olsa bile bu durum doğrudur.

 Dağıtım bildiriminin URL'si beş bölgeye ayrılmış olabilir:

- Bilgisayarım

- İnternet

- Yerel intranet

- Güvenilen siteler

- Kısıtlı siteler

  Dağıtım bildiriminin konumu kısıtlı siteler bölgesine atanmışsa, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümü yüklemez. Konum biliniyorsa ve güvenilirse, kullanıcı konumu kısıtlanmış siteler bölgesinden kaldırabilir ve çözümü yükleyebilir. Bölgeleri yönetme hakkında bilgi için bkz. [Güvenilen Yayımcıları ClickOnce yapılandırma.](/previous-versions/dotnet/articles/ms996418(v=msdn.10))

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer Artırılmış Güvenlik Yapılandırması veya Internet Explorer 7 yüklü olduğunda, çözümler ağ dosya paylaşımlarından veya web konumlarından yük olamaz
 Windows Internet Explorer Server 2003 ve üzerinde gelişmiş güvenlik yapılandırması (IEESC), Internet Explorer 7 ve üzerinde ise kullanıcıların İnternet'e göz atma becerisini önemli ölçüde kısıtlar. Kullanıcılar bir ağ dosya paylaşımından veya web konumdan Office çözümlerini yüklemeye çalışırken şu hata iletisini alsalar: *"SolutionName* dağıtım bildirimini imzalamak için kullanılan sertifika güvenilir değil çünkü bu uygulamada özelleştirilmiş işlevsellik çalışmıyor. Daha fazla yardım için yöneticinize başvurun."

 IEESC ve Internet Explorer 7 ve üzerindeyse, dağıtım bildiriminin URL'si İnternet bölgesinde kategorilere ayrılmışsa, bildirimin güvenilen yayımcıdan bir sertifikası olmalıdır veya çözüm yükilemez. IEESC olmadan varsayılan davranış, son kullanıcıdan güven kararı vermelerini istenir.

 IEESC ve Internet Explorer 7 ve daha yüksek bir uygulamanın etkisini yönetmek için güvenebileceğiniz web sitelerini ve evrensel adlandırma kuralı (UNC) yollarını belirleyin ve bunları güvenilen güvenlik bölgelerinden (Yerel intranet veya Güvenilen siteler) biri'ne ekleyin. Bölgeleri yönetme hakkında bilgi için bkz. [Güvenilen yayımcıları ClickOnce yapılandırma.](/previous-versions/dotnet/articles/ms996418(v=msdn.10))

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
