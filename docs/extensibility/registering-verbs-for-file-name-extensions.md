---
title: Dosya Adı Uzantıları için Fiilleri Kaydetme | Microsoft Docs
description: Kabuk anahtarı kullanarak bir dosya adı uzantısı için program tanımlayıcısıyla ilişkili bir fiil kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c223dea7e265d8d040d502c99ded09380e89690f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901233"
---
# <a name="register-verbs-for-file-name-extensions"></a>Dosya adı uzantıları için fiilleri kaydetme
Dosya adı uzantısının bir uygulamayla ilişkilendirmesi genellikle kullanıcı bir dosyaya çift tıkladığında oluşan tercih edilen bir eyleme sahip olur. Tercih edilen bu eylem, eyleme karşılık gelen açık gibi bir fiille bağlantılıdır.

 **\{ progid}\shell** konumunda bulunan Kabuk anahtarını kullanarak bir uzantı için program tanımlayıcısı (ProgID) ile ilişkili fiilleri HKEY_CLASSES_ROOT yapabilirsiniz. Daha fazla bilgi için bkz. [Dosya türleri.](/windows/desktop/shell/fa-file-types)

## <a name="register-standard-verbs"></a>Standart fiilleri kaydetme
 İşletim sistemi aşağıdaki standart fiilleri tanır:

- Aç

- Düzenle

- Oynama

- Yazdır

- Önizleme

  Mümkün olduğunda standart bir fiil kaydedin. En yaygın seçenek Açık fiil'tir. Fiili düzenle'yi yalnızca dosyayı açmakla dosyayı düzenlemek arasında net bir fark varsa kullanın. Örneğin, bir *.htm* dosyası açılırken tarayıcıda görüntülenirken, *.htm* bir HTML düzenleyicisi başlatılır. Standart fiiller işletim sistemi yereli ile yerelleştirilmiştir.

> [!NOTE]
> Standart fiilleri kaydederek Aç anahtarı için varsayılan değeri ayarlayacaksınız. Varsayılan değer, menüde görünen dizeyi içerir. İşletim sistemi bu dizeyi standart fiiller için sağlar.

 Kullanıcı dosyayı açtığında yeni bir örneği başlatmak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için proje dosyalarının kayıtlı olması gerekir. Aşağıdaki örnek, bir proje için standart fiil kaydını [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] göstermektedir.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Varolan bir örneğinde bir dosya açmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir DDEEXEC anahtarı kaydedin. Aşağıdaki örnek, bir .cs dosyası için standart fiil [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *kaydını* göstermektedir.

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Varsayılan fiili ayarlama
 Varsayılan fiil, kullanıcı Windows Gezgini'nde bir dosyaya çift tıkladığında yürütülen eylemdir. Varsayılan fiil, **\\ *progid*\Shell** anahtarı için varsayılan HKEY_CLASSES_ROOT belirtilen fiildir. Değer belirtilmezse varsayılan fiil, **\\ *progid*\Shell** anahtar HKEY_CLASSES_ROOT belirtilen ilk fiildir.

> [!NOTE]
> Yan yana dağıtımda bir uzantının varsayılan fiilini değiştirmeyi planlıyorsanız, yükleme ve kaldırma üzerindeki etkiyi göz önünde bulundurabilirsiniz. Yükleme sırasında özgün varsayılan değerin üzerine yazılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md)
