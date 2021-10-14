---
title: Web projeleri için özellik ayarları | Microsoft Docs
description: Bir web sitesi hata ayıklama yapılandırmasının özellik ayarlarını, uygulamanın Özellik Sayfaları iletişim kutusunda nasıl değiştir Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cd99b76882ee4407496475668193c7b5631af50d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129973148"
---
# <a name="property-pages-settings-for-web-projects"></a>Web Projeleri Özellik Sayfası Ayarları
Hata Ayıklama ve Sürüm Yapılandırmaları'da ele  alınarak, Özellik Sayfaları iletişim kutusunda bir web sitesi hata ayıklama [yapılandırmasının özellik ayarlarını değiştirebilirsiniz.](../debugger/how-to-set-debug-and-release-configurations.md) Aşağıdaki tablolarda, Özellik Sayfaları iletişim kutusunda hata ayıklayıcıyla ilgili **ayarların nerede bulunamaz olduğu** gösterir.

### <a name="start-options-category"></a>Başlangıç Seçenekleri kategorisi

| **Ayar** | **Açıklama** |
| - | - |
| **Başlatma Eylemi** | Uygulama başlatmayla ilgili seçenekleri gruplaan başlık. |
| **Geçerli Sayfayı kullan** | Geçerli sayfayı hata ayıklama için başlangıç noktası olarak belirtir. |
| **Belirli bir sayfa:** | Hata ayıklamaya başlamak istediğiniz Web sayfasını belirtir. |
| **Dış programı başlat:** | Hata ayıklamak istediğiniz programı başlatmak için komutunu belirtir. |
| **Komut satırı bağımsız değişkenleri:** | Yukarıda belirtilen komutun bağımsız değişkenlerini belirtir. |
| **Çalışma dizini:** | Hata ayıklaması yapılan programın çalışma dizinini belirtir. içinde [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] çalışma dizini, uygulamanın varsayılan olarak \bin\debug konumundan başlat olduğu dizindir. |
| **Başlangıç URL'si** | Hata ayıklamak istediğiniz Web uygulamasının konumunu belirtir. |
| **Sayfa açmayın. Dış bir uygulamanın isteğini bekleme** | Dış bir uygulamanın isteği için beklemesi gerekir. Bu seçenek, Internet Explorer başka bir uygulamayı başlatmaz. Yalnızca bir uygulama tarafından çağrıldıklarda hata ayıklamaya hazırlar. |
| **Sunucu** | Kullanılacak sunucuyla ilgili seçenekleri gruplaan başlık. |
| **Varsayılan Web sunucusunu kullanma** | Varsayılan Web sunucusunun kullan olduğunu belirtir. |
| **Özel sunucu kullanma** | Sunucu olarak kullanmak üzere Temel URL'yi girmenize olanak sağlar. |
| **Hata ayıklayıcı** | Yapılacak hata ayıklama türüyle ilgili seçenekleri gruplama başlığı. |
| **ASP.NET hata ayıklama** | Geliştirme platformu için yazılmış sunucu sayfalarının hata [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ayıklamasını sağlar. Başlangıç URL'si içinde bir URL **belirtmeniz gerekir.** |
| **Yerel kodda hata ayıklama** | Yönetilen uygulamanıza gelen yerel (yönetilemeyen) Win32 koduna yapılan çağrılarda hata ayıklamanıza olanak sağlar. |
| **SQL Server hata ayıklama** | Veritabanı nesnelerinin hata SQL Server izin verir. |
| **Silverlight hata ayıklama** | Silverlight bileşenlerinin hata ayıklamasını sağlar. |

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarlar Hazırlama](../debugger/debugger-settings-and-preparation.md)