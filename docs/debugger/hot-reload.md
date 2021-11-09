---
title: Kod yazmak ve hata ayıklamak için Çalışırken Yeniden Yükleme
description: Çalışırken Yeniden Yükleme ve devam ederken olduğu gibi, uygulamaları çalıştırarak kodunuz üzerinde değişiklik yapabilirsiniz
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
ms.openlocfilehash: 7ac42fe3706034c1b527ab45f89ca2c9a8092275
ms.sourcegitcommit: ac681e983f3b217c3fd9d2a31e3a3ddcc4dd3546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "132041939"
---
# <a name="write-and-debug-running-code-with-hot-reload-in-visual-studio-c-c-visual-basic"></a>Visual Studio 'de Çalışırken Yeniden Yükleme ile kod yazma ve hata ayıklama (C#, C++, Visual Basic)

2022'Visual Studio başlayarak, Çalışırken Yeniden Yükleme'daki Visual Studio deneyimi hem yönetilen .NET hem de yerel C++ uygulamaları için çalışır. Üzerinde çalıştığınız uygulamanın türü ne olursa olsun, Çalışırken Yeniden Yükleme'ın amacı düzenlemeler arasında mümkün olduğunca çok uygulama yeniden başlatma işlemi kaydetmenizi sağlamaktır. Böylece, uygulamaların yeniden oluşturmasını, yeniden başlatmasını, uygulamanın içinde bulunduğu önceki konuma yeniden gezinmeyi beklerken harcadığınız zamanı azaltarak daha üretken bir hale gelirsiniz.

Bunu, uygulamanın kod dosyalarını düzenlemenizi ve kod değişikliklerini çalışan uygulamaya hemen uygulamanıza (uygulama adı da bilinir) mümkün hale *Çalışırken Yeniden Yükleme.* Değişiklikleriniz uygulandıktan sonra, uygulamanın kendisinde bir eylem gerçekleştirerek (veya bir tür zamanlayıcı aracılığıyla vb.) kodunuzu yeniden yürütün ve değişiklikleri hemen bakın; kesme noktaları aracılığıyla uygulama duraklatma gerekmez!

## <a name="update-running-code-with-hot-reload"></a>Çalışan kodu Çalışırken Yeniden Yükleme

