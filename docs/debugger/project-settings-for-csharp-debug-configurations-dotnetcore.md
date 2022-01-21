---
title: .net C# hata ayıklama yapılandırması için Project Ayarlar | Microsoft Docs
description: proje özellik sayfalarının hata ayıklama sekmesini ve Build sekmesini kullanarak bir C# .net 5 + veya .net Core hata ayıklama Visual Studio yapılandırması için proje ayarlarını nasıl değiştirileceğini anlayın.
ms.date: 01/13/2022
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C# .NET Core
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2022'
ms.workload:
- dotnet
ms.openlocfilehash: 0efe8836d44f45af8e119eba865fd014977680cf
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137610036"
---
# <a name="project-settings-for-c-debug-configurations-net-5-net-core-and-aspnet-core"></a>C# hata ayıklama yapılandırmalarına yönelik Project ayarları (.net 5 +, .net Core ve ASP.NET Core)

C# proje hata ayıklama ayarlarını proje özellik sayfalarının [hata ayıklama sekmesinde](#debug-tab) ve [derleme sekmesinde](#build-tab) değiştirebilirsiniz.

Özellik sayfalarını açmak için **Çözüm Gezgini** içinde projeyi seçin ve ardından **Özellikler** simgesini seçin ya da projeye sağ tıklayıp **Özellikler**' i seçin.

