---
title: Proje Oluşturmak için Birden Çok İşlemci Kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631308"
---
# <a name="use-multiple-processors-to-build-projects"></a>Projeler oluşturmak için birden çok işlemci kullanın

MSBuild, birden çok işlemciye veya birden çok çekirdekli işlemciye sahip sistemlerden yararlanabilir. Kullanılabilir her işlemci için ayrı bir yapı işlemi oluşturulur. Örneğin, sistemin dört işlemcisi varsa, dört yapı işlemi oluşturulur. MSBuild bu yapıları aynı anda işleyebilir ve bu nedenle genel yapı süresi azalır. Ancak, paralel yapı, yapı işlemlerinin nasıl oluştuğunda bazı değişiklikler sunar. Bu konu bu değişiklikleri tartışır.

## <a name="project-to-project-references"></a>Projeden projeye başvurular

 Microsoft Build Engine, proje oluşturmak için paralel yapılar kullanırken projeden projeye (P2P) bir başvuruyla karşılaştığında, başvuruyu yalnızca bir kez oluşturur. İki proje aynı P2P başvurusuna sahipse, başvuru her proje için yeniden oluşturulmaz. Bunun yerine, yapı motoru ona bağlı her iki projeye aynı P2P başvuru verir. Aynı hedef için oturumda gelecekteki istekler aynı P2P başvuru sağlanır.

## <a name="cycle-detection"></a>Döngü algılama

 Döngü algılama işlevleri, MSBuild 2.0'da olduğu gibi, ancak artık MSBuild döngünün algılanmasını farklı bir zamanda veya yapıda bildirebilir.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Paralel yapılar sırasında hatalar ve özel durumlar

 Paralel yapılarda, hatalar ve özel durumlar, paralel olmayan bir yapıda olduğundan farklı zamanlarda oluşabilir ve bir proje oluşturmadığında, diğer proje oluşturma devam eder. MSBuild başarısız olana paralel olarak inşa eden herhangi bir proje inşasını durdurmaz. Diğer projeler başarılı olana veya başarısız olana kadar inşa etmeye devam ederler. Ancak, <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> etkinleştirildiyse, bir hata oluşsa bile hiçbir yapı durdurulmaz.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++ projesi (.vcxproj) ve çözüm (.sln) dosyaları

 Hem C++ projeleri (*.vcxproj*) hem de çözüm (*.sln*) dosyaları [MSBuild görevine](../msbuild/msbuild-task.md)geçirilebilir. C++ projeleri için VCWrapperProject çağrılır ve ardından dahili MSBuild projesi oluşturulur. C++ çözümleri için bir SolutionWrapperProject oluşturulur ve ardından dahili MSBuild projesi oluşturulur. Her iki durumda da, ortaya çıkan proje diğer MSBuild projesiyle aynı şekilde işlem görene.

## <a name="multi-process-execution"></a>Çok işlemli yürütme

 Yapıyla ilgili etkinliklerin hemen hemen tümü, yolla ilgili hataları önlemek için geçerli dizinin yapı işlemi boyunca sabit kalmasını gerektirir. Bu nedenle, birden çok dizin oluşturulmasına neden olacağından, projeler MSBuild'te farklı iş parçacıkları üzerinde çalıştırılamaz.

 Bu sorunu önlemek için ancak yine de çok işlemcili yapılar etkinleştirmek için, MSBuild "işlem yalıtımı" kullanır. MSBuild, işlem yalıtımı kullanarak, `n` sistemde bulunan `n` işlemci sayısına eşit olan maksimum işlem oluşturabilir. Örneğin, MSBuild iki işlemcisi olan bir sistemde bir çözüm oluşturursa, yalnızca iki yapı işlemi oluşturulur. Bu işlemler, çözümdeki tüm projeleri oluşturmak için yeniden kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Görevler](../msbuild/msbuild-tasks.md)
