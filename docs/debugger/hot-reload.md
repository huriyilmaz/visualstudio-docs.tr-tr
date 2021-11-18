---
title: Çalışırken Yeniden Yükleme kullanarak kod yazma ve hata Çalışırken Yeniden Yükleme
description: Çalışırken Yeniden Yükleme ve devam ederken olduğu gibi, uygulamaları çalışırken kodunuz üzerinde değişiklik yapma
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
ms.openlocfilehash: 6884aceaddb2133410797bb5f4e5a403badb08f7
ms.sourcegitcommit: a98fa8a8362525f67824ce52b7e71757f10f1362
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2021
ms.locfileid: "132736480"
---
# <a name="write-and-debug-running-code-with-hot-reload-in-visual-studio-c-c-visual-basic"></a>Visual Studio (C#, C++, Çalışırken Yeniden Yükleme) ile çalışan kodu yazma ve Visual Basic

2022'Visual Studio başlayarak, Çalışırken Yeniden Yükleme deneyimi Visual Studio yönetilen .NET ve yerel C++ uygulamaları için çalışır. Üzerinde çalışmakta olduğunuz uygulama türüne bakılmaksızın, Çalışırken Yeniden Yükleme'ın amacı düzenlemeler arasında mümkün olduğunca çok uygulama yeniden başlatma işlemi kaydetmenizi sağlamaktır. Böylece, uygulamaların yeniden oluşturmasını, yeniden başlatmasını, uygulamanın içinde bulunduğu önceki konuma yeniden gezinmeyi beklerken harcadığınız zamanı azaltarak daha üretken bir hale gelirsiniz.

Bunu, uygulamanın kod dosyalarını düzenlemenizi ve kod değişikliklerini çalışan uygulamaya hemen uygulamanıza (uygulama adı da bilinir) mümkün hale *Çalışırken Yeniden Yükleme.* Değişiklikleriniz uygulandıktan sonra, uygulamanın kendisinde bir eylem gerçekleştirerek (veya bir tür zamanlayıcı aracılığıyla vb.) kodunuzu yeniden yürütün ve değişiklikleri hemen bakın; kesme noktaları aracılığıyla uygulama duraklatma gerekmez!

## <a name="update-running-code-with-hot-reload"></a>Çalışan kodu Çalışırken Yeniden Yükleme