Daha fazla bilgi için bkz. [hata ayıklama ve yayın yapılandırması](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>bu ayarlar .NET Framework veya UWP uygulamalarına uygulanmaz. .NET Framework için hata ayıklama ayarlarını yapılandırmak için, bkz. [C# hata ayıklama yapılandırması Project ayarları](../debugger/project-settings-for-csharp-debug-configurations.md).

## <a name="debug-tab"></a>Hata ayıklama sekmesi

Visual Studio 2022 ' den başlayarak, hata ayıklama sekmesinden hata ayıklama **başlatma profilleri kullanıcı arabirimini aç** ' ı seçin ve ardından profil başlatma kullanıcı arabirimini açın ve debug ayarlarını değiştirin.

## <a name="launch-profile-net-5-net-core"></a>Profili Başlat (.NET 5 +, .NET Core)

|Ayar|Açıklama|
|-------------------------------------| - |
|**Komut satırı bağımsız değişkenleri** | Hata ayıklamakta olan uygulama için komut satırı bağımsız değişkenlerini belirtir. Komut adı, **dış program Başlat** bölümünde belirtilen uygulama adıdır. |
|**Çalışma dizini** | Hata ayıklanan uygulamanın çalışma dizinini belirtir. C# ' de, çalışma dizini varsayılan olarak *\Bin\Debug* ' dır. |
|**Uzak makineyi kullan**|Uzaktan hata ayıklama için, bu seçeneği belirleyin ve uzaktan hata ayıklama hedefinin adını veya bir [msvsmon sunucu adını](../debugger/remote-debugging.md)girin. <br />Uzak makinedeki bir uygulamanın konumu, **derleme** sekmesindeki **çıkış yolu** özelliği tarafından belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır. |
|**Ortam değişkenleri**|Uygulama işlemini çalıştırmadan önce ortam değişkenlerini ayarlar. ASP.NET Core için bkz. [ortamlar](/aspnet/core/fundamentals/environments#environments-1).|
|**Yönetilmeyen kod hata ayıklamayı etkinleştir** | Hata ayıklama GS, yönetilen uygulamadan yerel (yönetilmeyen) Win32 koduna çağrı yapılır. |
|**SQL Server hata ayıklamayı etkinleştir** | veritabanı nesnelerini SQL Server hata ayıklama ekler. |
|**WebView2 hata ayıklamayı etkinleştir**| Microsoft Edge (Chromium) tabanlı hata ayıklayıcı ile hata ayıklaması için JavaScript.|

## <a name="launch-profile-aspnet-core"></a>Profili Başlat (ASP.NET Core)

.net özelliklerine ek olarak, ASP.NET Core başlatma profilleri farklı ASP.NET Core profillerinin çeşitli ek özelliklerini içerir. Bu ayarlar, projenin *Launchsettings. JSON* dosyası için basit bir kullanıcı arabirimi sağlar. Bu dosya hakkında daha fazla bilgi için, [ASP.NET Core çoklu ortamları kullanma](/aspnet/core/fundamentals/environments)konusundaki geliştirme ve launchsettings. JSON bölümüne bakın.

Başlatma profilleri kullanıcı arabiriminde belirtilen ayarlar şunlardır.

|Ayar|Açıklama|
|-------------------------------------| - |
|**Tarayıcıyı Başlat**|Hata ayıklamayı başlattığınızda, **URL** AYARıNDA ayarladığınız URL 'yi kullanarak varsayılan tarayıcıyı başlatıp başlatmeyeceğinizi seçin.|
|**'Deki**|.NET veya .NET Core için ana bilgisayar URL 'sinin konumunu belirtir. projeden sonra adlı bir profil için (yani, *launchsettings. json* içindeki commandName özelliği *Project*), Kestrel sunucusu belirtilen bağlantı noktasını dinler. Bir IIS profili için bu, genellikle **Uygulama URL 'siyle** aynı değerdir. Daha fazla bilgi için, [projeyi yapılandırma](/aspnet/core/host-and-deploy/iis/development-time-iis-support#configure-the-project)altındaki IIS başlatma profili bölümüne bakın.|
|**Uygulama URL'si**|Uygulama URL 'lerini belirtir. Projeden sonra adlandırılmış bir profil için, bu özellik genellikle ve, Kestrel sunucu URL 'Lerini belirtir https://localhost:5001http://localhost:5000|

Visual Studio, varsayılan olarak bir IIS Express profili sağlar ve ııs profili gibi ek profiller de oluşturabilirsiniz. Bu ayarlar, *launchsettings. JSON* içindeki ayarlara de karşılık gelir. Bu iki profil türü, barındırma modeli gibi çeşitli ayarlar sağlar.

|Ayar|Açıklama|
|-------------------------------------| - |
|**Barındırma modeli**|Işlem (varsayılan) veya Işlem dışı olarak belirtin. daha fazla bilgi için bkz. ASP.NET Core docs 'ta [barındırma modelleri](/aspnet/core/host-and-deploy/aspnet-core-module#hosting-models) .|
|**Uygulama SSL URL 'SI**|IIS Express için, **uygulama SSL URL 'si** genellikle olur http://localhost:44334 .|

## <a name="build-tab"></a>Derleme sekmesi

|Ayar|Açıklama|
|-------------|-----------------|
|**Genel**  >  **Koşullu derleme sembolleri**|Seçilirse hata ayıklama ve Izleme sabitlerini tanımlayın.<br /><br /> Bu sabitler, [hata ayıklama sınıfının](/dotnet/api/system.diagnostics.debug) ve [izleme sınıfının](/dotnet/api/system.diagnostics.trace)koşullu derlemesini etkinleştirir. Bu sabitler tanımlı, hata ayıklama ve Izleme sınıfı yöntemleri [Çıkış penceresinde](../ide/reference/output-window.md)çıkış oluşturur. Bu sabitler olmadan hata ayıklama ve Izleme sınıfı yöntemleri derlenmez ve hiçbir çıkış oluşturulmaz.<br /><br />Genellikle, hata ayıklama bir yapılandırmanın hata ayıklama sürümünde tanımlanır ve yayın sürümünde tanımlanmamıştır. TRACE, hem hata ayıklama hem de sürüm sürümlerinde tanımlanmıştır.|
|**Genel**  >  **Kodu iyileştirme**|Bir hata yalnızca iyileştirilmiş kodda görüntülenmediği takdirde, hata ayıklama derlemeleri için bu ayarı seçimden ayrılın. İyileştirilmiş kodun hata ayıklaması zordur, çünkü yönergeler doğrudan kaynak kodundaki deyimlere karşılık gelmez.|
|**Hata ayıklama sembolleri**|Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Bkz. [hata ayıklama sembolleri](#debug-symbols). Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).|
|**Çıkış**  >  **Taban çıkış yolu**|Ara çıkış için temel klasörü belirtir. Çıktı genellikle hata ayıklama derlemesi için *bin\Debug* 'e gider.|
|**Çıkış**  >  **Taban ara çıkış yolu**|Ara çıkış için temel klasörü belirtir. Çıktı genellikle bir hata ayıklama derlemesi için *Obj\debug* öğesine gider.|

## <a name="debug-symbols"></a>Hata ayıklama sembolleri

Hata ayıklama sembolleri için aşağıdaki seçenekleri belirleyebilirsiniz.

- **Hiçbir sembol yayınlanmadı**

   Hata ayıklama bilgilerinin üretilmeyecek olduğunu belirtir.

- **PDB dosyası, geçerli platform**

   Bir oluşturur. Başka araçlar, özellikle hata ayıklayıcılar, ana yürütülebilir dosyada olanlar ve nasıl üretildiği hakkında bilgiler sağlayan, platforma özgü bir sembol dosyası olan PDB dosyası.

- **PDB dosyası, taşınabilir**

   Bir oluşturur. PDB dosyası, başka araçlar, özellikle hata ayıklayıcılar, ana yürütülebilir dosyada bulunan ve nasıl üretildiği hakkında bilgi sağlayan, platforma özgü olmayan taşınabilir bir sembol dosyası. Daha fazla bilgi için bkz. [TAŞINABILIR pdb](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) .

- **DLL/EXE içine gömülü, platformlar arasında taşınabilir**

   Taşınabilir sembol bilgilerini derlemeye gömer. Dış değil. PDB dosyası üretildi.

Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)