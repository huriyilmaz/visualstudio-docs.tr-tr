---
title: Sık yeniden yükleme kullanarak kodu yazma ve hata ayıklama
description: Düzenle ve devam et gibi sık yeniden yükleme, uygulamaları çalıştırırken kodunuzda değişiklik yapmanıza olanak tanır
ms.date: 11/05/2021
ms.topic: conceptual
helpviewer_keywords:
- Hot reload
- .NET Hot Reload
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2022'
ms.workload:
- multiple
ms.openlocfilehash: 34d866c3f704472972d1be61863d8f586df44fe3
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132002651"
---
# <a name="write-and-debug-running-code-with-hot-reload-in-visual-studio-c-c-visual-basic"></a>Visual Studio çalışırken çalışan kodu yazma ve hata ayıklama (C#, C++, Visual Basic)

Visual Studio 2022 ' den başlayarak, Visual Studio ' deki etkin yeniden yükleme deneyimi hem yönetilen .net hem de yerel C++ uygulamaları için çalışır. Üzerinde çalıştığınız uygulamanın türü ne olursa olsun, sık yeniden yükleme işleminin amacı, düzenlemeler arasında çok sayıda uygulama yeniden başlatmasının mümkün olduğunca tasarruf etmesi ve uygulamaların yeniden oluşturulmasını, yeniden başlamasını, uygulamanın kendisinde olduğunuz önceki konuma yeniden gitmesini ve Al seçeneğini azaltarak daha üretken olmasını sağlar.

Bunu, uygulamanızın kod dosyalarını düzenlemenizi ve kod değişikliklerini, *sık yükleme* olarak da bilinen çalışan uygulamaya hemen uygulamanızı sağlamak için kullanırız. Değişiklikleriniz uygulandıktan sonra, uygulamanın kendisinde bir eylem gerçekleştirerek (ya da bazı zamanlayıcı, vb.) kodunuzu yeniden yürütün ve değişiklikleri hemen görüntüleyin; uygulamanın kesme noktaları aracılığıyla duraklatılması gerekmez!

## <a name="update-running-code-with-hot-reload"></a>Çalışan kodu çalışırken yeniden yükleme ile Güncelleştir

