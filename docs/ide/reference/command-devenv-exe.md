---
title: -Command (devenv.exe)
description: Visual Studio IDE 'yi başlattıktan sonra belirtilen bir komutu yürütmek için komut Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38738dad275b38fe0c5a6a70104e80f6a794bab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882192"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Visual Studio IDE 'yi başlattıktan sonra belirtilen komutu yürütür.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Bağımsız değişkenler

*Name*

Gereklidir. Bir Visual Studio komutunun veya diğer adının, çift tırnak işareti içine alınmış olarak tamamı. Komut ve diğer ad sözdizimi hakkında daha fazla bilgi için bkz. [Visual Studio komutları](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Açıklamalar

Başlangıç tamamlandıktan sonra IDE, adlandırılmış komutunu yürütür.

::: moniker range="vs-2017"

Bu anahtarı kullanırsanız, IDE başlangıç sayfasını başlangıçta görüntülemez.

::: moniker-end

Bir eklenti bir komut kullanıma sunarsa, bu anahtarı komut satırından eklentiyi başlatmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eklenti yöneticisini kullanarak eklentileri denetleme](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Örnek

İlk örnek, Visual Studio 'Yu başlatır ve makro açık olan dosyaları aç makrosunu otomatik olarak çalıştırır.

İkinci örnek, IDE içinde bir Web gözatma sekmesi açar ve Microsoft Docs sitesine gider.

Üçüncü örnek adlı yeni bir dosya oluşturur `some_file.cs` ve onu bir kod düzenleyicisinde açar.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Komut penceresi](command-window.md)
