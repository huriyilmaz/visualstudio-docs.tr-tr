---
title: Çözümlerde MSBuild.exe hedef oluşturmak için MSBuild.exe'i kullanma
description: Çözümlerde belirli projelerin MSBuild.exe için komut satırı komut satırı kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 4aca0369b3720acaf43f39635ae0110d30f53524
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108765"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Nasıl MSBuild.exe kullanarak çözümlerde belirli hedefler MSBuild.exe

Bir *çözümdeMSBuild.exe* projelerin belirli hedeflerini derlemek içinMSBuild.exe'i kullanabilirsiniz.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Çözümde belirli bir projenin belirli bir hedefini oluşturmak için

1. Komut satırına yazın; burada, yürütmek istediğiniz hedefi `MSBuild.exe <SolutionName>.sln` `<SolutionName>` içeren çözümün dosya adına karşılık gelen yazın.

2. Anahtarın ardından `-target:` hedefi şu biçimde \<ProjectName> belirtin: \<TargetName> . Proje adı , , veya karakterlerini `%` `$` `@` içeriyorsa, bunları belirtilen hedef `;` `.` `(` `)` `'` `_` adda bir ile değiştirin.

## <a name="example"></a>Örnek

 Aşağıdaki örnek projenin hedefini yürütür ve ardından NewFolder çözüm klasöründe bulunan projenin `Rebuild` `NotInSlnFolder` `Clean` `InSolutionFolder` *hedefini* yürütür.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Sorun giderme

Kullanabileceğiniz seçenekleri incelemek için, uygulama tarafından sağlanan bir hata ayıklama seçeneğini MSBuild kullanabilirsiniz. Ortam değişkenini ayarlayın `MSBUILDEMITSOLUTION=1` ve çözümlerinizi derleme. Bu, derleme zamanında MSBuild iç görünümünü gösteren *\<SolutionName> .sln.metaproj* adlı MSBuild bir dosya üretir. Hangi hedeflerin derlemek için kullanılabilir olduğunu belirlemek için bu görünümü incelersiniz.

Bu iç görünüme ihtiyacınız yoksa, bu ortam değişkeni kümesiyle derlemeyin. Bu ayar, çözümünüzde projelerle ilgili sorunlara neden olabilir. Bunun yerine ikili [günlüğe](obtaining-build-logs-with-msbuild.md#save-a-binary-log) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
