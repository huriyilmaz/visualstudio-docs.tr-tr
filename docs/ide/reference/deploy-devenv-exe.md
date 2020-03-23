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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570134"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Bir yapı veya yeniden inşa ettikten sonra bir çözüm dağıtLar. Yalnızca yönetilen kod projeleri için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. *SolutionName'de*adı geçen `Debug` çözümü `Release`oluşturmak için kullanılacak çözüm yapılandırmasının adı (veya) Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu bağımsız değişken belirtilmemişse`""`veya boş bir dize ise ( ), araç çözümün etkin yapılandırmasını kullanır.

- `/Project`*ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. Projenin görüntü adını veya *ÇözümAdı* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Adlandırılmış yapı oluştururken kullanılacak `Debug` proje `Release`yapı yapılandırmasının adları (örneğin veya) kullanılacaktır. `/Project` Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu anahtar belirtilirse, *SolnConfigName* bağımsız değişkenini geçersiz kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Belirtilen proje bir dağıtım projesi olmalıdır. Belirtilen proje bir dağıtım projesi değilse, inşa edilen proje dağıtım için geçirildiğinde, bir hatayla başarısız olur.

Çift tırnak işaretlerine boşluklar içeren dizeleri ekleyin.

Hatalar da dahil olmak üzere yapılariçin özet bilgiler **Komut** penceresinde veya [/Out](out-devenv-exe.md) anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, proje `CSharpWinApp`yapı `Release` yapılandırmasını kullanarak `MySolution`projeyi dağıtır.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Proje (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Temiz (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
