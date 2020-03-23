---
title: Command penceresi çıktısı günlüğü tut komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6ba8fb419726018bd089e217386ab5dbd6a9c33
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568665"
---
# <a name="log-command-window-output-command"></a>Komut Penceresi Çıkışını Günlüğe Kaydet komutu

**Komut** penceresinden tüm giriş ve çıktıları bir dosyaya kopyalar.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`filename`\
İsteğe bağlı. Günlük dosyasının adı. Varsayılan olarak, dosya kullanıcının profil klasöründe oluşturulur. Dosya adı zaten varsa, günlük varolan dosyanın sonuna eklenir. Dosya belirtilmemişse, belirtilen son dosya kullanılır. Önceki bir dosya yoksa, cmdline.log adı verilen varsayılan günlük dosyası oluşturulur.

> [!TIP]
> Günlük dosyasının kaydedildiği konumu değiştirmek için, yol boşluk içeriyorsa tırnak işaretleriyle çevrili dosyanın tam yolunu girin.

## <a name="switches"></a>Anahtarlar

/on\
İsteğe bağlı. Belirtilen dosyadaki **Komut** penceresinin günlüğünü başlatır ve dosyayı yeni bilgilerle tamamlar.

/off\
İsteğe bağlı. **Komut** penceresinin günlüğünü durdurur.

/overwrite\
İsteğe bağlı. `filename` Bağımsız değişkende belirtilen dosya varolan bir dosyayla eşleşirse, dosya üzerine yazılır.

## <a name="remarks"></a>Açıklamalar

Dosya belirtilmemişse, cmdline.log dosyası varsayılan olarak oluşturulur. Varsayılan olarak, bu komutun diğer adı Log'dur.

## <a name="examples"></a>Örnekler

Bu örnek, yeni bir günlük dosyası, cmdlog oluşturur ve komut günlüğü başlatır.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Bu örnek, günlük komutları durdurur.

```cmd
>Tools.LogCommandWindowOutput /off
```

Bu örnek, daha önce kullanılan günlük dosyasında komutların günlüğe kaydetmedevam eder.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/Komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