1. Desteklenen bir uygulama türüne göre bir proje açın. .NET hakkında daha fazla bilgi için bkz. [.NET uygulama desteği.](#supported-net-app-frameworks-and-scenarios)

1. Hata ayıklayıcısı **ayarlarında veya hata ayıklama** başlatma profilinde Yerel kod hata ayıklamayı etkinleştir'in devre dışı bırakıldı olduğundan emin olun.

1. Uygulamayı F5 kullanarak veya uygulamanız için destekliyorsa **Ctrl+F5** kullanarak hata ayıklayıcısı eklenmiş olarak başlatabilirsiniz.  [](#supported-net-app-frameworks-and-scenarios)

1. Bir C#, C++ veya Visual Basic kod dosyasını, çalışan uygulamalar kullanıcı arabirimi (örneğin, bir düğmenin veya viewmodel komutunun ardındaki kod) ya da zamanlayıcı aracılığıyla bir aralıkta tetiklenen bir kodla yeniden yürütülerek kodu değiştirebilirsiniz.

1. Çalışırken Yeniden Yükleme düğmesini kullanarak **kod değişikliklerini** uygulama veya **ALT+F10 tuşlarına basın.**

   ![Çalışırken Yeniden Yükleme ekran görüntüsü.](../debugger/media/vs-2022/dotnet-hot-reload.gif)

## <a name="supported-net-app-frameworks-and-scenarios"></a>Desteklenen .NET uygulama çerçeveleri ve senaryoları

* **Visual Studio 2022** kullanırken ve hata ayıklayıcı ile uygulamanıza başlarken, temel Çalışırken Yeniden Yükleme deneyimi çoğu .NET uygulaması ve çerçeve sürümü türüyle çalışır. Bu destek .NET Framework, .NET Core ve .NET 5+ (hem C# hem de Visual Basic için) içerir. Desteklenen uygulamaların türü web (arka planı değişiklikleri), masaüstü, mobil, bulut ve diğer proje türleridir. Bu senaryoda beklenti şudur: Hata ayıklayıcıyı kullanıyorsanız, Çalışırken Yeniden Yükleme olduğunu varsayalım ve bunu deneyin!
* **Visual Studio 2022** kullanırken ancak hata ayıklayıcıyı kullanmazken (örneğin, uygulamayı başlatmak için CTRL-F5 kullanarak) Çalışırken Yeniden Yükleme çoğu .NET 6 uygulamasını hedeflese bile kullanılabilir. Bu, .NET 6'ya (.NET 5 veya altı) hedef almayan uygulamaların "hata ayıklayıcısı yok" senaryosunu desteklemeyecek ve hata ayıklayıcıyı kullanarak destek almak Çalışırken Yeniden Yükleme gelir.
* **.NET 6 Visual Studio 2022 kullanılırken en çok senaryolar de destekleni.** Bu, yukarıda bahsedilen yeni "hata ayıklayıcısı yok" özelliğiyle sınırlı değildir. Ayrıca Blazor projelerini hızlı bir şekilde yeniden yükleme ve daha genel olarak tüm ASP.NET Core uygulamaları ve CSS dosyalarını düzenleme desteği gibi diğer yeni özellikleri Çalışırken Yeniden Yükleme. Hem Visual Studio 2022 hem de .NET 6'ya yönelik uygulamaları birlikte kullanmak size en güçlü Çalışırken Yeniden Yükleme sunar.

Aşağıdaki tabloda, hata ayıklayıcı ekli (F5) ve hata ayıklayıcı ekli (Ctrl+F5) olmadan .NET Çalışırken Yeniden Yükleme'yi destekleyen uygulama türleri ve en düşük destek için .NET 6'nın gerekli olup olmadığı (yani F5) gösterir. Ctrl+F5 desteği için her zaman .NET 6 gereklidir. Ayrıca, özelliği destekleyen Visual Studio sürümü de gösterilir.

|Uygulama türü|.NET 6 gerekli (F5)|F5|Ctrl+F5|
|-|-|-|-|
|ASP.NET kodu geriden seçin|No|16.11|17.0|
|ASP.NET Razor (Blazor Server ve ASP.NET Core)|Yes|17.0|17.0|
|ASP.NET Razor (Blazor WASM)|Yes|Hayır|17.0|
|WPF|No|16.11|17.0|
|WinUI3|No|16.11|No|
|WinForms|No|16.11|17.0|
|Konsol|No|16.11|17.0|
|XAML .NET MAUI WinUI|Yes|17.1 Önizleme 1|No|
|XAML .NET MAUI Android|Yes|17.1 Önizleme 1|No|
|iOS için XAML .NET MAUI|Yes|17.1 Önizleme 1|No|
|XAML + Blazor .NET MAUI WinUI|Yes|17.1 Önizleme 1|No|
|XAML + Blazor .NET MAUI Android|Yes|17.1 Önizleme 1|No|
|xAML + Blazor .NET MAUI iOS|Yes|17.1 Önizleme 1|No|

Bu tür düzenlemelerle Çalışırken Yeniden Yükleme, uygulamayı başlatmak için kullanılan yöntem (F5 veya Ctrl+F5) tarafından değil çalışma zamanı tarafından belirlenir.

Aşağıdaki bölümlerde, yukarıdaki özeti genişletecek ve daha fazla ayrıntıya ineceğiz.

## <a name="support-for-c-apps"></a>C++ uygulamaları desteği

Visual Studio 2022'yi kullanırken ve hata ayıklayıcı ile uygulamanıza başlarken, hata ayıklayıcı (F5) altında Çalışırken Yeniden Yükleme **çalıştırabilirsiniz.** Çalışırken Yeniden Yükleme, CMake ve OpenFolder projeleri kullanılarak yerleşik uygulamalar için de de kullanılabilir.

Bu deneyim yerel Düzenle ve Devam Ile güçlendirilmiştir. Desteklenen düzenlemeler için bkz. Düzenle [ve Devam.](../debugger/edit-and-continue-visual-cpp.md)

## <a name="visual-studio-2022-with-a-net-app-when-using-the-debugger"></a>Visual Studio kullanırken bir .NET uygulamasıyla 2022'ye devam edin

Visual Studio 2022'yi kullanırken ve uygulamayı hata ayıklayıcısıyla başlatıyorsanız, Çalışırken Yeniden Yükleme Konsol, Windows Forms (WinForms), WPF, UWP, WinUI 3 (nota bakın) ve ASP.NET MVC, Web API'si ve hatta daha eski gibi çoğu ASP.NET web projesi türü (arka planı düzenlemeleri için) gibi çoğu uygulama çerçevesiyle çalışır Web Forms projeleri. Bunlar örnektir. .NET'e sahip ve yönetilen hata ayıklayıcısını Visual Studio her yerde temel destek Çalışırken Yeniden Yükleme gerekir. Bu durum, Azure İşlevleri gibi projelerin bile harika bir şekilde çalışması anlamına gelir.

> [!NOTE]
> WinUI 3 varsayılan olarak karma mod hata ayıklaması kullanır ve bu, Çalışırken Yeniden Yükleme. Yönetilen Hata Ayıklayıcı'nın düzgün çalışmasına olanak sağlayan Yönetilen Hata Ayıklayıcı'Çalışırken Yeniden Yükleme proje ayarlarında bunu değiştirebilirsiniz.

.NET MAUI uygulamaları, 2022 Visual Studio 17.1 Önizleme 1 sürümünden başlayarak de destekler.

## <a name="visual-studio-2022-with-a-net-app-but-not-using-the-debugger"></a>bir .net uygulaması ile 2022 Visual Studio, ancak hata ayıklayıcıyı kullanmıyor

konsol, WPF, Windows Forms (WinForms), ASP.NET Core MVC, Web apı ve Blazor gibi proje türleri de dahil olmak üzere çoğu .net 6 uygulaması hedeflenirken, dinamik yeniden yükleme, hata ayıklayıcı olmadan kullanılabilir.

Bu özellik .NET 6 + ' a özeldir. .NET 6 ' yı (.NET 5 veya altı) hedeflemenin olmadığı uygulamalar "hata ayıklayıcı yok" senaryosunu desteklemezler ve sık yükleme işlevselliğine erişim sağlamak için hata ayıklayıcıyı kullanmalıdır.

Ayrıca, şu anda tüm proje türlerinin "hata ayıklayıcı yok" senaryosunu desteklemediğini unutmayın. Özellikle:

* UWP uygulamaları, hata ayıklayıcı olmadan dinamik yeniden yükleme için desteklenmez. Bu tasarıma göre yapılır ve bunu geliştirmek için geçerli bir plan yoktur.
* İOS ve Android 'i hedefleyen Xamarin. Forms uygulamaları .NET Hot Reload 'i desteklemez (uygulamanızı hata ayıklayıcı ile başlatıp başlatamadığına bakılmaksızın), ancak XAML sık yükleme 'yi desteklemeye devam edecektir.
* .NET MAUı uygulamaları desteklenmez.

## <a name="visual-studio-2022-with-a-net-6-app"></a>.net 6 uygulamasıyla Visual Studio 2022

hem Visual Studio 2022 hem de .net 6 ' yı hedefleyen uygulamalarda çalışıyorsanız, en parlak ve yetenekli yeniden yükleme deneyiminin avantajlarını elde edersiniz.

Bu senaryoda desteklenir:

* Blazor uygulamaları (sunucu ve WebAssembly (bkz. Note))
* Blazor ve normal ASP.NET Core web sitelerinde Razor dosyalarını düzenlemeyle
* CSS etkin yeniden yükleme
* Hata ayıklayıcı olmadan uygulama çalıştırırken sık yeniden yükleme desteği (daha önce daha ayrıntılı olarak açıklandığı gibi)

.net 6 ' yı hedefliyorsanız yakında Visual Studio 2022 güncelleştirmelerinde ve .net özellik bantındaki ana sürümlerde geliştirmeler almaya devam edersiniz.

> [!NOTE]
> Visual Studio 2022 ' de, Visual Studio hata ayıklayıcı şu anda etkin olmadığında Blazor webassembly için sık yeniden yükleme desteği şu anda etkin değildir. uygulamanızı hata ayıklayıcı olmadan Visual Studio ile başlatırsanız, hala etkin yeniden yükleme yapabilirsiniz.

## <a name="supported-aspnet-core-scenarios"></a>desteklenen ASP.NET Core senaryoları

temel sık yükleme deneyimi birçok ASP.NET senaryo için desteklenir. En yaygın olarak kullanılabilecek özellik, çoğu Web uygulaması türü için arka plan kod ve diğer .NET sınıfı dosyalarını değiştirme olanağıdır. bu özellik Visual Studio hata ayıklayıcı kullanılırken çalışarak, her yerde düzenle ve devam et daha önce mevcut.

.net 6 ' yı hedefleyen ASP.NET Core geliştiriciler için, daha düşük .net sürümleri için kullanılamayan ek yetenekler vardır. Bu özellikler şunları içerir:

* **Cshtml:** Razor CSHTML dosyasını düzenleme çok sayıda düzenleme türünü destekler.
* **Tarayıcı yenileme:** Bir Razor dosyası düzenlendiğinde, hata ayıklarken Web tarayıcınızdaki değişiklikler otomatik olarak yenilenir. Bu özellik daha önce yalnızca hata ayıklayıcı olmadan uygulama başlatılırken kullanılabilir.
* **CSS etkin yeniden yükleme:** Uygulama çalışırken CSS dosyalarını değiştirebilirsiniz ve değişiklikler siz yazarken çalışan uygulamaya hemen uygulanır.
* **Hata ayıklayıcı yok:** web uygulamanızı hata ayıklayıcı olmadan başlatmak için Visual Studio kullanırken etkin yeniden yükleme desteği alırsınız (CTRL-F5).

> [!NOTE]
> Blazor bir uygulama üzerinde çalışırken ve Visual Studio 2022 kullanırken, Razor Pages için sık yükleme, şu anda yalnızca hata ayıklayıcı olmadan uygulama başlatırken çalışır.

## <a name="supported-net-edits"></a>Desteklenen .NET düzenlemeleri

.NET Hot Reload yeniden yükleme deneyimi [Düzenle ve devam et](../debugger/edit-and-continue-visual-csharp.md) mekanizmasıyla desteklenir. Geliştirmeler, Visual Studio eski sürümlerinde ilk olarak mümkün olan diğer düzenleme türleri için destek içerir. Geliştirmeler şunları içerir:

* Özel öznitelikleri ekleme, güncelleştirme veya silme
* Kayıt yapıları ekleme veya güncelleştirme
* #Line yönergeleri ekleme veya güncelleştirme
* Anahtar ifadeleri düzenleniyor
* Yönergedeki değişiklikler dahil olmak üzere #line yönergeleriyle dosyaları düzenlemeyle
* Üst düzey deyimleri Düzenle
* Genel using yönergeleri, dosya kapsamlı ad alanları, geliştirilmiş Lambdalar ve parametre-Less struct oluşturucuları gibi yeni C# 10 özelliklerinden herhangi birini kullanan kodu düzenlemeyle
* Lambda parametrelerini yeniden adlandırma
* Mevcut yöntemlerin parametrelerini yeniden adlandırma

Önceki geliştirmeler, hem dinamik yeniden yükleme hem de Düzenle ve devam et deneyimlerinde kullanılabilir.

## <a name="unsupported-net-scenarios"></a>Desteklenmeyen .NET senaryoları

Desteklenmeyen senaryolar:

* Xamarin. Forms uygulamaları iOS ve Android senaryolarında .NET Hot Reload 'i desteklemez. UWP uygulamasını hedeflerken, sık yeniden yükleme için kısmi destek alabilirsiniz. Bu tasarıma göre yapılır ve başka geliştirmeler yapmak zorunda kalmazsınız. (Note: XAML etkin yeniden yüklemesi, en son SDK 'daki Xamarin. Forms müşterileri için kullanılabilir ve desteklenmeye devam edecektir.)
* .net mauı uygulamaları Visual Studio 2022 sürüm 17,1 Preview 1 ' den önce desteklenmez. 17,1 Preview 1 ' den başlayarak, .NET MAUı desteklenir, ancak yalnızca hata ayıklayıcı eklenmiş olur.
* F # veya .NET Native hedefleme kullanılarak oluşturulan uygulamalar, sık yeniden yüklemeyi desteklemez.

hata ayıklayıcı olmadan Visual Studio kullanıyorsanız. NET Hot Reload yalnızca .NET 6 ' yı hedefleyen uygulamalar için çalışır.

Ayrıca, sık yeniden yükleme bazı proje yapılandırmalarında kullanılamaz:

* uygulamanızı çalıştırmak için Visual Studio hata ayıklayıcı kullanıyorsanız, ancak ayarlarda devre dışı bırakıldıysa `Edit and Continue` , sık yeniden yükleme desteklenmez.
* Yayın veya özel derleme konfigürasyonları desteklenmez. Projenizin hata ayıklama yapı yapılandırmasını kullanması gerekir.
* Bazı başlatma veya derleme iyileştirmeleri .NET Hot Reload 'te desteklenmez. Örneğin, projenizin hata ayıklama profili aşağıdaki yollarla yapılandırılırsa, .NET Hot Reload desteklenmez:
  * Projeniz için [kırpma](/dotnet/core/deploying/trimming/trimming-options) etkin. Örneğin, `PublishTrimmed` hata ayıklama profili için proje dosyanızda true olarak ayarlanırsa bu desteklenmez.
  * [Readytorun](/dotnet/core/deploying/ready-to-run) , projeniz için etkinleştirildi. Örneğin, `PublishReadyToRun` hata ayıklama profili için proje dosyanızda true olarak ayarlanırsa bu desteklenmez.
* WinUI 3 uygulamaları için yerel kod hata ayıklaması varsayılan olarak etkindir (ayar *Launchsettings. JSON*' dan olmasa bile) ve karışık mod hata ayıklaması bu şekilde yapıldığında .net Hot Reload desteklenmez. Bu nedenle, `nativeDebugging: false` .net Hot Reload 'in düzgün çalışmasını sağlamak Için *launchsettings. JSON* ' a açık ayarı eklemeniz gerekir.

## <a name="configure-hot-reload"></a>Dinamik yeniden yüklemeyi yapılandırma

dinamik **yeniden yükleme açılan düğmesinden** **Ayarlar** seçerek, sık yeniden yükleme yapılandırabilirsiniz.

![Dinamik yeniden yükleme yapılandırması ekran görüntüsü](../debugger/media/vs-2022/dotnet-hot-reload-configure.png)

Ya da,   >    >    >  **.NET/C++ Hot Reload** hata ayıklama araçları seçeneklerini açın.

Dinamik yeniden yükleme ayarları şunlardır:

* **Dinamik yeniden yükleme ve düzenleme ve hata ayıklama sırasında devam et 'ı etkinleştirin**. Hata ayıklayıcı ekli (F5) ile Başlarken sık yeniden yükleme etkinleştirilir.

* **Hata ayıklama olmadan Başlarken etkin yeniden yüklemeyi etkinleştirin**. Hata ayıklayıcı ekli olmadan Başlarken sık yeniden yükleme etkinleştirilir (CTRL + F5).

* **Dosya kaydetme üzerine sık yeniden yükleme Uygula**. Dosyayı kaydettiğinizde kod değişikliklerini uygular.

![.NET Hot reload için ayarların ekran görüntüsü](../debugger/media/vs-2022/dotnet-hot-reload-settings.png)

## <a name="warning-message"></a>Uyarı iletisi

Aşağıdaki iletişim kutusunu görürseniz, etkin yeniden yükleme, geçerli düzenlemeleri yeniden başlatmaya gerek kalmadan uygulayamaz. Uygulamayı yeniden oluşturmayı ve değişiklikleri uygulamayı (yeniden başlatmayı) seçebilir ya da düzenlemesine devam edebilirsiniz. Yeniden oluşturursanız, tüm uygulama durumu kaybedilir. Düzenlenmesine devam ederseniz, ek değişiklikler veya düzeltmeler, sık yeniden yükleme işleminin yeniden çalışmasına neden olabilir.

![Değişiklikleri Uygula iletişim kutusunun ekran görüntüsü](../debugger/media/vs-2022/dotnet-hot-reload-apply-changes.png)

iletişim kutusunda **her zaman yeniden oluştur** seçeneğini belirlerseniz, iletişim kutusunu geçerli Visual Studio oturumunda tekrar görmezsiniz ve Visual Studio iletişim kutusunu göstermek yerine otomatik olarak yeniden oluşturulur ve yeniden yüklenir.

> [!NOTE]
> Şu anda, hata ayıklayıcı ile sık yeniden yükleme kullanılırken standart Düzenle ve devam et iletişim kutusu gösterilir.

## <a name="see-also"></a>Ayrıca bkz.

[Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md) 
 [Düzenle ve devam et (C++)](../debugger/edit-and-continue-visual-cpp.md)
