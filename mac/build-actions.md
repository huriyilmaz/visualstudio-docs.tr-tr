---
title: Derleme Eylemleri
description: Bu makalede C# projeleri için kullanılan çeşitli derleme eylemleri açıklanmıştır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725987"
---
# <a name="build-actions"></a>Derleme eylemleri

Bir proje Mac için Visual Studio tüm dosyaların derleme eylemi vardır. Derleme eylemi, derleme sırasında dosyaya ne olacağını kontrol eder. 

>[!NOTE]
>Bu konu, Mac için Visual Studio. Bu Visual Studio hakkında daha fazla Windows bkz. [Derleme eylemleri.](/visualstudio/ide/build-actions)

## <a name="set-a-build-action"></a>Derleme eylemi ayarlama

Bir dosyanın derleme eylemlerini Mac için Visual Studio, aşağıda gösterildiği gibi herhangi bir dosyaya sağ tıklar ve Derleme Eylemi'ne göz atabilirsiniz:

![Çözüm gezgininden Derleme eylemlerini derle'yi seçme](media/projects-and-solutions-image1.png)

Bu dosya için derleme eylemleri açılır menüde gösterilir. 

## <a name="build-action-values"></a>Eylem değerleri oluşturma

Projelerde derlemek için yaygın olarak kullanılan derleme eylem Mac için Visual Studio şunlardır:

|Derleme Eylemi | Project türleri | Description |
|--|--|--|
| **Derlemek** | herhangi biri | Dosya, kaynak dosya olarak C# derleyiciye geçirildi.|
| **İçerik** | .NET, Xamarin | Daha ASP.NET için, bu dosyalar dağıtıldığında sitenin bir parçası olarak dahil edilir. Xamarin.iOS ve Xamarin.Mac projeleri uygulama paketine dahil edilir.|
| **Katıştırılmış Kaynak** | .NET | Dosya, derlemeye katıştırma kaynağı olarak C# derleyiciye geçirildi. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), ad `System.Reflection` alanı, daha sonra derlemeden dosyayı okumak için kullanılabilir.|
| **Hiçbiri** | herhangi biri | Dosya herhangi bir şekilde derlemenin parçası değildir ve IDE'den kolay erişim için projeye dahil edilir. Bu değer, örneğin "Beni Oku" dosyaları gibi belge dosyaları için kullanılabilir.|

> [!NOTE]
> Ek derleme eylemleri belirli proje türleri için tarafından tanımlanabilir, bu nedenle derleme eylemlerinin listesi proje türüne bağlıdır ve bu listede yer alan değerler görünebilir.  

Xamarin.iOS projelerinde **bundleResource** derleme eylemi vardır ve bu eylem dosyayı uygulama paketine ekler. Xamarin.Android'e özgü derleme eylemleriyle ilgili bilgiler derleme [işlemi kılavuzunda](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) bulunabilir.

Çözüm gezgininde birden fazla dosya seçerek derleme eylemlerini aynı anda birçok dosyaya ayarlamanıza da olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme eylemleri (Visual Studio üzerinde Windows)](/visualstudio/ide/build-actions)