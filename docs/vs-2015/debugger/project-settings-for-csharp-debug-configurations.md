---
title: C# hata ayıklama yapılandırması için proje ayarları | Microsoft Docs
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
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687525"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# Hata Ayıklama Yapılandırması Proje Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir C# hata ayıklama yapılandırması için proje ayarlarını, [hata ayıklama ve sürüm yapılandırmalarında](../debugger/how-to-set-debug-and-release-configurations.md)anlatıldığı gibi **Özellik sayfaları** penceresinde değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** penceresinde hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.  
  
> [!WARNING]
> Bu konu, Windows Mağazası uygulamaları için geçerlidir. Bkz. [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> Hata ayıklama sekmesi  
  
|**Ayar**|**Açıklama**|  
|-----------------|---------------------|  
|**Yapılandırma**|Uygulamayı derlemek için modu ayarlar. **Etkin (hata ayıklama)**, **hata ayıklama**, **yayın**, **Tüm yapılandırmaların**arasından seçim yapın.|  
|**Başlatma eylemi**|Bu denetim grubu, hata ayıklama menüsünden Başlat ' ı seçtiğinizde gerçekleştirilecek eylemi belirtir.<br /><br /> -   **Projeyi Başlat** varsayılandır ve başlangıç projesini hata ayıklama için başlatır. Daha fazla bilgi için bkz. [Başlangıç Projesi seçme](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Dış programı Başlat** , bir projenin parçası olmayan bir programı başlatıp eklemenize olanak sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [çalışan bir programa ekleme](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **URL 'de tarayıcıyı Başlat** bir Web uygulamasında hata ayıklamanıza olanak sağlar.|  
|**Komut satırı bağımsız değişkenleri**|Hata Ayıklanacak programın komut satırı bağımsız değişkenlerini belirtir. Komut adı, dış program Başlat bölümünde belirtilen program adıdır. Başlat eylemi başlangıç URL 'SI olarak ayarlandıysa, komut satırı bağımsız değişkenleri belirtilemez.|  
|**Çalışma dizini**|Hata ayıklanan programın çalışma dizinini belirtir. [!INCLUDE[csprcs](../includes/csprcs-md.md)]' De, çalışma dizini, uygulamanın varsayılan olarak \bin\debug 'dan başlatıldığı dizindir.|  
|**Uzak makineyi kullan**|Uygulamanın hata ayıklama amacıyla çalışacağı uzak makinenin adı veya bir [msvsmon sunucu adı](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Uzak makinedeki EXE konumu, yapılandırma özellikleri klasöründeki çıkış yolu özelliği tarafından belirtilir, derleme kategorisi. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır.|  
|**Yönetilmeyen kod hata ayıklamayı etkinleştir**|Yönetilen uygulamanızdan yerel (yönetilmeyen) Win32 koduna yapılan çağrıların hatalarını ayıklamanızı sağlar.|  
|**SQL Server hata ayıklamayı etkinleştir**|SQL Server veritabanı nesnelerinin hatalarını ayıklamasına izin verir.|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> Derleme sekmesi  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Koşullu derleme sembolleri:**|Hata ayıklama ve Izleme sabitleri burada tanımlanmıştır.<br /><br /> Bu sabitler, [hata ayıklama sınıfının](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) ve [izleme sınıfının](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx)koşullu derlemesini etkinleştirir. Bu sabitler tanımlı, hata ayıklama ve Izleme sınıfı yöntemleri [Çıkış penceresinde](../ide/reference/output-window.md)çıkış oluşturur. Bu sabitler olmadan hata ayıklama ve Izleme sınıfı yöntemleri derlenmez ve hiçbir çıkış oluşturulmaz.<br /><br /> -Hata ayıklama normalde bir programın hata ayıklama sürümünde tanımlanır ve yayın sürümünde tanımlanmamıştır.<br />-Trace normalde hata ayıklama ve yayın sürümlerinde tanımlanır.|  
|**Kodu iyileştirme**|Yalnızca iyileştirilmiş kodda görüntülenen bir hata bulmadığınız takdirde, bu ayarı hata ayıklama sürümünde devre dışı bırakmalısınız. Yönergeler doğrudan kaynak ortamınızdaki deyimlere karşılık gelmediğinden, iyileştirilmiş kod hata ayıklamayı zorlaştırır.|  
|**Çıkış yolu:**|Hata ayıklama için genellikle bin\Debug olarak ayarlanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
