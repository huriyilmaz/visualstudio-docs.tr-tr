---
title: Belleği Listele Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c500b1b516c2b1ab1bc66b7970fccc4ec7a85baa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568717"
---
# <a name="list-memory-command"></a>Belleği Listele Komutu
Belirtilen bellek aralığının içeriğini görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`expression`

İsteğe bağlı. Belleğin görüntülenmesine başlanacak bellek adresi.

## <a name="switches"></a>Anahtarlar
/ANSI&#124;Unicode

İsteğe bağlı. Belleğin baytlarına karşılık gelen karakterler olarak görüntüleyin, ANSI veya Unicode.

/Sayım:`number`

İsteğe bağlı. 'den `expression`başlayarak, görüntülenecek bellek kaç bayt ını belirler.

/Format:`formattype`

İsteğe bağlı. **Bellek** penceresinde bellek bilgilerini görüntülemek için biçim yazısını biçimlendirin; OneByte, TwoBytes, FourBytes, EightBytes, Float (32-bit) veya Double (64-bit) olabilir. OneByte kullanılırsa, `/Unicode` kullanılamaz.

/Hex&#124;İmzasız&#124;İmzasız

İsteğe bağlı. Numaraları görüntüleme biçimini belirtir: imzalı, imzasız veya hexadecimal olarak.

## <a name="remarks"></a>Açıklamalar
Tüm anahtarlarla tam bir **Debug.ListMemory** komutu yazmak yerine, belirli anahtarlarla önceden belirlenmiş belirli değerlere önceden ayarlanmış takma adları kullanarak komutu çağırabilirsiniz. Örneğin, girmek yerine:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

yazabilirsiniz:

```cmd
>df /Count:30 /Unicode
```

**Burada Debug.ListMemory** komutu için kullanılabilir diğer adların bir listesi:

|Diğer ad|Komut ve Anahtarlar|
|-----------| - |
|**D**|Debug.ListMemory|
|**Savcı**|Debug.ListBellek /Ansi|
|**Db**|Debug.ListBellek /Biçim:OneByte|
|**Dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**Dd**|Debug.ListBellek /Biçim:FourBytes|
|**Df**|Debug.ListMemory /Format:Float|
|**Dq**|Debug.ListBellek /Biçim:EightBytes|
|**Du**|Hata Ayıklama.ListBellek /Unicode|

## <a name="example"></a>Örnek

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Liste Çağrı Yığını Komutu](../../ide/reference/list-call-stack-command.md)
- [Liste Konuları Komutu](../../ide/reference/list-threads-command.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
