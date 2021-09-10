---
title: Derleme Eylemleri
description: Bu makalede, C# projeleri için kullanılabilecek çeşitli derleme eylemleri açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964761"
---
# <a name="build-actions"></a>Derleme eylemleri

bir Mac için Visual Studio projesindeki tüm dosyaların bir yapı eylemi vardır. Yapı eylemi, derleme sırasında dosyaya ne olacağını denetler. 

>[!NOTE]
>bu konu Mac için Visual Studio için geçerlidir. Windows Visual Studio için bkz. [derleme eylemleri](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Yapı eylemi ayarla

Mac için Visual Studio bir dosyaya yönelik derleme eylemi ayarlamak için, aşağıda gösterildiği gibi herhangi bir dosyaya sağ tıklayıp **derleme eylemine** göz atarak:

![Çözüm Gezgini 'nden derlemeyi derle eylemini seçme](media/projects-and-solutions-image1.png)

Bu dosya için derleme eylemleri, açılır menüde gösterilir. 

## <a name="build-action-values"></a>Derleme eylemi değerleri

Mac için Visual Studio oluşturabileceğiniz projeler için bazı yaygın derleme eylemleri şunlardır:

|Derleme eylemi | Project türleri | Description |
|--|--|--|
| **Se** | herhangi biri | Dosya, C# derleyicisine kaynak dosya olarak geçirilir.|
| **İçerik** | .NET, Xamarin | ASP.NET projeleri için, bu dosyalar dağıtıldığında sitenin bir parçası olarak dahil edilir. Xamarin. iOS ve Xamarin. Mac projeleri için uygulama paketi 'ne dahil edilecek.|
| **Gömülü kaynak** | .NET | Dosya, derlemeye gömülebilen bir kaynak olarak C# derleyicisine geçirilir. Ad alanından [Assembly. GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` derlemeden dosyayı okumak için kullanılabilir.|
| **Hiçbiri** | herhangi biri | Dosya, herhangi bir şekilde derleme kapsamında değildir ve IDE 'den kolay erişim için projeye dahil edilmiştir. Bu değer, örneğin "Benioku" dosyaları gibi belge dosyaları için kullanılabilir.|

> [!NOTE]
> Ek derleme eylemleri belirli proje türleri için tarafından tanımlanabilir, bu nedenle derleme eylemlerinin listesi proje türüne bağlıdır ve değerler bu listede yer alan görünebilir.  

Xamarin. iOS projeleri, dosyayı uygulama paketinin bir parçası olarak ekleyecek olan **Paketleresource** derleme eylemine sahiptir. Xamarin. Android 'e özgü derleme eylemleri hakkında bilgi, [Yapı işlemi](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) kılavuzunda bulunabilir.

Çözüm Gezgini 'nde birden fazla dosya seçmek de mümkündür ve derleme eylemini aynı anda birçok dosya olarak ayarlamanıza olanak tanır.

## <a name="see-also"></a>Ayrıca bkz.

- [derleme eylemleri (Windows Visual Studio)](/visualstudio/ide/build-actions)