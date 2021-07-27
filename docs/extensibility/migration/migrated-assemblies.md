---
title: VS SDK NuGet paketleri
description: Bir Visual Studio uzantısını Visual Studio 2022 Preview sürümüne geçirinken ihtiyacınız olan VS SDK meta paketi ve diğer NuGet paketleri hakkında bilgi edinebilirsiniz.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: cb30ac4aef7d4c30bfe1ba9856b05287cf9094be
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2021
ms.locfileid: "114591864"
---
# <a name="sdk-reference-packages"></a>SDK başvuru paketleri

[!INCLUDE [preview-note](../includes/preview-note.md)]

Uzantılar yazmanın Visual Studio en kolay yolu, NuGet [ `Microsoft.VisualStudio.Sdk` paketine başvuru yapmaktır.](https://www.nuget.org/packages/microsoft.visualstudio.sdk)
Bu paket Visual Studio 2017 (15.0), Visual Studio 2019 (16.0, 16.9) ve şimdi 2022'Visual Studio için kullanılabilir.

Uzantınıza bağlı olarak, yukarıdaki meta pakete dahil olmayan ek VS SDK paketleri eklemek gerekebilir.
Belirli diğer SDK paketlerine başvururken, bu paketler ana VS sürümleri arasında farklılık gösterebilir.

2022'den önce birçok birlikte çalışma derlemesi Visual Studio unutmayın. 2022 Visual Studio den itibaren, ekleme artık gerekli değildir veya desteklemektedir.
Lütfen *bunları* bağlama yerine birlikte çalışma derlemelerimize bakın.

Aşağıdaki tablo, 2022'de ön Visual Studio 2022'i hedeflerken başvurulacak yeni paket kimliğine zaten başvurulan derlemelerden veya paketlerden bir eşleme Visual Studio sağlar. Bazı durumlarda, derlemeler artık daha önce yalnızca yerel NuGet yüklemesinde kullanılabilir olan paketlerde Visual Studio kullanılabilir.

2022 Visual Studio öncesi | Visual Studio 2022
--|--
`envdte` | `Microsoft.VisualStudio.Interop`
`envdte100` | `Microsoft.VisualStudio.Interop`
`envdte80` | `Microsoft.VisualStudio.Interop`
`envdte90` | `Microsoft.VisualStudio.Interop`
`envdte90a` | `Microsoft.VisualStudio.Interop`
`extensibility` | `Microsoft.VisualStudio.Interop`
`Microsoft.MSXML` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.CommandBars` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Designer.Interfaces` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.OLE.Interop` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.SDK.EmbedInteropTypes` | (Eski. Başvuru kaldır.)
`Microsoft.VisualStudio.Shell.Embeddable` | `Microsoft.VisualStudio.Shell.Framework`
`Microsoft.VisualStudio.Shell.Interop.10.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.11.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.12.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.2.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.3.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.3.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.5.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.6.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.7.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.8.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.10.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.2.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.3.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.4.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.5.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.6.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.7.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.9.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.8.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.9.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.10.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.11.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.12.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.12.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.14.2.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.15.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.15.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.16.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.8.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.9.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.UserNotifications.Interop.12.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.VSHelp.dll` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.VSHelp80.dll` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.WCFReference.Interop` | `Microsoft.VisualStudio.Interop`
`stdole` | `Microsoft.VisualStudio.Interop`
`VSLangProj` | `Microsoft.VisualStudio.Interop`
`VSLangProj100` | `Microsoft.VisualStudio.Interop`
`VSLangProj110` | `Microsoft.VisualStudio.Interop`
`VSLangProj140` | `Microsoft.VisualStudio.Interop`
`VSLangProj150` | `Microsoft.VisualStudio.Interop`
`VSLangProj157` | `Microsoft.VisualStudio.Interop`
`VSLangProj158` | `Microsoft.VisualStudio.Interop`
`VSLangProj165` | `Microsoft.VisualStudio.Interop`
`VSLangProj2` | `Microsoft.VisualStudio.Interop`
`VSLangProj80` | `Microsoft.VisualStudio.Interop`
`VSLangProj90` | `Microsoft.VisualStudio.Interop`

Şimdi yalnızca bir birleştirilmiş birlikte çalışma derlemesi için kaç birlikte çalışma derlemesi kullanılabilir olduğunu unutmayın.
Bir paket yukarıdaki tabloda görünmese de iki sürümde aynı olabilir.
