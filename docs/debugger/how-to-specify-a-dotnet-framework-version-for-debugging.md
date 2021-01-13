---
title: Hata ayıklama için bir .NET Framework sürümü belirtin | Microsoft Docs
description: Hata ayıklama için eski bir .NET Framework sürümü belirtin. Visual Studio hata ayıklayıcı, .NET Framework eski sürümlerinin yanı sıra geçerli sürümü de hata ayıklamayı destekler.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b6b536cbfbd1019fc9b55a0113525f37030493f8
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149423"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Hata ayıklama için eski bir .NET Framework sürümü belirtin (C#, Visual Basic, F #)

Visual Studio hata ayıklayıcı, Microsoft .NET Framework 'ün eski sürümlerinin yanı sıra geçerli sürümü de hata ayıklamayı destekler. Visual Studio 'dan bir uygulama başlatırsanız hata ayıklayıcı, hata ayıklaması yaptığınız uygulamanın doğru .NET Framework sürümünü her zaman tanımlayabilir. Ancak, uygulama zaten çalışıyorsa ve **iliştirme 'yi** kullanarak hata ayıklamayı başlatırsanız, hata ayıklayıcı .NET Framework eski bir sürümünü her zaman tanımlayamayabilir. Bu durumda, şöyle bir hata iletisi alırsınız.

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

Bu hatanın göründüğü nadir durumlarda, bir kayıt defteri anahtarını, hangi sürümün kullanılacağı hata ayıklayıcıya göstermek için ayarlayabilirsiniz.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Hata ayıklama için bir .NET Framework sürümünü belirtmek için

1. Makinenizde yüklü .NET Framework sürümlerini bulmak için Windows\Microsoft.NET\Framework dizinine bakın. Sürüm numaraları şuna benzer:

    `V1.1.4322`

    Doğru sürüm numarasını belirleyip bunu bir yere göz önünde yapın.

2. **Kayıt defteri Düzenleyicisi 'ni** (regedit) başlatın.

3. **Kayıt defteri düzenleyicisinde** HKEY_LOCAL_MACHINE klasörünü açın.

4. Şuraya gidin: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\ {449Ec4cc-30D2-4032-9256-EE18EB41B62B}

    Anahtar yoksa, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine öğesine sağ tıklayın ve **Yeni anahtar**' a tıklayın. Yeni anahtarı adlandırın `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` .

5. {449EC4CC-30D2-4032-9256-EE18EB41B62B} sayfasına gittikten sonra **ad** sütununa bakın ve CLRVersionForDebugging anahtarını bulun.

   1. Anahtar yoksa, {449EC4CC-30D2-4032-9256-EE18EB41B62B} öğesine sağ tıklayın ve **Yeni dize değeri**' ne tıklayın. Ardından yeni dize değerine sağ tıklayın, **Yeniden Adlandır**' a tıklayın ve yazın `CLRVersionForDebugging` .

6. **CLRVersionForDebugging** öğesine çift tıklayın.

7. **Dize Düzenle** kutusuna **değer** kutusuna .NET Framework sürüm numarasını yazın. Örneğin: V 1.1.4322

8. **Tamam**'a tıklayın.

9. **Kayıt defteri düzenleyicisini** kapatın.

     Hata ayıklamaya başladığınızda yine de bir hata iletisi alırsanız, sürüm numarasını kayıt defterine doğru girdiğinizden emin olun. Ayrıca, Visual Studio tarafından desteklenen .NET Framework bir sürümünü kullandığınızı doğrulayın. Hata ayıklayıcı geçerli .NET Framework sürümü ve önceki sürümlerle uyumludur, ancak gelecekteki sürümlerle uyumlu olmayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)