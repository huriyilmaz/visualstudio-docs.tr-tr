---
title: Derleme Eylemleri
description: Bu makalede, C# projeleri için kullanılabilecek çeşitli yapı eylemleri açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714394"
---
# <a name="build-actions"></a>Derleme eylemleri

Mac projesi için Visual Studio'daki tüm dosyaların bir yapı eylemi var. Yapı eylemi, yapı sırasında dosyaya ne olduğunu denetler. 

>[!NOTE]
>Bu konu Mac için Visual Studio için geçerlidir. Windows'daki Visual Studio için [bkz.](/visualstudio/ide/build-actions)

## <a name="set-a-build-action"></a>Yapı eylemi ayarlama

Mac için Visual Studio'daki bir dosya için bir yapı eylemi ayarlamak için, aşağıda gösterildiği gibi, herhangi bir dosyaya ve **Eylem Oluştur'a**göz atabilirsiniz:

![Çözüm gezgininden Derleme yapı eylemini seçme](media/projects-and-solutions-image1.png)

Bu dosya için yapı eylemleri flyout menüsünde gösterilir. 

## <a name="build-action-values"></a>Eylem değerleri oluşturma

Mac için Visual Studio'da oluşturabileceğiniz projeler için ortak yapı eylemlerinden bazıları şunlardır:

|Eylem Oluştur | Proje türleri | Açıklama |
|--|--|--|
| **Derlemek** | herhangi bir | Dosya kaynak dosya olarak C# derleyicisine aktarılır.|
| **İçerik** | .NET, Xamarin | ASP.NET projeleriçin bu dosyalar dağıtıldığında sitenin bir parçası olarak bulunur. Xamarin.iOS ve Xamarin.Mac projeleri için uygulama paketine dahil edilecektir.|
| **Gömülü Kaynak** | .NET | Dosya, derlemeye katıştırılması gereken bir kaynak olarak C# derleyicisine aktarılır. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` ad alanından, daha sonra derleme dosyayı okumak için kullanılabilir.|
| **Yok** | herhangi bir | Dosya herhangi bir şekilde yapının bir parçası değildir ve IDE'den kolay erişim için projeye dahildir. Bu değer, örneğin "ReadMe" dosyaları gibi belge dosyaları için kullanılabilir.|

> [!NOTE]
> Ek yapı eylemleri belirli proje türleri için tanımlanabilir, bu nedenle yapı eylemleri listesi proje türüne bağlıdır ve bu listede olmayan değerler görünebilir.  

Xamarin.iOS projeleri, dosyayı uygulama paketinin bir parçası olarak ekleyecek **olan BundleResource** oluşturma eylemine sahiptir. Xamarin.Android belirli yapı eylemleri hakkında bilgi [yapı süreci](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) kılavuzunda bulunabilir.

Çözüm gezgininde birden fazla dosya seçerek yapı eylemini aynı anda birçok dosyaya ayarlamanızı da sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Eylemler oluşturma (Windows'ta Visual Studio)](/visualstudio/ide/build-actions)