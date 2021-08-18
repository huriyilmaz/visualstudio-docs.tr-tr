---
title: Geçerli Yığın Çerçevesini Ayarla Komutu
description: Geçerli yığın çerçevesini ayarla komutunu ve belirli bir yığın çerçevesini ayarlamanıza nasıl izin verdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6d003a953c411723ae8b7d52055923db21b85ba6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123820"
---
# <a name="set-current-stack-frame-command"></a>Geçerli Yığın Çerçevesini Ayarla Komutu
Belirli bir yığın çerçevesini ayarlamanıza olanak sağlar.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Bağımsız değişkenler
`index`

Gereklidir. Bir yığın çerçevesini dizinine göre seçer.

## <a name="example"></a>Örnek

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)