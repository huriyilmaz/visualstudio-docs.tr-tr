---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bb74501c15e961d8da8e1e29dd0d9979c79a305
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570095"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

İki dosyayı karşılaştırır. Farklar özel bir Visual Studio penceresinde görüntülenir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *Kaynak Dosya*

  Gereklidir. Karşılaştırılacak ilk dosyanın tam yolu ve adı.

- *Hedef Dosya*

  Gereklidir. Karşılaştırılacak ikinci dosyanın tam yolu ve adı.

- *SourceDisplayName*

  İsteğe bağlı. İlk dosyanın görüntü adı.

- *TargetDisplayName*

  İsteğe bağlı. İkinci dosyanın görüntü adı.

## <a name="remarks"></a>Açıklamalar

IDE'nin bir örneği zaten açıksa, dosya karşılaştırması geçerli IDE'deki bir sekmede görüntülenir.

## <a name="example"></a>Örnek

İlk örnek, iki dosyayı görüntü adlarını değiştirmeden karşılaştırır. İkinci örnek, her iki görüntü adlarını değiştirirken dosyaları karşılaştırır. Üçüncü ve dördüncü örnekler iki dosyayı karşılaştırır, ancak yalnızca ilk dosyaya veya ikinci dosyaya takma ad uygular.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
