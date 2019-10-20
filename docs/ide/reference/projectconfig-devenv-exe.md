---
title: -ProjectConfig (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc8b8640f73bc89b43a9ef80d6762e8b2a67c96
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655728"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

@No__t_0 bağımsız değişkeninde adlı projeyi derlediğinizde, temizledikten, yeniden oluşturduğunuzda veya dağıttığınızda uygulanacak bir proje derleme yapılandırması belirtir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Gerekli. Çözüm dosyasının tam yolu ve adı.

- {`/Build` | `/Clean` | `/Deploy` | `/Rebuild`}

  Gerekli. Projeyi [oluşturur](build-devenv-exe.md), [temizler](clean-devenv-exe.md), [dağıtır](deploy-devenv-exe.md)veya yeniden [oluşturur](rebuild-devenv-exe.md) .

- *SolnConfigName*

  İsteğe bağlı. *SolutionName*içinde adlı çözüme uygulanacak Çözüm yapılandırmasının adı (örneğin, `Debug` veya `Release`). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu bağımsız değişken belirtilmemişse veya boş bir dize (`""`) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig` *Projconfigname*

  İsteğe bağlı. Adlı `/Project` uygulanacak projenin derleme yapılandırma adı (`Debug` veya `Release` gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`).

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

@No__t_0 anahtarı, `/Build`,/`Clean`, `/Deploy` veya `/Rebuild` komutunun bir parçası olarak `/Project` anahtarla kullanılmalıdır.

Boşluk içeren dizeleri çift tırnak içine alın.

Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, komut penceresinde veya `/Out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Aşağıdaki komut, `MySolution` içinde `Debug` proje derleme yapılandırması kullanarak proje `CSharpWinApp` oluşturur:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)