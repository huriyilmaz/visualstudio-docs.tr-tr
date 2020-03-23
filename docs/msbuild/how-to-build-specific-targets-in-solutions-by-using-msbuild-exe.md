---
title: Çözümlerde belirli hedefler oluşturmak için MSBuild.exe'yi kullanın
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 178dfcaf0bdf8296fd271cb7c4e5dd0bbd251d7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633934"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Nasıl kullanılır: MSBuild.exe kullanarak çözümlerde belirli hedefler oluşturun

Bir çözümde belirli projelerin belirli hedeflerini oluşturmak için *MSBuild.exe'yi* kullanabilirsiniz.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Çözümde belirli bir projenin belirli bir hedefini oluşturmak için

1. Komut satırında, `MSBuild.exe <SolutionName>.sln`yürütmek `<SolutionName>` istediğiniz hedefi içeren çözümün dosya adına karşılık gelen , yazın.

2. ProjectName> `-target:` biçimindeki \<anahtardan sonra\<hedefi belirtin: TargetName>. `%`Proje `$`adı, karakterlerden herhangi birini `@`içeriyorsa, `)`, `'` `;` `.` `(`, , `_` , , , veya , bunları belirtilen hedef addaki bir adla değiştirin.

## <a name="example"></a>Örnek

 Aşağıdaki `Rebuild` örnek, `NotInSlnFolder` projenin hedefini yürütür ve ardından `Clean` *NewFolder* `InSolutionFolder` çözüm klasöründe bulunan projenin hedefini yürütür.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Sorun giderme

Kullanabileceğiniz seçenekleri incelemek isterseniz, bunu yapmak için MSBuild tarafından sağlanan hata ayıklama seçeneğini kullanabilirsiniz. Ortam değişkenini `MSBUILDEMITSOLUTION=1` ayarlayın ve çözümünüzü oluşturun. Bu, MsBuild'in oluşturma zamanında çözümün dahili görünümünü gösteren * \<SolutionName>.sln.metaproj* adlı bir MSBuild dosyası oluşturur. Hangi hedeflerin oluşturabileceğini belirlemek için bu görünümü inceleyebilirsiniz.

Bu iç görünüme ihtiyacınız olmadıkça bu ortam değişken kümesi ile oluşturmayın. Bu ayar, çözümünüzde proje oluşturmada sorunlara neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
