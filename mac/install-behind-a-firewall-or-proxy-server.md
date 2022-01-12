---
title: Güvenlik duvarı veya Mac için Visual Studio sunucusuyla yükleme ve kullanma
titleSuffix: ''
description: Bu belge, şirket ortamında çalışma izni vermek için güvenlik duvarınıza izin Mac için Visual Studio konakların (ve Xamarin dahil olmak üzere iş yüklerinin) listesini sağlar.
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.topic: reference
ms.date: 01/10/2022
ms.openlocfilehash: 5baa1c16960e0501731d337b4f4d3112f9374cdc
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806384"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Güvenlik duvarı veya Mac için Visual Studio sunucusu arkasında yükleme ve kullanma

Siz veya kuruluşta güvenlik duvarı veya ara sunucu gibi güvenlik önlemleri kullanıyorsanız, Mac için Visual Studio ve Azure Hizmetleri'nin yükleme ve kullanma deneyimine sahip olmak için bir "izin ver listesine" eklemek istediğiniz etki alanları ve açmak istediğiniz bağlantı noktaları ve protokoller vardır.

- [**Yükleme Mac için Visual Studio:**](#install-visual-studio-for-mac)Bu tablolar, kullanıcıların tüm özelliklerine ve iş yüklerine erişiminizin olması için bağlantı izni ver Mac için Visual Studio.

- [**Şu Mac için Visual Studio**](#use-visual-studio-for-mac)kullanın: Bu tablolar, ilgili özelliklere erişiminiz olması için bağlantı izni ver gereken etki alanlarını içerir.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

Mac için Visual Studio Yükleyicisi çeşitli etki alanlarından ve indirme sunucularından indirdiği için, yapılandırmalarınıza güvenilen olarak eklemek istediğiniz etki alanları ve URL'ler burada ve ardından gelir.

### <a name="microsoft-domains"></a>Microsoft etki alanları

| Domain| Amaç |
| ----------------------------------- |---------------------------|
| *.live.com| Kimlik Bilgisi Yönetimi |
| app.vssps.visualstudio.com| Yükleyici Meta Verileri|
| nw-umwatson.events.data.microsoft.com | Kilitlenme ve Hata Raporlama | 
| vortex.data.microsoft.com | Kilitlenme ve Hata Raporlama |
| az667904.vo.msecnd.net| Kilitlenme ve Hata Raporlama |
| xamarin.com | Yükleyici Meta Verileri|
| xampubdl.blob.core.windows.net| Yükleyici Paketleri|
| download.visualstudio.microsoft.com | Yükleyici Paketleri|
| xamarin.azureedge.net | Yükleyici Paketleri|
| developer.xamarin.com | Yükleyici Paketleri|
| static.xamarin.com | Yükleyici Paketleri|
| dl.xamarin.com | Yükleyici Paketleri|
| dc.services.visualstudio.com| Kilitlenme Raporlaması |

### <a name="third-party-domains"></a>Üçüncü taraf etki alanları

| Domain| Amaç |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple Güvenlik Hizmetleri |

## <a name="use-visual-studio-for-mac"></a>Mac için Visual Studio’yu kullanma

Bir ara sunucu veya güvenlik duvarının arkasındayken Mac için Visual Studio tüm özelliklere erişiminiz olduğundan emin olmak için, izin verilen erişim listesine aşağıdaki etki alanlarını ve bağlantı noktalarını eklemenizi öneririz.

### <a name="general"></a>Genel

| Domain | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL Çözümlemesi |
| vsstartpage.blob.core.windows.net| 80/443| Başlangıç Sayfası Verileri|
| software.xamarin.com |  80/443|Güncelleştiren Hizmeti|
| addins.monodevelop.com | 80/443| Uzantı Hizmetleri |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Deneysel Özellik ve Bildirimler |
| targetednotifications.azurewebsites.net|  80/443| Bildirimlerin genel listesini yalnızca belirli makine türleri/kullanım senaryoları için geçerli olan bir listeye filtrelemek için kullanılır|

### <a name="identity"></a>Kimlik

| Domain | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Kimlik Sağlayıcı|
| secure.aadcdn.microsoftonline-p.com | 80/443|Kimlik Sağlayıcı|
| dc.services.visualstudio.com| 80/443|Kilitlenme Raporlaması|
| management.azure.com|80/443| Azure Hizmetleri API'si |

### <a name="nuget"></a>NuGet

| Domain | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| Kimlik Sağlayıcı|

### <a name="android-projects"></a>Android projeleri

| Domain| Amaç|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emulator için saat sunucusu |
| connectivitycheck.gstatic.com | Android Emulator için bağlantı|
| cloudconfig.googleapis.com| Android Emulator için API 'Ler|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Windows benzer sorunları giderme](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
