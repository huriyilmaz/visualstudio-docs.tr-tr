---
title: Bir güvenlik duvarı veya proxy sunucusu arkasında Mac için Visual Studio yükleyip kullanma
description: Bu belge, güvenlik duvarınızda bir kurumsal ortamda çalışmak üzere Mac için Visual Studio (ve Xamarin dahil iş yükleri) izin vermek için izin verilmesi gereken ana bilgisayarların bir listesini sağlar.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 717eb9cd58f213c3d2c31a18c546a83ab8feb645
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984036"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Bir güvenlik duvarı veya proxy sunucusu arkasında Mac için Visual Studio yükleyip kullanma

Siz veya kuruluşunuz bir güvenlik duvarı veya proxy sunucusu gibi güvenlik önlemleri kullanıyorsa, bir "izin verilenler listesine" eklemek isteyebileceğiniz etki alanları vardır ve bu durumda, VI 'yi yükleyip kullandığınızda en iyi deneyimle karşılaşabilmeniz için, açmak isteyebileceğiniz bağlantı noktaları ve protokoller vardır Mac için Visual Studio ve Azure hizmetleri.

- [**Mac için Visual Studio yüklemek**](#install-visual-studio-for-mac): Bu tablolar, Mac için Visual Studio tüm özelliklerine ve iş yüklerine erişebilmek için bağlantı kurulmasına izin veren etki alanlarını içerir.

- [**Mac için Visual Studio kullan**](#use-visual-studio-for-mac): Bu tablolar, ilgili özelliklere erişebilmeniz için bağlantıya izin veren etki alanlarını içerir.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio'yu yükleyin

Mac için Visual Studio yükleyicisi çeşitli etki alanlarından indirir ve sunucuları indirdiğinden, yapılandırmalarında güvenilir olarak eklemek isteyebileceğiniz etki alanları ve URL 'Ler aşağıda verilmiştir.

### <a name="microsoft-domains"></a>Microsoft etki alanları

| Etki Alanı| Amaç |
| ----------------------------------- |---------------------------|
| *.live.com| Kimlik bilgisi yönetimi |
| app.vssps.visualstudio.com| Yükleyici meta verileri|
| vortex.data.microsoft.com | Kilitlenme ve hata raporlama |
| az667904.vo.msecnd.net| Kilitlenme ve hata raporlama |
| xamarin.com | Yükleyici meta verileri|
| xampubdl.blob.core.windows.net| Yükleyici paketleri|
| download.VisualStudio.microsoft.com | Yükleyici paketleri|
| xamarin.azureedge.net | Yükleyici paketleri|
| developer.xamarin.com | Yükleyici paketleri|
| static.xamarin.com | Yükleyici paketleri|
| DL.xamarin.com | Yükleyici paketleri|
| dc.services.visualstudio.com| Kilitlenme Raporlaması |

### <a name="third-party-domains"></a>Üçüncü taraf etki alanları

| Etki Alanı| Amaç |
| --------------------------|-------------------------|
| DL.Google.com | Android SDK |
| download.Oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple güvenlik hizmetleri |

## <a name="use-visual-studio-for-mac"></a>Mac için Visual Studio kullan

Proxy veya güvenlik duvarının arkasında Mac için Visual Studio ihtiyacınız olan her özelliğe erişiminizin olduğundan emin olmak için, izin verilen erişim listesine aşağıdaki etki alanlarını ve bağlantı noktalarını eklemeniz önerilir.

### <a name="general"></a>Genel

| Etki Alanı | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL çözümlemesi |
| vsstartpage.blob.core.windows.net| 80/443| Başlangıç sayfası verileri|
| software.xamarin.com |  80/443|Güncelleştirici hizmeti|
| addins.monodevelop.com | 80/443| Uzantı Hizmetleri |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Deneysel özellik ve bildirimler |
| targetednotifications.azurewebsites.NET|  80/443| Bildirimleri yalnızca belirli türlerini makineleri/kullanım senaryoları için uygun bir liste için genel bir listesini filtrelemek için kullanılan|

### <a name="identity"></a>Kimlik

| Etki Alanı | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Kimlik Sağlayıcı|
| secure.aadcdn.microsoftonline-p.com | 80/443|Kimlik Sağlayıcı|
| dc.services.visualstudio.com| 80/443|Kilitlenme Raporlaması|
| Management.Azure.com|80/443| Azure Hizmetleri API 'SI |

### <a name="nuget"></a>NuGet

| Etki Alanı | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| Kimlik Sağlayıcı|

### <a name="android-projects"></a>Android projeleri

| Etki Alanı| Amaç|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emulator için saat sunucusu |
| connectivitycheck.gstatic.com | Android Emulator için bağlantı|
| cloudconfig.googleapis.com| Android Emulator için API 'Ler|

## <a name="see-also"></a>Ayrıca bkz.

- [Yükleme ve bir güvenlik duvarı veya proxy sunucusunun arkasına Visual Studio ve Azure hizmetlerini kullanma](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Windows 'da benzer sorunları giderme](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
