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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8bb4b2860d40828a96e25ec6e6c73d947dd60c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567664"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Bağımsız değişkende adı geçen projeyi oluştururken, temizlediğinizde, yeniden inşa `/Project` ettiğinizde veya dağıtırken uygulanacak bir proje yapılandırması belirtir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Gereklidir. [Projeyi oluşturur,](build-devenv-exe.md) [temizler,](clean-devenv-exe.md) [dağıtır](deploy-devenv-exe.md)veya [yeniden oluşturur.](rebuild-devenv-exe.md)

- *SolnConfigName*

  İsteğe bağlı. *SolutionName'de*adı geçen `Debug` çözüme uygulanacak çözüm yapılandırmasının adı (örneğin veya) `Release` Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu bağımsız değişken belirtilmemişse`""`veya boş bir dize ise ( ), araç çözümün etkin yapılandırmasını kullanır.

- `/Project`*ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. Projenin görüntü adını veya *ÇözümAdı* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Projenin yapı yapılandırma adı (gibi `Debug` `Release`veya) `/Project` adlandırılmış uygulanacak. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ).

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

`/ProjectConfig` Anahtar, `/Project` anahtarla birlikte , / `/Build``Clean`, `/Deploy`veya `/Rebuild` komutun bir parçası olarak kullanılmalıdır.

Çift tırnak içinde boşluklar içeren dizeleri içine.

Hatalar da dahil olmak üzere yapılariçin özet bilgiler komut penceresinde veya `/Out` anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Aşağıdaki komut, proje `CSharpWinApp`yapı yapılandırmasını `Debug` kullanarak `MySolution`projeyi oluşturur:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Proje (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Temiz (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