1. Desteklenen bir uygulama türüne göre bir proje açın. .NET hakkında daha fazla bilgi için bkz. [.NET uygulama desteği](#supported-net-app-frameworks-and-scenarios).

1. Hata ayıklama ayarları veya hata ayıklama başlatma profilinde **yerel kod hata ayıklamayı etkinleştir** ' in devre dışı bırakıldığından emin olun.

1. Uygulamayı, **F5** veya [uygulamanız için destekleniyorsa](#supported-net-app-frameworks-and-scenarios), **CTRL + F5** kullanılarak eklenmiş hata ayıklayıcı ile başlatın.

1. çalışan uygulamalar kullanıcı arabirimi (örneğin, bir düğme veya viewmodel için arka plan kodu) veya bir süre ölçer aracılığıyla tetiklenen bir işlem veya kodu değiştirme gibi bir kod ile C#, C++ veya Visual Basic kod dosyası açın.

1. **Etkin yeniden yükle** düğmesini kullanarak kod değişikliklerini uygulayın veya **alt + F10** tuşlarına basın.

   ![Hot Reload Button 'ın ekran görüntüsü.](../debugger/media/vs-2022/dotnet-hot-reload.gif)

## <a name="supported-net-app-frameworks-and-scenarios"></a>Desteklenen .NET uygulama çerçeveleri ve senaryoları

* **Visual Studio 2022 kullanırken ve uygulamanızı hata ayıklayıcıyla başlattığınızda**, temel sık yükleme deneyimi çoğu .net uygulaması ve framework sürümü ile çalışır. bu destek .NET Framework, .net Core ve .net 5 + ' u (uygun olarak C# ve Visual Basic için) içerir. Desteklenen uygulamaların türü Web (arka plan kod değişiklikleri), Masaüstü, mobil, bulut ve diğer proje türlerini içerir. Bu senaryodaki beklenki, hata ayıklayıcıyı kullanıyorsanız, etkin yeniden yükleme ' nin sizin için kullanılabilir olduğunu varsayabilir ve bir deneme sunabilirsiniz!
* **Visual Studio 2022 kullanılırken** (örneğin, uygulamayı başlatmak için CTRL-F5 ' i kullanarak), .net 6 uygulamalarının çoğu için hedefleme sırasında bile sık yeniden yükleme kullanılabilir. Bu, .NET 6 ' i (.NET 5 veya daha önceki bir sürüm) hedeflenmediği uygulamaların "hata ayıklayıcı yok" senaryosunu desteklemedikleri ve etkin yeniden yükleme desteğini almak için hata ayıklayıcıyı kullanması gerektiği anlamına gelir.
* **.net 6 uygulamasıyla Visual Studio 2022 kullanırken, çoğu senaryo desteklenir.** Bu, yukarıda bahsedilen yeni "hata ayıklayıcı yok" özelliği ile sınırlı değildir. ayrıca, dinamik yeniden yükleme Blazor projelerine yönelik destek, daha fazla genel, ASP.NET Core uygulamalarda Razor dosyalarını düzenlemeyle ve CSS hot Reload gibi diğer yeni özellikleri de içerir. hem Visual Studio 2022 hem de .net 6 ' yı hedefleyen uygulamaların kullanılması en güçlü etkin yeniden yükleme deneyimi sağlar.

Aşağıdaki tabloda, hangi uygulama türlerinin hata ayıklayıcı ekli (F5) ve hata ayıklayıcı ekli (CTRL + F5) ve .NET 6 ' nın en düşük destek (yani, F5) için gerekli olup olmadığı gösterilmektedir. .NET 6, her zaman CTRL + F5 desteği için gereklidir. ayrıca, özelliği destekleyen en düşük Visual Studio sürümüdür.

|Uygulama türü|.NET 6 gerekli (F5)|F5|Ctrl+F5|
|-|-|-|-|
|arka plan kodu ASP.NET|Hayır|16,11|17.0|
|ASP.NET Razor (Blazor sunucusu ve ASP.NET Core)|Yes|17.0|17.0|
|ASP.NET Razor (Blazor te)|Yes|Hayır|17.0|
|WPF|Hayır|16,11|17.0|
|WinUI3|Hayır|16,11|Hayır|
|WinForms|Hayır|16,11|17.0|
|Konsol|Hayır|16,11|17.0|
|XAML .NET MAUı WinUI|Yes|17,1 Preview 1|Hayır|
|XAML .NET MAUı Android|Yes|17,1 Preview 1|Hayır|
|XAML .NET MAUı iOS|Yes|17,1 Preview 1|Hayır|
|XAML + Blazor .NET MAUı WinUI|Yes|17,1 Preview 1|Hayır|
|XAML + Blazor .NET MAUı Android|Yes|17,1 Preview 1|Hayır|
|XAML + Blazor .NET MAUı iOS|Yes|17,1 Preview 1|Hayır|

Etkin yeniden yükleme ile yapabileceğiniz düzenleme türleri, uygulamayı başlatmak için kullandığınız yönteme göre değil, çalışma zamanına göre belirlenir (F5 veya CTRL + F5).

Aşağıdaki bölümlerde, yukarıdaki Özet üzerinde geniştireceğiz ve daha fazla ayrıntıya değineceğiz.

## <a name="support-for-c-apps"></a>C++ uygulamaları için destek

Visual Studio 2022 kullanırken ve uygulamanızı hata ayıklayıcıyla başlattığınızda, **etkin yeniden yükle** düğmesini kullanarak, hata ayıklayıcı (F5) altında çalışırken yerel C++ uygulamasını anında yeniden yükleyebilirsiniz. Etkin yeniden yükleme, CMake ve OpenFolder projeleri kullanılarak oluşturulan uygulamalar için de desteklenir.

Bu deneyim yerel Düzenle ve devam et ile desteklenir. Desteklenen düzenlemeler için bkz. [Düzenle ve devam et](../debugger/edit-and-continue-visual-cpp.md).

## <a name="visual-studio-2022-with-a-net-app-when-using-the-debugger"></a>hata ayıklayıcı kullanılırken bir .net uygulaması ile 2022 Visual Studio

Visual Studio 2022 kullanırken ve uygulamayı hata ayıklayıcıyla başlattığınızda, sık yeniden yükleme, konsol, Windows Forms (WinForms), WPF, UWP, winuı 3 (bkz. note) gibi tipik uygulama türleri ve ASP.NET MVC, web apı 'si ve hatta daha eski Web Forms projeler dahil olmak üzere çoğu ASP.NET web projesi türü dahil olmak üzere çoğu app framework ile çalışır. Örnekler aşağıda verilmiştir. .net kullandığınız her yerde ve Visual Studio yönetilen hata ayıklayıcı kullanıyorsanız, temel sık yükleme desteğini almanız gerekir. Bu olgu, Azure Işlevleri gibi projelerin bu senaryoda harika çalıştığı anlamına gelir.

> [!NOTE]
> WinUI 3, varsayılan olarak, dinamik yeniden yüklemeyi desteklemeyen karma mod hata ayıklamayı kullanır. Bu projeyi, dinamik yeniden yükleme 'nin düzgün çalışmasını sağlayan yönetilen hata ayıklayıcıyı etkinleştirerek proje ayarlarında değiştirebilirsiniz.

.net mauı uygulamaları Visual Studio 2022 sürüm 17,1 Preview 1 ' den başlayarak desteklenir.

## <a name="visual-studio-2022-with-a-net-app-but-not-using-the-debugger"></a>Visual Studio 2022'ye bir .NET uygulamasıyla birlikte gelir, ancak hata ayıklayıcıyı kullanmaz

Çalışırken Yeniden Yükleme Konsol, WPF, Windows Forms (WinForms), ASP.NET Core MVC, Web API ve Blazor gibi proje türleri de dahil olmak üzere çoğu .NET 6 uygulaması türü hedefleniyorken hata ayıklayıcısı olmadan kullanılabilir.

Bu özellik .NET 6+ için özeldir. .NET 6'ya (.NET 5 veya altı) hedef almayan uygulamalar "hata ayıklayıcısı yok" senaryosunu desteklemez ve hata ayıklayıcıyı kullanarak Çalışırken Yeniden Yükleme gerekir.

Ayrıca tüm proje türlerinin şu anda "hata ayıklayıcısı yok" senaryosunu desteklemey olduğunu da düşünün. Özellikle:

* Hata ayıklayıcı olmadan UWP Çalışırken Yeniden Yükleme için desteklanmaz. Bu tasarıma göredir ve bunu geliştirmek için geçerli bir plan yoktur.
* iOS ve Android'i hedef alan Xamarin.Forms uygulamaları .NET Çalışırken Yeniden Yükleme'ı desteklemez (hata ayıklayıcı ile mi yoksa hata ayıklayıcı olmadan mı başlatıyor olursanız olun) ancak bu XAML Çalışırken Yeniden Yükleme.
* .NET MAUI uygulamaları desteklenmiyor.

## <a name="visual-studio-2022-with-a-net-6-app"></a>Visual Studio .NET 6 uygulamasıyla 2022'de

Hem 2022'Visual Studio hem de .NET 6'ya yönelik uygulamalarda çalışıyorsanız, en iyi ve en iyi deneyimin avantajlarından Çalışırken Yeniden Yükleme elde edin.

Bu senaryoda desteklenenler:

* Blazor uygulamaları (Sunucu ve WebAssembly (nota bakın))
* Hem Blazor hem de normal web sitelerinde Razor ASP.NET Core düzenleme
* CSS Çalışırken Yeniden Yükleme
* Çalışırken Yeniden Yükleme ayıklayıcı olmadan uygulama çalıştırma sırasında destek sağlar (daha önce daha ayrıntılı olarak açıklandığı gibi)

.NET 6'ya yönelik hedefleriniz varsa, gelecek 2022 güncelleştirmeleri ve .NET özellik Visual Studio ve ana sürümlerde geliştirmeler almaya devam edersiniz.

> [!NOTE]
> 2022 Visual Studio de Çalışırken Yeniden Yükleme hata ayıklayıcısını kullanırken Blazor WebAssembly için Visual Studio desteği şu anda etkin değildir. Hata ayıklayıcı olmadan Çalışırken Yeniden Yükleme üzerinden başlatmanız Visual Studio yine de bu soruna yol açabilirsiniz.

## <a name="supported-aspnet-core-scenarios"></a>Desteklenen ASP.NET Core Senaryoları

Temel Çalışırken Yeniden Yükleme deneyimi birçok farklı senaryo için ASP.NET destek sunar. En yaygın olarak kullanılabilen özellik, çoğu web uygulaması türü için arka arkasındaki kodu ve diğer .NET sınıf dosyalarını değiştirebilme özelliğidir. Bu özellik, Visual Studio hata ayıklayıcısını kullanırken çalışır ve Düzenle ve Devam'ın daha önce kullanılabilir olduğu her yerde mevcuttur.

.NET 6 ASP.NET Core ı hedef alan diğer geliştiriciler için, daha düşük .NET sürümleri için sağlanmaz ek özellikler vardır. Bu özellikler şunları içerir:

* **CSHTML:** Razor CSHTML dosyasını düzenlemek birçok tür düzenlemeyi destekler.
* **Tarayıcı Yenileme:** Razor dosyası düzenlendiğinde, hata ayıklama sırasında web tarayıcınızdaki değişiklikler otomatik olarak yenilenir. Bu özellik daha önce yalnızca hata ayıklayıcı olmadan uygulama başlatıcıda kullanılabilirdi.
* **CSS Çalışırken Yeniden Yükleme:** Uygulama çalışırken CSS dosyalarını değiştirebilirsiniz ve değişiklikler siz yazarak çalışan uygulamaya hemen uygulanır.
* **Hata Ayıklayıcısı Yok:** Hata ayıklayıcısı Çalışırken Yeniden Yükleme web Visual Studio başlatmak için Visual Studio kullanırken destek alırsınız (CTRL-F5).

> [!NOTE]
> Blazor Wasm uygulaması üzerinde çalışırken ve Visual Studio 2022'Çalışırken Yeniden Yükleme razor sayfaları için Çalışırken Yeniden Yükleme şu anda yalnızca hata ayıklayıcı olmadan uygulama başlatma sırasında çalışıyor.

## <a name="supported-net-edits"></a>Desteklenen .NET Düzenlemeleri

.NET Çalışırken Yeniden Yükleme deneyimi Düzenle ve Devam [Mekanizması ile güçlendirilmiştir.](../debugger/edit-and-continue-visual-csharp.md) Geliştirmeler arasında, önceki sürümlerde mümkün olanın ötesinde ek düzenleme türleri için destek Visual Studio. Geliştirmeler şunlardır:

* Özel Öznitelik ekleme, güncelleştirme veya silme
* Kayıt yapılarını ekleme veya güncelleştirme
* #line ekleme veya güncelleştirme
* Switch ifadelerini düzenleme
* Yönergenin kendisinde #line dahil olmak üzere, dosyaları #line yönergeleriyle düzenleme
* Üst düzey deyimleri düzenleme
* Genel kullanım yönergeleri, dosya kapsamlı ad alanları, geliştirilmiş lambdalar ve parametresiz yapı oluşturucuları gibi yeni C# 10 özelliklerinden herhangi birini kullanan kodu düzenleme
* Lambda parametrelerini yeniden adı
* Mevcut yöntemlerin parametrelerini yeniden adı

Yukarıdaki geliştirmeler hem Çalışırken Yeniden Yükleme ve Devam Edin deneyimleri için kullanılabilir.

## <a name="unsupported-net-scenarios"></a>Desteklenmeyen .NET Senaryoları

Desteklenmeyen senaryolar:

* Xamarin.Forms uygulamaları, iOS ve Android Çalışırken Yeniden Yükleme .NET uygulamalarını desteklemez. UWP uygulamasını hedeflerken Çalışırken Yeniden Yükleme kısmi destek elde edin. Bu, tasarıma göredir ve başka geliştirmeler de görmeyi bekleyeceğiz. (Not: XAML Çalışırken Yeniden Yükleme sdk'da Xamarin.Forms müşterileri için kullanılabilir ve desteklene devam edecek.)
* .NET MAUI 2022 sürüm 17.1 Önizleme 1'den önce Visual Studio uygulamaları desteklenmiyor. 17.1 Preview 1'den başlayarak, .NET MAUI yalnızca hata ayıklayıcı ekli olarak de destekleni.
* F# veya hedef kitle kullanılarak .NET Native uygulamalar bu uygulamaları Çalışırken Yeniden Yükleme.

## <a name="configure-hot-reload"></a>Yapılandırma Çalışırken Yeniden Yükleme

Açılan Çalışırken Yeniden Yükleme düğmeden **Ayarlar** seçerek **Çalışırken Yeniden Yükleme** yapılandırabilirsiniz.

![Yapılandırma ekran Çalışırken Yeniden Yükleme](../debugger/media/vs-2022/dotnet-hot-reload-configure.png)

Veya   >    >    >  **.NET/C++** Hata Ayıklama Araçları Seçenekleri'Çalışırken Yeniden Yükleme.

Uygulama ayarları Çalışırken Yeniden Yükleme içerir:

* **Hata Çalışırken Yeniden Yükleme ve Düzenle ve Devam'ı etkinleştirin.** Hata Çalışırken Yeniden Yükleme (F5) ile başlayarak hata ayıklayıcıyı sağlar.

* **Hata Çalışırken Yeniden Yükleme başlatma sırasında uygulamanın ayarını etkinleştirin.** Hata Çalışırken Yeniden Yükleme ekli olmadan (Ctrl+F5) başlatma sırasında hata ayıklamayı sağlar.

* **Dosya Çalışırken Yeniden Yükleme üzerine uygulama.** Dosyayı kaydeden kod değişikliklerini uygular.

![.NET için ayarların ekran Çalışırken Yeniden Yükleme](../debugger/media/vs-2022/dotnet-hot-reload-settings.png)

## <a name="warning-message"></a>Uyarı iletisi

Aşağıdaki iletişim kutusunu görüyorsanız, Çalışırken Yeniden Yükleme yeniden başlatmadan geçerli düzenlemeleri uygulayamaz. Uygulamayı yeniden oluşturma ve değişiklikleri uygulama (yeniden başlatma) veya düzenlemeye devam etmek için seçebilirsiniz. Yeniden oluşturmanız, tüm uygulama durumu kaybolur. Düzenlemeye devam edersiniz, ek değişiklikler veya düzeltmeler yeniden çalışmaya Çalışırken Yeniden Yükleme olabilir.

![Değişiklikleri uygula iletişim kutusunun ekran görüntüsü](../debugger/media/vs-2022/dotnet-hot-reload-apply-changes.png)

İletişim kutusunda **Her** zaman yeniden oluştur seçeneğini belirtirseniz, iletişim kutusunu geçerli Visual Studio oturumunda yeniden görmeyebilirsiniz ve Visual Studio iletişim kutusunu göstermek yerine otomatik olarak yeniden oluşturulur ve yeniden yüklenir.

> [!NOTE]
> Şu anda, hata ayıklayıcısıyla birlikte standart Düzenle Çalışırken Yeniden Yükleme iletişim kutusu gösterilmektedir.

## <a name="see-also"></a>Ayrıca bkz.

[Düzenle ve Devam Ediyor (Visual C#)](../debugger/edit-and-continue-visual-csharp.md) 
 [Düzenle ve Devam Edin (C++)](../debugger/edit-and-continue-visual-cpp.md)
