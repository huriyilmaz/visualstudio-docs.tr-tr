---
title: MSBuild 17.0 | Microsoft Docs
description: MSBuild 17.0 için değiştirilen ve güncelleştirilmiş özellikler hakkında bilgi alın ve sürüm notlarına bağlantı ekleyin.
ms.date: 10/25/2021
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 5ca502169d2c238be7871ca19cc9372e91f4207a
ms.sourcegitcommit: abfcccf63234819c75a61bf2c4c7f710a9d23cdb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132250601"
---
# <a name="whats-new-in-msbuild-170"></a>MSBuild 17.0'daki yeniler

Bu makalede, 17.0 MSBuild güncelleştirmeleri açıklanmıştır. Ayrıntılı sürüm notları için bkz. [MSBuild 17.0.0](https://github.com/dotnet/msbuild/releases/tag/v17.0.0).

MSBuild 17.0, [Visual Studio 2022](../ide/whats-new-visual-studio-2022.md) ve [.NET 6.0 ile birlikte gönderilir.](/dotnet/)

## <a name="changed-path"></a>Yol değiştirildi

 MSBuild her bir sürümü altındaki *\Current* klasörüne yüklenir Visual Studio yürütülebilir dosyalar *\Bin alt* klasöründe bulunur. Örneğin, *MSBuild.exe* 2022 Visual Studio ile yüklenmiş Community yolu *C:\Program Files\Microsoft Visual* Studio\2022\Community\MSBuild\Current\Bin\MSBuild.exe'dır. [Vssetup.powershell'i](https://github.com/Microsoft/vssetup.powershell)bulmak için aşağıdaki PowerShell modülünü de MSBuild kullanabilirsiniz.

## <a name="changed-properties"></a>Değiştirilen özellikler

 Aşağıdaki MSBuild sürüm numarası nedeniyle güncelleştirilmiştir.

- `MSBuildToolsVersion` araçların bu sürümü için "Geçerli" olarak kalır. Derleme sürümü, Visual Studio 2017 ve 15.1.0.0 olan Visual Studio 2019 ile aynıdır.

- `VisualStudioVersion` araçların bu sürümü için "17.0"

## <a name="64-bit"></a>64 bit

MSBuild.exe önce hem 32 bit hem de 64 bit sürümlere sahipti, ancak şimdi varsayılan sürüm 64 bittir. Visual Studio 2022 tüm derlemeler için MSBuild 64 bit sürümünü kullanır. 32 bit sürüm hala kullanılabilir ancak tüm derlemeleri 64 bit sürüme değiştirmenizi öneririz.

Görev sahipleri için bu, görevinizi MSBuild 64 bitlik bir işlemde yükleme denemesi anlamına gelir. Görevlerinizi 64 bitlik bir işlemde çalıştıracak şekilde güncelleştirmenizi öneririz, ancak uyumluluk için görevinizin yalnızca UsingTask içinde 32 bit olarak MSBuild olduğunu [söyleyebiliriz.](../msbuild/how-to-configure-targets-and-tasks.md)

## <a name="performance-improvements"></a>Performans geliştirmeleri

MSBuild daha hızlı! Bu sürümün odak noktası, birçok yaygın senaryonun performansını geliştirmektir. MSBuild 17.0 daha büyük projeler daha hızlı bir şekilde derlemeyi sağlar.

## <a name="net-versions"></a>.NET sürümleri

MSBuild (ve Visual Studio), artık .NET Framework 4.7.2 ve .NET 6.0'a yöneliktir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="logs"></a>Günlükler

İkili günlükler daha küçüktür ve daha fazla bilgi içerir.

## <a name="breaking-changes"></a>Yeni değişiklikler

- yöntemi `GetType()` artık özellik işlevlerinde çağrılamaz.
- MSBuild .NET için .NET 6'ya yöneliktir.

## <a name="other-behavior-changes"></a>Diğer davranış değişiklikleri

- `MSBuildCopyContentTransitively` artık varsayılan olarak açıktır ve artımlı derlemelerde çıkış klasörlerini tutarlılığı sağlar.

Bu sürümde yapılan diğer değişiklikler için ayrıntılı sürüm notlarına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
