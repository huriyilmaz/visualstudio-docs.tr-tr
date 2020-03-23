---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 434b2ad0f2a6ca4d84c6d82bf9a1a85876a4d975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570407"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Visual Studio IDE'yi başlattıktan sonra belirtilen komutu çalıştırıyor.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Bağımsız Değişkenler

*Commandname*

Gereklidir. Bir Visual Studio komutunun veya takma adının tam adı, çift tırnak işaretleriyle birlikte. Komut ve diğer ad sözdizimi hakkında daha fazla bilgi için [Visual Studio Komutları'na](../../ide/reference/visual-studio-commands.md)bakın.

## <a name="remarks"></a>Açıklamalar

Başlangıç tamamlandıktan sonra, IDE adlandırılmış komutu yürütür.

::: moniker range="vs-2017"

Bu anahtarı kullanırsanız, IDE başlangıç sayfasında Başlangıç Sayfasını görüntülemez.

::: moniker-end

Bir eklenti bir komut ortaya çıkarırsa, eklentiyi komut satırından başlatmak için bu anahtarı kullanabilirsiniz. Daha fazla bilgi için [bkz: Eklenti yöneticisini kullanarak eklentileri denetleme.](/previous-versions/xwdatdwh(v=vs.140))

## <a name="example"></a>Örnek

İlk örnek Visual Studio'yu başlatur ve makroyu Sık Kullanılan Dosyaları Aç'ı otomatik olarak çalıştırın.

İkinci örnek, IDE içinde bir web tarama sekmesini açar ve Microsoft Dokümanlar sitesine yönlendirilir.

Üçüncü örnek, adlı `some_file.cs` yeni bir dosya oluşturur ve bir kod düzenleyicisinde açar.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Komut penceresi](command-window.md)
