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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565623"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Belirtilen çözüm yapılandırmasını temizler ve oluşturur.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. *SolutionName'de*adı geçen `Debug` çözümü `Release`yeniden oluşturmak için kullanılacak çözüm yapılandırmasının adı (örneğin veya) kullanılacaktır. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu bağımsız değişken belirtilmemişse`""`veya boş bir dize ise ( ), araç çözümün etkin yapılandırmasını kullanır.

- `/Project`*ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. Projenin görüntü adını veya *ÇözümAdı* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Projenin yapı yapılandırma adı (örneğin `Debug` `Release`veya) `/Project` adlandırılmış yeniden oluştururken kullanılacak. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu anahtar belirtilirse, *SolnConfigName* bağımsız değişkenini geçersiz kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Bu anahtar, IDE içindeki **Çözüm Oluşturma** menüsüyle aynı şeyi yapar.

- Çift tırnak işaretlerine boşluklar içeren dizeleri ekleyin.

- Hatalar da dahil olmak üzere temizlik ve bina için özet bilgiler **Komut** penceresinde veya [/Out](out-devenv-exe.md) anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, proje yapı `CSharpWinApp`yapılandırmasını `Debug` kullanarak `MySolution`projeyi temizler ve yeniden oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Temiz (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
