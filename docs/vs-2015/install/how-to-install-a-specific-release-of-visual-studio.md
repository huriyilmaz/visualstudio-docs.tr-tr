---
title: 'Nasıl yapılır: belirli bir yayını yüklerken | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814565"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Nasıl Yapılır: Visual Studio’nun Belirli Bir Sürümünü Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İsteğe bağlı özelliklerimizin en güncel ve en iyi duruma getirilmiş sürümünü alabilmeniz için Visual Studio kurulumunu sık sık güncelleştiririz.  Ancak, Visual Studio 2015 ' in önceki bir sürümünü yüklemek istiyorsanız — Örneğin, iOS desteğiyle Visual Studio 'nun güncelleştirme öncesi 1 sürümü — daha sonra, Visual Studio kurulumunu kendi Özellik bildirim dosyalarının önceki bir sürümünü kullanacak şekilde zorlamanız gerekir. Bu makalede bunun nasıl yapılacağı açıklanmaktadır.

## <a name="installing-the-current-release"></a>Geçerli yayın yükleniyor
 Visual Studio 2015 ' nin ilk sürümünden itibaren, kurulum altyapısını ve bildirim dosyalarını birkaç kez güncelleştirdik.  Bu, web yükleyicisini temiz, internet 'e bağlı bir makinede [Visual Studio İndirmeleri](https://www.visualstudio.com/downloads/download-visual-studio-vs) Web sitesinden indirdiğinizde, kurulum en son ürün iyileştirmelerinin yanı sıra isteğe bağlı özellikler ve araçların yeni, son sürümlerini de içeren en son visual Studio 2015 güncelleştirmesini yükler.

## <a name="installing-earlier-releases"></a>Önceki sürümleri yükleme
 Visual Studio 'Nun nasıl yüklendiğini denetlemek için bir ISO görüntüsü oluşturabilir ve bağlayabilirsiniz ya da yükleyiciyi doğrudan [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) adresinden yükleyebilir ve sonra ek komut satırı parametreleriyle (/Customınstallpath,/Full,/InstallSelectableItems,/norestart, vb.) ekleyebilirsiniz.

 Aşağıdaki tabloda bazı belirli bir zaman noktası senaryosu ve Enterprise Edition yükleyicisine geçirmeniz gereken komut satırı parametreleri yer almaktadır. (Aynı parametreler topluluk veya profesyonel sürüm yükleyicilerle de birlikte çalışacaktır.)

|Visual Studio 2015 sürümü|Çalışmak için gerekenler|Kullanılacak komut satırı|Kurulum ne yapar|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (en son genel sürüm)|Güncelleştirmeler ile Visual Studio Enterprise (   [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)adresinden ulaşılabilir)|`vs_enterprise.exe`**Note:**  Bu yüklemenin varsayılan davranışı en son isteğe bağlı özellikleri sunar ve bu nedenle herhangi bir komut satırı parametresi gerektirmez.|Visual Studio Kurulumu en son feed.xml kullanır ve en son dosyaları yükler|
|Visual Studio Enterprise güncelleştirme 3 (daha fazla güncelleştirme 3-dönem güncelleştirmesi olmadan özgün güncelleştirme 3)|Visual Studio Enterprise RTM ( [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Visual Studio Kurulumu, güncelleştirme 3 ' te kullanıma sunulduğunda kullanılabilir feed.xml kullanacaktır|
|Güncelleştirme 2 Visual Studio Enterprise (özgün güncelleştirme 2, ancak tarih güncelleştirme 3 ' te güncelleştirmeler ile)|Visual Studio Enterprise RTM ( [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Visual Studio Kurulumu, güncelleştirme 3 ' ün yayınlanmadan önce geçerli olan feed.xml kullanacaktır|
|Visual Studio Enterprise (özgün güncelleştirme 2 ' ye daha fazla güncelleştirme 2-Era güncelleştirmesi olmadan)|Visual Studio Enterprise RTM ( [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Güncelleştirme 2 ' de yayınlandığında, Visual Studio Kurulumu kullanılabilir feed.xml kullanacaktır|
|Visual Studio Enterprise güncelleştirme 1 (özgün güncelleştirme 1, ancak önceki tarih güncelleştirme 2 ' ye sahip güncelleştirmeler ile)|Visual Studio Enterprise RTM ( [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Visual Studio Kurulumu, güncelleştirme 2 yayınlanmadan önce geçerli olan feed.xml kullanacaktır|
|Visual Studio Enterprise güncelleştirme 1 (daha fazla güncelleştirme 1-dönem güncelleştirmesi olmadan özgün güncelleştirme 1)|Visual Studio Enterprise RTM ( [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio Kurulumu, güncelleştirme 1 ' i kullanıma sunulduğunda kullanılabilir feed.xml kullanacaktır|
|Visual Studio Enterprise (orijinal RTM, ancak tarih güncelleştirme 1 ' i güncelleştirme ile)|Visual Studio Enterprise RTM (  [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio Kurulumu, güncelleştirme 1 ' den önce geçerli olan feed.xml kullanacaktır|
|Visual Studio Enterprise (güncelleştirme olmayan orijinal RTM)|Visual Studio Enterprise RTM ( [MSDN abonelikleri indirme sayfasından](https://msdn.microsoft.com/subscriptions/downloads/)ulaşılabilir)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio Kurulumu, RTM yayınlanmışsa kullanılabilir feed.xml kullanacaktır|

> [!IMPORTANT]
> Kullanmak istediğiniz dile bağlı olarak, lütfen "trk" (Ingilizce için) değerini aşağıdaki değerlerden biriyle değiştirin:
>
> - CHS (Çince (Basitleştirilmiş) için)
>   - cht (Çince (Geleneksel) için)
>   - CSY (Çekçe için)
>   - DEU (Almanca için)
>   - ESN (Ispanyolca için)
>   - FRA (Fransızca için)
>   - ITA (Italyanca)
>   - JPA (Japonca için)
>   - kor (Korece için)
>   - PLK (Lehçe için)
>   - PTB (Portekizce için)
>   - Rus (Rusça için)
>   - TRK (Türkçe için)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)