---
title: -Deploy (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8eeb1a03e584b0b39030ec56ca6945a2d5ced78
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570134"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Bir derleme veya yeniden derlemeden sonra bir çözüm dağıtır. Yalnızca yönetilen kod projeleri için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Gerekli. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. *SolutionName*içinde adlı çözümü oluşturmak için kullanılacak Çözüm yapılandırmasının adı (örneğin, `Debug` veya `Release`). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu bağımsız değişken belirtilmemişse veya boş bir dize (`""`) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig` *Projconfigname*

  İsteğe bağlı. Adlı `/Project` oluşturulurken kullanılacak bir proje derleme yapılandırması (`Debug` veya `Release`gibi) adları. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu anahtar belirtilmişse, *Solnconfigname* bağımsız değişkenini geçersiz kılar.

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Belirtilen proje bir dağıtım projesi olmalıdır. Belirtilen proje bir dağıtım projesi değilse, oluşturulan proje dağıtım için geçirildiğinde hata vererek başarısız olur.

Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya [/Out](out-devenv-exe.md) anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, `MySolution`içinde `Release` proje derleme yapılandırması kullanarak proje `CSharpWinApp`dağıtır.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
