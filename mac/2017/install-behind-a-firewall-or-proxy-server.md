---
title: Güvenlik duvarı veya proxy sunucusunun arkasında Mac için Visual Studio'u yükleyin ve kullanın
description: Bu belge, Mac için Visual Studio'nun (ve Xamarin dahil iş yüklerinin) kurumsal bir ortamda çalışmasına izin vermek için güvenlik duvarınızda izin verilmesi gereken ana bilgisayarların bir listesini sağlar.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: 738c5277ca6a669a834635f5c626e0cbabd7a7ef
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984942"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Güvenlik duvarı veya proxy sunucusunun arkasında Mac için Visual Studio'u yükleyin ve kullanın

Siz veya kuruluşunuz güvenlik duvarı veya proxy sunucusu gibi güvenlik önlemleri kullanıyorsa, yükleme ve kullandığınızda en iyi deneyimi yaşamanız için "izin verme listesine" eklemek isteyebileceğiniz etki alanları ve açmak isteyebileceğiniz bağlantı noktaları ve protokoller vardır Mac ve Azure Hizmetleri için Visual Studio.

- [**Mac için Visual Studio'yu Yükleyin**](#install-visual-studio-for-mac): Bu tablolar, Mac için Visual Studio'nun tüm özelliklerine ve iş yüklerine erişebilmeniz için bağlantıya izin vermesi gereken etki alanlarını içerir.

- [**Mac için Visual Studio'yu kullanın**](#use-visual-studio-for-mac): Bu tablolar, ilgili özelliklere erişebilmeniz için bağlantıya izin vermesi gereken etki alanlarını içerir.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

Mac Installer için Visual Studio çeşitli etki alanlarından ve indirme sunucularından indirdiği için, yapılandırmalarınıza güvenilen olarak eklemek isteyebileceğiniz etki alanları ve URL'ler aşağıda verebilirsiniz.

### <a name="microsoft-domains"></a>Microsoft etki alanları

| Domain| Amaç |
| ----------------------------------- |---------------------------|
| *.live.com| Kimlik Bilgisi Yönetimi |
| app.vssps.visualstudio.com| Yükleyici Meta verileri|
| vortex.data.microsoft.com | Kilitlenme ve Hata Raporlama |
| az667904.vo.msecnd.net| Kilitlenme ve Hata Raporlama |
| xamarin.com | Yükleyici Meta verileri|
| xampubdl.blob.core.windows.net| Yükleyici Paketleri|
| download.visualstudio.microsoft.com | Yükleyici Paketleri|
| xamarin.azureedge.net | Yükleyici Paketleri|
| developer.xamarin.com | Yükleyici Paketleri|
| dc.services.visualstudio.com| Kilitlenme Raporlama |

### <a name="third-party-domains"></a>Üçüncü taraf etki alanları

| Domain| Amaç |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple Güvenlik Hizmetleri |

## <a name="use-visual-studio-for-mac"></a>Mac için Visual Studio'u kullanma

Proxy veya güvenlik duvarının arkasındayken Mac için Visual Studio'da ihtiyacınız olan her özelliğe erişebildiğinizden emin olmak için, izin verilenler listesine aşağıdaki etki alanlarını ve bağlantı noktalarını eklemenizi öneririz.

### <a name="general"></a>Genel

| Domain | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL Çözümü |
| vsstartpage.blob.core.windows.net| 80/443| Sayfa Verilerini Başlat|
| software.xamarin.com |  80/443|Güncelleyici Servisi|
| addins.monodevelop.com | 80/443| Uzatma Hizmetleri |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Deneysel Özellik ve Bildirimler |
| targetednotifications.azurewebsites.net|  80/443| Yalnızca belirli makine türleri/kullanım senaryoları için geçerli olan bir listeye bildirimlerin genel listesini filtrelemek için kullanılır|

### <a name="identity"></a>Kimlik

| Domain | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Kimlik Sağlayıcı|
| secure.aadcdn.microsoftonline-p.com | 80/443|Kimlik Sağlayıcı|
| dc.services.visualstudio.com| 80/443|Kilitlenme Raporlama|
| management.azure.com|80/443| Azure Hizmetleri API'si |

### <a name="nuget"></a>NuGet

| Domain | Bağlantı noktaları|Amaç|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| Kimlik Sağlayıcı|

### <a name="android-projects"></a>Android projeleri

| Domain| Amaç|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emülatör için Zaman Sunucusu |
| connectivitycheck.gstatic.com | Android Emülatör için bağlantı|
| cloudconfig.googleapis.com| Android Emülatör için API'ler|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017 ve Azure Hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasına yükleyin ve kullanın](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Windows'daki benzer sorunları giderme](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