1. Desteklenen bir uygulama türüne göre bir proje açın. .NET hakkında daha fazla bilgi için bkz. [.NET uygulama desteği.](#supported-net-app-frameworks-and-scenarios)

1. Hata ayıklayıcısı **ayarlarında veya hata ayıklama** başlatma profilinde Yerel kod hata ayıklamayı etkinleştir'in devre dışı bırakıldı olduğundan emin olun.

1. Uygulamayı F5 kullanarak veya uygulamanız için destekliyorsa **Ctrl+F5** kullanarak hata ayıklayıcısı eklenmiş olarak başlatabilirsiniz.  [](#supported-net-app-frameworks-and-scenarios)

1. Bir C#, C++ veya Visual Basic kod dosyasını, çalışan uygulamalar kullanıcı arabirimi (örneğin, bir düğmenin veya viewmodel komutunun ardındaki kod) ya da zamanlayıcı aracılığıyla bir aralıkta tetiklenen bir kodla yeniden yürütülerek kodu değiştirebilirsiniz.

1. Çalışırken Yeniden Yükleme düğmesini kullanarak **kod değişikliklerini** uygulama veya **ALT+F10 tuşlarına basın.**

   ![Çalışırken Yeniden Yükleme ekran görüntüsü.](../debugger/media/vs-2022/dotnet-hot-reload.gif)

## <a name="supported-net-app-frameworks-and-scenarios"></a>Desteklenen .NET uygulama çerçeveleri ve senaryoları

* **Visual Studio 2022** kullanırken ve hata ayıklayıcı ile uygulamanıza başlarken, temel Çalışırken Yeniden Yükleme deneyimi çoğu .NET uygulaması ve çerçeve sürümü türüyle çalışır. Bu destek .NET Framework, .NET Core ve .NET 5+ (hem C# hem de Visual Basic için) içerir. Desteklenen uygulamaların türü web (arka planında kod değişiklikleri), masaüstü, mobil, bulut ve diğer proje türleridir. Bu senaryoda beklenti, hata ayıklayıcıyı kullanıyorsanız, Çalışırken Yeniden Yükleme olduğunu varsayalım ve bunu deneyin!
* **Visual Studio 2022** kullanırken ancak hata ayıklayıcıyı kullanmazken (örneğin, uygulamayı başlatmak için CTRL-F5 kullanarak) Çalışırken Yeniden Yükleme.NET 6 uygulamalarının çoğu türü hedeflese bile kullanılabilir. Bu, .NET 6'ı (.NET 5 veya altı) hedeflemeen uygulamaların "hata ayıklayıcısı yok" senaryosunu desteklemeyecek ve hata ayıklayıcıyı kullanarak destek almak Çalışırken Yeniden Yükleme anlamına gelir.
* **.NET 6 Visual Studio 2022'de en fazla senaryo desteklene.** Bu, yukarıda bahsedilen yeni "hata ayıklayıcısı yok" özelliğiyle sınırlı değildir. Ayrıca Blazor projelerini hızlı bir şekilde yeniden yükleme ve daha genel olarak tüm ASP.NET Core uygulamaları ve CSS dosyalarını düzenleme desteği gibi yeni Çalışırken Yeniden Yükleme. Hem Visual Studio 2022 hem de .NET 6'ya yönelik uygulamaları birlikte kullanmak size en güçlü Çalışırken Yeniden Yükleme sunar.

Aşağıdaki tabloda, hata ayıklayıcı ekli (F5) ve hata ayıklayıcı ekli (Ctrl+F5) olmadan .NET Çalışırken Yeniden Yükleme'yi destekleyen uygulama türleri ve en düşük destek için .NET 6'nın gerekli olup olmadığı (yani F5) gösterir. Ctrl+F5 desteği için her zaman .NET 6 gereklidir. Ayrıca, özelliği destekleyen en Visual Studio sürümü de gösterilir.

|Uygulama türü|.NET 6 gerekli (F5)|F5|Ctrl+F5|
|-|-|-|-|
|ASP.NET kodu geriden seçin|Hayır|16.11|17.0|
|ASP.NET Razor (Blazor Server ve ASP.NET Core)|Yes|17.0|17.0|
|ASP.NET Razor (Blazor WASM)|Yes|Hayır|17.0|
|WPF|Hayır|16.11|17.0|
|WinUI3|Hayır|16.11|Hayır|
|WinForms|Hayır|16.11|17.0|
|Konsol|Hayır|16.11|17.0|
|XAML .NET MAUI WinUI|Yes|17.1 Önizleme 1|Hayır|
|XAML .NET MAUI Android|Yes|17.1 Önizleme 1|Hayır|
|iOS için XAML .NET MAUI|Yes|17.1 Önizleme 1|Hayır|
|XAML + Blazor .NET MAUI WinUI|Yes|17.1 Önizleme 1|Hayır|
|XAML + Blazor .NET MAUI Android|Yes|17.1 Önizleme 1|Hayır|
|xAML + Blazor .NET MAUI iOS|Yes|17.1 Önizleme 1|Hayır|

Bu tür düzenlemelerle Çalışırken Yeniden Yükleme, uygulamayı başlatmak için kullanılan yöntem (F5 veya Ctrl+F5) tarafından değil çalışma zamanı tarafından belirlenir.

Aşağıdaki bölümlerde, yukarıdaki özeti genişletecek ve daha fazla ayrıntıya ineceğiz.

## <a name="support-for-c-apps"></a>C++ uygulamaları desteği

Visual Studio 2022'yi kullanırken ve hata ayıklayıcı ile uygulamanıza başlarken, hata ayıklayıcı (F5) altında Çalışırken Yeniden Yükleme çalıştırıldığında yerel bir C++ uygulamasını **sık sık yeniden Çalışırken Yeniden Yükleme.** Çalışırken Yeniden Yükleme, CMake ve OpenFolder projeleri kullanılarak yerleşik uygulamalar için de de kullanılabilir.

Bu deneyim yerel Düzenle ve Devam Ile güçlendirilmiştir. Desteklenen düzenlemeler için bkz. [Düzenle ve Devam.](../debugger/edit-and-continue-visual-cpp.md)

## <a name="visual-studio-2022-with-a-net-app-when-using-the-debugger"></a>Visual Studio 2022'de bir .NET uygulamasıyla birlikte kullanın

Visual Studio 2022'yi kullanırken ve uygulamayı hata ayıklayıcısıyla başlatıyorsanız, Çalışırken Yeniden Yükleme Konsol, Windows Forms (WinForms), WPF, UWP, WinUI 3 (nota bakın ASP.NET) ve ASP.NET MVC, Web API'si ve hatta daha eski Web Forms projeleri gibi tipik uygulama türleri de dahil olmak üzere çoğu uygulama çerçevesiyle çalışır. Bunlar örnektir. .NET'e sahip ve yönetilen hata ayıklayıcısını Visual Studio her yerde temel destek Çalışırken Yeniden Yükleme gerekir. Bu durum, Azure İşlevleri gibi projelerin bile bu senaryoda harika bir şekilde çalışması anlamına gelir.

> [!NOTE]
> WinUI 3 varsayılan olarak karma mod hata ayıklaması kullanır ve bu, Çalışırken Yeniden Yükleme. Yönetilen Hata Ayıklayıcı'nın düzgün çalışmasına olanak sağlayan Yönetilen Hata Ayıklayıcı'Çalışırken Yeniden Yükleme proje ayarlarında bunu değiştirebilirsiniz.

.NET MAUI uygulamaları, 2022 Visual Studio 17.1 Önizleme 1 sürümünden itibaren de destekleni.

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

.NET Çalışırken Yeniden Yükleme deneyimi Düzenle ve Devam [Edin mekanizmasıyla güçlendirilmiştir.](../debugger/edit-and-continue-visual-csharp.md) Geliştirmeler arasında, önceki sürümlerde mümkün olanın ötesinde ek düzenleme türleri için destek Visual Studio. Geliştirmeler şunlardır:

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

## <a name="unsupported-net-scenarios"></a>Desteklenmeyen .NET senaryoları

Desteklenmeyen senaryolar:

* Xamarin.Forms uygulamaları, iOS ve Android Çalışırken Yeniden Yükleme .NET uygulamalarını desteklemez. UWP uygulamasını hedeflerken Çalışırken Yeniden Yükleme kısmi destek elde edin. Bu, tasarıma göredir ve başka geliştirmeler de görmeyi bekleyeceğiz. (Not: XAML Çalışırken Yeniden Yükleme, en son SDK'da Xamarin.Forms müşterileri için kullanılabilir ve desteklene devam edecek.)
* .NET MAUI 2022 sürüm 17.1 Önizleme 1'den önce Visual Studio uygulamaları desteklenmiyor. 17.1 Önizleme 1'den başlayarak .NET MAUI, ancak yalnızca hata ayıklayıcı ekli olarak de destekleni.
* F# veya hedef kitle kullanılarak .NET Native uygulamalar bu uygulamaları Çalışırken Yeniden Yükleme.

Hata ayıklayıcı olmadan Visual Studio kullanıyorsanız. NET Çalışırken Yeniden Yükleme yalnızca .NET 6'ya yönelik uygulamalar için çalışır.

Ayrıca, Çalışırken Yeniden Yükleme bazı proje yapılandırmalarında kullanılamaz:

* Visual Studio hata ayıklayıcısını kullanarak uygulamayı çalıştırdı ancak ayarlarda devre `Edit and Continue` dışı Çalışırken Yeniden Yükleme desteklenmiyor.
* Yayın veya özel derleme yapılandırmaları desteklenmiyor. Projenizin Hata ayıklama derleme yapılandırmasını kullanması gerekir.
* .NET'te bazı başlatma veya derleme iyileştirmeleri Çalışırken Yeniden Yükleme. Örneğin, projenizin hata ayıklama profili aşağıdaki yollarla yapılandırılmışsa, .NET Çalışırken Yeniden Yükleme desteklenmiyor:
  * [Projeniz](/dotnet/core/deploying/trimming/trimming-options) için kırpma etkindir. Örneğin, hata ayıklama profili için proje dosyanız içinde `PublishTrimmed` True olarak ayarlanırsa bu destek desteklanmaz.
  * [Projeniz için ReadyToRun](/dotnet/core/deploying/ready-to-run) etkinleştirilir. Örneğin, hata ayıklama profili için proje dosyanız içinde `PublishReadyToRun` True olarak ayarlanırsa bu destek desteklanmaz.

## <a name="configure-hot-reload"></a>Yapılandırma Çalışırken Yeniden Yükleme

Açılan Çalışırken Yeniden Yükleme düğmesinden **Ayarlar** **seçerek Çalışırken Yeniden Yükleme** yapılandırabilirsiniz.

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
