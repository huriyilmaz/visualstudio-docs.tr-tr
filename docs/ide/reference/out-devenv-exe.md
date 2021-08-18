---
title: -Out (devenv.exe)
description: Out Devenv komut satırı anahtarını kullanarak, bir çözümü çalıştırdığınızda, çalıştırdığınızda, çıkarken, yükselttiğinizde, yapılandırdığınızda, yeniden oluşturduğunuzda, temizledikten veya dağıtırken hata, hataları ve hataları göstermek için bir dosya belirtin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: fbbb33f942bbfbafd2cc720ca436e9e951306249
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056192"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Bir çözümü [çalıştırmak](run-devenv-exe.md), [çalıştırmak ve çıkmak](runexit-devenv-exe.md), [yükseltmek](upgrade-devenv-exe.md), [derlemek](build-devenv-exe.md), [yeniden derlemek](rebuild-devenv-exe.md), [temizlemek](clean-devenv-exe.md)veya [dağıtmak](deploy-devenv-exe.md) için bir dosyayı depolamak ve göstermek için bir dosya belirtir.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Bağımsız değişkenler

- *Kısaltın*

  Gereklidir. Yürütülebilir dosya oluştururken çıkışın alınacağı dosyanın yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Varolmayan bir dosya adı belirtilmişse dosya otomatik olarak oluşturulur. Aksi takdirde dosya zaten var olur ve sonuçlar dosyanın var olan içeriğine eklenir.

Komut satırı derleme hataları, **komut** penceresinde ve **Çıkış** penceresinin çözüm Oluşturucu görünümünde görüntülenir. Bu anahtar, katılımsız derlemelerin sonuçlarını görüntülemek için yararlıdır.

## <a name="example"></a>Örnek

Bu örnek `MySolution` , dosyasını çalıştırır ve dosyaya hatalar yazar `MyErrorLog.txt` .

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
