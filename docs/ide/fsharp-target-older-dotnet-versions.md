---
title: 'F için önceki .NET Framework sürümlerini hedefle #'
description: Visual Studio'da F# kullanırken .NET Framework'ün eski sürümünü hedefleme hakkında bilgi edinin.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584588"
---
# <a name="target-older-versions-of-net-f"></a>.NET'in eski sürümlerini hedefle (F#)

Visual Studio Windows 8.1'e yüklendiğinde bir F# projesinde .NET Framework 2.0, 3.0 veya 3.5'i hedeflemeye çalışırsanız aşağıdaki hata görünebilir:

**Bu proje 2.0 F# çalışma zamanı gerektirir, ancak bu çalışma süresi yüklenmez.**

Bu hatanın aşağıdaki koşullar birleşimi altında oluştuğu bilinmektedir:

- Visual Studio'yı Windows 8.1'e yükledin.

- Visual Studio'yu yüklemeden önce .NET Framework 3.5'i etkinleştirmişsiniz.

- Projeniz .NET Framework 2.0, 3.0 veya 3.5'i hedefler.

Visual Studio'yu yüklediğinizde,.NET Framework'ün yüklü sürümlerini algılar. Visual Studio, F# 2.0 çalışma süresini yalnızca .NET Framework 3.5 yüklü ve etkin sayılsa yükler.

## <a name="resolve-the-error"></a>Hatayı çözümle

Bu hatayı gidermek için şunları yapabilirsiniz:

- .NET Framework'ün daha yeni bir sürümünü hedefle.

- Windows 8.1'deki .NET Framework 3.5'i etkinleştirin ve Visual Studio yüklemesini onararak F# 2.0 çalışma süresini yükleyin. Bunu yapmak için adımlar izleyin.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1'de .NET Framework 3.5'i etkinleştirmek için

1. **Başlangıç** ekranında **Denetim Masası**yazın.

   Siz yazarken, **Denetim Masası** simgesi **Uygulamalar** başlığıaltında görünür.

2. Denetim **Masası** simgesini seçin, **Programlar** simgesini seçin ve ardından **Windows özelliklerini aç veya kapat** bağlantısını seçin.

3. **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusunun seçildiğinden emin olun ve ardından **Tamam** düğmesini seçin. .NET Framework'ün isteğe bağlı bileşenleri için alt düğümler için onay kutularını seçmeniz gerekmez.

   .NET Framework 3.5 zaten değilse etkinleştirilir.

### <a name="to-install-the-f-20-runtime"></a>F# 2.0 çalışma süresini yüklemek için

Visual [Studio'yu onarmak için adımları](../install/repair-visual-studio.md)izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [F# kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio’da F#](fsharp-visual-studio.md)
