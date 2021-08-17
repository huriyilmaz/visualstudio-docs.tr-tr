---
title: 'F için önceki .NET Framework sürümleri hedefleme #'
description: Visual Studio'de F# kullanırken .NET Framework eski sürümünü hedefleme hakkında Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: a275a9f24ba3c3cbbfa2eb52a1166c46c1992421b2fee584c0fb628529b31c5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372939"
---
# <a name="target-older-versions-of-net-f"></a>.NET'in eski sürümlerini hedefleme (F#)

.NET Framework .NET Framework, 3.0 veya 3.5'i bir F# projesinde Visual Studio yüklü olduğunda hedeflemeye çalışsanız aşağıdaki hata Windows 8.1:

**Bu proje için 2.0 F# çalışma zamanı gerekir ancak bu çalışma zamanı yüklenmez.**

Bu hatanın aşağıdaki koşulların birleşimi altında oluştuğu bilinir:

- Visual Studio'Windows 8.1.

- .NET Framework 3.5'i yüklemeden önce Visual Studio.

- Projeniz 2.0.NET Framework, 3.0 veya 3.5'i hedefler.

Yükleme Visual Studio, uygulamanın yüklü sürümlerini .NET Framework. Visual Studio, F# 2.0 çalışma zamanı yalnızca .NET Framework 3.5 yüklü ve etkinse yüklenir.

## <a name="resolve-the-error"></a>Hatayı çözme

Bu hatayı çözmek için şunları da alabilirsiniz:

- Uygulamanın daha yeni bir sürümünü .NET Framework.

- .NET Framework 3.5'i Windows 8.1 ve ardından Visual Studio yüklemesini onararak F# 2.0 çalışma Visual Studio yükleyin. Bunu yapmak için aşağıdaki adımları izleyin.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>3.5 .NET Framework 3.5'i Windows 8.1

1. Başlangıç **ekranında** **Denetim Masası.**

   Siz yazarak Uygulamalar **Denetim Masası** simgesi **görünür.**

2. Yeni **Denetim Masası** simgesini seçin, Programlar **simgesini** seçin ve ardından Windows **özellikleri aç veya kapat bağlantısını** seçin.

3. **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusunun seçili olduğundan emin olun ve ardından **Tamam düğmesini** seçin. Alt düğümlerin isteğe bağlı bileşenleri için onay kutularını seçmenize gerek .NET Framework.

   3.5 .NET Framework 3.5 önceden etkinleştirilmediyse etkinleştirilir.

### <a name="to-install-the-f-20-runtime"></a>F# 2.0 çalışma zamanlarını yüklemek için

'i [onarmak için Visual Studio.](../install/repair-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- [F# kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio’da F#](fsharp-visual-studio.md)
