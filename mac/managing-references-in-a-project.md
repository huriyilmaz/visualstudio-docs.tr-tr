---
title: Project başvuruları yönetme
description: bu makalede, Mac için Visual Studio projedeki başvuruların nasıl yönetileceği açıklanmaktadır
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/09/2020
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 4977fcf4947db8838e8a6e4e4ba573121efba93e
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804829"
---
# <a name="managing-references-in-a-project"></a>Project başvuruları yönetme

Mac için Visual Studio projenize ek başvurular eklemenin iki yolu sağlar:

![Proje Başvuruları](media/projects-and-solutions-image10.png)

Bunlar:

* Başvurular
* NuGet paketleri (paketler klasörü aracılığıyla eklenir)

Ayrıca, Web başvuruları ve yerel başvurular da herhangi bir projeye eklenebilir.

## <a name="assembly-references"></a>Bütünleştirilmiş kod başvuruları

Xamarin içindeki her bir çerçeve bir düzine Derlemeleriyle birlikte gönderilir. Tüm bu derleme paketlerine, varsayılan olarak projenizde başvurulmaz.

Projenizde başvurulan paketleri düzenlemek için, başvurular klasörüne çift tıklayarak veya bağlam menüsü eylemlerinde **başvuruları Düzenle** ' yi seçerek, **başvuruları Düzenle** iletişim kutusunu kullanın:

![Derleme başvuruları iletişim kutusu](media/projects-and-solutions-image11.png)

Her Xamarin çerçevesi için kullanılabilen derlemeler hakkında bilgi için [kullanılabilir derlemeler](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) kılavuzuna bakın.

## <a name="nuget"></a>NuGet

NuGet, .net geliştirme için en popüler paket yöneticisidir. Mac için Visual Studio NuGet desteği projenize eklenecek paketleri aramanıza olanak tanır.

Bunu yapmak için, çözüm penceresinde **paket** klasörüne sağ tıklayın ve paket Ekle ' yi seçin.

NuGet paketi kullanma hakkında daha fazla bilgi Project gözden geçirmede [bir NuGet paketi dahil](nuget-walkthrough.md) edilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [başvuruları yönetme (Windows Visual Studio)](/visualstudio/ide/managing-references-in-a-project)
- [NuGet ve uzantı SDK 'sı (Windows Visual Studio) kullanarak başvuru ekleme](/visualstudio/extensibility/nuget-versus-sdk-references)
