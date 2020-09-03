---
title: 'F için önceki .NET Framework sürümlerini hedefle #'
description: "Visual Studio 'da F # kullanırken .NET Framework eski sürümü hedefleme hakkında bilgi edinin."
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75584588"
---
# <a name="target-older-versions-of-net-f"></a>.NET 'in eski sürümlerini hedefleyin (F #)

Windows 8.1 üzerinde Visual Studio yüklü olduğunda bir F # projesinde 2,0, 3,0 veya 3,5 .NET Framework hedeflemesini denediğinizde aşağıdaki hata görünebilir:

**Bu proje için 2,0 F # çalışma zamanı gerekiyor, ancak çalışma zamanı yüklü değil.**

Bu hatanın aşağıdaki koşullar birleşimi altında oluştuğu bilinmektedir:

- Visual Studio 'Yu Windows 8.1 yüklediniz.

- .NET Framework 3,5 ' i Visual Studio 'Yu yüklemeden önce etkinleştirmediniz.

- Projeniz 2,0, 3,0 veya 3,5 .NET Framework hedefler.

Visual Studio 'Yu yüklediğinizde, .NET Framework yüklü sürümlerini algılar. Visual Studio, F # 2,0 çalışma zamanını yalnızca 3,5 .NET Framework yüklüyse ve etkinse yüklenir.

## <a name="resolve-the-error"></a>Hatayı çözümle

Bu hatayı çözmek için şunlardan birini yapabilirsiniz:

- .NET Framework daha yeni bir sürümünü hedefleyin.

- Windows 8.1 .NET Framework 3,5 ' i etkinleştirin ve sonra Visual Studio yüklemesini onararak F # 2,0 çalışma zamanını yükledikten sonra. Bunu yapmak için adımları izleyin.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1 .NET Framework 3,5 ' i etkinleştirmek için

1. **Başlangıç** ekranında **Denetim Masası**yazın.

   Siz yazarken, **Denetim Masası** simgesi **uygulamalar** başlığı altında görüntülenir.

2. **Denetim Masası** simgesini seçin, **Programlar** simgesini seçin ve ardından **Windows özelliklerini aç veya kapat** bağlantısını seçin.

3. **.NET Framework 3,5 (.net 2,0 ve 3,0 dahil)** onay kutusunun seçili olduğundan emin olun ve **Tamam** düğmesini seçin. .NET Framework isteğe bağlı bileşenleri için alt düğümlerin onay kutularını seçmeniz gerekmez.

   .NET Framework 3,5, zaten yoksa etkindir.

### <a name="to-install-the-f-20-runtime"></a>F # 2,0 çalışma zamanını yüklemek için

[Visual Studio 'yu onarmak için adımları](../install/repair-visual-studio.md)izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [F # Kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio’da F#](fsharp-visual-studio.md)
