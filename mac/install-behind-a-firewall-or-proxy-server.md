---
title: Mac için Visual Studio bir güvenlik duvarı veya ara sunucu ile yükleyip kullanma
titleSuffix: ''
description: bu belge, güvenlik duvarınızda bir kurumsal ortamda çalışmak üzere Mac için Visual Studio (ve Xamarin dahil iş yükleri) izin vermek için izin verilmesi gereken ana bilgisayarların bir listesini sağlar.
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 25a4597c8d523b63e7ceb0cf8b5eff71af58071a
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964777"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>bir güvenlik duvarı veya proxy sunucusu arkasında Mac için Visual Studio yükleyip kullanma

siz veya kuruluşunuz bir güvenlik duvarı veya ara sunucu gibi güvenlik önlemleri kullanıyorsa, Mac için Visual Studio ve Azure hizmetlerini yükleyip kullandığınızda en iyi deneyimlere sahip olmanız için, açmak isteyebileceğiniz bir "izin verilenler listesine" ve bağlantı noktalarına ve protokollere eklemek isteyebileceğiniz etki alanları vardır.

- [**Mac için Visual Studio yüklemek**](#install-visual-studio-for-mac): bu tablolar, Mac için Visual Studio tüm özelliklerine ve iş yüklerine erişebilmek için bağlantı kurulmasına izin veren etki alanlarını içerir.

- [**Mac için Visual Studio kullan**](#use-visual-studio-for-mac): bu tablolar, ilgili özelliklere erişebilmeniz için bağlantıya izin veren etki alanlarını içerir.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

Mac için Visual Studio yükleyicisi çeşitli etki alanlarından indirir ve sunucuları indirdiğinden, yapılandırmalarında güvenilir olarak eklemek isteyebileceğiniz etki alanları ve url 'ler aşağıda verilmiştir.

### <a name="microsoft-domains"></a>Microsoft etki alanları

| Etki alanı| Amaç |
| ----------------------------------- |---------------------------|
| *.live.com| Kimlik bilgisi yönetimi |
| app.vssps.visualstudio.com| Yükleyici meta verileri|
| vortex.data.microsoft.com | Kilitlenme ve hata raporlama |
| az667904.vo.msecnd.net| Kilitlenme ve hata raporlama |
| xamarin.com | Yükleyici meta verileri|
| xampubdl.blob.core.windows.net| Yükleyici paketleri|
| download.visualstudio.microsoft.com | Yükleyici paketleri|
| xamarin.azureedge.net | Yükleyici paketleri|
| developer.xamarin.com | Yükleyici paketleri|
| static.xamarin.com | Yükleyici paketleri|
| dl.xamarin.com | Yükleyici paketleri|
| dc.services.visualstudio.com| Kilitlenme raporlaması |

### <a name="third-party-domains"></a>Üçüncü taraf etki alanları

| Etki alanı| Amaç |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple güvenlik hizmetleri |

## <a name="use-visual-studio-for-mac"></a>Mac için Visual Studio’yu kullanma

proxy veya güvenlik duvarının arkasında Mac için Visual Studio ihtiyacınız olan her özelliğe erişiminizin olduğundan emin olmak için, izin verilen erişim listesine aşağıdaki etki alanlarını ve bağlantı noktalarını eklemeniz önerilir.

### <a name="general"></a>Genel

| Etki alanı | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL çözümlemesi |
| vsstartpage.blob.core.windows.net| 80/443| Başlangıç sayfası verileri|
| software.xamarin.com |  80/443|Güncelleştirici hizmeti|
| addins.monodevelop.com | 80/443| Uzantı Hizmetleri |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Deneysel özellik ve bildirimler |
| targetednotifications.azurewebsites.net|  80/443| Yalnızca belirli makine/kullanım senaryosu türleri için geçerli olan bir listeye yönelik genel bildirim listesini filtrelemek için kullanılır|

### <a name="identity"></a>Kimlik

| Etki alanı | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Kimlik Sağlayıcı|
| secure.aadcdn.microsoftonline-p.com | 80/443|Kimlik Sağlayıcı|
| dc.services.visualstudio.com| 80/443|Kilitlenme raporlaması|
| management.azure.com|80/443| Azure Hizmetleri API 'SI |

### <a name="nuget"></a>NuGet

| Etki alanı | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| Kimlik Sağlayıcı|

### <a name="android-projects"></a>Android projeleri

| Etki alanı| Amaç|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emulator için saat sunucusu |
| connectivitycheck.gstatic.com | Android Emulator için bağlantı|
| cloudconfig.googleapis.com| Android Emulator için API 'Ler|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Windows benzer sorunları giderme](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
