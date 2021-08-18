---
title: Dosya adı uzantıları için fiiller kaydetme | Microsoft Docs
description: Bir kabuk anahtarı kullanarak bir dosya adı uzantısı için programlı tanımlayıcıyla ilişkili bir fiil kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 00359f3d7d367333af8796b8d1a6ece104287539
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124496"
---
# <a name="register-verbs-for-file-name-extensions"></a>Dosya adı uzantıları için fiilleri kaydetme
Bir dosya adı uzantısının uygulamayla ilişkilendirilmesi genellikle Kullanıcı bir dosyayı çift tıkladığında oluşan tercih edilen bir eyleme sahiptir. Bu tercih edilen eylem, eyleme karşılık gelen, örneğin açık olan bir fiil ile bağlantılıdır.

 Bir uzantı için programlı tanımlayıcı (ProgID) ile ilişkili fiilleri **HKEY_CLASSES_ROOT \{ ProgID} \Shell** konumunda bulunan kabuk anahtarını kullanarak kaydedebilirsiniz. Daha fazla bilgi için bkz. [dosya türleri](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Standart fiilleri Kaydet
 İşletim sistemi aşağıdaki standart fiilleri tanır:

- Aç

- Düzenle

- Oynama

- Yazdır

- Önizleme

  Mümkün olduğunda, standart bir fiil kaydedin. En yaygın seçim açık fiildir. Dosyayı açma ve dosyayı düzenleme arasında net bir fark varsa, düzenleme fiilini kullanın. Örneğin, bir *.htm* dosyayı açmak tarayıcıda görüntülenir, ancak bir *.htm* dosyasını düzenlediğinizde bir HTML Düzenleyicisi başlatılır. Standart fiiller, işletim sistemi yerel ayarıyla yereldir.

> [!NOTE]
> Standart fiilleri kaydederken, Open anahtarı için varsayılan değeri ayarlamayın. Varsayılan değer, menüdeki Görüntüleme dizesini içerir. İşletim sistemi bu dizeyi standart fiiller için sağlar.

 Project dosyalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bir kullanıcı dosyayı açtığında yeni bir örneğini başlatmak için kaydedilmelidir. Aşağıdaki örnekte, bir proje için standart bir fiil kaydı gösterilmektedir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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

 Var olan bir örneğinde bir dosyayı açmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , BIR DDEEXEC anahtarı kaydedin. Aşağıdaki örnekte [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *. cs* dosyası için standart bir fiil kaydı gösterilmektedir.

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

## <a name="set-the-default-verb"></a>Varsayılan fiili ayarla
 varsayılan fiil, kullanıcı Windows Explorer 'da bir dosyayı çift tıkladığında yürütülen eylemdir. Varsayılan fiil, **HKEY_CLASSES_ROOT \\ *ProgID*\ Shell** anahtarı için varsayılan değer olarak belirtilen fiildir. Hiçbir değer belirtilmemişse, varsayılan fiil **HKEY_CLASSES_ROOT \\ *ProgID*\ Shell** anahtar listesinde belirtilen ilk fiildir.

> [!NOTE]
> Yan yana dağıtımda bir uzantının varsayılan fiilini değiştirmeyi planlıyorsanız, yükleme ve kaldırma üzerindeki etkiyi göz önünde bulundurun. Yükleme sırasında özgün varsayılan değerin üzerine yazılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md)
