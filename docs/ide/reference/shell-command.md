---
title: Kabuk Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c19f436eddb3311e3bba70420dba6067ce2a8dca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645280"
---
# <a name="shell-command"></a>Kabuk Komutu
@No__t_0 içinden çalıştırılabilir programları başlatır.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Arguments
`path`

Gerekli. Yürütülecek dosyanın yolu ve dosya adı ya da açılacak belge. Belirtilen dosya yol ortam değişkeninde dizinlerden birinde değilse tam yol gereklidir.

`args`

İsteğe bağlı. Çağrılan programa geçirilecek herhangi bir bağımsız değişken.

## <a name="switches"></a>Anahtarlar
/CommandWindow [veya]/Command [veya]/c [veya]/cmd

İsteğe bağlı. Yürütülebilir dosyanın çıktısının **komut** penceresinde görüntülendiğini belirtir.

/dir: `folder` [veya]/d: `folder`

İsteğe bağlı. Program çalıştırıldığında ayarlanacak çalışma dizinini belirtir.

/OutputWindow [veya]/output [veya]/Out [veya]/o

İsteğe bağlı. Yürütülebilir dosyanın çıktısının **Çıkış** penceresinde görüntülendiğini belirtir.

## <a name="remarks"></a>Açıklamalar
/Dir/o/c anahtarlarının `Tools.Shell` hemen sonra belirtilmesi gerekir. Yürütülebilir dosyanın adından sonra belirtilen her şey, komut satırı bağımsız değişkenleri olarak kendisine geçirilir.

Önceden tanımlanmış diğer ad `Shell` `Tools.Shell` yerine kullanılabilir.

> [!CAUTION]
> @No__t_0 bağımsız değişkeni, dizin yolunu ve dosya adını sağlarsa, aşağıdaki gibi tüm yol adını sabit tırnak ("" ") içine almalısınız:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Her üç çift tırnak ("" ") kümesi, `Shell` işlemcisi tarafından tek bir çift tırnak karakteri olarak yorumlanır. Bu nedenle, önceki örnek `Shell` komutuna aşağıdaki yol dizesini geçirir:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Yol dizesini değişmez tırnak işaretleri ("" ") içine aldıysanız, Windows yalnızca ilk alana kadar olan dizenin kısmını kullanır. Örneğin, yukarıdaki yol dizesi düzgün şekilde alıntılanmışsa Windows, C:\ dizininde bulunan "program" adlı bir dosya arar. kök dizin. Bir C:\Program.exe yürütülebilir dosyası gerçekten kullanılabilir ise, Windows 'un bu şekilde yüklendiğine karşın, Windows bu programı istenen "c:\Program Files\SomeFile.exe" programının yerine yürütmeye çalışır.

## <a name="example"></a>Örnek
Aşağıdaki komut, dosya `MyText.txt` `Text` klasöre kopyalamak için xcopy. exe ' yi kullanır. Xcopy. exe ' den alınan çıkış, hem **komut penceresinde** hem de **Çıkış** penceresinde görüntülenir.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Çıktı Penceresi](../../ide/reference/output-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)