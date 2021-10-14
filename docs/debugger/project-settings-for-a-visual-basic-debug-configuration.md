---
title: Project Ayarlar VB hata ayıklama yapılandırması için | Microsoft Docs
description: Uygulamanın Özellik Sayfaları penceresinde bir Visual Basic hata ayıklama yapılandırmasının proje ayarlarını Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b4177def9d8a73af775ca9f462d04c6f112259b2
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970093"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları
Hata Ayıklama ve Sürüm Yapılandırmaları 'da ele alınarak Özellik Sayfaları penceresinde bir hata ayıklama yapılandırması [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [için proje ayarlarını değiştirebilirsiniz.](../debugger/how-to-set-debug-and-release-configurations.md)  Aşağıdaki tablolarda, Özellik Sayfaları penceresinde hata ayıklayıcıyla ilgili ayarların **nerede bulunamaz olduğu** gösterilir.

> [!WARNING]
> Bu konu UWP uygulamaları için geçerli değildir. Bkz. [Hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

### <a name="debug-tab"></a>Hata ayıklama sekmesi

| Ayar | Açıklama |
|------------------------------| - |
| **Yapılandırma** | Uygulamayı derlemek için modu ayarlar. Etkin **(Hata Ayıklama) , Hata** **Ayıklama,** Sürüm, **Tüm Yapılandırmalar** **arasında seçim.** |
| **Başlatma Eylemi** | Bu denetim grubu, Hata Ayıklama menüsünden Başlat'ı seçen eylemi belirtir.<br /><br /> -   **Başlangıç projesi** varsayılandır ve hata ayıklama için başlangıç projesini başlatıyor. <br />-   **Dış programı başlat,** bir projenin parçası olan bir programı başlatmanız ve bağlamanız için olanak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sağlar. Daha fazla bilgi için [bkz. Çalışan İşlemlere Ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)<br />-   **URL'de tarayıcıyı başlat,** bir Web uygulamasında hata ayıklamaya olanak sağlar. |
| **Komut Satırı Bağımsız Değişkenleri** | Hata ayıklanır programın komut satırı bağımsız değişkenlerini belirtir. Komut adı, Dış programı başlat içinde belirtilen program adıdır. Başlatma Eylemi Başlangıç URL'si olarak ayarlanırsa, komut satırı bağımsız değişkenleri yoksayılır. |
| **Çalışma Dizini** | Hata ayıklaması yapılan programın çalışma dizinini belirtir. içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] çalışma dizini, uygulamanın başlat olduğu dizindir. Varsayılan çalışma dizini, geçerli yapılandırmaya bağlı olarak \bin\Debug veya \bin\Release dizinidir. |
| **Uzak Makine Kullanma** | Onay kutusu seçildiğinde uzaktan hata ayıklama etkinleştirilir. Metin kutusuna uygulamanın hata ayıklama amacıyla çalıştıracak olduğu uzak makinenin adını veya [Msvsmon sunucu adını yazabilirsiniz.](../debugger/remote-debugging.md) EXE'nin uzak makinede konumu, Derleme sekmesindeki Çıkış Yolu özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır. |
| **Unmanaged code debugging** | Yönetilen uygulamanıza gelen yerel (yönetilemeyen) Win32 koduna yapılan çağrılarda hata ayıklamanıza olanak sağlar. Bu, bir projede Hata Ayıklayıcı Türü için Karışık'ı seçmekle aynı etkiye [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] sahiptir. |
| **SQL Server ayıklama** | Veritabanı nesnelerinin hata SQL Server izin verir. |

### <a name="compile-tab-press-advanced-compile-options-button"></a>Derle sekmesi: Gelişmiş Derleme Seçenekleri düğmesine basın

| Ayar | Açıklama |
|---------------------------| - |
| **İyileştirmeleri etkinleştirme** | Bu seçeneğin işaretlenmemiş olması gerekir. İyileştirme aslında yürütülen kodun içinde görülen kaynak koddan farklı olmasına neden olur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve bu nedenle hata ayıklamayı zorlaştırabilir. Kod en iyi duruma getirilmişse, hata ayıklama sırasında semboller varsayılan olarak Yalnızca kendi kodum. |
| **Hata ayıklama bilgileri oluşturma** | Hem hata ayıklama hem de yayın sürümlerinde varsayılan olarak tanımlanan bu ayar (/debug derleyici seçeneğine eşdeğerdir) derleme zamanında hata ayıklama bilgileri oluşturur. Hata ayıklayıcı, hata ayıklarken değişken adlarını ve diğer bilgileri yararlı bir şekilde göstermek için bu bilgileri kullanır. Programınızı bu bilgiler olmadan derlersanız hata ayıklayıcısı işlevselliği sınırlı olacaktır. Daha fazla bilgi için bkz. [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **DEBUG Sabiti Tanımlama** | Bu sembolün tanımlanması, Hata Ayıklama sınıfından çıkış işlevlerinin koşullu [olarak derlemeye olanak sağlar.](/dotnet/api/system.diagnostics.debug) Bu simge tanımlandığı zaman, Hata ayıklama sınıfı yöntemleri Çıktı penceresine [çıkış oluşturur.](../ide/reference/output-window.md) Bu sembol olmadan Hata ayıklama sınıfı yöntemleri derlanmaz ve hiçbir çıkış oluşturulmaz. Bu simge Hata Ayıklama sürümünde tanımlanmalıdır ve Yayın sürümünde tanımlanmamıştır. Yayın sürümünde bu simgeyi tanımlamak, programınızı yavaşlatan gereksiz kod oluşturur. |
| **TRACE Sabiti Tanımlama** | Bu sembolün tanımlanması, Trace sınıfından çıkış işlevlerinin koşullu olarak [derlemeye olanak sağlar.](/dotnet/api/system.diagnostics.trace) Bu simge tanımlandığı zaman, Trace sınıfı yöntemleri Çıktı penceresine [çıkış oluşturur.](../ide/reference/output-window.md) Bu sembol olmadan, İzleme sınıfı yöntemleri derlanmaz ve hiçbir İzleme çıkışı oluşturulmaz. Bu simge hem Hata Ayıklama hem de Yayın sürümleri için varsayılan olarak tanımlanır. |

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarlar Hazırlama](../debugger/debugger-settings-and-preparation.md)