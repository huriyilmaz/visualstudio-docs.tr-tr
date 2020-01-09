---
title: -Rebuild (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76fe4bcf3441163604d93e9264ed6f78fcf0224b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565623"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Belirtilen çözüm yapılandırmasını temizler ve oluşturur.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Gerekli. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. *SolutionName*içinde adlı çözümü yeniden derlemek için kullanılacak Çözüm yapılandırmasının adı (örneğin, `Debug` veya `Release`). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu bağımsız değişken belirtilmemişse veya boş bir dize (`""`) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig` *Projconfigname*

  İsteğe bağlı. Adlı `/Project` yeniden oluşturulurken kullanılacak projenin derleme yapılandırma adı (`Debug` veya `Release`gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu anahtar belirtilmişse, *Solnconfigname* bağımsız değişkenini geçersiz kılar.

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Bu anahtar, IDE içindeki **çözümü yeniden derle** menü komutuyla aynı şeyi yapar.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Temizleme ve oluşturma için hatalar da dahil olmak üzere Özet bilgiler, **komut** penceresinde veya [/Out](out-devenv-exe.md) anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, `MySolution`içinde `Debug` proje derleme yapılandırması kullanılarak proje `CSharpWinApp`temizler ve yeniden oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
