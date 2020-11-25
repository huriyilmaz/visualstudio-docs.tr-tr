---
title: -ProjectConfig (devenv.exe)
description: Projeyi derlediğinizde, temizledikten, yeniden oluşturduğunuzda veya dağıtırken uygulanacak bir proje derleme yapılandırması belirtmek için ProjectConfig Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06c6f98e9d022a7b253fdd0ea25a60ff01a4d756
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040075"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Bağımsız değişkende adlı projeyi derlediğinizde, temizledikten, yeniden oluşturduğunuzda veya dağıttığınızda uygulanacak bir proje derleme yapılandırması belirtir `/Project` .

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Gereklidir. Projeyi [oluşturur](build-devenv-exe.md), [temizler](clean-devenv-exe.md), [dağıtır](deploy-devenv-exe.md)veya yeniden [oluşturur](rebuild-devenv-exe.md) .

- *SolnConfigName*

  İsteğe bağlı. `Debug` `Release` *SolutionName* içinde adlı çözüme uygulanacak Çözüm yapılandırmasının adı (veya gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize ( `""` ) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*Projconfigname*

  İsteğe bağlı. Ada uygulanacak projenin derleme yapılandırma adı (veya gibi `Debug` `Release` ) `/Project` . Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ).

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

`/ProjectConfig`Anahtar `/Project` `/Build` ,, `Clean` `/Deploy` veya komutunun bir parçası olarak anahtar ile birlikte kullanılmalıdır `/Rebuild` .

Boşluk içeren dizeleri çift tırnak içine alın.

Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, komut penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/Out` .

## <a name="example"></a>Örnek

Aşağıdaki komut, `CSharpWinApp` `Debug` içindeki proje yapı yapılandırmasını kullanarak projeyi oluşturur `MySolution` :

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
