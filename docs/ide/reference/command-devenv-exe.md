---
title: -Command (devenv.exe)
description: Visual Studio IDE'leri başlattıktan sonra belirli bir komutu yürütmek için Command devenv komut satırı anahtarının nasıl Visual Studio öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 871eeddd248255924d8fa0787af9dad73b250c7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062322"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

IDE'de belirtilen komutu çalıştırarak Visual Studio yürütür.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Bağımsız değişkenler

*Commandname*

Gereklidir. Visual Studio komutunun tam adı veya çift tırnak içine alınmış diğer adı. Komut ve diğer ad söz dizimi hakkında daha fazla bilgi için [bkz. Visual Studio.](../../ide/reference/visual-studio-commands.md)

## <a name="remarks"></a>Açıklamalar

Başlatma tamamlandıktan sonra, IDE adlandırılmış komutu yürütür.

::: moniker range="vs-2017"

Bu anahtarı kullanırsanız, IDE başlangıçta Başlangıç Sayfasını görüntülemez.

::: moniker-end

Eklenti bir komutu açığa çıkarırsa, eklentiyi komut satırdan başlatmak için bu anahtarı kullanabilirsiniz. Daha fazla bilgi [için, bkz. How to: Control eklentileri by using the add-in manager](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Örnek

İlk örnek, dosya Visual Studio ve Sık Kullanılan Dosyaları Aç makroyu otomatik olarak çalıştırır.

İkinci örnek, IDE içinde bir web gözatma sekmesi açar ve Microsoft Docs açar.

Üçüncü örnek adlı yeni bir dosya `some_file.cs` oluşturur ve bir kod düzenleyicisinde açar.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Komut penceresi](command-window.md)
