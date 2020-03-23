---
title: Projede Başvuruları Yönetme
description: Bu makalede, Mac için Visual Studio'daki bir projedeki başvuruların nasıl yönetilen
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: a14630c5448632a939e1768040b910caf6276c2a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692911"
---
# <a name="managing-references-in-a-project"></a>Projede Başvuruları Yönetme

Mac için Visual Studio, projenize ek referanslar eklemenin iki aracını sağlar:

![Proje Başvuruları](media/projects-and-solutions-image10.png)

Bunlar:

* Başvurular
* NuGets (Paketler klasörü üzerinden eklendi)

Buna ek olarak, Web Başvuruları ve yerel başvurular da herhangi bir projeye eklenebilir.

## <a name="assembly-references"></a>Montaj başvuruları

Xamarin gemileri içinde her çerçeve bir düzine den fazla meclisleri ile. Bu derleme paketlerinin tümü varsayılan olarak projenizde başvurulmuyor.

Projenizde başvurulan paketleri düzenlemek için, Başvurular klasörüne çift tıklayarak veya bağlam menüsü eylemlerinde **Başvuruları Edit'i** seçerek görüntülenebilen **Başvuruları Edit** iletişim kutusunu kullanın:

![Derleme Başvuruları iletişim kutusu](media/projects-and-solutions-image11.png)

Her Xamarin çerçevesi için mevcut derlemeler hakkında daha fazla bilgi için [Kullanılabilir Derlemeler](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) kılavuzuna bakın.

## <a name="nuget"></a>NuGet

NuGet ,NET geliştirme için en popüler paket yöneticisidir. Mac'in NuGet desteği için Visual Studio, projenize ekleyecek paketleri aramanızı sağlar.

Bunu yapmak için, Çözüm Defteri'ndeki **Paket** klasörüne sağ tıklayın ve Paket Ekle'yi seçin.

NuGet Paketi'ni kullanma hakkında daha fazla [bilgi, Proje nizin izinin](nuget-walkthrough.md) içinde bir NuGet paketi dahil etme'de verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuruları yönetme (Windows'ta Visual Studio)](/visualstudio/ide/managing-references-in-a-project)
- [NuGet ve uzantılı SDK 'yi kullanarak referans ekleme (Windows'ta Visual Studio)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)