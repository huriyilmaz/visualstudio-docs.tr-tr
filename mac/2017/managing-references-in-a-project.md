---
title: Project başvuruları yönetme
description: bu makalede, Mac için Visual Studio projedeki başvuruların nasıl yönetileceği açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 3dfeea15e0d9003e3ae0e46b74c844016d298595
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962243"
---
# <a name="managing-references-in-a-project"></a>Project başvuruları yönetme

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

NuGet, .net geliştirme için en popüler paket yöneticisidir. Mac için Visual Studio NuGet desteği projenize eklenecek paketleri aramanıza olanak tanır.

Bunu yapmak için Çözüm Bölmesi **paket** klasörüne sağ tıklayın ve paket Ekle ' yi seçin.

NuGet paketi kullanma hakkında daha fazla bilgi Project gözden geçirmede [bir NuGet paketi dahil](nuget-walkthrough.md) edilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [başvuruları yönetme (Windows Visual Studio)](/visualstudio/ide/managing-references-in-a-project)
- [proje başvurusu olarak SDK ile NuGet karşılaştırması](/visualstudio/extensibility/nuget-versus-sdk-references)
