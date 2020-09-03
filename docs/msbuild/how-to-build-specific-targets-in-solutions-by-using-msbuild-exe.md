---
title: Çözümlerde belirli hedefleri derlemek için MSBuild.exe kullanma
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633934"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Nasıl yapılır: MSBuild.exe kullanarak çözümlerde belirli hedefleri derleme

Bir çözümde belirli projelerin belirli hedeflerini oluşturmak için *MSBuild.exe* kullanabilirsiniz.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Bir çözümde belirli bir projenin belirli bir hedefini oluşturmak için

1. Komut satırında, `MSBuild.exe <SolutionName>.sln` , `<SolutionName>` çalıştırmak istediğiniz hedefi içeren çözümün dosya adına karşılık gelen yazın.

2. Şu biçimdeki anahtardan sonra hedefi belirtin `-target:` \<ProjectName> : \<TargetName> . Proje adı,,,,,, veya karakterlerinden herhangi birini içeriyorsa,,,,,, `%` `$` veya karakterlerini `@` `;` `.` `(` `)` `'` `_` belirtilen hedef adında bir ile değiştirin.

## <a name="example"></a>Örnek

 Aşağıdaki örnek `Rebuild` projenin hedefini yürütür `NotInSlnFolder` ve ardından `Clean` `InSolutionFolder` *newfolder* çözüm klasöründe bulunan projenin hedefini yürütür.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Sorun giderme

Sizin için kullanılabilir seçenekleri incelemek isterseniz, MSBuild tarafından sağlanan bir hata ayıklama seçeneğini kullanabilirsiniz. Ortam değişkenini ayarlayın `MSBUILDEMITSOLUTION=1` ve çözümünüzü derleyin. Bu işlem, derleme zamanında çözümün, MSBuild 'in iç görünümünü gösteren * \<SolutionName> . sln. metaproj* adlı bir MSBuild dosyası oluşturur. Bu görünümü, hangi hedeflerin derleme için kullanılabilir olduğunu belirlemek için inceleyebilirsiniz.

Bu iç görünüme ihtiyaç duymadığınız takdirde bu ortam değişkeni kümesiyle derleme. Bu ayar, çözümünüzde proje oluşturma sorunlarına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBUILD](../msbuild/msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
