---
title: Bir çalışma Project
description: Bu makalede, Mac için Visual Studio'de bir projedeki başvuruların nasıl yönet Mac için Visual Studio
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: f32a4d8ddb851524da8c24b6890a36ed7e622e30d95bb7cd2f0a7cb9d17a8454
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121421920"
---
# <a name="managing-references-in-a-project"></a>Bir çalışma Project

Mac için Visual Studio projenize ek başvurular eklemek için iki farklı kaynak sağlar:

![Proje Başvuruları](media/projects-and-solutions-image10.png)

Bunlar:

* Başvurular
* NuGet paketleri (Paketler klasörü aracılığıyla eklenir)

Ayrıca, Web Başvuruları ve yerel başvurular herhangi bir projeye de eklenebilir.

## <a name="assembly-references"></a>Derleme başvuruları

Xamarin içindeki her çerçeve, bir düzineden fazla derleme ile birlikte birlikte teslim eder. Bu derleme paketlerinin hepsi varsayılan olarak projenize başvurulamaz.

Projenize başvurulan paketleri düzenlemek için,  Başvurular klasörüne çift tıklayarak veya bağlam menüsü eylemlerinde Başvuruları Düzenle'yi seçerek gösterilen Başvuruları Düzenle iletişim kutusunu kullanın: 

![Derleme Başvuruları iletişim kutusu](media/projects-and-solutions-image11.png)

Her Xamarin çerçevesi için kullanılabilen derlemeler hakkında bilgi için Kullanılabilir [Derlemeler kılavuzuna](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) bakın.

## <a name="nuget"></a>NuGet

NuGet .NET geliştirme için en popüler paket yöneticisidir. Mac için Visual Studio'NuGet desteği, projenize eklemek istediğiniz paketleri aramanıza olanak sağlar.

Bunu yapmak için Çözüm Penceresi'nin **Paket klasörüne** sağ tıklayın ve Paket Ekle'yi seçin.

NuGet Paketi kullanma hakkında daha fazla bilgi, NuGet paketinizi dahil Project [sağlanır.](nuget-walkthrough.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuruları yönetme (Visual Studio Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Uzantı SDK'sı NuGet başvuru ekleme (Visual Studio Windows)](/visualstudio/extensibility/nuget-versus-sdk-references)
