---
title: İçin önceki .NET Framework sürümlerini hedefleF#
description: Visual Studio 'da kullanırken F# .NET Framework eski sürümü hedefleme hakkında bilgi edinin.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: df263ee4b2bd6ec7b6239826725a85c26f0acf80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603533"
---
# <a name="target-older-versions-of-net-f"></a>.NET (F#) uygulamasının eski sürümlerini hedefleyin

Visual Studio Windows 8.1 üzerine yüklendiğinde 2,0, 3,0 veya 3,5 .NET Framework bir F# projede hedefdenemeye çalışırsanız aşağıdaki hata görünebilir:

**Bu proje 2,0 F# çalışma zamanını gerektiriyor, ancak çalışma zamanı yüklü değil.**

Bu hatanın aşağıdaki koşullar birleşimi altında oluştuğu bilinmektedir:

- Visual Studio 'Yu Windows 8.1 yüklediniz.

- .NET Framework 3,5 ' i Visual Studio 'Yu yüklemeden önce etkinleştirmediniz.

- Projeniz 2,0, 3,0 veya 3,5 .NET Framework hedefler.

Visual Studio 'Yu yüklediğinizde, .NET Framework yüklü sürümlerini algılar. Visual Studio, F# 2,0 çalışma zamanını yalnızca 3,5 .NET Framework yüklüyse ve etkinse yüklenir.

## <a name="resolve-the-error"></a>Hatayı çözümle

Bu hatayı çözmek için şunlardan birini yapabilirsiniz:

- .NET Framework daha yeni bir sürümünü hedefleyin.

- Windows 8.1 .NET Framework 3,5 ' i etkinleştirin ve sonra Visual Studio F# yüklemesini onararak 2,0 çalışma zamanını yükledikten sonra. Bunu yapmak için adımları izleyin.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1 .NET Framework 3,5 ' i etkinleştirmek için

1. **Başlangıç** ekranında **Denetim Masası**yazın.

   Siz yazarken, **Denetim Masası** simgesi **uygulamalar** başlığı altında görüntülenir.

2. **Denetim Masası** simgesini seçin, **Programlar** simgesini seçin ve ardından **Windows özelliklerini aç veya kapat** bağlantısını seçin.

3. **.NET Framework 3,5 (.net 2,0 ve 3,0 dahil)** onay kutusunun seçili olduğundan emin olun ve **Tamam** düğmesini seçin. .NET Framework isteğe bağlı bileşenleri için alt düğümlerin onay kutularını seçmeniz gerekmez.

   .NET Framework 3,5, zaten yoksa etkindir.

### <a name="to-install-the-f-20-runtime"></a>F# 2,0 çalışma zamanını yüklemek için

[Visual Studio 'yu onarmak için adımları](../install/repair-visual-studio.md)izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [F#Kılavuz (.NET Framework)](/dotnet/fsharp/)
- [F#Visual Studio 'da](fsharp-visual-studio.md)