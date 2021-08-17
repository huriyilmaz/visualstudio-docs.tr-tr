---
title: Web projeleri için özellik ayarları | Microsoft Docs
description: Visual Studio özellik sayfaları iletişim kutusunda bir Web sitesi hata ayıklama yapılandırması için özellik ayarlarını nasıl değiştirileceğini öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5425b3172e18f224aaf989afecb3a40c1062e640e27b388b32c18a9f5adf3ee6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453084"
---
# <a name="property-pages-settings-for-web-projects"></a>Web Projeleri Özellik Sayfası Ayarları
Web sitesi hata ayıklama yapılandırması için özellik ayarlarını, [hata ayıklama ve sürüm yapılandırmalarında](../debugger/how-to-set-debug-and-release-configurations.md)anlatıldığı gibi **Özellik sayfaları** iletişim kutusunda değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** iletişim kutusunda hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.

### <a name="start-options-category"></a>Başlangıç seçenekleri kategorisi

| **Ayar** | **Açıklama** |
| - | - |
| **Başlatma eylemi** | Uygulama başlatma ile ilgili seçenekleri gruplandıran başlık. |
| **Geçerli sayfayı kullan** | Hata ayıklama için başlangıç noktası olarak geçerli sayfayı belirtir. |
| **Belirli sayfa:** | Hata ayıklamaya başlamak istediğiniz Web sayfasını belirtir. |
| **Dış programı Başlat:** | Hata ayıklamak istediğiniz programı başlatma komutunu belirtir. |
| **Komut satırı bağımsız değişkenleri:** | Yukarıda belirtilen komut için bağımsız değişkenleri belirtir. |
| **Çalışma dizini:** | Hata ayıklanan programın çalışma dizinini belirtir. ' De [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , çalışma dizini uygulamanın başlatıldığı dizindir, varsayılan olarak, \bin\Debug ' dır. |
| **Başlangıç URL 'SI** | Hata ayıklamak istediğiniz Web uygulamasının konumunu belirtir. |
| **Bir sayfa açmayın. Dış uygulamadan gelen bir isteği bekle** | Bir dış uygulamadan bir istek beklendiğini diyor. Bu seçenek, Internet Explorer 'ı veya başka bir uygulamayı başlatamaz. Yalnızca bir uygulama tarafından çağrıldığında hata ayıklama için hazırlar. |
| **Sunucu** | Kullanılacak sunucu ile ilgili seçenekleri gruplandıran başlık. |
| **Varsayılan Web sunucusunu kullan** | Varsayılan Web sunucusunu kullanacağınızı diyor. |
| **Özel sunucu kullan** | Sunucu olarak kullanılacak temel URL 'YI girmenize olanak sağlar. |
| **Hata ayıklayıcıları** | Yapılacak hata ayıklama türüyle ilgili seçenekleri gruplandıran başlık. |
| **ASP.NET hata ayıklama** | Geliştirme platformu için yazılan sunucu sayfalarının hata ayıklamasını sağlar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . **Başlangıç URL**'SINDE bir URL belirtmeniz gerekir. |
| **Yerel kod hata ayıklaması** | Yönetilen uygulamanızdan yerel (yönetilmeyen) Win32 koduna yapılan çağrıların hatalarını ayıklamanızı sağlar. |
| **SQL Server hata ayıklama** | SQL Server veritabanı nesnelerinin hatalarını ayıklamasına izin verir. |
| **Silverlight hata ayıklaması** | Silverlight bileşenlerinde hata ayıklamasına izin verir. |

## <a name="see-also"></a>Ayrıca bkz.
- [hata ayıklayıcı Ayarlar ve hazırlığı](../debugger/debugger-settings-and-preparation.md)