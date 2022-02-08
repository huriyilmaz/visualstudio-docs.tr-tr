---
title: Derleme eylemlerini ayarlama
description: Bu makalede C# projeleri için kullanılmaktadır çeşitli derleme eylemleri açıklanmıştır
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 09/18/2019
ms.topic: conceptual
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 219d16b4b9f383f771e67c2b1c737ca1830bea5a
ms.sourcegitcommit: 782992423db6e1cbbf206715c9b3b400c80052a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "138100936"
---
# <a name="configure-build-actions"></a>Derleme eylemlerini yapılandırma

Bir proje Mac için Visual Studio tüm dosyalar bir derleme eylemine sahip olur. Derleme eylemi, proje derlenmiş olduğunda dosyaya ne olacağını kontrol eder. 

>[!NOTE]
>Bu konu, Mac için Visual Studio. Daha Visual Studio için Windows bkz. [Derleme eylemleri](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Derleme eylemi ayarlama

Bir dosyanın derleme eylemlerini Mac için Visual Studio, aşağıda gösterildiği gibi herhangi bir dosyaya sağ tıklar ve Derleme Eylemi'ne göz atabilirsiniz:

![Çözüm gezgininden Derleme eylemlerini derle'yi seçme](media/projects-and-solutions-image1.png)

Bu dosya için derleme eylemleri açılır menüde gösterilir. 

## <a name="build-action-values"></a>Eylem değerleri oluşturma

Projelerde derlemek için yaygın olarak kullanılan derleme eylem Mac için Visual Studio şunlardır:

|Derleme Eylemi | Project türleri | Description |
|--|--|--|
| **Derlemek** | herhangi biri | Dosya, kaynak dosya olarak C# derleyiciye geçirildi.|
| **İçerik** | .NET, Xamarin | Daha ASP.NET projeleri için, bu dosyalar dağıtıldığında sitenin bir parçası olarak dahil edilir. Xamarin.iOS ve Xamarin.Mac projeleri uygulama paketine dahil edilir.|
| **Katıştırılmış Kaynak** | .NET | Dosya, derlemeye katıştırma kaynağı olarak C# derleyiciye geçirildi. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` daha sonra ad alanının derlemeden dosyasını okumak için kullanılabilir.|
| **Hiçbiri** | herhangi biri | Dosya herhangi bir şekilde derlemenin parçası değildir ve IDE'den kolay erişim için projeye dahil edilir. Bu değer, örneğin "Beni Oku" dosyaları gibi belge dosyaları için kullanılabilir.|

> [!NOTE]
> Ek derleme eylemleri, tarafından belirli proje türleri için tanımlanabilir, bu nedenle derleme eylemlerinin listesi proje türüne bağlıdır ve bu listede yer alan değerler görünebilir.  

Xamarin.iOS projelerinde, dosyayı uygulama paketine ekecek **BundleResource** derleme eylemi vardır. Xamarin.Android'e özgü derleme eylemleriyle ilgili bilgiler derleme [işlemi kılavuzunda](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) bulunabilir.

Çözüm gezgininde birden fazla dosya seçerek derleme eylemlerini aynı anda birçok dosyaya ayarlamanıza da olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme eylemleri (Visual Studio üzerinde Windows)](/visualstudio/ide/build-actions)
