---
title: Web projeleri için özellik sayfaları ayarları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cb7cd3f8c3678d37feb2267f68ab5d2b3d970e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150849"
---
# <a name="property-pages-settings-for-web-projects"></a>Web Projeleri Özellik Sayfası Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web sitesi hata ayıklama yapılandırması için özellik ayarlarını, [hata ayıklama ve sürüm yapılandırmalarında](../debugger/how-to-set-debug-and-release-configurations.md)anlatıldığı gibi **Özellik sayfaları** iletişim kutusunda değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** iletişim kutusunda hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Yapılandırma özellikleri klasörü (başlangıç seçenekleri kategorisi)  
  
|**Ayar**|**Açıklama**|  
|-----------------|---------------------|  
|**Başlatma eylemi**|Uygulama başlatma ile ilgili seçenekleri gruplandıran başlık.|  
|**Geçerli sayfayı kullan**|Hata ayıklama için başlangıç noktası olarak geçerli sayfayı belirtir.|  
|**Belirli sayfa:**|Hata ayıklamaya başlamak istediğiniz Web sayfasını belirtir.|  
|**Dış programı Başlat:**|Hata ayıklamak istediğiniz programı başlatma komutunu belirtir.|  
|**Komut satırı bağımsız değişkenleri:**|Yukarıda belirtilen komut için bağımsız değişkenleri belirtir.|  
|**Çalışma dizini:**|Hata ayıklanan programın çalışma dizinini belirtir. ' De [!INCLUDE[csprcs](../includes/csprcs-md.md)] , çalışma dizini uygulamanın başlatıldığı dizindir, varsayılan olarak, \bin\Debug ' dır.|  
|**Başlangıç URL 'SI**|Hata ayıklamak istediğiniz Web uygulamasının konumunu belirtir.|  
|**Bir sayfa açmayın. Dış uygulamadan gelen bir isteği bekle**|Bir dış uygulamadan bir istek beklendiğini diyor. Bu seçenek, Internet Explorer 'ı veya başka bir uygulamayı başlatamaz. Yalnızca bir uygulama tarafından çağrıldığında hata ayıklama için hazırlar.|  
|**Sunucu**|Kullanılacak sunucu ile ilgili seçenekleri gruplandıran başlık.|  
|**Varsayılan Web sunucusunu kullan**|Varsayılan Web sunucusunu kullanacağınızı diyor.|  
|**Özel sunucu kullan**|Sunucu olarak kullanılacak temel URL 'YI girmenize olanak sağlar.|  
|**Hata ayıklayıcıları**|Yapılacak hata ayıklama türüyle ilgili seçenekleri gruplandıran başlık.|  
|**ASP.NET hata ayıklama**|Geliştirme platformu için yazılan sunucu sayfalarının hata ayıklamasını sağlar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . **Başlangıç URL**'SINDE bir URL belirtmeniz gerekir.|  
|**Yerel kod hata ayıklaması**|Yönetilen uygulamanızdan yerel (yönetilmeyen) Win32 koduna yapılan çağrıların hatalarını ayıklamanızı sağlar.|  
|**SQL Server hata ayıklama**|SQL Server veritabanı nesnelerinin hatalarını ayıklamasına izin verir.|  
|**Silverlight hata ayıklaması**|Silverlight bileşenlerinde hata ayıklamasına izin verir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
