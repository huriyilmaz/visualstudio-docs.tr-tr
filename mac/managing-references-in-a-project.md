---
title: Projedeki başvuruları yönetme
description: Bu makalede, Mac için Visual Studio projedeki başvuruların nasıl yönetileceği açıklanmaktadır
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 28ea53826a19a9ec97349060702cf13c68342ad2
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939004"
---
# <a name="managing-references-in-a-project"></a>Projedeki başvuruları yönetme

Mac için Visual Studio projenize ek başvurular eklemenin iki yolu sağlar:

![Proje Başvuruları](media/projects-and-solutions-image10.png)

Bunlar:

* Başvurular
* Nual (Paketler klasörü aracılığıyla eklenir)

Ayrıca, Web başvuruları ve yerel başvurular da herhangi bir projeye eklenebilir.

## <a name="assembly-references"></a>Bütünleştirilmiş kod başvuruları

Xamarin içindeki her bir çerçeve bir düzine Derlemeleriyle birlikte gönderilir. Tüm bu derleme paketlerine, varsayılan olarak projenizde başvurulmaz.

Projenizde başvurulan paketleri düzenlemek için, başvurular klasörüne çift tıklayarak veya bağlam menüsü eylemlerinde **başvuruları Düzenle** ' yi seçerek, **başvuruları Düzenle** iletişim kutusunu kullanın:

![Derleme başvuruları iletişim kutusu](media/projects-and-solutions-image11.png)

Her Xamarin çerçevesi için kullanılabilen derlemeler hakkında bilgi için [kullanılabilir derlemeler](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) kılavuzuna bakın.

## <a name="nuget"></a>NuGet

NuGet, .NET geliştirme için en popüler paket yöneticisidir. Mac için Visual Studio NuGet desteği projenize eklenecek paketleri aramanızı sağlar.

Bunu yapmak için Çözüm Bölmesi **paket** klasörüne sağ tıklayın ve paket Ekle ' yi seçin.

NuGet paketi kullanma hakkında daha fazla bilgi için, projenizin Gözden geçirmedeki [bir NuGet paketi de dahil](nuget-walkthrough.md) edilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuruları yönetme (Windows üzerinde Visual Studio)](/visualstudio/ide/managing-references-in-a-project)
- [Bir uzantı SDK 'sına karşı başvuruları ekleme (Windows üzerinde Visual Studio)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)