---
title: Dosya Adı Uzantıları için Fiillerin Kaydedilmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701528"
---
# <a name="register-verbs-for-file-name-extensions"></a>Dosya adı uzantıları için fiilleri kaydetme
Bir dosya adı uzantısı ile bir uygulama ilişkisi genellikle bir kullanıcı bir dosyayı çift tıklattığında oluşan tercih edilen bir eylem vardır. Bu tercih edilen eylem, örneğin açık olan ve eyleme karşılık gelen bir fiille bağlantılıdır.

 Bir programlı tanımlayıcıyla (ProgID) ilişkili **fiilleri,\{progid}\kabuk HKEY_CLASSES_ROOT**bulunan Shell tuşunu kullanarak bir uzantı için kaydedebilirsiniz. Daha fazla bilgi için [Dosya türlerine](/windows/desktop/shell/fa-file-types)bakın.

## <a name="register-standard-verbs"></a>Standart fiilleri kaydetme
 İşletim sistemi aşağıdaki standart fiilleri tanır:

- Open

- Düzenle

- Oynama

- Yazdır

- Önizleme

  Mümkün olduğunda, standart bir fiil kaydedin. En yaygın seçim Açık fiildir. Yalnızca dosyayı açma ve dosyayı düzenleme arasında net bir fark varsa Düzenle fiilini kullanın. Örneğin, bir *.htm* dosyasını açmak tarayıcıda görüntülerken, *.htm* dosyasını düzenlemek bir HTML düzenleyicisi başlatır. Standart fiiller işletim sistemi yerellesiyle yerelleştirilmiştir.

> [!NOTE]
> Standart fiilleri kaydederken, Açık tuşu için varsayılan değeri ayarlamayın. Varsayılan değer menüdeki görüntü dizesini içerir. İşletim sistemi bu dizeyi standart fiiller için sağlar.

 Proje dosyaları, kullanıcı nın dosyayı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne zaman açtığının yeni bir örneğini başlatmak için kaydedilmelidir. Aşağıdaki örnekte, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proje için standart bir fiil kaydı gösterilmektedir.

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

 Varolan bir durumda bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]dosyayı açmak için bir DDEEXEC anahtarı kaydedin. Aşağıdaki örnekte [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs* dosyası için standart bir fiil kaydı gösterilmektedir.

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
 Varsayılan fiil, bir kullanıcı Windows Gezgini'nde bir dosyayı çift tıklattığında gerçekleştirilen eylemdir. Varsayılan fiil, **HKEY_CLASSES_ROOT\\*progid*\Shell** tuşu için varsayılan değer olarak belirtilen fiildir. Değer belirtilmemişse, varsayılan fiil **HKEY_CLASSES_ROOT\\*progid*\Shell** anahtar listesinde belirtilen ilk fiildir.

> [!NOTE]
> Yan yana dağıtımda uzantı için varsayılan fiili değiştirmeyi planlıyorsanız, yükleme ve kaldırma üzerindeki etkisini göz önünde bulundurun. Yükleme sırasında özgün varsayılan değer üzerine yazılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md)
