---
title: 'Nasıl yapılır: MSBuild.exe kullanarak çözümlerde belirli hedefleri derleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bfef86b8ea82077ba7fe3f753f9835c06c3380a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156653"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Nasıl Yapılır: MSBuild.exe Kullanarak Çözümlerde Belirli Hedefleri Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir çözümde belirli projelerin belirli hedeflerini oluşturmak için MSBuild.exe kullanabilirsiniz.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Bir çözümde belirli bir projenin belirli bir hedefini oluşturmak için  
  
1. Komut satırında, `MSBuild.exe <SolutionName>.sln` , `<SolutionName>` çalıştırmak istediğiniz hedefi içeren çözümün dosya adına karşılık gelen yazın.  
  
2. *ProjectName*:*hedefadı*biçimindeki **/t** anahtarından sonra hedefi belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `Rebuild` projenin hedefini yürütür `NotInSlnFolder` ve sonra `Clean` `InSolutionFolder` çözüm klasöründe bulunan projenin hedefini yürütür `NewFolder` .  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [MSBUILD](msbuild.md)  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)
