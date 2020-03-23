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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567781"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Oluşturmak, temizlemek, yeniden oluşturmak veya dağıtmak için belirtilen çözüm yapılandırması içinde tek bir proje tanımlar.

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

  İsteğe bağlı. *SolutionName'de*adı geçen `Debug` çözüme uygulanan çözüm yapılandırmasının adı (örneğin veya) `Release` Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu bağımsız değişken belirtilmemişse`""`veya boş bir dize ise ( ), araç çözümün etkin yapılandırmasını kullanır.

- `/Project`*ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. Projenin görüntü adını veya *ÇözümAdı* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Projenin yapı yapılandırma adı (gibi `Debug` `Release`veya) `/Project` adlandırılmış uygulanacak. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ).

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Bir , , `devenv` `/Build` `/Clean` `/Rebuild`, veya `/Deploy` komutun bir parçası kullanılmalıdır.

- Çift tırnak işaretlerine boşluklar içeren dizeleri ekleyin.

- Hatalar da dahil olmak üzere yapılariçin özet bilgiler **Komut** penceresinde veya `/Out` anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, proje `CSharpWinApp`yapı `Debug` yapılandırmasını kullanarak `MySolution`projeyi oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Temiz (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
