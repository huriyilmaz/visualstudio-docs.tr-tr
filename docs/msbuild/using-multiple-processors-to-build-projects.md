---
title: Projeleri derlemek için birden çok Işlemci kullanma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065b11b689189f5ad833ce642cfcfc94da06f83d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747196"
---
# <a name="use-multiple-processors-to-build-projects"></a>Projeleri derlemek için birden çok işlemci kullanma
MSBuild, birden çok işlemciyi veya birden çok çekirdekli işlemciyi olan sistemlerden yararlanabilir. Kullanılabilir her işlemci için ayrı bir yapı işlemi oluşturulur. Örneğin, sistemde dört işlemci varsa dört yapı işlemi oluşturulur. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], bu yapıları aynı anda işleyebilir ve bu nedenle genel derleme süresi azaltılır. Ancak paralel oluşturma, derleme işlemlerinin oluşma biçiminde bazı değişiklikler sunar. Bu konuda bu değişiklikler ele alınmaktadır.

## <a name="project-to-project-references"></a>Projeden projeye başvurular
 @No__t_0 bir proje oluşturmak için paralel derlemeler kullanırken bir projeden projeye (P2P) başvurusuyla karşılaştığında, başvuruyu yalnızca bir kez oluşturur. İki proje aynı P2P başvurusuna sahip ise, başvuru her bir proje için yeniden derlenmez. Bunun yerine, derleme altyapısı, kendisine bağımlı olan projelere aynı P2P başvurusunu döndürür. Aynı hedefe yönelik oturumdaki gelecekteki isteklere aynı P2P başvurusu sunulmaktadır.

## <a name="cycle-detection"></a>Döngüyü algılama
 Cycle Detection, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 ' de olduğu gibi çalışır, ancak artık [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] farklı bir zamanda veya derlemede bir döngüdeki algılamayı rapor edebilir.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Paralel derlemeler sırasında hatalar ve özel durumlar
 Paralel derlemelerde, hatalar ve özel durumlar, paralel olmayan bir derlemede olduklarından farklı zamanlarda ve bir proje oluşturmadığı zaman, diğer proje de devam eder. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], başarısız olan ve paralel olarak oluşturmakta olan herhangi bir proje derlemesini durdurmayacak. Diğer projeler, başarılı veya başarısız olana kadar derlenmeye devam eder. Ancak, <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> etkinleştirildiyse bir hata oluşsa bile hiçbir derleme durdurulur.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++Proje (. vcxproj) ve çözüm (. sln) dosyaları
 @No__t_0 projeler ( *. vcxproj*) ve çözüm ( *. sln*) dosyaları [MSBuild görevine](../msbuild/msbuild-task.md)geçirilebilir. @No__t_0 projeler için, VCWrapperProject çağrılır ve sonra iç [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesi oluşturulur. @No__t_0 çözümleri için bir SolutionWrapperProject oluşturulur ve sonra iç [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesi oluşturulur. Her iki durumda da, sonuçta elde edilen proje diğer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesiyle aynı şekilde değerlendirilir.

## <a name="multi-process-execution"></a>Çok işlem yürütme
 Neredeyse tüm derleme ile ilgili etkinlikler, yol ile ilgili hataları engellemek için derleme işlemi boyunca geçerli dizinin sabit kalmasını gerektirir. Bu nedenle, birden çok dizinlerin oluşturulmasına neden olacağından [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeler farklı iş parçacıkları üzerinde çalıştırılamaz.

 Bu sorundan kaçınmak, ancak çok işlemcili derlemelerin yine de etkinleştirilmesi için, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] "işlem yalıtımı" kullanır. @No__t_0, işlem yalıtımı kullanarak, `n` sistemde kullanılabilen işlemcilerin sayısına eşit olan en fazla `n` işlem oluşturabilir. Örneğin, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] iki işlemcili bir sistemde bir çözüm oluşturduğunda, yalnızca iki derleme işlemi oluşturulur. Bu süreçler Çözümdeki tüm projeleri oluşturmak için yeniden kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Görevler](../msbuild/msbuild-tasks.md)