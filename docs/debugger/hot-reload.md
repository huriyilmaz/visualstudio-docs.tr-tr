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
ms.openlocfilehash: fd616cb467d5367fd317601ecfdbacf5fc946b48
ms.sourcegitcommit: ba40c6208b2cb27d047fec4fa2c83c6be4f9ee5a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "134463514"
---
# <a name="write-and-debug-running-code-with-hot-reload-in-visual-studio-c-visual-basic-c"></a>Visual Studio çalışırken çalışan kodu yazma ve hata ayıklama (C#, Visual Basic, C++)

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

|Uygulama türü|.NET 6 gerekli|F5|Ctrl+F5|
|-|-|-|-|
|ASP.NET arka plan kodu|No|16,11|17.0|
|ASP.NET Razor (Blazor sunucusu ve ASP.NET Core)|Yes|17.0|17.0|
|ASP.NET Razor (Blazor te)|Yes|17,1|17.0|
|WPF|No|16,11|17.0|
|WinUI3|No|16,11|--|
|WinForms|No|16,11|17.0|
|Konsol|No|16,11|17.0|
|.NET MAUı (WinUI 3)|Yes|17,1|--|
|.NET MAUı (Android)|Yes|17,1|--|
|.NET MAUı (iOS)|Yes|17,1|--|
|.NET MAUı Blazor hibrit (WinUI 3)|Yes|17,1|--|
|.NET MAUı Blazor hibrit (Android)|Yes|17,1|--|
|.NET MAUı Blazor hibrit (iOS)|Yes|17,1|--|

Etkin yeniden yükleme ile yapabileceğiniz düzenleme türleri, uygulamayı başlatmak için kullandığınız yönteme göre değil, çalışma zamanına göre belirlenir (F5 veya CTRL + F5).

Aşağıdaki bölümlerde, yukarıdaki Özet üzerinde geniştireceğiz ve daha fazla ayrıntıya değineceğiz.

## <a name="support-for-c-apps"></a>C++ uygulamaları için destek

Visual Studio 2022 kullanırken ve uygulamanızı hata ayıklayıcıyla başlattığınızda, **etkin yeniden yükle** düğmesini kullanarak, hata ayıklayıcı (F5) altında çalışırken yerel C++ uygulamasını anında yeniden yükleyebilirsiniz. Etkin yeniden yükleme, CMake ve OpenFolder projeleri kullanılarak oluşturulan uygulamalar için de desteklenir.

Bu deneyim yerel Düzenle ve devam et ile desteklenir. Desteklenen düzenlemeler için bkz. [Düzenle ve devam et](../debugger/edit-and-continue-visual-cpp.md).

## <a name="visual-studio-2022-with-a-net-app-when-using-the-debugger"></a>hata ayıklayıcı kullanılırken bir .net uygulaması ile 2022 Visual Studio

Visual Studio 2022 ' i kullanırken ve uygulamayı hata ayıklayıcıyla başlattığınızda, sık yeniden yükleme, konsol, Windows Forms (WinForms), WPF, UWP, winuı 3 (bkz. note) ASP.NET ve ASP.NET MVC, web apı 'si ve hatta daha eski gibi tipik uygulama türleri dahil çoğu uygulama çerçevesi ile çalışır projeleri Web Forms. Örnekler aşağıda verilmiştir. .net kullandığınız her yerde ve Visual Studio yönetilen hata ayıklayıcı kullanıyorsanız, temel sık yükleme desteğini almanız gerekir. Bu olgu, Azure Işlevleri gibi projelerin bu senaryoda harika çalıştığı anlamına gelir.

> [!NOTE]
> WinUI 3, varsayılan olarak, dinamik yeniden yüklemeyi desteklemeyen karma mod hata ayıklamayı kullanır. Bu projeyi, dinamik yeniden yükleme 'nin düzgün çalışmasını sağlayan yönetilen hata ayıklayıcıyı etkinleştirerek proje ayarlarında değiştirebilirsiniz. Bunu projenizde etkinleştirmek için, launchSettings. json ' u değiştirin ve `"nativeDebugging": false` özelliğinden sonra ekleyin `commandName` .

.net mauı uygulamaları Visual Studio 2022 sürüm 17,1 Preview 1 ' den başlayarak desteklenir.

## <a name="visual-studio-2022-with-a-net-app-but-not-using-the-debugger"></a>bir .net uygulaması ile 2022 Visual Studio, ancak hata ayıklayıcıyı kullanmıyor

konsol, WPF, Windows Forms (WinForms), ASP.NET Core MVC, Web apı ve Blazor gibi proje türleri de dahil olmak üzere çoğu .net 6 uygulaması hedeflenirken, dinamik yeniden yükleme, hata ayıklayıcı olmadan kullanılabilir.

Bu özellik .NET 6 + ' a özeldir. .NET 6 ' yı (.NET 5 veya altı) hedeflemenin olmadığı uygulamalar "hata ayıklayıcı yok" senaryosunu desteklemezler ve sık yükleme işlevselliğine erişim sağlamak için hata ayıklayıcıyı kullanmalıdır.

Ayrıca, şu anda tüm proje türlerinin "hata ayıklayıcı yok" senaryosunu desteklemediğini unutmayın. Özellikle:

