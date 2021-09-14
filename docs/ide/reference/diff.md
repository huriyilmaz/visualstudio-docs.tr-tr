---
title: -Diff (devenv.exe)
description: İki dosya karşılaştırmak için Diff devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b3db029bc530cf90f48fd92901c7c55a7a0e9ae1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625892"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

İki dosyanın karşılaştırması. Farklılıklar özel bir Visual Studio görüntülenir.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SourceFile*

  Gereklidir. Karşılaştırıla ilk dosyanın tam yolu ve adı.

- *TargetFile*

  Gereklidir. Karşılaştırıla ikinci dosyanın tam yolu ve adı.

- *SourceDisplayName*

  İsteğe bağlı. İlk dosyanın görünen adı.

- *TargetDisplayName*

  İsteğe bağlı. İkinci dosyanın görünen adı.

## <a name="remarks"></a>Açıklamalar

IDE'nin bir örneği zaten açıksa, dosya karşılaştırması geçerli IDE'nin bir sekmesinde görünür.

## <a name="example"></a>Örnek

İlk örnek, görünen adlarını değiştirmeden iki dosya karşılaştırıyor. İkinci örnek, her iki görünen adı da değiştirirken dosyaları karşılar. Üçüncü ve dördüncü örneklerde iki dosya karşılaştır ancak yalnızca birinci dosyaya veya ikinci dosyaya bir diğer ad uygulanır.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
