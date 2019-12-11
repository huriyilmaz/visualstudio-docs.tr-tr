---
title: Projedeki başvuruları yönetme
description: Bu makalede, Mac için Visual Studio projedeki başvuruların nasıl yönetileceği açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: f9925954083c7fe64ad29c7cfed618a84d7a6386
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984866"
---
# <a name="managing-references-in-a-project"></a>Projedeki başvuruları yönetme

Mac için Visual Studio projenize ek başvurular eklemenin iki yolu sağlar:

![Proje Başvuruları](media/projects-and-solutions-image10.png)

Bunlar:

* Referanslar
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