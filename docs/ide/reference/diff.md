---
title: -Diff (devenv.exe)
description: İki dosyayı karşılaştırmak için diff Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: b1a8c4c8868de187b9e9aa5183e44c29145220e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882153"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

İki dosyayı karşılaştırır. Farklar özel bir Visual Studio penceresinde görüntülenir.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *Kaynakdosya*

  Gereklidir. Karşılaştırılacak ilk dosyanın tam yolu ve adı.

- *Hedefdosya*

  Gereklidir. Karşılaştırılacak ikinci dosyanın tam yolu ve adı.

- *Kaynağıngörünenadı*

  İsteğe bağlı. İlk dosyanın görünen adı.

- *Hedefingörünenadı*

  İsteğe bağlı. İkinci dosyanın görünen adı.

## <a name="remarks"></a>Açıklamalar

IDE 'nin bir örneği zaten açıksa, dosya karşılaştırması geçerli IDE 'deki bir sekmede görüntülenir.

## <a name="example"></a>Örnek

İlk örnek, görünen adlarını değiştirmeden iki dosyayı karşılaştırır. İkinci örnek, her iki görüntü adını değiştirirken dosyaları karşılaştırır. Üçüncü ve dördüncü örnekler iki dosyayı karşılaştırır, ancak bir diğer adı yalnızca ilk dosyaya veya ikinci dosyaya uygular.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
