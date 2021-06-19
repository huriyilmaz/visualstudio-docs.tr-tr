---
title: Hata ayıklama .NET Framework için bir sürüm | Microsoft Docs
description: Hata ayıklama için .NET Framework eski bir sürüm belirtin. Hata Visual Studio hata ayıklayıcısı, hem eski .NET Framework hem de geçerli sürümde hata ayıklamayı destekler.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 83b30067530b9a48769879f3a222fee2afa725c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384674"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Hata ayıklama için eski .NET Framework sürümü belirtme (C#, Visual Basic, F#)

Hata Visual Studio ayıklayıcısı, hem Microsoft .NET Framework'un eski sürümlerinde hem de geçerli sürümde hata ayıklamayı destekler. Bir uygulamayı hata ayıklayıcısından Visual Studio, hata ayıklayıcı her zaman hata ayıklarken .NET Framework uygulamanın doğru sürümünü tanımlayabilir. Ancak, uygulama zaten çalışıyorsa ve 'a Ekle'ye kullanarak hata ayıklamaya başlıyorsanız, hata ayıklayıcı her zaman uygulamanın eski bir sürümünü .NET Framework. Bu durumda, şöyle bir hata iletisi alırsınız:

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

Bu hatanın görüntülendiğinde nadir durumlarda, hata ayıklayıcıya hangi sürümün kullanılamayacaklarını belirtmek için bir kayıt defteri anahtarı ayarlayın.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Hata ayıklama için .NET Framework sürümü belirtmek için

1. Makinenize yüklenmiş olan Microsoft.NET\Framework dizinine .NET Framework dizinine bakın. Sürüm numaraları şuna benzer:

    `V1.1.4322`

    Doğru sürüm numarasını belirleyin ve not edin.

2. Kayıt Defteri **Düzenleyicisi'ni** (regedit) başlatma.

3. Kayıt **Defteri Düzenleyicisi'nde** HKEY_LOCAL_MACHINE açın.

4. Şu sayfaya gidin: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\ {449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Anahtar yoksa, Anahtar'a sağ tıklayın HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine Yeni **Anahtar'a tıklayın.** Yeni anahtarı olarak ad `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` girin.

5. {449EC4CC-30D2-4032-9256-EE18EB41B62B} yolunun ardından **Ad** sütununa bakın ve CLRVersionForDebugging anahtarını bulun.

   1. Anahtar yoksa {449EC4CC-30D2-4032-9256-EE18EB41B62B} öğesini sağ tıklatın ve Yeni Dize Değeri'ne **tıklayın.** Ardından yeni dize değerine sağ tıklayın, Yeniden **Adlandır'a tıklayın** ve `CLRVersionForDebugging` yazın.

6. **CLRVersionForDebugging'e çift tıklayın.**

7. Dizeyi **Düzenle** kutusuna Değer kutusuna .NET Framework numarasını **yazın.** Örneğin: V1.1.4322

8. **Tamam**'a tıklayın.

9. Kayıt Defteri **Düzenleyicisi'ni kapatın.**

     Hata ayıklamaya başlarken hata iletisi almaya devam ediyorsanız, kayıt defterine sürüm numarasını doğru girdiğinizi doğrulayın. Ayrıca, uygulama tarafından desteklenen bir .NET Framework sürümü Visual Studio. Hata ayıklayıcısı geçerli sürüm ve .NET Framework sürümleriyle uyumludur, ancak gelecek sürümlerle uyumlu olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcı Ayarları ve Hazırlama](../debugger/debugger-settings-and-preparation.md)