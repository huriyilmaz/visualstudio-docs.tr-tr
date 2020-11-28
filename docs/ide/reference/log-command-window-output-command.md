---
title: Command penceresi çıktısı günlüğü tut komutu
description: Günlük komutu penceresi çıkış komutu ve Komut penceresi tüm giriş ve çıkışları bir dosyaya nasıl kopyaladığı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cab4f102832e8dfa6ce51b61abed8e3bfd672c40
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305274"
---
# <a name="log-command-window-output-command"></a>Komut Penceresi Çıkışını Günlüğe Kaydet komutu

**Komut** penceresinden tüm giriş ve çıkışları bir dosyaya kopyalar.

## <a name="syntax"></a>Söz dizimi

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Bağımsız değişkenler

`filename`\
İsteğe bağlı. Günlük dosyasının adı. Varsayılan olarak, dosya kullanıcının profil klasöründe oluşturulur. Dosya adı zaten varsa, günlük varolan dosyanın sonuna eklenir. Dosya belirtilmemişse, belirtilen son dosya kullanılır. Önceki bir dosya mevcut değilse, komut satırı. log adlı varsayılan bir günlük dosyası oluşturulur.

> [!TIP]
> Günlük dosyasının kaydedildiği konumu değiştirmek için, yolun herhangi bir boşluk içermesi durumunda tırnak işaretleriyle çevrelenen dosyanın tam yolunu girin.

## <a name="switches"></a>Anahtarlar

/on
İsteğe bağlı. Belirtilen dosyadaki **komut** penceresi için günlüğü başlatır ve dosyayı yeni bilgilerle ekler.

/off
İsteğe bağlı. **Komut** penceresi için günlüğü sonlandırır.

/overwrite
İsteğe bağlı. `filename`Bağımsız değişkende belirtilen dosya varolan bir dosyayla eşleşiyorsa, dosyanın üzerine yazılır.

## <a name="remarks"></a>Açıklamalar

Dosya belirtilmemişse, komut satırı. log dosyası varsayılan olarak oluşturulur. Varsayılan olarak, bu komutun diğer adı günlüğe kaydedilir.

## <a name="examples"></a>Örnekler

Bu örnek, yeni bir günlük dosyası oluşturur, cmdlog ve komut günlüğünü başlatır.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Bu örnek günlüğe kaydetme komutlarını durduruyor.

```cmd
>Tools.LogCommandWindowOutput /off
```

Bu örnek, daha önce kullanılan günlük dosyasındaki komutların günlüğe kaydedilmesini sürdürür.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
