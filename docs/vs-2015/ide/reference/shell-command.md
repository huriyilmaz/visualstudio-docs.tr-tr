---
title: Kabuk komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ad49aadf6be56fb330b883050e6a6ff893cf054a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663550"
---
# <a name="shell-command"></a>Kabuk Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

@No__t_0 içinden çalıştırılabilir programları başlatır.

## <a name="syntax"></a>Sözdizimi

```
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Arguments
 `path` gerekiyor. Yürütülecek dosyanın yolu ve dosya adı ya da açılacak belge. Belirtilen dosya yol ortam değişkeninde dizinlerden birinde değilse tam yol gereklidir.

 Isteğe bağlı `args`. Çağrılan programa geçirilecek herhangi bir bağımsız değişken.

## <a name="switches"></a>Anahtarlar
 /CommandWindow [veya]/Command [veya]/c [veya]/cmd Isteğe bağlı. Yürütülebilir dosyanın çıktısının **komut** penceresinde görüntülendiğini belirtir.

 /dir: `folder` [veya]/d: `folder` Isteğe bağlı. Program çalıştırıldığında ayarlanacak çalışma dizinini belirtir.

 /OutputWindow [veya]/output [veya]/Out [veya]/o Isteğe bağlı. Yürütülebilir dosyanın çıktısının **Çıkış** penceresinde görüntülendiğini belirtir.

## <a name="remarks"></a>Açıklamalar
 /Dir/o/c anahtarlarının `Tools.Shell` hemen sonra belirtilmesi gerekir. Yürütülebilir dosyanın adından sonra belirtilen her şey, komut satırı bağımsız değişkenleri olarak kendisine geçirilir.

 Önceden tanımlanmış diğer ad `Shell` `Tools.Shell` yerine kullanılabilir.

> [!CAUTION]
> @No__t_0 bağımsız değişkeni, dizin yolunu ve dosya adını sağlarsa, aşağıdaki gibi tüm yol adını sabit tırnak ("" ") içine almalısınız:

```
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Her üç çift tırnak ("" ") kümesi, `Shell` işlemcisi tarafından tek bir çift tırnak karakteri olarak yorumlanır. Bu nedenle, önceki örnek `Shell` komutuna aşağıdaki yol dizesini geçirir:

```
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Yol dizesini değişmez tırnak işaretleri ("" ") içine aldıysanız, Windows yalnızca ilk alana kadar olan dizenin kısmını kullanır. Örneğin, yukarıdaki yol dizesi düzgün şekilde alıntılanmışsa Windows, C:\ dizininde bulunan "program" adlı bir dosya arar. kök dizin. Bir C:\Program.exe yürütülebilir dosyası gerçekten kullanılabilir ise, Windows 'un bu şekilde yüklendiğine karşın, Windows bu programı istenen "c:\Program Files\SomeFile.exe" programının yerine yürütmeye çalışır.

## <a name="example"></a>Örnek
 Aşağıdaki komut, dosya `MyText.txt` `Text` klasöre kopyalamak için xcopy. exe ' yi kullanır. Xcopy. exe ' den alınan çıkış, hem **komut penceresinde** hem de **Çıkış** penceresinde görüntülenir.

```
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Çıkış penceresi](../../ide/reference/output-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