* UWP uygulamaları, hata ayıklayıcı olmadan dinamik yeniden yükleme için desteklenmez. Bu tasarıma göre yapılır ve bunu geliştirmek için geçerli bir plan yoktur.
* İOS ve Android 'i hedefleyen Xamarin. Forms uygulamaları .NET Hot Reload 'i desteklemez (uygulamanızı hata ayıklayıcı ile başlatıp başlatamadığına bakılmaksızın), ancak XAML sık yükleme 'yi desteklemeye devam edecektir.
* .NET MAUı uygulamaları yalnızca hata ayıklayıcı ile desteklenir.

## <a name="visual-studio-2022-with-a-net-6-app"></a>.net 6 uygulamasıyla Visual Studio 2022

hem Visual Studio 2022 hem de .net 6 ' yı hedefleyen uygulamalarda çalışıyorsanız, en parlak ve yetenekli yeniden yükleme deneyiminin avantajlarını elde edersiniz.

Bu senaryoda desteklenir:

* Blazor uygulamaları (sunucu ve WebAssembly (bkz. Note))
* Blazor ve normal ASP.NET Core web sitelerinde Razor dosyalarını düzenlemeyle
* CSS etkin yeniden yükleme
* Hata ayıklayıcı olmadan uygulama çalıştırırken sık yeniden yükleme desteği (daha önce daha ayrıntılı olarak açıklandığı gibi)

.net 6 ' yı hedefliyorsanız yakında Visual Studio 2022 güncelleştirmelerinde ve .net özellik bantındaki ana sürümlerde geliştirmeler almaya devam edersiniz.

> [!NOTE]
> Visual Studio 2022 ' nin ilk sürümünde (sürüm 17,0), Visual Studio hata ayıklayıcı şu anda etkin değil, ancak 17,1 ' den başlayarak kullanılabilir. uygulamanızı hata ayıklayıcı olmadan veya 17,1 sürümüne güncelleştirerek Visual Studio aracılığıyla başlatırsanız, hala etkin yeniden yükleme yapabilirsiniz.

## <a name="supported-aspnet-core-scenarios"></a>desteklenen ASP.NET Core senaryoları

temel sık yükleme deneyimi birçok ASP.NET senaryo için desteklenir. En yaygın olarak kullanılabilecek özellik, çoğu Web uygulaması türü için arka plan kod ve diğer .NET sınıfı dosyalarını değiştirme olanağıdır. bu özellik Visual Studio hata ayıklayıcı kullanılırken çalışarak, her yerde düzenle ve devam et daha önce mevcut.

.net 6 ' yı hedefleyen ASP.NET Core geliştiriciler için, daha düşük .net sürümleri için kullanılamayan ek yetenekler vardır. Bu özellikler şunları içerir:

* **Cshtml:** Razor CSHTML dosyasını düzenleme çok sayıda düzenleme türünü destekler.
* **Tarayıcı yenileme:** Bir Razor dosyası düzenlendiğinde, hata ayıklarken Web tarayıcınızdaki değişiklikler otomatik olarak yenilenir. Bu özellik daha önce yalnızca hata ayıklayıcı olmadan uygulama başlatılırken kullanılabilir.
* **CSS etkin yeniden yükleme:** Uygulama çalışırken CSS dosyalarını değiştirebilirsiniz ve değişiklikler siz yazarken çalışan uygulamaya hemen uygulanır.
* **Hata ayıklayıcı yok:** web uygulamanızı hata ayıklayıcı olmadan başlatmak için Visual Studio kullanırken etkin yeniden yükleme desteği alırsınız (CTRL-F5).

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

Ayrıca, .net 6 projelerinizi launchSetting. JSON ve ayarını olarak değiştirerek proje düzeyinde .NET Hot Reload 'ın kullanılabilir olup olmadığını kontrol edebilirsiniz `hotReloadEnabled` `false` .

Örnek:

```xaml
{
  "profiles": {
    "Console": {
      "commandName": "Project",
      "hotReloadEnabled": false
    }
  }
}
```

## <a name="warning-message"></a>Uyarı iletisi

Aşağıdaki iletişim kutusunu görürseniz, etkin yeniden yükleme, geçerli düzenlemeleri yeniden başlatmaya gerek kalmadan uygulayamaz. Uygulamayı yeniden oluşturmayı ve değişiklikleri uygulamayı (yeniden başlatmayı) seçebilir ya da düzenlemesine devam edebilirsiniz. Yeniden oluşturursanız, tüm uygulama durumu kaybedilir. Düzenlenmesine devam ederseniz, ek değişiklikler veya düzeltmeler, sık yeniden yükleme işleminin yeniden çalışmasına neden olabilir.

![Değişiklikleri Uygula iletişim kutusunun ekran görüntüsü](../debugger/media/vs-2022/dotnet-hot-reload-apply-changes.png)

iletişim kutusunda **her zaman yeniden oluştur** seçeneğini belirlerseniz, iletişim kutusunu geçerli Visual Studio oturumunda tekrar görmezsiniz ve Visual Studio iletişim kutusunu göstermek yerine otomatik olarak yeniden oluşturulur ve yeniden yüklenir.

> [!NOTE]
> Visual Studio ilk sürümünde (sürüm 17,0) standart düzenle ve devam et iletişim kutusu, hata ayıklayıcı ile sık yeniden yükleme kullanılırken gösterilmeye devam eder. Bu bir hatadır ve 17,1 Preview 2 sürümünden itibaren çözüldü.

## <a name="see-also"></a>Ayrıca bkz.

[Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md) 
 [Düzenle ve devam et (C++)](../debugger/edit-and-continue-visual-cpp.md)
