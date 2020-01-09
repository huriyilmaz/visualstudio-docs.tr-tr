---
title: -Project (devenv.exe)
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4b57a5bd51ff20de8da87798aa398db04bc1c7d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567781"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Derleme, Temizleme, yeniden oluşturma veya dağıtma için belirtilen çözüm yapılandırması içinde tek bir projeyi tanımlar.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Gerekli. Çözüm dosyasının tam yolu ve adı.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Gerekli. Projeyi [oluşturur](build-devenv-exe.md), [temizler](clean-devenv-exe.md), [dağıtır](deploy-devenv-exe.md)veya yeniden [oluşturur](rebuild-devenv-exe.md) .

- *SolnConfigName*

  İsteğe bağlı. *SolutionName*içinde adlı çözüme uygulanan çözüm yapılandırmasının adı (örneğin, `Debug` veya `Release`). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu bağımsız değişken belirtilmemişse veya boş bir dize (`""`) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig` *Projconfigname*

  İsteğe bağlı. Adlı `/Project` uygulanacak projenin derleme yapılandırma adı (`Debug` veya `Release`gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`).

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Bir `devenv` `/Build`, `/Clean`, `/Rebuild`veya `/Deploy` komutunun bir parçası kullanılmalıdır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya `/Out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, `MySolution`içinde `Debug` proje derleme yapılandırması kullanarak proje `CSharpWinApp`oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv. exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
