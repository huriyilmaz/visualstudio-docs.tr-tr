---
title: Derleme Eylemleri
description: Bu makalede, C# projeleri için kullanılabilecek çeşitli yapı eylemleri açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983253"
---
# <a name="build-actions"></a>Derleme eylemleri

Mac projesi için Visual Studio'daki tüm dosyaların bir yapı eylemi var. Yapı sırasında dosyaya ne olduğunu denetler. Bu davranış, aşağıda gösterildiği gibi, herhangi bir dosyaya sağ tıklayarak ve **Eylem Oluştur'a**göz atarak ayarlanabilir:

![Çözüm gezgininden Derleme yapı eylemini seçme](media/projects-and-solutions-image1.png)

C# projeleri için ortak yapı eylemlerinden bazıları şunlardır:

* **Yok** - Dosya herhangi bir şekilde yapının bir parçası değildir - IDE'den kolay erişim için projeye dahildir.
* **Derle** - Dosya kaynak dosya olarak C# derleyicisine geçirilir.
* **EmbeddedResource** - Dosya, derlemeye katıştırılması gereken bir kaynak olarak C# derleyicisine geçirilir. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` ad alanından, daha sonra derleme dosyayı okumak için kullanılabilir.
* **İçerik** - ASP.NET projelerde, bu dosyalar dağıtıldığında sitenin bir parçası olarak eklenecektir. Xamarin.iOS ve Xamarin.Mac projeleri için uygulama paketine dahil edilecektir.

Çözüm gezgininde birden fazla dosya seçerek yapı eylemini aynı anda birçok dosyaya ayarlamanızı sağlar.

Ayrıca, belirli projeler için yapı eylemleri vardır. Xamarin.iOS projeleri, dosyayı uygulama paketinin bir parçası olarak ekleyecek **olan BundleResource** oluşturma eylemine sahiptir. Xamarin.Android belirli yapı eylemleri hakkında bilgi [yapı süreci](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) kılavuzunda bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Eylemler oluşturma (Windows'ta Visual Studio)](/visualstudio/ide/build-actions)