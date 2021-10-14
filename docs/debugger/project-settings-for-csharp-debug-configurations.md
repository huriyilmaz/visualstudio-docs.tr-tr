---
title: C# hata ayıklama yapılandırması için Project Ayarlar | Microsoft Docs
description: proje özellik sayfaları 'nın hata ayıklama sekmesini ve Build sekmesini kullanarak Visual Studio C# hata ayıklama yapılandırması için proje ayarlarını değiştirmeyi anlayın.
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 2f06e853ec236c979e2881b8243363964cee53b7
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971731"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# hata ayıklama yapılandırması proje ayarları

C# proje hata ayıklama ayarlarını proje özellik sayfalarının [hata ayıklama sekmesinde](#debug-tab) ve [derleme sekmesinde](#build-tab) değiştirebilirsiniz.

Özellik sayfalarını açmak için **Çözüm Gezgini** içinde projeyi seçin ve ardından **Özellikler** simgesini seçin ya da projeye sağ tıklayıp **Özellikler**' i seçin.

Daha fazla bilgi için bkz. [hata ayıklama ve yayın yapılandırması](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>bu ayarlar .net Core, ASP.NET veya UWP uygulamalarına uygulanmaz. UWP uygulamalarının hata ayıklama ayarlarını yapılandırmak için bkz. [UWP uygulaması için hata ayıklama oturumu başlatma](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Hata ayıklama sekmesi

|Ayar|Açıklama|
|-------------------------------------| - |
| **Yapılandırma** | Uygulamayı oluşturmak için modu ayarlar. Açılan listeden **etkin (hata ayıklama)**, **hata ayıklama**, **yayın** veya **Tüm yapılandırmaların** seçimini yapın. |
| **Başlatma eylemi** | Hata ayıklama yapılandırmasında **Başlat** ' ı seçtiğinizde eylemi belirtir.<br />- **Proje** varsayılan olarak başlatılır ve hata ayıklama için başlangıç projesini başlatır. Daha fazla bilgi için bkz. [Başlangıç Projesi seçme](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Dış program Başlat** ve bir projenin parçası olmayan bir uygulamaya ekler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. [hata ayıklayıcı ile çalışan Işlemlere iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **TARAYıCıYı URL Ile Başlat** bir Web uygulamasında hata ayıklamanıza olanak sağlar. |
| **Başlatma seçenekleri**  >  **Komut satırı bağımsız değişkenleri** | Hata ayıklamakta olan uygulama için komut satırı bağımsız değişkenlerini belirtir. Komut adı, **dış program Başlat** bölümünde belirtilen uygulama adıdır. |
| **Başlatma seçenekleri**  >  **Çalışma dizini** | Hata ayıklanan uygulamanın çalışma dizinini belirtir. C# ' de, çalışma dizini varsayılan olarak *\Bin\Debug* ' dır.
| **Başlatma seçenekleri**  >  **Uzak makineyi kullan**|Uzaktan hata ayıklama için, bu seçeneği belirleyin ve uzaktan hata ayıklama hedefinin adını veya bir [msvsmon sunucu adını](../debugger/remote-debugging.md)girin. <br />Uzak makinedeki bir uygulamanın konumu, **derleme** sekmesindeki **çıkış yolu** özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır.
| **Hata ayıklayıcı altyapısı**  >  **Yönetilmeyen kod hata ayıklamayı etkinleştir** | Hata ayıklama GS, yönetilen uygulamadan yerel (yönetilmeyen) Win32 koduna çağrı yapılır. |
| **Hata ayıklayıcı altyapısı**  >  **SQL Server hata ayıklamayı etkinleştir** | veritabanı nesnelerini SQL Server hata ayıklama ekler. |

## <a name="build-tab"></a>Derleme sekmesi

|Ayar|Açıklama|
|-------------|-----------------|
|**Genel**  >  **Koşullu derleme sembolleri**|Seçilirse hata ayıklama ve Izleme sabitlerini tanımlayın.<br /><br /> Bu sabitler, [hata ayıklama sınıfının](/dotnet/api/system.diagnostics.debug) ve [izleme sınıfının](/dotnet/api/system.diagnostics.trace)koşullu derlemesini etkinleştirir. Bu sabitler tanımlı, hata ayıklama ve Izleme sınıfı yöntemleri [Çıkış penceresinde](../ide/reference/output-window.md)çıkış oluşturur. Bu sabitler olmadan hata ayıklama ve Izleme sınıfı yöntemleri derlenmez ve hiçbir çıkış oluşturulmaz.<br /><br />Genellikle, hata ayıklama bir yapılandırmanın hata ayıklama sürümünde tanımlanır ve yayın sürümünde tanımlanmamıştır. TRACE, hem hata ayıklama hem de sürüm sürümlerinde tanımlanmıştır.|
|**Genel**  >  **Kodu iyileştirme**|Bir hata yalnızca iyileştirilmiş kodda görüntülenmediği takdirde, hata ayıklama derlemeleri için bu ayarı seçimden ayrılın. İyileştirilmiş kodun hata ayıklaması zordur, çünkü yönergeler doğrudan kaynak kodundaki deyimlere karşılık gelmez.|
|**Çıkış**  >  **Çıkış yolu**|Hata ayıklama için genellikle *bin\Debug* olarak ayarlanır.|
|**Gelişmiş** düğmesi|Gelişmiş hata ayıklama seçenekleri hakkında bilgi için bkz. [Gelişmiş derleme ayarları iletişim kutusu (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Sembol (*. pdb*) dosyaları için taşınabilir biçim, .NET Core uygulamaları için son platformlar arası bir biçimdir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)