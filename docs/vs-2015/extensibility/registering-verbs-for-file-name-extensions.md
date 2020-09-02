---
title: Dosya adı uzantıları için fiiller kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685277"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Dosya Adı Uzantıları için Fiil Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir dosya adı uzantısının uygulamayla ilişkilendirilmesi genellikle Kullanıcı bir dosyayı çift tıkladığında oluşan tercih edilen bir eyleme sahiptir. Bu tercih edilen eylem, eyleme karşılık gelen, örneğin açık olan bir fiil ile bağlantılıdır.  
  
 Bir uzantı için programlı tanımlayıcı (ProgID) ile ilişkili fiilleri, HKEY_CLASSES_ROOT \\ *ProgID*\ Shellkonumunda bulunan kabuk anahtarını kullanarak kaydedebilirsiniz. Daha fazla bilgi için bkz. [dosya türleri](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Standart fiilleri kaydetme  
 İşletim sistemi aşağıdaki standart fiilleri tanır:  
  
- Açık  
  
- Düzenle  
  
- Oynama  
  
- Yazdırma  
  
- Önizleme  
  
  Mümkün olduğunda, standart bir fiil kaydedin. En yaygın seçim açık fiildir. Dosyayı açma ve dosyayı düzenleme arasında net bir fark varsa, düzenleme fiilini kullanın. Örneğin, bir. htm dosyasını açmak tarayıcıda görüntüler, ancak bir. htm dosyasını düzenlediğinizde bir HTML Düzenleyicisi başlatılır. Standart fiiller, işletim sistemi yerel ayarıyla yereldir.  
  
> [!NOTE]
> Standart fiilleri kaydederken, Open anahtarı için varsayılan değeri ayarlamayın. Varsayılan değer, menüdeki Görüntüleme dizesini içerir. İşletim sistemi bu dizeyi standart fiiller için sağlar.  
  
 Proje dosyaları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir Kullanıcı dosyayı açtığında yeni bir örneğini başlatmak için kaydedilmelidir. Aşağıdaki örnekte, bir proje için standart bir fiil kaydı gösterilmektedir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
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
  
 Var olan bir örneğinde bir dosyayı açmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , BIR DDEEXEC anahtarı kaydedin. Aşağıdaki örnekte. cs dosyası için standart bir fiil kaydı gösterilmektedir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
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
  
## <a name="setting-the-default-verb"></a>Varsayılan fiil ayarlanıyor  
 Varsayılan fiil, bir Kullanıcı Windows Gezgini 'nde bir dosyayı çift tıkladığında yürütülen eylemdir. Varsayılan fiil, HKEY_CLASSES_ROOT \\ *ProgID*\ Shell anahtarı için varsayılan değer olarak belirtilen fiildir. Hiçbir değer belirtilmemişse, varsayılan fiil HKEY_CLASSES_ROOT \\ *ProgID*\ Shell anahtar listesinde belirtilen ilk fiildir.  
  
> [!NOTE]
> Yan yana dağıtımda bir uzantının varsayılan fiilini değiştirmeyi planlıyorsanız, yükleme ve kaldırma üzerindeki etkiyi göz önünde bulundurun. Yükleme sırasında özgün varsayılan değerin üzerine yazılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yan Yana Dosya İlişkilendirmelerini Yönetme](../extensibility/managing-side-by-side-file-associations.md)
