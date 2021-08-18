---
title: -Project (devenv.exe)
description: Projeyi derlemek, temizlemek Project yeniden derlemek veya dağıtmak için belirtilen çözüm yapılandırmasında tek bir projeyi tanımlamak için Project devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5be70c47759831c452e513ab2a4d4432840c1022
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123833"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Derlemek, temizlemek, yeniden derlemek veya dağıtmak için belirtilen çözüm yapılandırmasında tek bir projeyi tanımlar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Gereklidir. [Projeyi derleme,](build-devenv-exe.md) [temizleme,](clean-devenv-exe.md) [dağıtma](deploy-devenv-exe.md)veya [yeniden derleme.](rebuild-devenv-exe.md)

- *SolnConfigName*

  İsteğe bağlı. SolutionName içinde adlı çözüme uygulanan `Debug` `Release` çözüm yapılandırmasının adı (veya *gibi).* Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize () `""` ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. *SolutionName* klasöründen projenin görünen adını veya göreli yolunu proje dosyasına girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Projenin, adına uygulanacak derleme yapılandırma adı `Debug` `Release` (veya `/Project` gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ).

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- , , veya `devenv` `/Build` komutunun `/Clean` `/Rebuild` bir parçası `/Deploy` kullanılmalıdır.

- Çift tırnak içinde boşluk içeren dizeleri içine alın.

- Hatalar da dahil olmak üzere derlemelerin özet bilgileri Komut penceresinde **veya** anahtarıyla belirtilen herhangi bir günlük dosyasında `/Out` görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, içindeki proje `CSharpWinApp` derleme yapılandırmasını `Debug` kullanarak projesini derlemeye devam `MySolution` ediyor.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
