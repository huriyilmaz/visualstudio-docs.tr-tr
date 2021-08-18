---
title: Office çözüm güvenliği sorunlarını giderme
description: Microsoft Office çözümlerini güvenli hale getirirken karşılaşabileceğiniz yaygın sorunları çözmeye yönelik bazı ipuçları hakkında bilgi edinin.
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
ms.openlocfilehash: b23dcf46853c2e8a236c4bf2db21911f3ad7708d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032166"
---
# <a name="troubleshoot-office-solution-security"></a>Office çözüm güvenliği sorunlarını giderme
  bu konu, güvenlik Office çözümleriyle çalışırken karşılaşabileceğiniz yaygın sorunları çözmeye yönelik ipuçları içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Güvenilen çözümler, yasak sitelerden yüklenemez
 Web sitesi Internet Explorer kısıtlı siteler bölgesinde listeleniyorsa, kullanıcılar Web konumundan bir çözüm yükleyemez. Bu, çözüm güvenilir bir sertifikayla imzalansa bile geçerlidir.

 Dağıtım bildiriminin URL 'SI beş bölgelerden birine kategorize edilebilir:

- Bilgisayarım

- İnternet

- Yerel intranet

- Güvenilen siteler

- Yasak siteler

  Dağıtım bildiriminin konumu yasak siteler bölgesine atanmışsa, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümü yüklemez. Konum biliniyorsa ve güvenilir bir şekilde güveniliyorsa, Kullanıcı bu konumu yasak siteler bölgesinden kaldırabilir ve çözümü yükleyebilir. bölgeleri yönetme hakkında daha fazla bilgi için bkz. [ClickOnce güvenilir yayımcıları yapılandırma](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer Artırılmış Güvenlik Yapılandırması veya Internet Explorer 7 yüklendiğinde çözümler ağ dosya paylaşımlarından veya Web konumlarından yüklenemez
 Windows Server 2003 ve üzeri sürümlerde ınternet explorer artırılmış güvenlik yapılandırması (ıeesc) ve ınternet explorer 7 ve üzeri, kullanıcıların internet 'e gözatmasına önemli ölçüde kısıtlama sağlar. kullanıcılar bir ağ dosya paylaşımından veya web konumundan Office çözümleri yüklemeye çalıştığında, *solutionname* için dağıtım bildirimini imzalamak için kullanılan sertifika güvenilir olmadığından, bu uygulamadaki özelleştirilmiş işlevsellik çalışmayacak. Daha fazla yardım için yöneticinize başvurun. "

 IEESC ve Internet Explorer 7 ve üzeri ile, dağıtım bildiriminin URL 'SI Internet bölgesinde sınıflandırıldığından, bildirimin güvenilen bir yayımcının sertifikası olmalıdır veya çözüm yüklenemez. IEESC olmadan, varsayılan davranış, son kullanıcıdan bir güven kararı vermesini istemelidir.

 IEESC ve Internet Explorer 7 ve üzeri etkilerini yönetmek için, güvendiğiniz Web sitelerini ve evrensel adlandırma kuralı (UNC) yollarını ve bunları güvenilir güvenlik bölgelerinden (yerel intranet veya güvenilen siteler) birine ekleyin. bölgeleri yönetme hakkında daha fazla bilgi için bkz. [ClickOnce güvenilir yayımcıları yapılandırma](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
