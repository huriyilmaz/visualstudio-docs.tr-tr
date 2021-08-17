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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 30baf6cb3ed9a66d6c9d5696909f215e5721fcbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151398"
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
