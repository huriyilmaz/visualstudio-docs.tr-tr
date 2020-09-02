---
title: Visual Basic hata ayıklama yapılandırması için proje ayarları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27acc89790e0759d3b284e3d9a4c6798c3d9a16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687571"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [ayıklama ve sürüm yapılandırmalarında](../debugger/how-to-set-debug-and-release-configurations.md)açıklanan şekilde, **Özellik sayfaları** penceresinde bir hata ayıklama yapılandırması için proje ayarlarını değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** penceresinde hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.  
  
> [!WARNING]
> Bu konu, Mağaza uygulamaları için geçerlidir. Bkz. [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Hata ayıklama sekmesi  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Yapılandırma**|Uygulamayı derlemek için modu ayarlar. **Etkin (hata ayıklama)**, **hata ayıklama**, **yayın**, **Tüm yapılandırmaların**arasından seçim yapın.|  
|**Başlatma eylemi**|Bu denetim grubu, hata ayıklama menüsünden Başlat ' ı seçtiğinizde gerçekleştirilecek eylemi belirtir.<br /><br /> -   **Projeyi Başlat** varsayılandır ve başlangıç projesini hata ayıklama için başlatır. Daha fazla bilgi için bkz. [nib nasıl yapılır: başlangıç projelerini ayarlama](https://msdn.microsoft.com/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Dış programı Başlat** , bir projenin parçası olmayan bir programı başlatıp eklemenize olanak sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **URL 'de tarayıcıyı Başlat** bir Web uygulamasında hata ayıklamanıza olanak sağlar.|  
|**Komut satırı bağımsız değişkenleri**|Hata Ayıklanacak programın komut satırı bağımsız değişkenlerini belirtir. Komut adı, dış program Başlat bölümünde belirtilen program adıdır. Başlat eylemi başlangıç URL 'SI olarak ayarlandıysa komut satırı bağımsız değişkenleri yok sayılır.|  
|**Çalışma dizini**|Hata ayıklanan programın çalışma dizinini belirtir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]' De, çalışma dizini, uygulamanın başlatıldığı dizindir. Geçerli yapılandırmaya bağlı olarak, varsayılan çalışma dizini \bin\Debug veya \bin\Release ' dir.|  
|**Uzak makineyi kullan**|Onay kutusu seçildiğinde, uzaktan hata ayıklama etkinleştirilir. Metin kutusunda, uygulamanın hata ayıklama amacıyla çalışacağı uzak makinenin adını veya bir [msvsmon sunucu adını](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c)yazabilirsiniz. Uzak makinedeki EXE konumu, derleme sekmesindeki çıkış yolu özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır.|  
|**Yönetilmeyen kod hata ayıklaması**|Yönetilen uygulamanızdan yerel (yönetilmeyen) Win32 koduna yapılan çağrıların hatalarını ayıklamanızı sağlar. Bu, bir projede hata ayıklayıcı türü için karışık seçme ile aynı etkiye sahiptir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] .|  
|**SQL Server hata ayıklama**|SQL Server veritabanı nesnelerinin hatalarını ayıklamasına izin verir.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Derle sekmesi: Gelişmiş derleme seçenekleri düğmesine basın  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**İyileştirmeleri etkinleştir**|Bu seçenek işaretlenmemelidir. İyileştirme, aslında yürütülen kodun içinde görülen kaynak koddan farklı olmasına neden olur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve bu nedenle hata ayıklamayı zorlaştırır. Kod iyileştirildiğinden, Yalnızca kendi kodum hata ayıklaması sırasında semboller varsayılan olarak yüklenmez.|  
|**Hata ayıklama bilgisi oluştur**|Hem hata ayıklama hem de yayın sürümlerinde varsayılan olarak tanımlanan bu ayar (/debug derleyici seçeneğine eşdeğerdir) derleme zamanında hata ayıklama bilgileri oluşturur. Hata ayıklayıcı, hata ayıklama sırasında yararlı bir biçimde değişken adlarını ve diğer bilgileri göstermek için bu bilgileri kullanır. Programınızı bu bilgi olmadan derlerseniz, hata ayıklayıcı işlevselliği sınırlı olacaktır. Daha fazla bilgi için bkz. [/Debug](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Hata ayıklama sabiti tanımla**|Bu sembolün tanımlanması, çıkış işlevlerinin [hata ayıklama sınıfından](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx)koşullu derlemesini mümkün bir şekilde sunar. Bu sembol tanımlanmış olduğunda, hata ayıklama sınıfı yöntemleri [Çıkış penceresinde](../ide/reference/output-window.md)çıkış oluşturur. Bu sembol olmadan hata ayıklama sınıfı yöntemleri derlenmez ve hiçbir çıkış oluşturulmaz. Bu simge hata ayıklama sürümünde tanımlanmalıdır ve yayın sürümünde tanımlanmamıştır. Bu sembolün bir yayın sürümünde tanımlanması, programınızı yavaşlattığı gereksiz kodu oluşturur.|  
|**Izleme sabitini tanımlama**|Bu sembolün tanımlanması, [Trace sınıfından](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx)çıkış işlevlerinin koşullu derlemesini mümkün bir şekilde sunar. Bu sembol tanımlanmış olarak, Trace class yöntemleri [Çıkış penceresinde](../ide/reference/output-window.md)çıktı oluşturur. Bu sembol olmadan, Izleme sınıfı yöntemleri derlenmez ve hiçbir Izleme çıkışı oluşturulmaz. Bu simge, hem hata ayıklama hem de yayın sürümleri için varsayılan olarak tanımlanmıştır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
