---
title: Çözümlerdeki belirli hedefleri derlemek için MSBuild. exe ' yi kullanma
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
ms.openlocfilehash: 921b5d2d4aad7cfe48b7f6cc9cb802fde9520e19
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585264"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Nasıl yapılır: MSBuild. exe kullanarak çözümlerde belirli hedefleri derleme
Bir çözümde belirli projelerin belirli hedeflerini oluşturmak için *MSBuild. exe* ' yi kullanabilirsiniz.

#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Bir çözümde belirli bir projenin belirli bir hedefini oluşturmak için

1. Komut satırında `MSBuild.exe <SolutionName>.sln`yazın; burada `<SolutionName>` yürütmek istediğiniz hedefi içeren çözümün dosya adına karşılık gelir.

2. `-target:` anahtar \<ProjectName >:\<TargetName > biçiminde bir hedef belirtin. Proje adı `%`, `$`, `@`, `;`, `.`, `(`, `)`veya `'`karakterlerinden birini içeriyorsa, bunları belirtilen hedef adında bir `_` ile değiştirin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `NotInSlnFolder` projenin `Rebuild` hedefini yürütür ve sonra *newfolder* çözüm klasöründe bulunan `InSolutionFolder` projesinin `Clean` hedefini yürütür.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Sorun giderme

Sizin için kullanılabilir seçenekleri incelemek isterseniz, MSBuild tarafından sağlanan bir hata ayıklama seçeneğini kullanabilirsiniz. `MSBUILDEMITSOLUTION=1` ortam değişkenini ayarlayın ve çözümünüzü derleyin. Bu işlem, derleme zamanında çözümün, MSBuild 'in iç görünümünü gösteren *\<SolutionName >. sln. metaproj* adlı bir MSBuild dosyası oluşturur. Bu görünümü, hangi hedeflerin derleme için kullanılabilir olduğunu belirlemek için inceleyebilirsiniz.

Bu iç görünüme ihtiyaç duymadığınız takdirde bu ortam değişkeni kümesiyle derleme. Bu ayar, çözümünüzde proje oluşturma sorunlarına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
