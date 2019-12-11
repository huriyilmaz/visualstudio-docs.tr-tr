---
title: Derleme Eylemleri
description: Bu makalede, projeler için C# kullanılabilecek çeşitli derleme eylemleri açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983253"
---
# <a name="build-actions"></a>Derleme eylemleri

Bir Mac için Visual Studio projesindeki tüm dosyaların bir yapı eylemi vardır. Derleme sırasında dosyaya ne olacağını denetler. Bu davranış, aşağıda gösterildiği gibi herhangi bir dosyaya sağ tıklayıp **derleme eylemine**göz atarak ayarlanabilir:

![Çözüm Gezgini 'nden derlemeyi derle eylemini seçme](media/projects-and-solutions-image1.png)

Projeler için C# ortak derleme eylemlerinden bazıları şunlardır:

* **Hiçbiri** -dosya, derlemeyi herhangi bir şekilde DEĞIL, IDE 'den kolay erişim için projeye dahil edilmiştir.
* **Derle** -dosya C# derleyiciye kaynak dosya olarak geçirilir.
* **EmbeddedResource** -dosya, derlemeye gömülebilen bir kaynak C# olarak derleyiciye geçirilir. `System.Reflection` ad alanından [Assembly. GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), derlemeden dosyayı okumak için kullanılabilir.
* **İçerik** -ASP.NET projeleri için, bu dosyalar dağıtıldığında sitenin bir parçası olarak dahil edilir. Xamarin. iOS ve Xamarin. Mac projeleri için uygulama paketi 'ne dahil edilecek.

Çözüm Gezgini 'nde birden fazla dosya seçmek mümkündür ve derleme eylemini bir kerede birçok dosya olarak ayarlamanıza olanak tanır.

Ayrıca, belirli projeler için derleme eylemleri vardır. Xamarin. iOS projeleri, dosyayı uygulama paketinin bir parçası olarak ekleyecek olan **Paketleresource** derleme eylemine sahiptir. Xamarin. Android 'e özgü derleme eylemleri hakkında bilgi, [Yapı işlemi](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) kılavuzunda bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme eylemleri (Windows üzerinde Visual Studio)](/visualstudio/ide/build-actions)